---
title: 'Instrukcje: Wyświetlanie wielu wierszy w formancie TextBox formularzy Windows'
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
ms.openlocfilehash: d80a0262455b9b5e0e8535d88eb6292ab60e3ea8
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57716013"
---
# <a name="how-to-view-multiple-lines-in-the-windows-forms-textbox-control"></a><span data-ttu-id="ccc05-102">Instrukcje: Wyświetlanie wielu wierszy w formancie TextBox formularzy Windows</span><span class="sxs-lookup"><span data-stu-id="ccc05-102">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>
<span data-ttu-id="ccc05-103">Domyślnie w formularzach Windows <xref:System.Windows.Forms.TextBox> kontrolka Wyświetla pojedynczą linie tekstu i nie są wyświetlane paski przewijania.</span><span class="sxs-lookup"><span data-stu-id="ccc05-103">By default, the Windows Forms <xref:System.Windows.Forms.TextBox> control displays a single line of text and does not display scroll bars.</span></span> <span data-ttu-id="ccc05-104">Jeśli tekst jest dłuższy niż dostępna ilość miejsca, tylko część tekstu jest widoczna.</span><span class="sxs-lookup"><span data-stu-id="ccc05-104">If the text is longer than the available space, only part of the text is visible.</span></span> <span data-ttu-id="ccc05-105">To zachowanie domyślne można zmienić, ustawiając <xref:System.Windows.Forms.TextBox.Multiline%2A>, <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A>, i <xref:System.Windows.Forms.TextBox.ScrollBars%2A> właściwości odpowiednie wartości.</span><span class="sxs-lookup"><span data-stu-id="ccc05-105">You can change this default behavior by setting the <xref:System.Windows.Forms.TextBox.Multiline%2A>, <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A>, and <xref:System.Windows.Forms.TextBox.ScrollBars%2A> properties to appropriate values.</span></span>  
  
### <a name="to-display-a-carriage-return-in-the-textbox-control"></a><span data-ttu-id="ccc05-106">Aby wyświetlić znak powrotu karetki w formancie TextBox</span><span class="sxs-lookup"><span data-stu-id="ccc05-106">To display a carriage return in the TextBox control</span></span>  
  
-   <span data-ttu-id="ccc05-107">Aby wyświetlić znak powrotu karetki w wielowierszowym <xref:System.Windows.Forms.TextBox>, użyj <xref:System.Environment.NewLine%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="ccc05-107">To display a carriage return in a multi-line <xref:System.Windows.Forms.TextBox>, use the <xref:System.Environment.NewLine%2A> property.</span></span>  
  
     <span data-ttu-id="ccc05-108">Należy pamiętać, że interpretacji znaków ucieczki (\\) jest specyficzny dla języka.</span><span class="sxs-lookup"><span data-stu-id="ccc05-108">Be aware that the interpretation of escape characters (\\) is language-specific.</span></span> <span data-ttu-id="ccc05-109">Visual Basic stosuje `Chr$(13) & Chr$(10)` przy użyciu kombinacji znak powrotu karetki, jak powrotu i wysuwu wiersza.</span><span class="sxs-lookup"><span data-stu-id="ccc05-109">Visual Basic uses `Chr$(13) & Chr$(10)` for the carriage return and linefeed character combination.</span></span>  
  
### <a name="to-view-multiple-lines-in-the-textbox-control"></a><span data-ttu-id="ccc05-110">Aby wyświetlić wiele wierszy w formancie TextBox</span><span class="sxs-lookup"><span data-stu-id="ccc05-110">To view multiple lines in the TextBox control</span></span>  
  
1.  <span data-ttu-id="ccc05-111">Ustaw <xref:System.Windows.Forms.TextBox.Multiline%2A> właściwość `true`.</span><span class="sxs-lookup"><span data-stu-id="ccc05-111">Set the <xref:System.Windows.Forms.TextBox.Multiline%2A> property to `true`.</span></span> <span data-ttu-id="ccc05-112">Jeśli <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> jest `true` (ustawienie domyślne), następnie pojawi się jako jeden lub więcej akapitów tekstu w kontrolce; w przeciwnym razie zostanie wyświetlony jako listy, w której niektóre linie mogą zostać obcięte na brzegu kontrolki.</span><span class="sxs-lookup"><span data-stu-id="ccc05-112">If <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> is `true` (the default), then the text in the control will appear as one or more paragraphs; otherwise it will appear as a list, in which some lines may be clipped at the edge of the control.</span></span>  
  
2.  <span data-ttu-id="ccc05-113">Ustaw <xref:System.Windows.Forms.TextBox.ScrollBars%2A> właściwość do odpowiedniej wartości.</span><span class="sxs-lookup"><span data-stu-id="ccc05-113">Set the <xref:System.Windows.Forms.TextBox.ScrollBars%2A> property to an appropriate value.</span></span>  
  
    |<span data-ttu-id="ccc05-114">Wartość</span><span class="sxs-lookup"><span data-stu-id="ccc05-114">Value</span></span>|<span data-ttu-id="ccc05-115">Opis</span><span class="sxs-lookup"><span data-stu-id="ccc05-115">Description</span></span>|  
    |-----------|-----------------|  
    |<xref:System.Windows.Forms.ScrollBars.None>|<span data-ttu-id="ccc05-116">Użyj tej wartości, jeśli tekst będzie akapitu, prawie zawsze pasuje do formantu.</span><span class="sxs-lookup"><span data-stu-id="ccc05-116">Use this value if the text will be a paragraph that almost always fits the control.</span></span> <span data-ttu-id="ccc05-117">Użytkownik może użyć wskaźnika myszy, aby poruszać się wewnątrz formantu, jeśli tekst jest zbyt długa, aby wyświetlić wszystkie na raz.</span><span class="sxs-lookup"><span data-stu-id="ccc05-117">The user can use the mouse pointer to move around inside the control if the text is too long to display all at once.</span></span>|  
    |<xref:System.Windows.Forms.ScrollBars.Horizontal>|<span data-ttu-id="ccc05-118">Użyj tej wartości, jeśli chcesz wyświetlić listę wierszy, z których część może być dłuższy niż szerokość <xref:System.Windows.Forms.TextBox> kontroli.</span><span class="sxs-lookup"><span data-stu-id="ccc05-118">Use this value if you want to display a list of lines, some of which may be longer than the width of the <xref:System.Windows.Forms.TextBox> control.</span></span>|  
    |<xref:System.Windows.Forms.ScrollBars.Both>|<span data-ttu-id="ccc05-119">Użyj tej wartości, jeśli lista może być dłuższa niż wysokość formantu.</span><span class="sxs-lookup"><span data-stu-id="ccc05-119">Use this value if the list may be longer than the height of the control.</span></span>|  
  
3.  <span data-ttu-id="ccc05-120">Ustaw <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> właściwość do odpowiedniej wartości.</span><span class="sxs-lookup"><span data-stu-id="ccc05-120">Set the <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> property to an appropriate value.</span></span>  
  
    |<span data-ttu-id="ccc05-121">Wartość</span><span class="sxs-lookup"><span data-stu-id="ccc05-121">Value</span></span>|<span data-ttu-id="ccc05-122">Opis</span><span class="sxs-lookup"><span data-stu-id="ccc05-122">Description</span></span>|  
    |-----------|-----------------|  
    |`false`|<span data-ttu-id="ccc05-123">Tekst w kontrolce nie będzie automatycznie zawijany, dzięki czemu będzie ona przewiń w prawo aż do osiągnięcia końca wiersza.</span><span class="sxs-lookup"><span data-stu-id="ccc05-123">Text in the control will not automatically be wrapped, so it will scroll to the right until a line break is reached.</span></span> <span data-ttu-id="ccc05-124">Użyj tej wartości, jeśli została wybrana opcja <xref:System.Windows.Forms.ScrollBars.Horizontal> paski przewijania lub <xref:System.Windows.Forms.ScrollBars.Both>powyżej.</span><span class="sxs-lookup"><span data-stu-id="ccc05-124">Use this value if you chose <xref:System.Windows.Forms.ScrollBars.Horizontal> scroll bars or <xref:System.Windows.Forms.ScrollBars.Both>, above.</span></span>|  
    |<span data-ttu-id="ccc05-125">`true` (ustawienie domyślne)</span><span class="sxs-lookup"><span data-stu-id="ccc05-125">`true` (default)</span></span>|<span data-ttu-id="ccc05-126">Poziomy pasek przewijania nie będzie widoczna.</span><span class="sxs-lookup"><span data-stu-id="ccc05-126">The horizontal scrollbar will not appear.</span></span> <span data-ttu-id="ccc05-127">Użyj tej wartości, jeśli została wybrana opcja <xref:System.Windows.Forms.ScrollBars.Vertical> paski przewijania lub <xref:System.Windows.Forms.ScrollBars.None>powyżej, aby wyświetlić jeden lub więcej akapitów.</span><span class="sxs-lookup"><span data-stu-id="ccc05-127">Use this value if you chose <xref:System.Windows.Forms.ScrollBars.Vertical> scroll bars or <xref:System.Windows.Forms.ScrollBars.None>, above, to display one or more paragraphs.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ccc05-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ccc05-128">See also</span></span>
- <xref:System.Windows.Forms.TextBox>
- [<span data-ttu-id="ccc05-129">TextBox, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="ccc05-129">TextBox Control Overview</span></span>](textbox-control-overview-windows-forms.md)
- [<span data-ttu-id="ccc05-130">Instrukcje: Kontrolowanie punktu wstawiania w formancie TextBox formularzy Windows</span><span class="sxs-lookup"><span data-stu-id="ccc05-130">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [<span data-ttu-id="ccc05-131">Instrukcje: Tworzenie pola tekstowego hasła za pomocą kontrolki TextBox formularzy Windows</span><span class="sxs-lookup"><span data-stu-id="ccc05-131">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="ccc05-132">Instrukcje: Tworzenie pola tekstowego tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="ccc05-132">How to: Create a Read-Only Text Box</span></span>](how-to-create-a-read-only-text-box-windows-forms.md)
- [<span data-ttu-id="ccc05-133">Instrukcje: Umieszczanie cudzysłowu w ciągu</span><span class="sxs-lookup"><span data-stu-id="ccc05-133">How to: Put Quotation Marks in a String</span></span>](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [<span data-ttu-id="ccc05-134">Instrukcje: Zaznaczanie tekstu w formancie TextBox formularzy Windows</span><span class="sxs-lookup"><span data-stu-id="ccc05-134">How to: Select Text in the Windows Forms TextBox Control</span></span>](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="ccc05-135">TextBox, kontrolka</span><span class="sxs-lookup"><span data-stu-id="ccc05-135">TextBox Control</span></span>](textbox-control-windows-forms.md)
