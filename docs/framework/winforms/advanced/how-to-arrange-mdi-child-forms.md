---
title: "Porady: aranżowanie formularzy podrzędnych MDI"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- child forms [Windows Forms], arranging
- MDI [Windows Forms], arranging child forms
ms.assetid: a0786378-3206-4ccc-898e-7d3b38cc5089
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6a0a32f6a97e02db8e395db504f36bb5270b195c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-arrange-mdi-child-forms"></a><span data-ttu-id="afa34-102">Porady: aranżowanie formularzy podrzędnych MDI</span><span class="sxs-lookup"><span data-stu-id="afa34-102">How to: Arrange MDI Child Forms</span></span>
<span data-ttu-id="afa34-103">Często aplikacje będą mieć poleceń menu Akcje, takie jak kafelka, Cascade i Rozmieść, które sterowania układem Otwórz formularzy podrzędnych MDI.</span><span class="sxs-lookup"><span data-stu-id="afa34-103">Often, applications will have menu commands for actions such as Tile, Cascade, and Arrange, which control the layout of the open MDI child forms.</span></span> <span data-ttu-id="afa34-104">Można użyć <xref:System.Windows.Forms.Form.LayoutMdi%2A> metody za pomocą jednego z <xref:System.Windows.Forms.MdiLayout> formularza nadrzędnego wartości wyliczenia do rozmieszczanie formularzy podrzędnych MDI.</span><span class="sxs-lookup"><span data-stu-id="afa34-104">You can use the <xref:System.Windows.Forms.Form.LayoutMdi%2A> method with one of the <xref:System.Windows.Forms.MdiLayout> enumeration values to rearrange the child forms in an MDI parent form.</span></span>  
  
 <span data-ttu-id="afa34-105"><xref:System.Windows.Forms.MdiLayout> Wartości wyliczenia są wyświetlane formularze podrzędne jako kaskadowych, jak rozmieszczany poziomo czy pionowo lub ikony formularza podrzędnego rozmieszczone wzdłuż dolnej części formularza MDI.</span><span class="sxs-lookup"><span data-stu-id="afa34-105">The <xref:System.Windows.Forms.MdiLayout> enumeration values display child forms as cascading, as horizontally or vertically tiled, or as child form icons arranged along the lower portion of the MDI form.</span></span> <span data-ttu-id="afa34-106">Te wartości mają ten sam efekt co polecenia systemu Windows **kaskadowo windows**, **Pokaż okna sąsiadująco**, **wyświetlanie okien skumulowany**, i **wyświetlanie pulpitu** odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="afa34-106">These values have the same effect as the Windows commands **Cascade windows**, **Show windows side by side**, **Show windows stacked**, and **Show the desktop**, respectively.</span></span>  
  
 <span data-ttu-id="afa34-107">Te metody są często używane jako procedury obsługi zdarzeń, wywoływana przez element menu <xref:System.Windows.Forms.Control.Click> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="afa34-107">Often, these methods are used as the event handlers called by a menu item's <xref:System.Windows.Forms.Control.Click> event.</span></span> <span data-ttu-id="afa34-108">W ten sposób element menu z tekstem "Kaskadowo" mogą być uwzględnione na okien podrzędnych MDI.</span><span class="sxs-lookup"><span data-stu-id="afa34-108">In this way, a menu item with the text "Cascade Windows" can have the desired effect on the MDI child windows.</span></span>  
  
### <a name="to-arrange-child-forms"></a><span data-ttu-id="afa34-109">Aby Rozmieść formularze podrzędne</span><span class="sxs-lookup"><span data-stu-id="afa34-109">To arrange child forms</span></span>  
  
1.  <span data-ttu-id="afa34-110">W metodzie, użyj <xref:System.Windows.Forms.Form.LayoutMdi%2A> metodę, aby ustawić <xref:System.Windows.Forms.MdiLayout> wyliczenia do formularza nadrzędnego MDI.</span><span class="sxs-lookup"><span data-stu-id="afa34-110">In a method, use the <xref:System.Windows.Forms.Form.LayoutMdi%2A> method to set the <xref:System.Windows.Forms.MdiLayout> enumeration for the MDI parent form.</span></span> <span data-ttu-id="afa34-111">W poniższym przykładzie użyto <xref:System.Windows.Forms.MdiLayout.Cascade?displayProperty=nameWithType> wartość wyliczenia dla okien podrzędnych MDI formularza nadrzędnego (`Form1`).</span><span class="sxs-lookup"><span data-stu-id="afa34-111">The following example uses the <xref:System.Windows.Forms.MdiLayout.Cascade?displayProperty=nameWithType> enumeration value for the child windows of the MDI parent form (`Form1`).</span></span> <span data-ttu-id="afa34-112">Wyliczenie jest używane w kodzie podczas obsługi zdarzenia <xref:System.Windows.Forms.Control.Click> zdarzenie **Kaskadowo** elementu menu.</span><span class="sxs-lookup"><span data-stu-id="afa34-112">The enumeration is used in code during the event handler for the <xref:System.Windows.Forms.Control.Click> event of the **Cascade Windows** menu item.</span></span>  
  
    ```vb  
    Protected Sub CascadeWindows_Click(ByVal sender As System.Object, ByVal e As System.EventArgs)  
       Me.LayoutMdi(System.Windows.Forms.MdiLayout.Cascade)  
    End Sub  
    ```  
  
    ```csharp  
    protected void CascadeWindows_Click(object sender, System.EventArgs e){  
       this.LayoutMdi(System.Windows.Forms.MdiLayout.Cascade);  
    }  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="afa34-113">Można również podzielić windows i windows rozmieszczenie jako ikony, zmieniając <xref:System.Windows.Forms.MdiLayout> wartość wyliczenia używane.</span><span class="sxs-lookup"><span data-stu-id="afa34-113">You can also tile windows and arranging windows as icons by changing the <xref:System.Windows.Forms.MdiLayout> enumeration value used.</span></span>  
  
2.  <span data-ttu-id="afa34-114">Jeśli używasz programu Visual C#, umieść następujący kod w Konstruktorze formularza, aby zarejestrować program obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="afa34-114">If you’re using Visual C#, place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="afa34-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="afa34-115">See Also</span></span>  
 [<span data-ttu-id="afa34-116">Aplikacje interfejsu wielu dokumentów (MDI)</span><span class="sxs-lookup"><span data-stu-id="afa34-116">Multiple-Document Interface (MDI) Applications</span></span>](../../../../docs/framework/winforms/advanced/multiple-document-interface-mdi-applications.md)  
 [<span data-ttu-id="afa34-117">Instrukcje: tworzenie formularzy nadrzędnych MDI</span><span class="sxs-lookup"><span data-stu-id="afa34-117">How to: Create MDI Parent Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md)  
 [<span data-ttu-id="afa34-118">Instrukcje: tworzenie formularzy podrzędnych MDI</span><span class="sxs-lookup"><span data-stu-id="afa34-118">How to: Create MDI Child Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-mdi-child-forms.md)  
 [<span data-ttu-id="afa34-119">Instrukcje: określanie elementu podrzędnego MDI Active</span><span class="sxs-lookup"><span data-stu-id="afa34-119">How to: Determine the Active MDI Child</span></span>](../../../../docs/framework/winforms/advanced/how-to-determine-the-active-mdi-child.md)  
 [<span data-ttu-id="afa34-120">Instrukcje: wysyłanie danych do Active MDI Child</span><span class="sxs-lookup"><span data-stu-id="afa34-120">How to: Send Data to the Active MDI Child</span></span>](../../../../docs/framework/winforms/advanced/how-to-send-data-to-the-active-mdi-child.md)
