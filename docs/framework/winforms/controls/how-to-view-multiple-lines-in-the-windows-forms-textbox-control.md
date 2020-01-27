---
title: Wyświetl wiele wierszy w kontrolce TextBox
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
ms.openlocfilehash: 61ea671c1e86fa8254bfc1b043a46f3b7aa6af1d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728283"
---
# <a name="how-to-view-multiple-lines-in-the-windows-forms-textbox-control"></a><span data-ttu-id="21273-102">Porady: wyświetlanie wielu wierszy w formancie TextBox formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="21273-102">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>
<span data-ttu-id="21273-103">Domyślnie formant Windows Forms <xref:System.Windows.Forms.TextBox> wyświetla pojedynczy wiersz tekstu i nie wyświetla pasków przewijania.</span><span class="sxs-lookup"><span data-stu-id="21273-103">By default, the Windows Forms <xref:System.Windows.Forms.TextBox> control displays a single line of text and does not display scroll bars.</span></span> <span data-ttu-id="21273-104">Jeśli tekst jest dłuższy niż dostępne miejsce, widoczna jest tylko część tekstu.</span><span class="sxs-lookup"><span data-stu-id="21273-104">If the text is longer than the available space, only part of the text is visible.</span></span> <span data-ttu-id="21273-105">To zachowanie domyślne można zmienić, ustawiając właściwości <xref:System.Windows.Forms.TextBox.Multiline%2A>, <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A>i <xref:System.Windows.Forms.TextBox.ScrollBars%2A> na odpowiednie wartości.</span><span class="sxs-lookup"><span data-stu-id="21273-105">You can change this default behavior by setting the <xref:System.Windows.Forms.TextBox.Multiline%2A>, <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A>, and <xref:System.Windows.Forms.TextBox.ScrollBars%2A> properties to appropriate values.</span></span>  
  
### <a name="to-display-a-carriage-return-in-the-textbox-control"></a><span data-ttu-id="21273-106">Aby wyświetlić znak powrotu karetki w kontrolce TextBox</span><span class="sxs-lookup"><span data-stu-id="21273-106">To display a carriage return in the TextBox control</span></span>  
  
- <span data-ttu-id="21273-107">Aby wyświetlić znak powrotu karetki w <xref:System.Windows.Forms.TextBox>wielowierszowym, należy użyć właściwości <xref:System.Environment.NewLine%2A>.</span><span class="sxs-lookup"><span data-stu-id="21273-107">To display a carriage return in a multi-line <xref:System.Windows.Forms.TextBox>, use the <xref:System.Environment.NewLine%2A> property.</span></span>  
  
     <span data-ttu-id="21273-108">Należy pamiętać, że interpretacja znaków ucieczki (\\) jest specyficzna dla języka.</span><span class="sxs-lookup"><span data-stu-id="21273-108">Be aware that the interpretation of escape characters (\\) is language-specific.</span></span> <span data-ttu-id="21273-109">Visual Basic używa `Chr$(13) & Chr$(10)` kombinacji znaków powrotu karetki i znaku wysuwu wiersza.</span><span class="sxs-lookup"><span data-stu-id="21273-109">Visual Basic uses `Chr$(13) & Chr$(10)` for the carriage return and linefeed character combination.</span></span>  
  
### <a name="to-view-multiple-lines-in-the-textbox-control"></a><span data-ttu-id="21273-110">Aby wyświetlić wiele wierszy w kontrolce TextBox</span><span class="sxs-lookup"><span data-stu-id="21273-110">To view multiple lines in the TextBox control</span></span>  
  
1. <span data-ttu-id="21273-111">Ustaw <xref:System.Windows.Forms.TextBox.Multiline%2A> właściwość `true`.</span><span class="sxs-lookup"><span data-stu-id="21273-111">Set the <xref:System.Windows.Forms.TextBox.Multiline%2A> property to `true`.</span></span> <span data-ttu-id="21273-112">Jeśli <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> jest `true` (domyślnie), tekst w kontrolce będzie wyświetlany jako jeden lub więcej akapitów; w przeciwnym razie pojawi się jako lista, w której niektóre wiersze mogą być przycinane na krawędzi formantu.</span><span class="sxs-lookup"><span data-stu-id="21273-112">If <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> is `true` (the default), then the text in the control will appear as one or more paragraphs; otherwise it will appear as a list, in which some lines may be clipped at the edge of the control.</span></span>  
  
2. <span data-ttu-id="21273-113">Ustaw właściwość <xref:System.Windows.Forms.TextBox.ScrollBars%2A> na odpowiednią wartość.</span><span class="sxs-lookup"><span data-stu-id="21273-113">Set the <xref:System.Windows.Forms.TextBox.ScrollBars%2A> property to an appropriate value.</span></span>  
  
    |<span data-ttu-id="21273-114">Wartość</span><span class="sxs-lookup"><span data-stu-id="21273-114">Value</span></span>|<span data-ttu-id="21273-115">Opis</span><span class="sxs-lookup"><span data-stu-id="21273-115">Description</span></span>|  
    |-----------|-----------------|  
    |<xref:System.Windows.Forms.ScrollBars.None>|<span data-ttu-id="21273-116">Użyj tej wartości, jeśli tekst będzie akapitem, który prawie zawsze pasuje do formantu.</span><span class="sxs-lookup"><span data-stu-id="21273-116">Use this value if the text will be a paragraph that almost always fits the control.</span></span> <span data-ttu-id="21273-117">Użytkownik może użyć wskaźnika myszy, aby poruszać się wewnątrz kontrolki, jeśli tekst jest zbyt długi, aby wyświetlić go jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="21273-117">The user can use the mouse pointer to move around inside the control if the text is too long to display all at once.</span></span>|  
    |<xref:System.Windows.Forms.ScrollBars.Horizontal>|<span data-ttu-id="21273-118">Użyj tej wartości, jeśli chcesz wyświetlić listę linii, a niektóre z nich mogą być dłuższe niż szerokość kontrolki <xref:System.Windows.Forms.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="21273-118">Use this value if you want to display a list of lines, some of which may be longer than the width of the <xref:System.Windows.Forms.TextBox> control.</span></span>|  
    |<xref:System.Windows.Forms.ScrollBars.Both>|<span data-ttu-id="21273-119">Użyj tej wartości, jeśli lista może być dłuższa niż wysokość formantu.</span><span class="sxs-lookup"><span data-stu-id="21273-119">Use this value if the list may be longer than the height of the control.</span></span>|  
  
3. <span data-ttu-id="21273-120">Ustaw właściwość <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> na odpowiednią wartość.</span><span class="sxs-lookup"><span data-stu-id="21273-120">Set the <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> property to an appropriate value.</span></span>  
  
    |<span data-ttu-id="21273-121">Wartość</span><span class="sxs-lookup"><span data-stu-id="21273-121">Value</span></span>|<span data-ttu-id="21273-122">Opis</span><span class="sxs-lookup"><span data-stu-id="21273-122">Description</span></span>|  
    |-----------|-----------------|  
    |`false`|<span data-ttu-id="21273-123">Tekst w kontrolce nie zostanie automatycznie opakowany, więc przewinięcie w prawo do momentu osiągnięcia końca wiersza.</span><span class="sxs-lookup"><span data-stu-id="21273-123">Text in the control will not automatically be wrapped, so it will scroll to the right until a line break is reached.</span></span> <span data-ttu-id="21273-124">Użyj tej wartości, jeśli wybrano <xref:System.Windows.Forms.ScrollBars.Horizontal> paski przewijania lub <xref:System.Windows.Forms.ScrollBars.Both>, powyżej.</span><span class="sxs-lookup"><span data-stu-id="21273-124">Use this value if you chose <xref:System.Windows.Forms.ScrollBars.Horizontal> scroll bars or <xref:System.Windows.Forms.ScrollBars.Both>, above.</span></span>|  
    |<span data-ttu-id="21273-125">`true` (wartość domyślna)</span><span class="sxs-lookup"><span data-stu-id="21273-125">`true` (default)</span></span>|<span data-ttu-id="21273-126">Poziomy pasek przewijania nie zostanie wyświetlony.</span><span class="sxs-lookup"><span data-stu-id="21273-126">The horizontal scrollbar will not appear.</span></span> <span data-ttu-id="21273-127">Użyj tej wartości, jeśli wybrano <xref:System.Windows.Forms.ScrollBars.Vertical> paski przewijania lub <xref:System.Windows.Forms.ScrollBars.None>, aby wyświetlić jeden lub więcej akapitów.</span><span class="sxs-lookup"><span data-stu-id="21273-127">Use this value if you chose <xref:System.Windows.Forms.ScrollBars.Vertical> scroll bars or <xref:System.Windows.Forms.ScrollBars.None>, above, to display one or more paragraphs.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="21273-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="21273-128">See also</span></span>

- <xref:System.Windows.Forms.TextBox>
- [<span data-ttu-id="21273-129">TextBox, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="21273-129">TextBox Control Overview</span></span>](textbox-control-overview-windows-forms.md)
- [<span data-ttu-id="21273-130">Instrukcje: kontrolowanie punktu wstawiania w kontrolce TextBox formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="21273-130">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [<span data-ttu-id="21273-131">Instrukcje: tworzenie pola tekstowego hasła za pomocą kontrolki TextBox formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="21273-131">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="21273-132">Instrukcje: tworzenie pola tekstowego tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="21273-132">How to: Create a Read-Only Text Box</span></span>](how-to-create-a-read-only-text-box-windows-forms.md)
- [<span data-ttu-id="21273-133">Instrukcje: umieszczanie cudzysłowu w ciągu</span><span class="sxs-lookup"><span data-stu-id="21273-133">How to: Put Quotation Marks in a String</span></span>](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [<span data-ttu-id="21273-134">Instrukcje: zaznaczanie tekstu w kontrolce TextBox formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="21273-134">How to: Select Text in the Windows Forms TextBox Control</span></span>](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="21273-135">TextBox, kontrolka</span><span class="sxs-lookup"><span data-stu-id="21273-135">TextBox Control</span></span>](textbox-control-windows-forms.md)
