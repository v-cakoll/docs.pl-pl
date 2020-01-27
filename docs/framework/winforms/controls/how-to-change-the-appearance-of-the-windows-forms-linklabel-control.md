---
title: Zmiana wyglądu kontrolki LinkLabel
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- LinkLabel properties
- LinkLabel control [Windows Forms], changing appearance of links
- links [Windows Forms], changing appearance
- examples [Windows Forms], LinkLabel control
- LinkLabel control [Windows Forms], examples
ms.assetid: fdc5854f-5162-4457-8cbe-1042feb2d132
ms.openlocfilehash: 0b38722fb1647ea215c3bb8978dd3f54b300a0e0
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746622"
---
# <a name="how-to-change-the-appearance-of-the-windows-forms-linklabel-control"></a><span data-ttu-id="e15ec-102">Porady: zmienianie wyglądu formantu LinkLabel formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="e15ec-102">How to: Change the Appearance of the Windows Forms LinkLabel Control</span></span>
<span data-ttu-id="e15ec-103">Możesz zmienić tekst wyświetlany przez formant <xref:System.Windows.Forms.LinkLabel>, aby dopasować go do różnych celów.</span><span class="sxs-lookup"><span data-stu-id="e15ec-103">You can change the text displayed by the <xref:System.Windows.Forms.LinkLabel> control to suit a variety of purposes.</span></span> <span data-ttu-id="e15ec-104">Na przykład typowym celem jest wskazanie użytkownikowi, który tekst może być kliknięty przez ustawienie tekstu, który ma być wyświetlany w określonym kolorze z podkreśleniem.</span><span class="sxs-lookup"><span data-stu-id="e15ec-104">For example, it is common practice to indicate to the user that text can be clicked by setting the text to appear in a specific color with an underline.</span></span> <span data-ttu-id="e15ec-105">Gdy użytkownik kliknie tekst, kolor zmieni się na inny kolor.</span><span class="sxs-lookup"><span data-stu-id="e15ec-105">After the user clicks the text, the color changes to a different color.</span></span> <span data-ttu-id="e15ec-106">Aby kontrolować to zachowanie, można ustawić pięć różnych właściwości: właściwości <xref:System.Windows.Forms.LinkLabel.LinkBehavior%2A>, <xref:System.Windows.Forms.LinkLabel.LinkArea%2A>, <xref:System.Windows.Forms.LinkLabel.LinkColor%2A>, <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>i <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A>.</span><span class="sxs-lookup"><span data-stu-id="e15ec-106">To control this behavior, you can set five different properties: the <xref:System.Windows.Forms.LinkLabel.LinkBehavior%2A>, <xref:System.Windows.Forms.LinkLabel.LinkArea%2A>, <xref:System.Windows.Forms.LinkLabel.LinkColor%2A>, <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>, and <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> properties.</span></span>  
  
### <a name="to-change-the-appearance-of-a-linklabel-control"></a><span data-ttu-id="e15ec-107">Aby zmienić wygląd formantu LinkLabel</span><span class="sxs-lookup"><span data-stu-id="e15ec-107">To change the appearance of a LinkLabel control</span></span>  
  
1. <span data-ttu-id="e15ec-108">Ustaw <xref:System.Windows.Forms.LinkLabel.LinkColor%2A> i <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A> właściwości na żądane kolory.</span><span class="sxs-lookup"><span data-stu-id="e15ec-108">Set the <xref:System.Windows.Forms.LinkLabel.LinkColor%2A> and <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A> properties to the colors you want.</span></span>  
  
     <span data-ttu-id="e15ec-109">Można to zrobić programowo lub w czasie projektowania w oknie **Właściwości** .</span><span class="sxs-lookup"><span data-stu-id="e15ec-109">This can be done either programmatically or at design time in the **Properties** window.</span></span>  
  
    ```vb  
    ' You can set the color using decimal values for red, green, and blue  
    LinkLabel1.LinkColor = Color.FromArgb(0, 0, 255)  
    ' Or you can set the color using defined constants  
    LinkLabel1.VisitedLinkColor = Color.Purple  
    ```  
  
    ```csharp  
    // You can set the color using decimal values for red, green, and blue  
    linkLabel1.LinkColor = Color.FromArgb(0, 0, 255);  
    // Or you can set the color using defined constants  
    linkLabel1.VisitedLinkColor = Color.Purple;  
    ```  
  
    ```cpp  
    // You can set the color using decimal values for red, green, and blue  
    linkLabel1->LinkColor = Color::FromArgb(0, 0, 255);  
    // Or you can set the color using defined constants  
    linkLabel1->VisitedLinkColor = Color::Purple;  
    ```  
  
2. <span data-ttu-id="e15ec-110">Ustaw właściwość <xref:System.Windows.Forms.LinkLabel.Text%2A> na odpowiedni podpis.</span><span class="sxs-lookup"><span data-stu-id="e15ec-110">Set the <xref:System.Windows.Forms.LinkLabel.Text%2A> property to an appropriate caption.</span></span>  
  
     <span data-ttu-id="e15ec-111">Można to zrobić programowo lub w czasie projektowania w oknie **Właściwości** .</span><span class="sxs-lookup"><span data-stu-id="e15ec-111">This can be done either programmatically or at design time in the **Properties** window.</span></span>  
  
    ```vb  
    LinkLabel1.Text = "Click here to see more."  
    ```  
  
    ```csharp  
    linkLabel1.Text = "Click here to see more.";  
    ```  
  
    ```cpp  
    linkLabel1->Text = "Click here to see more.";  
    ```  
  
3. <span data-ttu-id="e15ec-112">Ustaw właściwość <xref:System.Windows.Forms.LinkLabel.LinkArea%2A>, aby określić, która część podpisu będzie wskazywana jako link.</span><span class="sxs-lookup"><span data-stu-id="e15ec-112">Set the <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> property to determine which part of the caption will be indicated as a link.</span></span>  
  
     <span data-ttu-id="e15ec-113">Wartość <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> jest reprezentowana przy użyciu <xref:System.Windows.Forms.LinkArea> zawierającej dwie liczby, początkową pozycję znaku i liczbę znaków.</span><span class="sxs-lookup"><span data-stu-id="e15ec-113">The <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> value is represented with a <xref:System.Windows.Forms.LinkArea> containing two numbers, the starting character position and the number of characters.</span></span> <span data-ttu-id="e15ec-114">Można to zrobić programowo lub w czasie projektowania w oknie **Właściwości** .</span><span class="sxs-lookup"><span data-stu-id="e15ec-114">This can be done either programmatically or at design time in the **Properties** window.</span></span>  
  
    ```vb  
    LinkLabel1.LinkArea = new LinkArea(6,4)  
    ```  
  
    ```csharp  
    linkLabel1.LinkArea = new LinkArea(6,4);  
    ```  
  
    ```cpp  
    linkLabel1->LinkArea = LinkArea(6,4);  
    ```  
  
4. <span data-ttu-id="e15ec-115">Ustaw właściwość <xref:System.Windows.Forms.LinkLabel.LinkBehavior%2A> na <xref:System.Windows.Forms.LinkBehavior.AlwaysUnderline>, <xref:System.Windows.Forms.LinkBehavior.HoverUnderline>lub <xref:System.Windows.Forms.LinkBehavior.NeverUnderline>.</span><span class="sxs-lookup"><span data-stu-id="e15ec-115">Set the <xref:System.Windows.Forms.LinkLabel.LinkBehavior%2A> property to <xref:System.Windows.Forms.LinkBehavior.AlwaysUnderline>, <xref:System.Windows.Forms.LinkBehavior.HoverUnderline>, or <xref:System.Windows.Forms.LinkBehavior.NeverUnderline>.</span></span>  
  
     <span data-ttu-id="e15ec-116">Jeśli jest ustawiona na <xref:System.Windows.Forms.LinkBehavior.HoverUnderline>, część podpisu określoną przez <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> zostanie podkreślona tylko wtedy, gdy wskaźnik zatrzyma się na nim.</span><span class="sxs-lookup"><span data-stu-id="e15ec-116">If it is set to <xref:System.Windows.Forms.LinkBehavior.HoverUnderline>, the part of the caption determined by <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> will only be underlined when the pointer rests on it.</span></span>  
  
5. <span data-ttu-id="e15ec-117">W obsłudze zdarzeń <xref:System.Windows.Forms.LinkLabel.LinkClicked> ustaw właściwość <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> na `true`.</span><span class="sxs-lookup"><span data-stu-id="e15ec-117">In the <xref:System.Windows.Forms.LinkLabel.LinkClicked> event handler, set the <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> property to `true`.</span></span>  
  
     <span data-ttu-id="e15ec-118">Po odwiedzeniu łącza, często można zmienić jego wygląd w jakiś sposób, zazwyczaj przez kolor.</span><span class="sxs-lookup"><span data-stu-id="e15ec-118">When a link has been visited, it is common practice to change its appearance in some way, usually by color.</span></span> <span data-ttu-id="e15ec-119">Tekst zostanie zmieniony na kolor określony przez właściwość <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>.</span><span class="sxs-lookup"><span data-stu-id="e15ec-119">The text will change to the color specified by the <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A> property.</span></span>  
  
    ```vb  
    Protected Sub LinkLabel1_LinkClicked (ByVal sender As Object, _  
       ByVal e As EventArgs) Handles LinkLabel1.LinkClicked  
       ' Change the color of the link text  
       ' by setting LinkVisited to True.  
       LinkLabel1.LinkVisited = True  
       ' Then do whatever other action is appropriate  
    End Sub  
    ```  
  
    ```csharp  
    protected void LinkLabel1_LinkClicked(object sender, System.EventArgs e)  
    {  
       // Change the color of the link text by setting LinkVisited   
       // to True.  
       linkLabel1.LinkVisited = true;  
       // Then do whatever other action is appropriate  
    }  
    ```  
  
    ```cpp  
    private:  
       System::Void linkLabel1_LinkClicked(System::Object ^  sender,  
          System::Windows::Forms::LinkLabelLinkClickedEventArgs ^  e)  
       {  
          // Change the color of the link text by setting LinkVisited   
          // to True.  
          linkLabel1->LinkVisited = true;  
          // Then do whatever other action is appropriate  
       }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="e15ec-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e15ec-120">See also</span></span>

- <xref:System.Windows.Forms.LinkLabel.LinkArea%2A>
- <xref:System.Windows.Forms.LinkLabel.LinkColor%2A>
- <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>
- <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A>
- [<span data-ttu-id="e15ec-121">LinkLabel, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="e15ec-121">LinkLabel Control Overview</span></span>](linklabel-control-overview-windows-forms.md)
- [<span data-ttu-id="e15ec-122">Instrukcje: łączenie z obiektem lub stroną internetową za pomocą kontrolki LinkLabel formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e15ec-122">How to: Link to an Object or Web Page with the Windows Forms LinkLabel Control</span></span>](link-to-an-object-or-web-page-with-wf-linklabel-control.md)
- [<span data-ttu-id="e15ec-123">LinkLabel, kontrolka</span><span class="sxs-lookup"><span data-stu-id="e15ec-123">LinkLabel Control</span></span>](linklabel-control-windows-forms.md)
