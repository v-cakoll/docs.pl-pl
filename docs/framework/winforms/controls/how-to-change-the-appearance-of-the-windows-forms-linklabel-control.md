---
title: 'Instrukcje: zmienianie wyglądu kontrolki LinkLabel formularzy systemu Windows'
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
ms.openlocfilehash: f0a5805561509501ca38a7fec6b4731af190e3c3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59322020"
---
# <a name="how-to-change-the-appearance-of-the-windows-forms-linklabel-control"></a><span data-ttu-id="a2b5b-102">Instrukcje: zmienianie wyglądu kontrolki LinkLabel formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="a2b5b-102">How to: Change the Appearance of the Windows Forms LinkLabel Control</span></span>
<span data-ttu-id="a2b5b-103">Możesz zmienić tekst wyświetlany przez <xref:System.Windows.Forms.LinkLabel> kontroli dostosowanych do różnych celów.</span><span class="sxs-lookup"><span data-stu-id="a2b5b-103">You can change the text displayed by the <xref:System.Windows.Forms.LinkLabel> control to suit a variety of purposes.</span></span> <span data-ttu-id="a2b5b-104">Na przykład jest powszechną praktyką, aby poinformować użytkownika, czy tekst można kliknąć, ustawiając tekst wyświetlany w kolorze określonej za pomocą podkreślenia.</span><span class="sxs-lookup"><span data-stu-id="a2b5b-104">For example, it is common practice to indicate to the user that text can be clicked by setting the text to appear in a specific color with an underline.</span></span> <span data-ttu-id="a2b5b-105">Po kliknięciu tego tekstu zmienia kolor na inny kolor.</span><span class="sxs-lookup"><span data-stu-id="a2b5b-105">After the user clicks the text, the color changes to a different color.</span></span> <span data-ttu-id="a2b5b-106">Aby kontrolować to zachowanie, należy ustawić pięć różnych właściwości: <xref:System.Windows.Forms.LinkLabel.LinkBehavior%2A>, <xref:System.Windows.Forms.LinkLabel.LinkArea%2A>, <xref:System.Windows.Forms.LinkLabel.LinkColor%2A>, <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>, i <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="a2b5b-106">To control this behavior, you can set five different properties: the <xref:System.Windows.Forms.LinkLabel.LinkBehavior%2A>, <xref:System.Windows.Forms.LinkLabel.LinkArea%2A>, <xref:System.Windows.Forms.LinkLabel.LinkColor%2A>, <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>, and <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> properties.</span></span>  
  
### <a name="to-change-the-appearance-of-a-linklabel-control"></a><span data-ttu-id="a2b5b-107">Aby zmienić wygląd formantu LinkLabel</span><span class="sxs-lookup"><span data-stu-id="a2b5b-107">To change the appearance of a LinkLabel control</span></span>  
  
1. <span data-ttu-id="a2b5b-108">Ustaw <xref:System.Windows.Forms.LinkLabel.LinkColor%2A> i <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A> właściwości kolory mają.</span><span class="sxs-lookup"><span data-stu-id="a2b5b-108">Set the <xref:System.Windows.Forms.LinkLabel.LinkColor%2A> and <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A> properties to the colors you want.</span></span>  
  
     <span data-ttu-id="a2b5b-109">Można to zrobić albo programowo, albo w czasie projektowania w **właściwości** okna.</span><span class="sxs-lookup"><span data-stu-id="a2b5b-109">This can be done either programmatically or at design time in the **Properties** window.</span></span>  
  
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
  
2. <span data-ttu-id="a2b5b-110">Ustaw <xref:System.Windows.Forms.LinkLabel.Text%2A> właściwość odpowiedni podpis.</span><span class="sxs-lookup"><span data-stu-id="a2b5b-110">Set the <xref:System.Windows.Forms.LinkLabel.Text%2A> property to an appropriate caption.</span></span>  
  
     <span data-ttu-id="a2b5b-111">Można to zrobić albo programowo, albo w czasie projektowania w **właściwości** okna.</span><span class="sxs-lookup"><span data-stu-id="a2b5b-111">This can be done either programmatically or at design time in the **Properties** window.</span></span>  
  
    ```vb  
    LinkLabel1.Text = "Click here to see more."  
    ```  
  
    ```csharp  
    linkLabel1.Text = "Click here to see more.";  
    ```  
  
    ```cpp  
    linkLabel1->Text = "Click here to see more.";  
    ```  
  
3. <span data-ttu-id="a2b5b-112">Ustaw <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> właściwości w celu określenia, która część podpisu zostanie wskazany jako link.</span><span class="sxs-lookup"><span data-stu-id="a2b5b-112">Set the <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> property to determine which part of the caption will be indicated as a link.</span></span>  
  
     <span data-ttu-id="a2b5b-113"><xref:System.Windows.Forms.LinkLabel.LinkArea%2A> Wartość jest reprezentowane przez <xref:System.Windows.Forms.LinkArea> zawierający dwie liczby, począwszy od pozycji znaku i liczbę znaków.</span><span class="sxs-lookup"><span data-stu-id="a2b5b-113">The <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> value is represented with a <xref:System.Windows.Forms.LinkArea> containing two numbers, the starting character position and the number of characters.</span></span> <span data-ttu-id="a2b5b-114">Można to zrobić albo programowo, albo w czasie projektowania w **właściwości** okna.</span><span class="sxs-lookup"><span data-stu-id="a2b5b-114">This can be done either programmatically or at design time in the **Properties** window.</span></span>  
  
    ```vb  
    LinkLabel1.LinkArea = new LinkArea(6,4)  
    ```  
  
    ```csharp  
    linkLabel1.LinkArea = new LinkArea(6,4);  
    ```  
  
    ```cpp  
    linkLabel1->LinkArea = LinkArea(6,4);  
    ```  
  
4. <span data-ttu-id="a2b5b-115">Ustaw <xref:System.Windows.Forms.LinkLabel.LinkBehavior%2A> właściwości <xref:System.Windows.Forms.LinkBehavior.AlwaysUnderline>, <xref:System.Windows.Forms.LinkBehavior.HoverUnderline>, lub <xref:System.Windows.Forms.LinkBehavior.NeverUnderline>.</span><span class="sxs-lookup"><span data-stu-id="a2b5b-115">Set the <xref:System.Windows.Forms.LinkLabel.LinkBehavior%2A> property to <xref:System.Windows.Forms.LinkBehavior.AlwaysUnderline>, <xref:System.Windows.Forms.LinkBehavior.HoverUnderline>, or <xref:System.Windows.Forms.LinkBehavior.NeverUnderline>.</span></span>  
  
     <span data-ttu-id="a2b5b-116">Jeśli jest równa <xref:System.Windows.Forms.LinkBehavior.HoverUnderline>, część podpisu ustalany na podstawie <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> zostanie podkreślone tylko po zatrzymaniu na nim wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="a2b5b-116">If it is set to <xref:System.Windows.Forms.LinkBehavior.HoverUnderline>, the part of the caption determined by <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> will only be underlined when the pointer rests on it.</span></span>  
  
5. <span data-ttu-id="a2b5b-117">W <xref:System.Windows.Forms.LinkLabel.LinkClicked> ustawić programu obsługi zdarzeń <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> właściwość `true`.</span><span class="sxs-lookup"><span data-stu-id="a2b5b-117">In the <xref:System.Windows.Forms.LinkLabel.LinkClicked> event handler, set the <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> property to `true`.</span></span>  
  
     <span data-ttu-id="a2b5b-118">Po odwiedzeniu łącza jest powszechną praktyką było jej zmiany w jakiś sposób, zwykle według kolorów.</span><span class="sxs-lookup"><span data-stu-id="a2b5b-118">When a link has been visited, it is common practice to change its appearance in some way, usually by color.</span></span> <span data-ttu-id="a2b5b-119">Tekst zmieni się na kolor określony przy użyciu <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="a2b5b-119">The text will change to the color specified by the <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A> property.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a2b5b-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a2b5b-120">See also</span></span>

- <xref:System.Windows.Forms.LinkLabel.LinkArea%2A>
- <xref:System.Windows.Forms.LinkLabel.LinkColor%2A>
- <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>
- <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A>
- [<span data-ttu-id="a2b5b-121">LinkLabel, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="a2b5b-121">LinkLabel Control Overview</span></span>](linklabel-control-overview-windows-forms.md)
- [<span data-ttu-id="a2b5b-122">Instrukcje: Łączenie do obiektu lub strony za pomocą formantu LinkLabel formularzy Windows w sieci Web</span><span class="sxs-lookup"><span data-stu-id="a2b5b-122">How to: Link to an Object or Web Page with the Windows Forms LinkLabel Control</span></span>](link-to-an-object-or-web-page-with-wf-linklabel-control.md)
- [<span data-ttu-id="a2b5b-123">LinkLabel, kontrolka</span><span class="sxs-lookup"><span data-stu-id="a2b5b-123">LinkLabel Control</span></span>](linklabel-control-windows-forms.md)
