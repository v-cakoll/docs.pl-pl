---
title: "Porady: zmienianie wyglądu formantu LinkLabel formularzy systemu Windows"
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
- cpp
helpviewer_keywords:
- LinkLabel properties
- LinkLabel control [Windows Forms], changing appearance of links
- links [Windows Forms], changing appearance
- examples [Windows Forms], LinkLabel control
- LinkLabel control [Windows Forms], examples
ms.assetid: fdc5854f-5162-4457-8cbe-1042feb2d132
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 42aaef183178e7170d3046b4c5daefc8647f7cc1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-change-the-appearance-of-the-windows-forms-linklabel-control"></a><span data-ttu-id="7d629-102">Porady: zmienianie wyglądu formantu LinkLabel formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="7d629-102">How to: Change the Appearance of the Windows Forms LinkLabel Control</span></span>
<span data-ttu-id="7d629-103">Można zmienić tekst wyświetlany przez <xref:System.Windows.Forms.LinkLabel> kontroli dostosowanych do różnych celów.</span><span class="sxs-lookup"><span data-stu-id="7d629-103">You can change the text displayed by the <xref:System.Windows.Forms.LinkLabel> control to suit a variety of purposes.</span></span> <span data-ttu-id="7d629-104">Na przykład jest typowym rozwiązaniem, aby poinformować użytkownika, można kliknąć przez ustawienie tekst wyświetlany w kolorze określonych podkreślony tekst.</span><span class="sxs-lookup"><span data-stu-id="7d629-104">For example, it is common practice to indicate to the user that text can be clicked by setting the text to appear in a specific color with an underline.</span></span> <span data-ttu-id="7d629-105">Po kliknięciu tekst zmienia kolor na inny kolor.</span><span class="sxs-lookup"><span data-stu-id="7d629-105">After the user clicks the text, the color changes to a different color.</span></span> <span data-ttu-id="7d629-106">Aby kontrolować to zachowanie, można ustawić pięciu różnych właściwości: <xref:System.Windows.Forms.LinkLabel.LinkBehavior%2A>, <xref:System.Windows.Forms.LinkLabel.LinkArea%2A>, <xref:System.Windows.Forms.LinkLabel.LinkColor%2A>, <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>, i <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="7d629-106">To control this behavior, you can set five different properties: the <xref:System.Windows.Forms.LinkLabel.LinkBehavior%2A>, <xref:System.Windows.Forms.LinkLabel.LinkArea%2A>, <xref:System.Windows.Forms.LinkLabel.LinkColor%2A>, <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>, and <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> properties.</span></span>  
  
### <a name="to-change-the-appearance-of-a-linklabel-control"></a><span data-ttu-id="7d629-107">Zmiana wyglądu formantu LinkLabel</span><span class="sxs-lookup"><span data-stu-id="7d629-107">To change the appearance of a LinkLabel control</span></span>  
  
1.  <span data-ttu-id="7d629-108">Ustaw <xref:System.Windows.Forms.LinkLabel.LinkColor%2A> i <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A> właściwości do kolorów ma.</span><span class="sxs-lookup"><span data-stu-id="7d629-108">Set the <xref:System.Windows.Forms.LinkLabel.LinkColor%2A> and <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A> properties to the colors you want.</span></span>  
  
     <span data-ttu-id="7d629-109">Można to zrobić albo programowo lub w czasie projektowania w **właściwości** okna.</span><span class="sxs-lookup"><span data-stu-id="7d629-109">This can be done either programmatically or at design time in the **Properties** window.</span></span>  
  
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
  
2.  <span data-ttu-id="7d629-110">Ustaw <xref:System.Windows.Forms.LinkLabel.Text%2A> właściwości odpowiedni podpis.</span><span class="sxs-lookup"><span data-stu-id="7d629-110">Set the <xref:System.Windows.Forms.LinkLabel.Text%2A> property to an appropriate caption.</span></span>  
  
     <span data-ttu-id="7d629-111">Można to zrobić albo programowo lub w czasie projektowania w **właściwości** okna.</span><span class="sxs-lookup"><span data-stu-id="7d629-111">This can be done either programmatically or at design time in the **Properties** window.</span></span>  
  
    ```vb  
    LinkLabel1.Text = "Click here to see more."  
    ```  
  
    ```csharp  
    linkLabel1.Text = "Click here to see more.";  
    ```  
  
    ```cpp  
    linkLabel1->Text = "Click here to see more.";  
    ```  
  
3.  <span data-ttu-id="7d629-112">Ustaw <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> właściwości w celu określenia, która część podpis zostanie wskazany jako łącze.</span><span class="sxs-lookup"><span data-stu-id="7d629-112">Set the <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> property to determine which part of the caption will be indicated as a link.</span></span>  
  
     <span data-ttu-id="7d629-113"><xref:System.Windows.Forms.LinkLabel.LinkArea%2A> Wartość odpowiada z <xref:System.Windows.Forms.LinkArea> zawierającego dwóch liczb, pozycję początkową znaku i liczbę znaków.</span><span class="sxs-lookup"><span data-stu-id="7d629-113">The <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> value is represented with a <xref:System.Windows.Forms.LinkArea> containing two numbers, the starting character position and the number of characters.</span></span> <span data-ttu-id="7d629-114">Można to zrobić albo programowo lub w czasie projektowania w **właściwości** okna.</span><span class="sxs-lookup"><span data-stu-id="7d629-114">This can be done either programmatically or at design time in the **Properties** window.</span></span>  
  
    ```vb  
    LinkLabel1.LinkArea = new LinkArea(6,4)  
    ```  
  
    ```csharp  
    linkLabel1.LinkArea = new LinkArea(6,4);  
    ```  
  
    ```cpp  
    linkLabel1->LinkArea = LinkArea(6,4);  
    ```  
  
4.  <span data-ttu-id="7d629-115">Ustaw <xref:System.Windows.Forms.LinkLabel.LinkBehavior%2A> właściwości <xref:System.Windows.Forms.LinkBehavior.AlwaysUnderline>, <xref:System.Windows.Forms.LinkBehavior.HoverUnderline>, lub <xref:System.Windows.Forms.LinkBehavior.NeverUnderline>.</span><span class="sxs-lookup"><span data-stu-id="7d629-115">Set the <xref:System.Windows.Forms.LinkLabel.LinkBehavior%2A> property to <xref:System.Windows.Forms.LinkBehavior.AlwaysUnderline>, <xref:System.Windows.Forms.LinkBehavior.HoverUnderline>, or <xref:System.Windows.Forms.LinkBehavior.NeverUnderline>.</span></span>  
  
     <span data-ttu-id="7d629-116">Jeśli wartość jest ustawiona na <xref:System.Windows.Forms.LinkBehavior.HoverUnderline>, część podpisu ustaleniami <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> tylko zostanie podkreślone, gdy wskaźnik znajduje się na nim.</span><span class="sxs-lookup"><span data-stu-id="7d629-116">If it is set to <xref:System.Windows.Forms.LinkBehavior.HoverUnderline>, the part of the caption determined by <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> will only be underlined when the pointer rests on it.</span></span>  
  
5.  <span data-ttu-id="7d629-117">W <xref:System.Windows.Forms.LinkLabel.LinkClicked> ustawiony program obsługi zdarzeń, <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> właściwości `true`.</span><span class="sxs-lookup"><span data-stu-id="7d629-117">In the <xref:System.Windows.Forms.LinkLabel.LinkClicked> event handler, set the <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> property to `true`.</span></span>  
  
     <span data-ttu-id="7d629-118">Po odwiedzeniu łącza, jest powszechną praktyką było zmienić jego wyglądu w jakiś sposób zazwyczaj kolorów.</span><span class="sxs-lookup"><span data-stu-id="7d629-118">When a link has been visited, it is common practice to change its appearance in some way, usually by color.</span></span> <span data-ttu-id="7d629-119">Tekst zmieni kolor określone przez <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="7d629-119">The text will change to the color specified by the <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A> property.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7d629-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7d629-120">See Also</span></span>  
 <xref:System.Windows.Forms.LinkLabel.LinkArea%2A>  
 <xref:System.Windows.Forms.LinkLabel.LinkColor%2A>  
 <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>  
 <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A>  
 [<span data-ttu-id="7d629-121">Informacje o formancie LinkLabel</span><span class="sxs-lookup"><span data-stu-id="7d629-121">LinkLabel Control Overview</span></span>](../../../../docs/framework/winforms/controls/linklabel-control-overview-windows-forms.md)  
 [<span data-ttu-id="7d629-122">Porady: łączenie z obiektu lub strony sieci Web za pomocą formantu LinkLabel formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="7d629-122">How to: Link to an Object or Web Page with the Windows Forms LinkLabel Control</span></span>](../../../../docs/framework/winforms/controls/link-to-an-object-or-web-page-with-wf-linklabel-control.md)  
 [<span data-ttu-id="7d629-123">Linklabel — formant</span><span class="sxs-lookup"><span data-stu-id="7d629-123">LinkLabel Control</span></span>](../../../../docs/framework/winforms/controls/linklabel-control-windows-forms.md)
