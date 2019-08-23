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
ms.openlocfilehash: 7e4d5a80961ae37951251dffa30cb8e75b20be27
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69955114"
---
# <a name="how-to-arrange-mdi-child-forms"></a><span data-ttu-id="19d76-102">Instrukcje: Rozmieszczanie formularzy podrzędnych MDI</span><span class="sxs-lookup"><span data-stu-id="19d76-102">How to: Arrange MDI Child Forms</span></span>
<span data-ttu-id="19d76-103">Często aplikacje będą mieć polecenia menu dla akcji, takich jak kafelki, Kaskada i rozmieszczenia, które kontrolują układ otwartych formularzy podrzędnych MDI.</span><span class="sxs-lookup"><span data-stu-id="19d76-103">Often, applications will have menu commands for actions such as Tile, Cascade, and Arrange, which control the layout of the open MDI child forms.</span></span> <span data-ttu-id="19d76-104">Możesz użyć <xref:System.Windows.Forms.Form.LayoutMdi%2A> metody z jedną <xref:System.Windows.Forms.MdiLayout> z wartości wyliczenia, aby zmienić rozmieszczenie formularzy podrzędnych w formularzu nadrzędnym MDI.</span><span class="sxs-lookup"><span data-stu-id="19d76-104">You can use the <xref:System.Windows.Forms.Form.LayoutMdi%2A> method with one of the <xref:System.Windows.Forms.MdiLayout> enumeration values to rearrange the child forms in an MDI parent form.</span></span>  
  
 <span data-ttu-id="19d76-105">Wartości <xref:System.Windows.Forms.MdiLayout> wyliczenia wyświetlają formularze podrzędne jako kaskadowe, tak jak w poziomie lub w pionie, lub jako ikony formularza podrzędnego ułożone wzdłuż dolnej części formularza MDI.</span><span class="sxs-lookup"><span data-stu-id="19d76-105">The <xref:System.Windows.Forms.MdiLayout> enumeration values display child forms as cascading, as horizontally or vertically tiled, or as child form icons arranged along the lower portion of the MDI form.</span></span> <span data-ttu-id="19d76-106">Te wartości mają ten sam efekt, co okna poleceń **kaskadowych systemu**Windows, **Pokaż okna obok siebie**, **pokazuje stosy systemu Windows**, a **także wyświetla pulpit**.</span><span class="sxs-lookup"><span data-stu-id="19d76-106">These values have the same effect as the Windows commands **Cascade windows**, **Show windows side by side**, **Show windows stacked**, and **Show the desktop**, respectively.</span></span>  
  
 <span data-ttu-id="19d76-107">Często te metody są używane jako programy obsługi zdarzeń wywoływane przez <xref:System.Windows.Forms.Control.Click> zdarzenie elementu menu.</span><span class="sxs-lookup"><span data-stu-id="19d76-107">Often, these methods are used as the event handlers called by a menu item's <xref:System.Windows.Forms.Control.Click> event.</span></span> <span data-ttu-id="19d76-108">W ten sposób element menu z tekstem "Kaskada Windows" może mieć żądany efekt w oknach podrzędnych MDI.</span><span class="sxs-lookup"><span data-stu-id="19d76-108">In this way, a menu item with the text "Cascade Windows" can have the desired effect on the MDI child windows.</span></span>  
  
### <a name="to-arrange-child-forms"></a><span data-ttu-id="19d76-109">Aby rozmieścić formularze podrzędne</span><span class="sxs-lookup"><span data-stu-id="19d76-109">To arrange child forms</span></span>  
  
1. <span data-ttu-id="19d76-110">W metodzie Użyj <xref:System.Windows.Forms.Form.LayoutMdi%2A> metody, aby <xref:System.Windows.Forms.MdiLayout> ustawić Wyliczenie dla formularza nadrzędnego MDI.</span><span class="sxs-lookup"><span data-stu-id="19d76-110">In a method, use the <xref:System.Windows.Forms.Form.LayoutMdi%2A> method to set the <xref:System.Windows.Forms.MdiLayout> enumeration for the MDI parent form.</span></span> <span data-ttu-id="19d76-111">W poniższym przykładzie użyta <xref:System.Windows.Forms.MdiLayout.Cascade?displayProperty=nameWithType> zostanie wartość wyliczenia dla okien podrzędnych nadrzędnego formularza MDI (`Form1`).</span><span class="sxs-lookup"><span data-stu-id="19d76-111">The following example uses the <xref:System.Windows.Forms.MdiLayout.Cascade?displayProperty=nameWithType> enumeration value for the child windows of the MDI parent form (`Form1`).</span></span> <span data-ttu-id="19d76-112">Wyliczenie jest używane w kodzie podczas obsługi zdarzeń dla <xref:System.Windows.Forms.Control.Click> zdarzenia elementu menu kaskadowego **systemu Windows** .</span><span class="sxs-lookup"><span data-stu-id="19d76-112">The enumeration is used in code during the event handler for the <xref:System.Windows.Forms.Control.Click> event of the **Cascade Windows** menu item.</span></span>  
  
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
    > <span data-ttu-id="19d76-113">Możesz również kafelki okna i rozmieszczać okna jako ikony, zmieniając <xref:System.Windows.Forms.MdiLayout> użytą wartość wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="19d76-113">You can also tile windows and arranging windows as icons by changing the <xref:System.Windows.Forms.MdiLayout> enumeration value used.</span></span>  
  
2. <span data-ttu-id="19d76-114">Jeśli używasz wizualizacji C#, Umieść poniższy kod w Konstruktorze formularza, aby zarejestrować procedurę obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="19d76-114">If you’re using Visual C#, place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="19d76-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="19d76-115">See also</span></span>

- [<span data-ttu-id="19d76-116">Aplikacje interfejsu wielu dokumentów (MDI)</span><span class="sxs-lookup"><span data-stu-id="19d76-116">Multiple-Document Interface (MDI) Applications</span></span>](multiple-document-interface-mdi-applications.md)
- [<span data-ttu-id="19d76-117">Instrukcje: Tworzenie formularzy nadrzędnych MDI</span><span class="sxs-lookup"><span data-stu-id="19d76-117">How to: Create MDI Parent Forms</span></span>](how-to-create-mdi-parent-forms.md)
- [<span data-ttu-id="19d76-118">Instrukcje: Tworzenie formularzy podrzędnych MDI</span><span class="sxs-lookup"><span data-stu-id="19d76-118">How to: Create MDI Child Forms</span></span>](how-to-create-mdi-child-forms.md)
- [<span data-ttu-id="19d76-119">Instrukcje: Określanie aktywnego elementu podrzędnego MDI</span><span class="sxs-lookup"><span data-stu-id="19d76-119">How to: Determine the Active MDI Child</span></span>](how-to-determine-the-active-mdi-child.md)
- [<span data-ttu-id="19d76-120">Instrukcje: Wyślij dane do aktywnego elementu podrzędnego MDI</span><span class="sxs-lookup"><span data-stu-id="19d76-120">How to: Send Data to the Active MDI Child</span></span>](how-to-send-data-to-the-active-mdi-child.md)
