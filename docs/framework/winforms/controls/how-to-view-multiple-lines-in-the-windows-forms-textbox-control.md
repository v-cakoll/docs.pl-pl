---
title: Wyświetl wiele wierszy w kontrolce TextBox
description: Dowiedz się, jak wyświetlić wiele wierszy w kontrolce TextBox Windows Forms, ustawiając właściwości wielowierszowe, WordWrap i ScrollBar.
ms.date: 03/30/2017
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
ms.openlocfilehash: e40d720bcd56366f4f06bfe2e2d347aaf9aa9d6c
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174474"
---
# <a name="how-to-view-multiple-lines-in-the-windows-forms-textbox-control"></a><span data-ttu-id="24478-103">Porady: wyświetlanie wielu wierszy w formancie TextBox formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="24478-103">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>
<span data-ttu-id="24478-104">Domyślnie <xref:System.Windows.Forms.TextBox> formant Windows Forms wyświetla pojedynczy wiersz tekstu i nie wyświetla pasków przewijania.</span><span class="sxs-lookup"><span data-stu-id="24478-104">By default, the Windows Forms <xref:System.Windows.Forms.TextBox> control displays a single line of text and does not display scroll bars.</span></span> <span data-ttu-id="24478-105">Jeśli tekst jest dłuższy niż dostępne miejsce, widoczna jest tylko część tekstu.</span><span class="sxs-lookup"><span data-stu-id="24478-105">If the text is longer than the available space, only part of the text is visible.</span></span> <span data-ttu-id="24478-106">To zachowanie domyślne można zmienić <xref:System.Windows.Forms.TextBox.Multiline%2A> , ustawiając <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> właściwości, i <xref:System.Windows.Forms.TextBox.ScrollBars%2A> na odpowiednie wartości.</span><span class="sxs-lookup"><span data-stu-id="24478-106">You can change this default behavior by setting the <xref:System.Windows.Forms.TextBox.Multiline%2A>, <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A>, and <xref:System.Windows.Forms.TextBox.ScrollBars%2A> properties to appropriate values.</span></span>  
  
### <a name="to-display-a-carriage-return-in-the-textbox-control"></a><span data-ttu-id="24478-107">Aby wyświetlić znak powrotu karetki w kontrolce TextBox</span><span class="sxs-lookup"><span data-stu-id="24478-107">To display a carriage return in the TextBox control</span></span>  
  
- <span data-ttu-id="24478-108">Aby wyświetlić znak powrotu karetki w wielowierszowym <xref:System.Windows.Forms.TextBox> , należy użyć <xref:System.Environment.NewLine%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="24478-108">To display a carriage return in a multi-line <xref:System.Windows.Forms.TextBox>, use the <xref:System.Environment.NewLine%2A> property.</span></span>  
  
     <span data-ttu-id="24478-109">Należy pamiętać, że interpretacja znaków ucieczki ( \\ ) jest specyficzna dla języka.</span><span class="sxs-lookup"><span data-stu-id="24478-109">Be aware that the interpretation of escape characters (\\) is language-specific.</span></span> <span data-ttu-id="24478-110">Visual Basic używa `Chr$(13) & Chr$(10)` do kombinacji znaków powrotu karetki i znaku wysuwu wiersza.</span><span class="sxs-lookup"><span data-stu-id="24478-110">Visual Basic uses `Chr$(13) & Chr$(10)` for the carriage return and linefeed character combination.</span></span>  
  
### <a name="to-view-multiple-lines-in-the-textbox-control"></a><span data-ttu-id="24478-111">Aby wyświetlić wiele wierszy w kontrolce TextBox</span><span class="sxs-lookup"><span data-stu-id="24478-111">To view multiple lines in the TextBox control</span></span>  
  
1. <span data-ttu-id="24478-112">Ustaw <xref:System.Windows.Forms.TextBox.Multiline%2A> Właściwość na wartość `true` .</span><span class="sxs-lookup"><span data-stu-id="24478-112">Set the <xref:System.Windows.Forms.TextBox.Multiline%2A> property to `true`.</span></span> <span data-ttu-id="24478-113">Jeśli <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> jest `true` (domyślnie), tekst w kontrolce będzie wyświetlany jako jeden lub więcej akapitów; w przeciwnym razie pojawi się jako lista, w której niektóre wiersze mogą być przycinane na krawędzi formantu.</span><span class="sxs-lookup"><span data-stu-id="24478-113">If <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> is `true` (the default), then the text in the control will appear as one or more paragraphs; otherwise it will appear as a list, in which some lines may be clipped at the edge of the control.</span></span>  
  
2. <span data-ttu-id="24478-114">Ustaw <xref:System.Windows.Forms.TextBox.ScrollBars%2A> Właściwość na odpowiednią wartość.</span><span class="sxs-lookup"><span data-stu-id="24478-114">Set the <xref:System.Windows.Forms.TextBox.ScrollBars%2A> property to an appropriate value.</span></span>  
  
    |<span data-ttu-id="24478-115">Wartość</span><span class="sxs-lookup"><span data-stu-id="24478-115">Value</span></span>|<span data-ttu-id="24478-116">Opis</span><span class="sxs-lookup"><span data-stu-id="24478-116">Description</span></span>|  
    |-----------|-----------------|  
    |<xref:System.Windows.Forms.ScrollBars.None>|<span data-ttu-id="24478-117">Użyj tej wartości, jeśli tekst będzie akapitem, który prawie zawsze pasuje do formantu.</span><span class="sxs-lookup"><span data-stu-id="24478-117">Use this value if the text will be a paragraph that almost always fits the control.</span></span> <span data-ttu-id="24478-118">Użytkownik może użyć wskaźnika myszy, aby poruszać się wewnątrz kontrolki, jeśli tekst jest zbyt długi, aby wyświetlić go jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="24478-118">The user can use the mouse pointer to move around inside the control if the text is too long to display all at once.</span></span>|  
    |<xref:System.Windows.Forms.ScrollBars.Horizontal>|<span data-ttu-id="24478-119">Użyj tej wartości, jeśli chcesz wyświetlić listę linii, a niektóre z nich mogą być dłuższe niż szerokość <xref:System.Windows.Forms.TextBox> kontrolki.</span><span class="sxs-lookup"><span data-stu-id="24478-119">Use this value if you want to display a list of lines, some of which may be longer than the width of the <xref:System.Windows.Forms.TextBox> control.</span></span>|  
    |<xref:System.Windows.Forms.ScrollBars.Both>|<span data-ttu-id="24478-120">Użyj tej wartości, jeśli lista może być dłuższa niż wysokość formantu.</span><span class="sxs-lookup"><span data-stu-id="24478-120">Use this value if the list may be longer than the height of the control.</span></span>|  
  
3. <span data-ttu-id="24478-121">Ustaw <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> Właściwość na odpowiednią wartość.</span><span class="sxs-lookup"><span data-stu-id="24478-121">Set the <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> property to an appropriate value.</span></span>  
  
    |<span data-ttu-id="24478-122">Wartość</span><span class="sxs-lookup"><span data-stu-id="24478-122">Value</span></span>|<span data-ttu-id="24478-123">Opis</span><span class="sxs-lookup"><span data-stu-id="24478-123">Description</span></span>|  
    |-----------|-----------------|  
    |`false`|<span data-ttu-id="24478-124">Tekst w kontrolce nie zostanie automatycznie opakowany, więc przewinięcie w prawo do momentu osiągnięcia końca wiersza.</span><span class="sxs-lookup"><span data-stu-id="24478-124">Text in the control will not automatically be wrapped, so it will scroll to the right until a line break is reached.</span></span> <span data-ttu-id="24478-125">Użyj tej wartości, jeśli wybrano <xref:System.Windows.Forms.ScrollBars.Horizontal> paski przewijania lub <xref:System.Windows.Forms.ScrollBars.Both> powyżej.</span><span class="sxs-lookup"><span data-stu-id="24478-125">Use this value if you chose <xref:System.Windows.Forms.ScrollBars.Horizontal> scroll bars or <xref:System.Windows.Forms.ScrollBars.Both>, above.</span></span>|  
    |<span data-ttu-id="24478-126">`true`wartooć</span><span class="sxs-lookup"><span data-stu-id="24478-126">`true` (default)</span></span>|<span data-ttu-id="24478-127">Poziomy pasek przewijania nie zostanie wyświetlony.</span><span class="sxs-lookup"><span data-stu-id="24478-127">The horizontal scrollbar will not appear.</span></span> <span data-ttu-id="24478-128">Użyj tej wartości, jeśli wybrano <xref:System.Windows.Forms.ScrollBars.Vertical> paski przewijania lub <xref:System.Windows.Forms.ScrollBars.None> powyżej, aby wyświetlić jeden lub więcej akapitów.</span><span class="sxs-lookup"><span data-stu-id="24478-128">Use this value if you chose <xref:System.Windows.Forms.ScrollBars.Vertical> scroll bars or <xref:System.Windows.Forms.ScrollBars.None>, above, to display one or more paragraphs.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="24478-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="24478-129">See also</span></span>

- <xref:System.Windows.Forms.TextBox>
- [<span data-ttu-id="24478-130">TextBox, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="24478-130">TextBox Control Overview</span></span>](textbox-control-overview-windows-forms.md)
- [<span data-ttu-id="24478-131">Instrukcje: kontrolowanie punktu wstawiania w kontrolce TextBox formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="24478-131">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [<span data-ttu-id="24478-132">Instrukcje: tworzenie pola tekstowego hasła za pomocą kontrolki TextBox formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="24478-132">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="24478-133">Instrukcje: tworzenie pola tekstowego tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="24478-133">How to: Create a Read-Only Text Box</span></span>](how-to-create-a-read-only-text-box-windows-forms.md)
- [<span data-ttu-id="24478-134">Instrukcje: umieszczanie cudzysłowu w ciągu</span><span class="sxs-lookup"><span data-stu-id="24478-134">How to: Put Quotation Marks in a String</span></span>](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [<span data-ttu-id="24478-135">Porady: zaznaczanie tekstu w formancie TextBox formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="24478-135">How to: Select Text in the Windows Forms TextBox Control</span></span>](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="24478-136">TextBox — Formant</span><span class="sxs-lookup"><span data-stu-id="24478-136">TextBox Control</span></span>](textbox-control-windows-forms.md)
