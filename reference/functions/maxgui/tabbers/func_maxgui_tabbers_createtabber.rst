.. _func_maxgui_tabbers_createtabber:

============
CreateTabber
============

CreateTabber - 

Description
===========

.. code-block:: blitzmax

    CreateTabber:TGadget(x,y,w,h,group:TGadget,style=0)

Create a Tabber gadget.

A Tabber gadget shows a list of tabs above a client area typically used for
handling multiple documents.

[ @{Event ID} | @Description
* EVENT_GADGETACTION | A new tab has been selected. Event data should contain the tab index.
]

See Also: #AddGadgetItem, #ClearGadgetItems, #ModifyGadgetItem, #SelectGadgetItem,
#RemoveGadgetItem and #SelectedGadgetItem.

Parameters
==========

Return Values
=============

Nothing.

Examples
========

.. code-block:: blitzmax

    ' createtabber.bmx
    
    Import MaxGui.Drivers
    
    Strict 
    
    Local window:TGadget
    Local tabber:TGadget
    Local document:TGadget[3]
    Local currentdocument:TGadget
    
    ' CreateDocument creates a hidden panel that fills entire tabber client area 
    
    Function CreateDocument:TGadget(tabber:TGadget)
        Local    panel:TGadget
        panel=CreatePanel(0,0,ClientWidth(tabber),ClientHeight(tabber),tabber)
        SetGadgetLayout panel,1,1,1,1
        HideGadget panel
        Return panel
    End Function
    
    ' create a default window with a tabber gadget that fills entire client area
    
    window=CreateWindow("My Window",30,20,400,300)
    
    tabber=CreateTabber(0,0,ClientWidth(window),ClientHeight(window),window)
    SetGadgetLayout tabber,1,1,1,1 
    
    ' add three items and corresponding document panels to the tabber
    
    AddGadgetItem tabber,"Document 0",False,-1,""
    AddGadgetItem tabber,"Document 1",False,-1,"Tabber Tip 1"
    AddGadgetItem tabber,"Document 2",False,-1,"tips 4 2"
    
    document[0]=CreateDocument(tabber)
    document[1]=CreateDocument(tabber)
    document[2]=CreateDocument(tabber)
    
    SetPanelColor document[0],255,200,200
    SetPanelColor document[1],200,255,200
    SetPanelColor document[2],200,200,255
    
    ' our documents start off hidden so make first one current and show
    
    currentdocument=document[0]
    ShowGadget currentdocument
    
    ' standard message loop with special tabber GADGET_ACTION handling
    
    While WaitEvent()
        Select EventID()
            Case EVENT_GADGETACTION
                If EventSource()=tabber
                    HideGadget currentdocument
                    currentdocument=document[EventData()]
                    ShowGadget currentdocument
                EndIf
            Case EVENT_WINDOWCLOSE
                End
        End Select
    Wend

See Also
========



