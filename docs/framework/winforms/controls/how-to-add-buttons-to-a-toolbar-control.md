---
title: 'Porady: dodawanie przycisków do formantu ToolBar'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- toolbars [Windows Forms], adding buttons
- ToolBar control [Windows Forms], adding buttons
- ToolBar control [Windows Forms], adding separators
- examples [Windows Forms], toolbars
- ToolBar control [Windows Forms], adding drop-down menus
ms.assetid: 78a58a8d-1041-4e38-9219-4096fa6a5c5c
ms.openlocfilehash: 1bb6de58010e70a4edafacafe3dc00b511fc63de
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182339"
---
# <a name="how-to-add-buttons-to-a-toolbar-control"></a><span data-ttu-id="8217a-102">Porady: dodawanie przycisków do formantu ToolBar</span><span class="sxs-lookup"><span data-stu-id="8217a-102">How to: Add Buttons to a ToolBar Control</span></span>
> [!NOTE]
> <span data-ttu-id="8217a-103">Formant <xref:System.Windows.Forms.ToolStrip> zastępuje i dodaje funkcjonalność <xref:System.Windows.Forms.ToolBar> do formantu; jednak <xref:System.Windows.Forms.ToolBar> formant jest zachowywany zarówno dla zgodności z powrotem i przyszłego użycia, jeśli wybierzesz.</span><span class="sxs-lookup"><span data-stu-id="8217a-103">The <xref:System.Windows.Forms.ToolStrip> control replaces and adds functionality to the <xref:System.Windows.Forms.ToolBar> control; however, the <xref:System.Windows.Forms.ToolBar> control is retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="8217a-104">Integralną częścią <xref:System.Windows.Forms.ToolBar> formantu są przyciski dodawany do niego.</span><span class="sxs-lookup"><span data-stu-id="8217a-104">An integral part of the <xref:System.Windows.Forms.ToolBar> control is the buttons you add to it.</span></span> <span data-ttu-id="8217a-105">Mogą one służyć do zapewnienia łatwego dostępu do poleceń menu lub, alternatywnie, mogą być umieszczone w innym obszarze interfejsu użytkownika aplikacji, aby udostępnić polecenia użytkownikom, które nie są dostępne w strukturze menu.</span><span class="sxs-lookup"><span data-stu-id="8217a-105">These can be used to provide easy access to menu commands or, alternately, they can be placed in another area of the user interface of your application to expose commands to your users that are not available in the menu structure.</span></span>  
  
 <span data-ttu-id="8217a-106">Poniższe przykłady zakładają, że <xref:System.Windows.Forms.ToolBar> formant został`Form1`dodany do formularza systemu Windows ( ).</span><span class="sxs-lookup"><span data-stu-id="8217a-106">The examples below assume that a <xref:System.Windows.Forms.ToolBar> control has been added to a Windows Form (`Form1`).</span></span>  
  
### <a name="to-add-buttons-programmatically"></a><span data-ttu-id="8217a-107">Aby programowo dodać przyciski</span><span class="sxs-lookup"><span data-stu-id="8217a-107">To add buttons programmatically</span></span>  
  
1. <span data-ttu-id="8217a-108">W procedurze utwórz przyciski paska <xref:System.Windows.Forms.ToolBar.Buttons%2A?displayProperty=nameWithType> narzędzi, dodając je do kolekcji.</span><span class="sxs-lookup"><span data-stu-id="8217a-108">In a procedure, create toolbar buttons by adding them to the <xref:System.Windows.Forms.ToolBar.Buttons%2A?displayProperty=nameWithType> collection.</span></span>  
  
2. <span data-ttu-id="8217a-109">Określ ustawienia właściwości dla pojedynczego przycisku, <xref:System.Windows.Forms.ToolBar.Buttons%2A> przekazując indeks przycisku za pośrednictwem właściwości.</span><span class="sxs-lookup"><span data-stu-id="8217a-109">Specify property settings for an individual button by passing the button's index via the <xref:System.Windows.Forms.ToolBar.Buttons%2A> property.</span></span>  
  
     <span data-ttu-id="8217a-110">Poniższy przykład zakłada formularz <xref:System.Windows.Forms.ToolBar> z formantu już dodane.</span><span class="sxs-lookup"><span data-stu-id="8217a-110">The example below assumes a form with a <xref:System.Windows.Forms.ToolBar> control already added.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="8217a-111">Kolekcja <xref:System.Windows.Forms.ToolBar.Buttons%2A?displayProperty=nameWithType> jest kolekcją opartą na wartości zero, więc kod powinien postępować odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="8217a-111">The <xref:System.Windows.Forms.ToolBar.Buttons%2A?displayProperty=nameWithType> collection is a zero-based collection, so code should proceed accordingly.</span></span>  
  
    ```vb  
    Public Sub CreateToolBarButtons()  
    ' Create buttons and set text property.  
       ToolBar1.Buttons.Add("One")  
       ToolBar1.Buttons.Add("Two")  
       ToolBar1.Buttons.Add("Three")  
       ToolBar1.Buttons.Add("Four")  
    ' Set properties of StatusBar panels.  
    ' Set Style property.  
       ToolBar1.Buttons(0).Style = ToolBarButtonStyle.PushButton  
       ToolBar1.Buttons(1).Style = ToolBarButtonStyle.Separator  
       ToolBar1.Buttons(2).Style = ToolBarButtonStyle.ToggleButton  
       ToolBar1.Buttons(3).Style = ToolBarButtonStyle.DropDownButton  
    ' Set the ToggleButton's PartialPush property.  
       ToolBar1.Buttons(2).PartialPush = True  
    ' Instantiate a ContextMenu component and menu items.  
    ' Set the DropDownButton's DropDownMenu property to the context menu.  
       Dim cm As New ContextMenu()  
       Dim miOne As New MenuItem("One")  
       Dim miTwo As New MenuItem("Two")  
       Dim miThree As New MenuItem("Three")  
       cm.MenuItems.Add(miOne)  
       cm.MenuItems.Add(miTwo)  
       cm.MenuItems.Add(miThree)  
       ToolBar1.Buttons(3).DropDownMenu = cm  
    ' Set the PushButton's Pushed property.  
       ToolBar1.Buttons(0).Pushed = True  
    ' Set the ToolTipText property of one of the buttons.  
       ToolBar1.Buttons(1).ToolTipText = "Button 2"  
    End Sub  
    ```  
  
    ```csharp  
    public void CreateToolBarButtons()  
    {  
       // Create buttons and set text property.  
       toolBar1.Buttons.Add("One");  
       toolBar1.Buttons.Add("Two");  
       toolBar1.Buttons.Add("Three");  
       toolBar1.Buttons.Add("Four");  
  
       // Set properties of StatusBar panels.  
       // Set Style property.  
       toolBar1.Buttons[0].Style = ToolBarButtonStyle.PushButton;  
       toolBar1.Buttons[1].Style = ToolBarButtonStyle.Separator;  
       toolBar1.Buttons[2].Style = ToolBarButtonStyle.ToggleButton;  
       toolBar1.Buttons[3].Style = ToolBarButtonStyle.DropDownButton;  
  
       // Set the ToggleButton's PartialPush property.  
       toolBar1.Buttons[2].PartialPush = true;  
  
       // Instantiate a ContextMenu component and menu items.  
       // Set the DropDownButton's DropDownMenu property to
       // the context menu.  
       ContextMenu cm = new ContextMenu();  
       MenuItem miOne = new MenuItem("One");  
       MenuItem miTwo = new MenuItem("Two");  
       MenuItem miThree = new MenuItem("Three");  
       cm.MenuItems.Add(miOne);  
       cm.MenuItems.Add(miTwo);  
       cm.MenuItems.Add(miThree);  
  
       toolBar1.Buttons[3].DropDownMenu = cm;  
       // Set the PushButton's Pushed property.  
       toolBar1.Buttons[0].Pushed = true;  
       // Set the ToolTipText property of 1 of the buttons.  
       toolBar1.Buttons[1].ToolTipText = "Button 2";  
    }  
    ```  
  
    ```cpp  
    public:  
       void CreateToolBarButtons()  
       {  
          // Create buttons and set text property.  
          toolBar1->Buttons->Add( "One" );  
          toolBar1->Buttons->Add( "Two" );  
          toolBar1->Buttons->Add( "Three" );  
          toolBar1->Buttons->Add( "Four" );  
  
          // Set properties of StatusBar panels.  
          // Set Style property.  
          toolBar1->Buttons[0]->Style = ToolBarButtonStyle::PushButton;  
          toolBar1->Buttons[1]->Style = ToolBarButtonStyle::Separator;  
          toolBar1->Buttons[2]->Style = ToolBarButtonStyle::ToggleButton;  
          toolBar1->Buttons[3]->Style = ToolBarButtonStyle::DropDownButton;  
  
          // Set the ToggleButton's PartialPush property.  
          toolBar1->Buttons[2]->PartialPush = true;  
  
          // Instantiate a ContextMenu component and menu items.  
          // Set the DropDownButton's DropDownMenu property to
          // the context menu.  
          System::Windows::Forms::ContextMenu^ cm = gcnew System::Windows::Forms::ContextMenu;  
          MenuItem^ miOne = gcnew MenuItem( "One" );  
          MenuItem^ miTwo = gcnew MenuItem( "Two" );  
          MenuItem^ miThree = gcnew MenuItem( "Three" );  
          cm->MenuItems->Add( miOne );  
          cm->MenuItems->Add( miTwo );  
          cm->MenuItems->Add( miThree );  
          toolBar1->Buttons[3]->DropDownMenu = cm;  
  
          // Set the PushButton's Pushed property.  
          toolBar1->Buttons[0]->Pushed = true;  
  
          // Set the ToolTipText property of 1 of the buttons.  
          toolBar1->Buttons[1]->ToolTipText = "Button 2";  
       }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="8217a-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8217a-112">See also</span></span>

- <xref:System.Windows.Forms.ToolBar>
- [<span data-ttu-id="8217a-113">Instrukcje: określanie ikony dla przycisku kontrolki ToolBar</span><span class="sxs-lookup"><span data-stu-id="8217a-113">How to: Define an Icon for a ToolBar Button</span></span>](how-to-define-an-icon-for-a-toolbar-button.md)
- [<span data-ttu-id="8217a-114">Instrukcje: zdarzenia wyzwalaczy menu dla przycisków kontrolki Toolbar</span><span class="sxs-lookup"><span data-stu-id="8217a-114">How to: Trigger Menu Events for Toolbar Buttons</span></span>](how-to-trigger-menu-events-for-toolbar-buttons.md)
- [<span data-ttu-id="8217a-115">ToolBar — Informacje o formancie</span><span class="sxs-lookup"><span data-stu-id="8217a-115">ToolBar Control Overview</span></span>](toolbar-control-overview-windows-forms.md)
- [<span data-ttu-id="8217a-116">ToolBar — Formant</span><span class="sxs-lookup"><span data-stu-id="8217a-116">ToolBar Control</span></span>](toolbar-control-windows-forms.md)
