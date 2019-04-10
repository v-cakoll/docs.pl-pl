---
title: 'Instrukcje: definiowanie zachowania dotyczącego zmieniania rozmiaru i pozycjonowania w podzielonym oknie'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- split windows [Windows Forms], resizing
- splitter windows [Windows Forms], resizing
- SplitContainer control [Windows Forms], resizing
ms.assetid: 9bf73f36-ed2d-4a02-b15a-0770eff4fdfa
ms.openlocfilehash: 4ed1d2a5230502bc598906da0db5164396986e66
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59217071"
---
# <a name="how-to-define-resize-and-positioning-behavior-in-a-split-window"></a><span data-ttu-id="6ff2f-102">Instrukcje: definiowanie zachowania dotyczącego zmieniania rozmiaru i pozycjonowania w podzielonym oknie</span><span class="sxs-lookup"><span data-stu-id="6ff2f-102">How to: Define Resize and Positioning Behavior in a Split Window</span></span>
<span data-ttu-id="6ff2f-103">Panele <xref:System.Windows.Forms.SplitContainer> kontroli nadają się również do bycia ze zmienionym rozmiarem i przetwarzany przez użytkowników.</span><span class="sxs-lookup"><span data-stu-id="6ff2f-103">The panels of the <xref:System.Windows.Forms.SplitContainer> control lend themselves well to being resized and manipulated by users.</span></span> <span data-ttu-id="6ff2f-104">Jednak będzie konieczny będzie Aby programistycznie sterować rozdzielacza — gdzie jest umieszczony i w jakim stopniu można go przenieść.</span><span class="sxs-lookup"><span data-stu-id="6ff2f-104">However, there will be times when you will want to programmatically control the splitter—where it is positioned and to what degree it can be moved.</span></span>  
  
 <span data-ttu-id="6ff2f-105"><xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> Właściwości i inne właściwości na <xref:System.Windows.Forms.SplitContainer> kontroli zapewniają ścisłą kontrolę nad zachowaniem interfejsu użytkownika do własnych potrzeb.</span><span class="sxs-lookup"><span data-stu-id="6ff2f-105">The <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> property and the other properties on the <xref:System.Windows.Forms.SplitContainer> control give you precise control over the behavior of your user interface to suit your needs.</span></span> <span data-ttu-id="6ff2f-106">Te właściwości są wymienione w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="6ff2f-106">These properties are listed in the following table.</span></span>  
  
|<span data-ttu-id="6ff2f-107">Nazwa</span><span class="sxs-lookup"><span data-stu-id="6ff2f-107">Name</span></span>|<span data-ttu-id="6ff2f-108">Opis</span><span class="sxs-lookup"><span data-stu-id="6ff2f-108">Description</span></span>|  
|----------|-----------------|  
|<xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A> <span data-ttu-id="6ff2f-109">property</span><span class="sxs-lookup"><span data-stu-id="6ff2f-109">property</span></span>|<span data-ttu-id="6ff2f-110">Określa, czy rozdzielacza ruchome za pomocą klawiatury lub myszy.</span><span class="sxs-lookup"><span data-stu-id="6ff2f-110">Determines if the splitter is movable by means of the keyboard or mouse.</span></span>|  
|<xref:System.Windows.Forms.SplitContainer.SplitterDistance%2A> <span data-ttu-id="6ff2f-111">property</span><span class="sxs-lookup"><span data-stu-id="6ff2f-111">property</span></span>|<span data-ttu-id="6ff2f-112">Określa odległość w pikselach pasek podziału ruchome z lewej lub górnej krawędzi.</span><span class="sxs-lookup"><span data-stu-id="6ff2f-112">Determines the distance in pixels from the left or upper edge to the movable splitter bar.</span></span>|  
|<xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> <span data-ttu-id="6ff2f-113">property</span><span class="sxs-lookup"><span data-stu-id="6ff2f-113">property</span></span>|<span data-ttu-id="6ff2f-114">Określa minimalną odległość w pikselach, że rozdzielacza mogą być przenoszone przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="6ff2f-114">Determines the minimum distance, in pixels, that the splitter can be moved by the user.</span></span>|  
  
 <span data-ttu-id="6ff2f-115">Poniższy przykład modyfikuje <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> właściwości do utworzenia efektu "przyciągania rozdzielacz"; gdy użytkownik przeciąga rozdzielacz, zwiększa się w jednostkach 10 pikseli, a nie wartość domyślna: 1.</span><span class="sxs-lookup"><span data-stu-id="6ff2f-115">The example below modifies the <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> property to create a "snapping splitter" effect; when the user drags the splitter, it increments in units of 10 pixels rather than the default 1.</span></span>  
  
### <a name="to-define-splitcontainer-resize-behavior"></a><span data-ttu-id="6ff2f-116">Aby zdefiniować zachowanie przy zmianie rozmiaru SplitContainer</span><span class="sxs-lookup"><span data-stu-id="6ff2f-116">To define SplitContainer resize behavior</span></span>  
  
1.  <span data-ttu-id="6ff2f-117">W procedurze, należy ustawić <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> właściwość żądany rozmiar, dzięki czemu uzyskuje się zachowanie "przyciąganie" rozdzielacza.</span><span class="sxs-lookup"><span data-stu-id="6ff2f-117">In a procedure, set the <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> property to the desired size, so that the 'snapping' behavior of the splitter is achieved.</span></span>  
  
     <span data-ttu-id="6ff2f-118">W poniższym przykładzie kodu w formularzu <xref:System.Windows.Forms.Form.Load> zdarzenie, podziału w ramach <xref:System.Windows.Forms.SplitContainer> kontrolki jest ustawiona na szybkie 10 pikseli po przeciągnięciu.</span><span class="sxs-lookup"><span data-stu-id="6ff2f-118">In the following code example, within the form's <xref:System.Windows.Forms.Form.Load> event, the splitter within the <xref:System.Windows.Forms.SplitContainer> control is set to jump 10 pixels when dragged.</span></span>  
  
    ```vb  
    Private Sub Form1_Load(ByVal sender As System.Object, _  
        ByVal e As System.EventArgs) Handles MyBase.Load  
        Dim splitSnapper as new SplitContainer()  
        splitSnapper.SplitterIncrement = 10  
        splitSnapper.Dock = DockStyle.Fill  
        splitSnapper.Parent = me  
    End Sub  
    ```  
  
    ```csharp  
    private void Form1_Load(System.Object sender, System.EventArgs e)  
    {  
        SplitContainer splitSnapper = new SplitContainer();  
        splitSnapper.SplitterIncrement = 10;  
        splitSnapper.Dock = DockStyle.Fill;  
        splitSnapper.Parent = this;  
    }  
    ```  
  
     <span data-ttu-id="6ff2f-119">(Visual C#) Umieść następujący kod w Konstruktorze formularza, aby zarejestrować program obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="6ff2f-119">(Visual C#) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.Load += new System.EventHandler(this.Form1_Load);  
    ```  
  
     <span data-ttu-id="6ff2f-120">Przenoszenie rozdzielacza nieco do lewej lub prawej odniesie żadnego skutku zauważalny; Gdy wskaźnik myszy przechodzi 10 pikseli w dowolnym kierunku, rozdzielacza będą przyciągane do nowej pozycji.</span><span class="sxs-lookup"><span data-stu-id="6ff2f-120">Moving the splitter slightly to the left or right will have no discernible effect; however, when the mouse pointer goes 10 pixels in either direction, the splitter will snap to the new position.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ff2f-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6ff2f-121">See also</span></span>

- <xref:System.Windows.Forms.SplitContainer>
- <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A>
