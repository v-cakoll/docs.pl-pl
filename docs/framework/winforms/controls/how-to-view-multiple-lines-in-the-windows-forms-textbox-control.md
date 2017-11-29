---
title: "Porady: wyświetlanie wielu wierszy w formancie TextBox formularzy systemu Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- newline
- end of line
- ScrollBars property [Windows Forms], in TextBox control
- CRLF
- MultiLine property in TextBox control
- line-feed
- TextBox control [Windows Forms], viewing multiple lines
- carriage return
ms.assetid: 43173201-0b74-4067-a472-605029ca5f35
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0e8f39e031835275818504151e66834f0634b7f2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-view-multiple-lines-in-the-windows-forms-textbox-control"></a><span data-ttu-id="3c35c-102">Porady: wyświetlanie wielu wierszy w formancie TextBox formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="3c35c-102">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>
<span data-ttu-id="3c35c-103">Domyślnie program Windows Forms <xref:System.Windows.Forms.TextBox> kontroli Wyświetla pojedynczą linie tekstu i nie są wyświetlane paski przewijania.</span><span class="sxs-lookup"><span data-stu-id="3c35c-103">By default, the Windows Forms <xref:System.Windows.Forms.TextBox> control displays a single line of text and does not display scroll bars.</span></span> <span data-ttu-id="3c35c-104">Jeśli tekst jest dłuższy niż dostępne miejsce, widoczna jest tylko część tekstu.</span><span class="sxs-lookup"><span data-stu-id="3c35c-104">If the text is longer than the available space, only part of the text is visible.</span></span> <span data-ttu-id="3c35c-105">To zachowanie domyślne można zmienić, ustawiając <xref:System.Windows.Forms.TextBox.Multiline%2A>, <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A>, i <xref:System.Windows.Forms.TextBox.ScrollBars%2A> właściwości, aby odpowiednie wartości.</span><span class="sxs-lookup"><span data-stu-id="3c35c-105">You can change this default behavior by setting the <xref:System.Windows.Forms.TextBox.Multiline%2A>, <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A>, and <xref:System.Windows.Forms.TextBox.ScrollBars%2A> properties to appropriate values.</span></span>  
  
### <a name="to-display-a-carriage-return-in-the-textbox-control"></a><span data-ttu-id="3c35c-106">Aby wyświetlić karetki w formancie TextBox</span><span class="sxs-lookup"><span data-stu-id="3c35c-106">To display a carriage return in the TextBox control</span></span>  
  
-   <span data-ttu-id="3c35c-107">Aby wyświetlić karetki w wielu wierszach <xref:System.Windows.Forms.TextBox>, użyj <xref:System.Environment.NewLine%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="3c35c-107">To display a carriage return in a multi-line <xref:System.Windows.Forms.TextBox>, use the <xref:System.Environment.NewLine%2A> property.</span></span>  
  
     <span data-ttu-id="3c35c-108">Należy pamiętać, że interpretacji znaki specjalne (\\) jest specyficzny dla języka.</span><span class="sxs-lookup"><span data-stu-id="3c35c-108">Be aware that the interpretation of escape characters (\\) is language-specific.</span></span> <span data-ttu-id="3c35c-109">Używa języka Visual Basic `Chr$(13) & Chr$(10)` karetki kombinacji znak powrotu i wysuwu wiersza.</span><span class="sxs-lookup"><span data-stu-id="3c35c-109">Visual Basic uses `Chr$(13) & Chr$(10)` for the carriage return and linefeed character combination.</span></span>  
  
### <a name="to-view-multiple-lines-in-the-textbox-control"></a><span data-ttu-id="3c35c-110">Aby wyświetlić wiele wierszy w formancie TextBox</span><span class="sxs-lookup"><span data-stu-id="3c35c-110">To view multiple lines in the TextBox control</span></span>  
  
1.  <span data-ttu-id="3c35c-111">Ustaw <xref:System.Windows.Forms.TextBox.Multiline%2A> właściwości `true`.</span><span class="sxs-lookup"><span data-stu-id="3c35c-111">Set the <xref:System.Windows.Forms.TextBox.Multiline%2A> property to `true`.</span></span> <span data-ttu-id="3c35c-112">Jeśli <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> jest `true` (ustawienie domyślne), to tekst w formancie pojawi się jako jeden lub więcej akapitów; w przeciwnym razie zostanie wyświetlony jako listy, w której niektóre wiersze mogą przycinana na granicy formantu.</span><span class="sxs-lookup"><span data-stu-id="3c35c-112">If <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> is `true` (the default), then the text in the control will appear as one or more paragraphs; otherwise it will appear as a list, in which some lines may be clipped at the edge of the control.</span></span>  
  
2.  <span data-ttu-id="3c35c-113">Ustaw <xref:System.Windows.Forms.TextBox.ScrollBars%2A> właściwości odpowiednią wartość.</span><span class="sxs-lookup"><span data-stu-id="3c35c-113">Set the <xref:System.Windows.Forms.TextBox.ScrollBars%2A> property to an appropriate value.</span></span>  
  
    |<span data-ttu-id="3c35c-114">Wartość</span><span class="sxs-lookup"><span data-stu-id="3c35c-114">Value</span></span>|<span data-ttu-id="3c35c-115">Opis</span><span class="sxs-lookup"><span data-stu-id="3c35c-115">Description</span></span>|  
    |-----------|-----------------|  
    |<xref:System.Windows.Forms.ScrollBars.None>|<span data-ttu-id="3c35c-116">Użyj tej wartości, czy tekst będzie akapitu który prawie zawsze pasuje do formantu.</span><span class="sxs-lookup"><span data-stu-id="3c35c-116">Use this value if the text will be a paragraph that almost always fits the control.</span></span> <span data-ttu-id="3c35c-117">Użytkownik może użyć wskaźnik myszy do przenoszenia wewnątrz formantu, jeśli tekst jest zbyt długi, aby wyświetlić wszystkie naraz.</span><span class="sxs-lookup"><span data-stu-id="3c35c-117">The user can use the mouse pointer to move around inside the control if the text is too long to display all at once.</span></span>|  
    |<xref:System.Windows.Forms.ScrollBars.Horizontal>|<span data-ttu-id="3c35c-118">Użyj tej wartości, jeśli chcesz wyświetlić listę wierszy, z których część może być dłuższy niż szerokość <xref:System.Windows.Forms.TextBox> formantu.</span><span class="sxs-lookup"><span data-stu-id="3c35c-118">Use this value if you want to display a list of lines, some of which may be longer than the width of the <xref:System.Windows.Forms.TextBox> control.</span></span>|  
    |<xref:System.Windows.Forms.ScrollBars.Both>|<span data-ttu-id="3c35c-119">Użyj tej wartości, jeśli lista może być dłuższa niż wysokość formantu.</span><span class="sxs-lookup"><span data-stu-id="3c35c-119">Use this value if the list may be longer than the height of the control.</span></span>|  
  
3.  <span data-ttu-id="3c35c-120">Ustaw <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> właściwości odpowiednią wartość.</span><span class="sxs-lookup"><span data-stu-id="3c35c-120">Set the <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> property to an appropriate value.</span></span>  
  
    |<span data-ttu-id="3c35c-121">Wartość</span><span class="sxs-lookup"><span data-stu-id="3c35c-121">Value</span></span>|<span data-ttu-id="3c35c-122">Opis</span><span class="sxs-lookup"><span data-stu-id="3c35c-122">Description</span></span>|  
    |-----------|-----------------|  
    |`false`|<span data-ttu-id="3c35c-123">Tekst w formancie nie będzie automatycznie zawijany, więc zostanie przewiń w prawo, aż do osiągnięcia końca wiersza.</span><span class="sxs-lookup"><span data-stu-id="3c35c-123">Text in the control will not automatically be wrapped, so it will scroll to the right until a line break is reached.</span></span> <span data-ttu-id="3c35c-124">Użyj tej wartości, jeśli została wybrana opcja <xref:System.Windows.Forms.ScrollBars.Horizontal> paski przewijania lub <xref:System.Windows.Forms.ScrollBars.Both>powyżej.</span><span class="sxs-lookup"><span data-stu-id="3c35c-124">Use this value if you chose <xref:System.Windows.Forms.ScrollBars.Horizontal> scroll bars or <xref:System.Windows.Forms.ScrollBars.Both>, above.</span></span>|  
    |<span data-ttu-id="3c35c-125">`true`(ustawienie domyślne)</span><span class="sxs-lookup"><span data-stu-id="3c35c-125">`true` (default)</span></span>|<span data-ttu-id="3c35c-126">Poziomy pasek przewijania nie będą wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="3c35c-126">The horizontal scrollbar will not appear.</span></span> <span data-ttu-id="3c35c-127">Użyj tej wartości, jeśli została wybrana opcja <xref:System.Windows.Forms.ScrollBars.Vertical> paski przewijania lub <xref:System.Windows.Forms.ScrollBars.None>powyżej, aby wyświetlić jeden lub więcej akapitów.</span><span class="sxs-lookup"><span data-stu-id="3c35c-127">Use this value if you chose <xref:System.Windows.Forms.ScrollBars.Vertical> scroll bars or <xref:System.Windows.Forms.ScrollBars.None>, above, to display one or more paragraphs.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3c35c-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3c35c-128">See Also</span></span>  
 <xref:System.Windows.Forms.TextBox>  
 [<span data-ttu-id="3c35c-129">Informacje o formancie TextBox</span><span class="sxs-lookup"><span data-stu-id="3c35c-129">TextBox Control Overview</span></span>](../../../../docs/framework/winforms/controls/textbox-control-overview-windows-forms.md)  
 [<span data-ttu-id="3c35c-130">Porady: kontrolowanie punktu wstawiania w formancie TextBox formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="3c35c-130">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)  
 [<span data-ttu-id="3c35c-131">Porady: Tworzenie pola tekstowego hasła za pomocą formantu TextBox formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="3c35c-131">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)  
 [<span data-ttu-id="3c35c-132">Porady: Tworzenie pola tekstowego tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="3c35c-132">How to: Create a Read-Only Text Box</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-read-only-text-box-windows-forms.md)  
 [<span data-ttu-id="3c35c-133">Porady: umieszczanie cudzysłowu w ciągu</span><span class="sxs-lookup"><span data-stu-id="3c35c-133">How to: Put Quotation Marks in a String</span></span>](../../../../docs/framework/winforms/controls/how-to-put-quotation-marks-in-a-string-windows-forms.md)  
 [<span data-ttu-id="3c35c-134">Porady: Zaznaczanie tekstu w oknach formantu TextBox formularzy</span><span class="sxs-lookup"><span data-stu-id="3c35c-134">How to: Select Text in the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-select-text-in-the-windows-forms-textbox-control.md)  
 [<span data-ttu-id="3c35c-135">TextBox — formant</span><span class="sxs-lookup"><span data-stu-id="3c35c-135">TextBox Control</span></span>](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)
