---
title: 'Instrukcje: Rozmieszczanie formularzy podrzędnych MDI'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- child forms [Windows Forms], arranging
- MDI [Windows Forms], arranging child forms
ms.assetid: a0786378-3206-4ccc-898e-7d3b38cc5089
ms.openlocfilehash: c7a9d03ef60586e1162f088d662dfe44bbdcb591
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61938115"
---
# <a name="how-to-arrange-mdi-child-forms"></a><span data-ttu-id="fc588-102">Instrukcje: Rozmieszczanie formularzy podrzędnych MDI</span><span class="sxs-lookup"><span data-stu-id="fc588-102">How to: Arrange MDI Child Forms</span></span>
<span data-ttu-id="fc588-103">Aplikacje mają często poleceń menu Akcje, takie jak kafelków, Cascade i rozmieszczanie, które sterowania układem Otwórz formularzy podrzędnych MDI.</span><span class="sxs-lookup"><span data-stu-id="fc588-103">Often, applications will have menu commands for actions such as Tile, Cascade, and Arrange, which control the layout of the open MDI child forms.</span></span> <span data-ttu-id="fc588-104">Możesz użyć <xref:System.Windows.Forms.Form.LayoutMdi%2A> metody przy użyciu jednego z <xref:System.Windows.Forms.MdiLayout> wartości wyliczenia, aby zmienić kolejność formularze podrzędne MDI nadrzędnego formularza.</span><span class="sxs-lookup"><span data-stu-id="fc588-104">You can use the <xref:System.Windows.Forms.Form.LayoutMdi%2A> method with one of the <xref:System.Windows.Forms.MdiLayout> enumeration values to rearrange the child forms in an MDI parent form.</span></span>  
  
 <span data-ttu-id="fc588-105"><xref:System.Windows.Forms.MdiLayout> Wartości wyliczenia wyświetlanie formularzy podrzędnych jako kaskadowych jako sąsiadująco w poziomie lub pionie, lub ikony formularza podrzędnego rozmieszczone wzdłuż dolnej części formularza MDI.</span><span class="sxs-lookup"><span data-stu-id="fc588-105">The <xref:System.Windows.Forms.MdiLayout> enumeration values display child forms as cascading, as horizontally or vertically tiled, or as child form icons arranged along the lower portion of the MDI form.</span></span> <span data-ttu-id="fc588-106">Te wartości mogą być taki sam skutek jak poleceń programu Windows **kaskadowo windows**, **Pokaż okna sąsiadująco**, **Pokaż okna skumulowany**, i **wyświetlanie pulpitu** , odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="fc588-106">These values have the same effect as the Windows commands **Cascade windows**, **Show windows side by side**, **Show windows stacked**, and **Show the desktop**, respectively.</span></span>  
  
 <span data-ttu-id="fc588-107">Metody te są często używane jako procedury obsługi zdarzeń, wywoływany przez element menu <xref:System.Windows.Forms.Control.Click> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="fc588-107">Often, these methods are used as the event handlers called by a menu item's <xref:System.Windows.Forms.Control.Click> event.</span></span> <span data-ttu-id="fc588-108">W ten sposób element menu z tekstem "Windows Cascade" może mieć odpowiednią wpływu na oknami podrzędnymi MDI.</span><span class="sxs-lookup"><span data-stu-id="fc588-108">In this way, a menu item with the text "Cascade Windows" can have the desired effect on the MDI child windows.</span></span>  
  
### <a name="to-arrange-child-forms"></a><span data-ttu-id="fc588-109">Aby aranżowanie formularzy podrzędnych</span><span class="sxs-lookup"><span data-stu-id="fc588-109">To arrange child forms</span></span>  
  
1. <span data-ttu-id="fc588-110">W metodzie, użyj <xref:System.Windows.Forms.Form.LayoutMdi%2A> metodę, aby ustawić <xref:System.Windows.Forms.MdiLayout> wyliczenia do formularza nadrzędnego MDI.</span><span class="sxs-lookup"><span data-stu-id="fc588-110">In a method, use the <xref:System.Windows.Forms.Form.LayoutMdi%2A> method to set the <xref:System.Windows.Forms.MdiLayout> enumeration for the MDI parent form.</span></span> <span data-ttu-id="fc588-111">W poniższym przykładzie użyto <xref:System.Windows.Forms.MdiLayout.Cascade?displayProperty=nameWithType> wartość wyliczenia okien podrzędnych formularza nadrzędnego MDI (`Form1`).</span><span class="sxs-lookup"><span data-stu-id="fc588-111">The following example uses the <xref:System.Windows.Forms.MdiLayout.Cascade?displayProperty=nameWithType> enumeration value for the child windows of the MDI parent form (`Form1`).</span></span> <span data-ttu-id="fc588-112">Wyliczenia jest używana w kodzie podczas obsługi zdarzeń dla <xref:System.Windows.Forms.Control.Click> zdarzenia **Windows Cascade** elementu menu.</span><span class="sxs-lookup"><span data-stu-id="fc588-112">The enumeration is used in code during the event handler for the <xref:System.Windows.Forms.Control.Click> event of the **Cascade Windows** menu item.</span></span>  
  
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
    >  <span data-ttu-id="fc588-113">Można również podzielić windows i windows rozmieszczenie jako ikony, zmieniając <xref:System.Windows.Forms.MdiLayout> wartość wyliczenia używane.</span><span class="sxs-lookup"><span data-stu-id="fc588-113">You can also tile windows and arranging windows as icons by changing the <xref:System.Windows.Forms.MdiLayout> enumeration value used.</span></span>  
  
2. <span data-ttu-id="fc588-114">Jeśli używasz Visual C#, umieść następujący kod w Konstruktorze formularza, aby zarejestrować program obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="fc588-114">If you’re using Visual C#, place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="fc588-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fc588-115">See also</span></span>

- [<span data-ttu-id="fc588-116">Aplikacje interfejsu wielu dokumentów (MDI)</span><span class="sxs-lookup"><span data-stu-id="fc588-116">Multiple-Document Interface (MDI) Applications</span></span>](multiple-document-interface-mdi-applications.md)
- [<span data-ttu-id="fc588-117">Instrukcje: Tworzenie formularzy nadrzędnych MDI</span><span class="sxs-lookup"><span data-stu-id="fc588-117">How to: Create MDI Parent Forms</span></span>](how-to-create-mdi-parent-forms.md)
- [<span data-ttu-id="fc588-118">Instrukcje: Tworzenie formularzy podrzędnych MDI</span><span class="sxs-lookup"><span data-stu-id="fc588-118">How to: Create MDI Child Forms</span></span>](how-to-create-mdi-child-forms.md)
- [<span data-ttu-id="fc588-119">Instrukcje: Określanie elementu podrzędnego Active MDI</span><span class="sxs-lookup"><span data-stu-id="fc588-119">How to: Determine the Active MDI Child</span></span>](how-to-determine-the-active-mdi-child.md)
- [<span data-ttu-id="fc588-120">Instrukcje: Wysyłanie danych do Active MDI Child</span><span class="sxs-lookup"><span data-stu-id="fc588-120">How to: Send Data to the Active MDI Child</span></span>](how-to-send-data-to-the-active-mdi-child.md)
