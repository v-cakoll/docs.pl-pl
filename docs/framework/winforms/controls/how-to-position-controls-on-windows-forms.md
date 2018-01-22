---
title: 'Porady: formanty pozycji na formularzach systemu Windows'
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
f1_keywords:
- Location
- Location.Y
- Location.X
helpviewer_keywords:
- controls [Windows Forms]
- controls [Windows Forms], moving
- snaplines
- controls [Windows Forms], positioning
ms.assetid: 4693977e-34a4-4f19-8221-68c3120c2b2b
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4519be86d83fce5afc7410c9f76591158ed71cb6
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-position-controls-on-windows-forms"></a><span data-ttu-id="a205c-102">Porady: formanty pozycji na formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="a205c-102">How to: Position Controls on Windows Forms</span></span>
<span data-ttu-id="a205c-103">Formanty pozycji, za pomocą projektanta formularzy systemu Windows lub określ <xref:System.Windows.Forms.Control.Location%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="a205c-103">To position controls, use the Windows Forms Designer, or specify the <xref:System.Windows.Forms.Control.Location%2A> property.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a205c-104">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="a205c-104">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="a205c-105">Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="a205c-105">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="a205c-106">Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="a205c-106">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-position-a-control-on-the-design-surface-of-the-windows-forms-designer"></a><span data-ttu-id="a205c-107">Aby umieścić kontrolkę na powierzchnię projektanta formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="a205c-107">To position a control on the design surface of the Windows Forms Designer</span></span>  
  
-   <span data-ttu-id="a205c-108">Przeciągnij kontrolki w odpowiedniej lokalizacji przy użyciu myszy.</span><span class="sxs-lookup"><span data-stu-id="a205c-108">Drag the control to the appropriate location with the mouse.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a205c-109">Wybierz kontrolkę i przenieść go z STRZAŁKĄ klucze do bardziej precyzyjne rozmieszczanie.</span><span class="sxs-lookup"><span data-stu-id="a205c-109">Select the control and move it with the ARROW keys to position it more precisely.</span></span> <span data-ttu-id="a205c-110">Ponadto *linie przyciągania* ułatwiają rozmieszczenie formantów w formularzu.</span><span class="sxs-lookup"><span data-stu-id="a205c-110">Also, *snaplines* assist you in placing controls precisely on your form.</span></span> <span data-ttu-id="a205c-111">Aby uzyskać więcej informacji, zobacz [wskazówki: rozmieszczanie formantów na formularzach systemu Windows przy użyciu linie przyciągania](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).</span><span class="sxs-lookup"><span data-stu-id="a205c-111">For more information, see [Walkthrough: Arranging Controls on Windows Forms Using Snaplines](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).</span></span>  
  
### <a name="to-position-a-control-using-the-properties-window"></a><span data-ttu-id="a205c-112">Aby umieścić kontrolkę w oknie właściwości</span><span class="sxs-lookup"><span data-stu-id="a205c-112">To position a control using the Properties window</span></span>  
  
1.  <span data-ttu-id="a205c-113">Kliknij formant, który ma zostać ustawiony.</span><span class="sxs-lookup"><span data-stu-id="a205c-113">Click the control you want to position.</span></span>  
  
2.  <span data-ttu-id="a205c-114">W **właściwości** okna, wartości typu <xref:System.Windows.Forms.Control.Location%2A> właściwości oddzielonych przecinkami, aby umieścić kontrolki wewnątrz jej kontenera.</span><span class="sxs-lookup"><span data-stu-id="a205c-114">In the **Properties** window, type values for the <xref:System.Windows.Forms.Control.Location%2A> property, separated by a comma, to position the control within its container.</span></span>  
  
     <span data-ttu-id="a205c-115">Pierwsza liczba (X) jest odległość między lewą krawędzią kontenera; Druga liczba (Y) jest odległość od górnej granicy obszaru kontenera (w pikselach).</span><span class="sxs-lookup"><span data-stu-id="a205c-115">The first number (X) is the distance from the left border of the container; the second number (Y) is the distance from the upper border of the container area, measured in pixels.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a205c-116">Można rozwinąć <xref:System.Windows.Forms.Control.Location%2A> właściwość do typu **X** i **Y** wartości pojedynczo.</span><span class="sxs-lookup"><span data-stu-id="a205c-116">You can expand the <xref:System.Windows.Forms.Control.Location%2A> property to type the **X** and **Y** values individually.</span></span>  
  
### <a name="to-position-a-control-programmatically"></a><span data-ttu-id="a205c-117">Aby programowo położenie formantu</span><span class="sxs-lookup"><span data-stu-id="a205c-117">To position a control programmatically</span></span>  
  
1.  <span data-ttu-id="a205c-118">Ustaw <xref:System.Windows.Forms.Control.Location%2A> właściwości formantu <xref:System.Drawing.Point>.</span><span class="sxs-lookup"><span data-stu-id="a205c-118">Set the <xref:System.Windows.Forms.Control.Location%2A> property of the control to a <xref:System.Drawing.Point>.</span></span>  
  
    ```vb  
    Button1.Location = New Point(100, 100)  
    ```  
  
    ```csharp  
    button1.Location = new Point(100, 100);  
    ```  
  
    ```cpp  
    button1->Location = Point(100, 100);  
    ```  
  
2.  <span data-ttu-id="a205c-119">Zmień współrzędną X lokalizacji kontrolki przy użyciu <xref:System.Windows.Forms.Control.Left%2A> podwłaściwości.</span><span class="sxs-lookup"><span data-stu-id="a205c-119">Change the X coordinate of the control's location using the <xref:System.Windows.Forms.Control.Left%2A> subproperty.</span></span>  
  
    ```vb  
    Button1.Left = 300  
    ```  
  
    ```csharp  
    button1.Left = 300;  
    ```  
  
    ```cpp  
    button1->Left = 300;  
    ```  
  
### <a name="to-increment-a-controls-location-programmatically"></a><span data-ttu-id="a205c-120">Aby zwiększyć programowo położenie formantu</span><span class="sxs-lookup"><span data-stu-id="a205c-120">To increment a control's location programmatically</span></span>  
  
1.  <span data-ttu-id="a205c-121">Ustaw <xref:System.Windows.Forms.Control.Left%2A> podwłaściwości, aby zwiększyć współrzędną X formantu.</span><span class="sxs-lookup"><span data-stu-id="a205c-121">Set the <xref:System.Windows.Forms.Control.Left%2A> subproperty to increment the X coordinate of the control.</span></span>  
  
    ```vb  
    Button1.Left += 200  
    ```  
  
    ```csharp  
    button1.Left += 200;  
    ```  
  
    ```cpp  
    button1->Left += 200;  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="a205c-122">Użyj <xref:System.Windows.Forms.Control.Location%2A> właściwości można ustawić formantu X i Y pozycji jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="a205c-122">Use the <xref:System.Windows.Forms.Control.Location%2A> property to set a control's X and Y positions simultaneously.</span></span> <span data-ttu-id="a205c-123">Aby ustawić pozycji pojedynczo, użyj formantu <xref:System.Windows.Forms.Control.Left%2A> (**X**) lub <xref:System.Windows.Forms.Control.Top%2A> (**Y**) podwłaściwości.</span><span class="sxs-lookup"><span data-stu-id="a205c-123">To set a position individually, use the control's <xref:System.Windows.Forms.Control.Left%2A> (**X**) or <xref:System.Windows.Forms.Control.Top%2A> (**Y**) subproperty.</span></span> <span data-ttu-id="a205c-124">Nie należy próbować ustawiane niejawnie współrzędne X i Y <xref:System.Drawing.Point> strukturę, która reprezentuje przycisk lokalizacji, ponieważ ta struktura zawiera kopię współrzędnych przycisku.</span><span class="sxs-lookup"><span data-stu-id="a205c-124">Do not try to implicitly set the X and Y coordinates of the <xref:System.Drawing.Point> structure that represents the button's location, because this structure contains a copy of the button's coordinates.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a205c-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a205c-125">See Also</span></span>  
 [<span data-ttu-id="a205c-126">Kontrolki formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a205c-126">Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/index.md)  
 [<span data-ttu-id="a205c-127">Przewodnik: rozmieszczanie kontrolek na formularzach Windows Forms za pomocą linii przyciągania</span><span class="sxs-lookup"><span data-stu-id="a205c-127">Walkthrough: Arranging Controls on Windows Forms Using Snaplines</span></span>](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)  
 [<span data-ttu-id="a205c-128">Przewodnik: rozmieszczanie kontrolek w aplikacji Windows Forms za pomocą kontrolki TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="a205c-128">Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel</span></span>](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)  
 [<span data-ttu-id="a205c-129">Przewodnik: rozmieszczanie kontrolek w formularzach Windows Forms za pomocą kontrolki FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="a205c-129">Walkthrough: Arranging Controls on Windows Forms Using a FlowLayoutPanel</span></span>](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)  
 [<span data-ttu-id="a205c-130">Rozmieszczanie kontrolek na formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a205c-130">Arranging Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)  
 [<span data-ttu-id="a205c-131">Etykietowanie pojedynczych kontrolek formularzy Windows Forms i określanie skrótów dla nich</span><span class="sxs-lookup"><span data-stu-id="a205c-131">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)  
 [<span data-ttu-id="a205c-132">Kontrolki do użycia w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a205c-132">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 [<span data-ttu-id="a205c-133">Kontrolki formularzy Windows Forms według funkcji</span><span class="sxs-lookup"><span data-stu-id="a205c-133">Windows Forms Controls by Function</span></span>](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)  
 [<span data-ttu-id="a205c-134">Porady: Ustawianie lokalizacji ekranu formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="a205c-134">How to: Set the Screen Location of Windows Forms</span></span>](http://msdn.microsoft.com/library/cb023ab7-dea7-4284-9aa6-8c03c59b60c6)
