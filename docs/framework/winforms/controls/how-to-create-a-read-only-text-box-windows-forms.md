---
title: 'Instrukcje: Tworzenie pola tekstowego tylko do odczytu (Windows Forms)'
ms.date: 03/30/2017
helpviewer_keywords:
- TextBox control [Windows Forms], read-only
- read-only text boxes
- text boxes [Windows Forms], read-only
ms.assetid: 60baa9ab-fa57-44ad-bb7c-61b05aa64296
ms.openlocfilehash: be85eedf272e596ceb10e7510b8c99ce6aed0727
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59130731"
---
# <a name="how-to-create-a-read-only-text-box-windows-forms"></a><span data-ttu-id="94023-102">Instrukcje: Tworzenie pola tekstowego tylko do odczytu (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="94023-102">How to: Create a Read-Only Text Box (Windows Forms)</span></span>
<span data-ttu-id="94023-103">Można edytować pole tekstowe Windows Forms można przekształcić do kontrolki tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="94023-103">You can transform an editable Windows Forms text box into a read-only control.</span></span> <span data-ttu-id="94023-104">Na przykład pola tekstowego może wyświetlić wartość, która zwykle jest edytowany, ale nie może być aktualnie, ze względu na stan aplikacji.</span><span class="sxs-lookup"><span data-stu-id="94023-104">For example, the text box may display a value that is usually edited but may not be currently, due to the state of the application.</span></span>  
  
### <a name="to-create-a-read-only-text-box"></a><span data-ttu-id="94023-105">Aby utworzyć pole tekstowe tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="94023-105">To create a read-only text box</span></span>  
  
1.  <span data-ttu-id="94023-106">Ustaw <xref:System.Windows.Forms.TextBox> kontrolki <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> właściwość `true`.</span><span class="sxs-lookup"><span data-stu-id="94023-106">Set the <xref:System.Windows.Forms.TextBox> control's <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> property to `true`.</span></span> <span data-ttu-id="94023-107">Z właściwością ustawioną na `true`, użytkownicy nadal mogą przewijać i wyróżnianie tekstu w polu tekstowym bez możliwości zmiany.</span><span class="sxs-lookup"><span data-stu-id="94023-107">With the property set to `true`, users can still scroll and highlight text in a text box without allowing changes.</span></span> <span data-ttu-id="94023-108">A **kopiowania** polecenie działa w polu tekstowym, ale **Wytnij** i **Wklej** polecenia nie są.</span><span class="sxs-lookup"><span data-stu-id="94023-108">A **Copy** command is functional in a text box, but **Cut** and **Paste** commands are not.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="94023-109"><xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> Właściwość ma wpływ tylko na interakcji z użytkownikiem w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="94023-109">The <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> property only affects user interaction at run time.</span></span> <span data-ttu-id="94023-110">Nadal można zmienić zawartości pola tekstowego programowo w czasie wykonywania, zmieniając <xref:System.Windows.Forms.TextBox.Text%2A> właściwości pola tekstowego.</span><span class="sxs-lookup"><span data-stu-id="94023-110">You can still change text box contents programmatically at run time by changing the <xref:System.Windows.Forms.TextBox.Text%2A> property of the text box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94023-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="94023-111">See also</span></span>

- <xref:System.Windows.Forms.TextBox>
- [<span data-ttu-id="94023-112">TextBox, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="94023-112">TextBox Control Overview</span></span>](textbox-control-overview-windows-forms.md)
- [<span data-ttu-id="94023-113">Instrukcje: kontrolowanie punktu wstawiania w kontrolce TextBox formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="94023-113">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [<span data-ttu-id="94023-114">Instrukcje: tworzenie pola tekstowego hasła za pomocą kontrolki TextBox formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="94023-114">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="94023-115">Instrukcje: umieszczanie cudzysłowu w ciągu</span><span class="sxs-lookup"><span data-stu-id="94023-115">How to: Put Quotation Marks in a String</span></span>](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [<span data-ttu-id="94023-116">Instrukcje: zaznaczanie tekstu w kontrolce TextBox formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="94023-116">How to: Select Text in the Windows Forms TextBox Control</span></span>](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="94023-117">Instrukcje: wyświetlanie wielu wierszy w kontrolce TextBox formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="94023-117">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="94023-118">TextBox, kontrolka</span><span class="sxs-lookup"><span data-stu-id="94023-118">TextBox Control</span></span>](textbox-control-windows-forms.md)
