---
title: "Porady: wyświetlanie pasków przewijania w komórkach formantu RichTextBox formularzy systemu Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- text boxes [Windows Forms], displaying scroll bars
- scroll bars [Windows Forms], displaying in controls
- RichTextBox control [Windows Forms], displaying scroll bars
ms.assetid: cdeb42e1-86e8-410c-ba46-18aec264ef5f
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3b20c526b27eb185bf79eaf0ace47e5a9fded42a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-display-scroll-bars-in-the-windows-forms-richtextbox-control"></a><span data-ttu-id="bce70-102">Porady: wyświetlanie pasków przewijania w komórkach formantu RichTextBox formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="bce70-102">How to: Display Scroll Bars in the Windows Forms RichTextBox Control</span></span>
<span data-ttu-id="bce70-103">Domyślnie program Windows Forms <xref:System.Windows.Forms.RichTextBox> kontrolka Wyświetla pasków przewijania w poziomie i w pionie w razie potrzeby.</span><span class="sxs-lookup"><span data-stu-id="bce70-103">By default, the Windows Forms <xref:System.Windows.Forms.RichTextBox> control displays horizontal and vertical scroll bars as necessary.</span></span> <span data-ttu-id="bce70-104">Istnieje siedem możliwe wartości <xref:System.Windows.Forms.RichTextBox.ScrollBars%2A> właściwość <xref:System.Windows.Forms.RichTextBox> kontroli, które są opisane w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="bce70-104">There are seven possible values for the <xref:System.Windows.Forms.RichTextBox.ScrollBars%2A> property of the <xref:System.Windows.Forms.RichTextBox> control, which are described in the table below.</span></span>  
  
### <a name="to-display-scroll-bars-in-a-richtextbox-control"></a><span data-ttu-id="bce70-105">Wyświetlanie pasków przewijania w formancie RichTextBox</span><span class="sxs-lookup"><span data-stu-id="bce70-105">To display scroll bars in a RichTextBox control</span></span>  
  
1.  <span data-ttu-id="bce70-106">Ustaw <xref:System.Windows.Forms.RichTextBox.Multiline%2A> właściwości `true`.</span><span class="sxs-lookup"><span data-stu-id="bce70-106">Set the <xref:System.Windows.Forms.RichTextBox.Multiline%2A> property to `true`.</span></span> <span data-ttu-id="bce70-107">Nie typu pasek, łącznie z przewijania poziomo, nie wyświetla w przypadku <xref:System.Windows.Forms.RichTextBox.Multiline%2A> właściwość jest ustawiona na `false`.</span><span class="sxs-lookup"><span data-stu-id="bce70-107">No type of scroll bar, including horizontal, will display if the <xref:System.Windows.Forms.RichTextBox.Multiline%2A> property is set to `false`.</span></span>  
  
2.  <span data-ttu-id="bce70-108">Ustaw <xref:System.Windows.Forms.RichTextBox.ScrollBars%2A> odpowiednie wartości dla właściwości <xref:System.Windows.Forms.RichTextBoxScrollBars> wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="bce70-108">Set the <xref:System.Windows.Forms.RichTextBox.ScrollBars%2A> property to an appropriate value of the <xref:System.Windows.Forms.RichTextBoxScrollBars> enumeration.</span></span>  
  
    |<span data-ttu-id="bce70-109">Wartość</span><span class="sxs-lookup"><span data-stu-id="bce70-109">Value</span></span>|<span data-ttu-id="bce70-110">Opis</span><span class="sxs-lookup"><span data-stu-id="bce70-110">Description</span></span>|  
    |-----------|-----------------|  
    |<span data-ttu-id="bce70-111"><xref:System.Windows.Forms.RichTextBoxScrollBars.Both>(ustawienie domyślne)</span><span class="sxs-lookup"><span data-stu-id="bce70-111"><xref:System.Windows.Forms.RichTextBoxScrollBars.Both> (default)</span></span>|<span data-ttu-id="bce70-112">Wyświetla poziomy lub pionowy pasek przewijania i/lub tylko wtedy, gdy tekst przekracza szerokość lub długość kontrolki.</span><span class="sxs-lookup"><span data-stu-id="bce70-112">Displays horizontal or vertical scroll bars, or both, only when text exceeds the width or length of the control.</span></span>|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.None>|<span data-ttu-id="bce70-113">Nigdy nie wyświetla żadnego typu pasek przewijania.</span><span class="sxs-lookup"><span data-stu-id="bce70-113">Never displays any type of scroll bar.</span></span>|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.Horizontal>|<span data-ttu-id="bce70-114">Wyświetla przewijania poziomego paska tylko wtedy, gdy tekst przekracza szerokość formantu.</span><span class="sxs-lookup"><span data-stu-id="bce70-114">Displays a horizontal scroll bar only when the text exceeds the width of the control.</span></span> <span data-ttu-id="bce70-115">(W tym celu włączone, <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> musi mieć ustawioną właściwość `false`.)</span><span class="sxs-lookup"><span data-stu-id="bce70-115">(For this to occur, the <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> property must be set to `false`.)</span></span>|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.Vertical>|<span data-ttu-id="bce70-116">Wyświetla przewijania pionowego paska tylko wtedy, gdy tekst przekracza wysokość formantu.</span><span class="sxs-lookup"><span data-stu-id="bce70-116">Displays a vertical scroll bar only when the text exceeds the height of the control.</span></span>|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.ForcedHorizontal>|<span data-ttu-id="bce70-117">Wyświetla paska podczas przewijania poziomego <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> właściwość jest ustawiona na `false`.</span><span class="sxs-lookup"><span data-stu-id="bce70-117">Displays a horizontal scroll bar when the <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> property is set to `false`.</span></span> <span data-ttu-id="bce70-118">Wygaszone paska przewijania, gdy tekst nie przekracza szerokość formantu.</span><span class="sxs-lookup"><span data-stu-id="bce70-118">The scroll bar appears dimmed when text does not exceed the width of the control.</span></span>|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.ForcedVertical>|<span data-ttu-id="bce70-119">Zawsze wyświetla pionowy pasek przewijania.</span><span class="sxs-lookup"><span data-stu-id="bce70-119">Always displays a vertical scroll bar.</span></span> <span data-ttu-id="bce70-120">Wygaszone paska przewijania, gdy tekst nie przekracza długość kontrolki.</span><span class="sxs-lookup"><span data-stu-id="bce70-120">The scroll bar appears dimmed when text does not exceed the length of the control.</span></span>|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.ForcedBoth>|<span data-ttu-id="bce70-121">Zawsze wyświetla pionowy pasek przewijania.</span><span class="sxs-lookup"><span data-stu-id="bce70-121">Always displays a vertical scrollbar.</span></span> <span data-ttu-id="bce70-122">Wyświetla paska podczas przewijania poziomego <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> właściwość jest ustawiona na `false`.</span><span class="sxs-lookup"><span data-stu-id="bce70-122">Displays a horizontal scroll bar when the <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> property is set to `false`.</span></span> <span data-ttu-id="bce70-123">Paski przewijania pojawiają się wygaszone, gdy tekst nie przekracza szerokość lub długość kontrolki.</span><span class="sxs-lookup"><span data-stu-id="bce70-123">The scroll bars appear grayed when text does not exceed the width or length of the control.</span></span>|  
  
3.  <span data-ttu-id="bce70-124">Ustaw <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> właściwości odpowiednią wartość.</span><span class="sxs-lookup"><span data-stu-id="bce70-124">Set the <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> property to an appropriate value.</span></span>  
  
    |<span data-ttu-id="bce70-125">Wartość</span><span class="sxs-lookup"><span data-stu-id="bce70-125">Value</span></span>|<span data-ttu-id="bce70-126">Opis</span><span class="sxs-lookup"><span data-stu-id="bce70-126">Description</span></span>|  
    |-----------|-----------------|  
    |`false`|<span data-ttu-id="bce70-127">Tekst w formancie nie zostanie automatycznie dopasowana do szerokość formantu, więc zostanie przewiń w prawo, aż do osiągnięcia końca wiersza.</span><span class="sxs-lookup"><span data-stu-id="bce70-127">Text in the control is not automatically adjusted to fit the width of the control, so it will scroll to the right until a line break is reached.</span></span> <span data-ttu-id="bce70-128">Użyj tej wartości w przypadku wybrania paski przewijania w poziomie i/lub powyżej.</span><span class="sxs-lookup"><span data-stu-id="bce70-128">Use this value if you chose horizontal scroll bars or both, above.</span></span>|  
    |<span data-ttu-id="bce70-129">`true`(ustawienie domyślne)</span><span class="sxs-lookup"><span data-stu-id="bce70-129">`true` (default)</span></span>|<span data-ttu-id="bce70-130">Tekst w formancie zostanie automatycznie dopasowana do szerokość formantu.</span><span class="sxs-lookup"><span data-stu-id="bce70-130">Text in the control is automatically adjusted to fit the width of the control.</span></span> <span data-ttu-id="bce70-131">Poziomy pasek przewijania nie będą wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="bce70-131">The horizontal scrollbar will not appear.</span></span> <span data-ttu-id="bce70-132">Użyj tej wartości, jeśli została wybrana opcja pionowe paski przewijania lub Brak, powyżej, aby wyświetlić jeden lub więcej akapitów.</span><span class="sxs-lookup"><span data-stu-id="bce70-132">Use this value if you chose vertical scroll bars or none, above, to display one or more paragraphs.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bce70-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bce70-133">See Also</span></span>  
 <xref:System.Windows.Forms.RichTextBoxScrollBars>  
 <xref:System.Windows.Forms.RichTextBox>  
 [<span data-ttu-id="bce70-134">RichTextBox — formant</span><span class="sxs-lookup"><span data-stu-id="bce70-134">RichTextBox Control</span></span>](../../../../docs/framework/winforms/controls/richtextbox-control-windows-forms.md)  
 [<span data-ttu-id="bce70-135">Formanty do użycia w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="bce70-135">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
