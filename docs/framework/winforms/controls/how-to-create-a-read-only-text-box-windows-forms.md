---
title: 'Porady: tworzenie pola tekstowego tylko do odczytu'
ms.date: 03/30/2017
helpviewer_keywords:
- TextBox control [Windows Forms], read-only
- read-only text boxes
- text boxes [Windows Forms], read-only
ms.assetid: 60baa9ab-fa57-44ad-bb7c-61b05aa64296
ms.openlocfilehash: 17ae9524009c687cd62fb315f842e188e120ac68
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76731275"
---
# <a name="how-to-create-a-read-only-text-box-windows-forms"></a><span data-ttu-id="86ac5-102">Porady: tworzenie pola tekstowego tylko do odczytu (Formularze systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="86ac5-102">How to: Create a Read-Only Text Box (Windows Forms)</span></span>

<span data-ttu-id="86ac5-103">Możesz przekształcić edytowalne pole tekstowe Windows Forms na kontrolkę tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="86ac5-103">You can transform an editable Windows Forms text box into a read-only control.</span></span> <span data-ttu-id="86ac5-104">Na przykład pole tekstowe może wyświetlać wartość, która jest zwykle edytowana, ale może nie być obecnie ze względu na stan aplikacji.</span><span class="sxs-lookup"><span data-stu-id="86ac5-104">For example, the text box may display a value that is usually edited but may not be currently, due to the state of the application.</span></span>

## <a name="to-create-a-read-only-text-box"></a><span data-ttu-id="86ac5-105">Aby utworzyć pole tekstowe tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="86ac5-105">To create a read-only text box</span></span>

1. <span data-ttu-id="86ac5-106">Ustaw właściwość <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> kontrolki <xref:System.Windows.Forms.TextBox> na `true`.</span><span class="sxs-lookup"><span data-stu-id="86ac5-106">Set the <xref:System.Windows.Forms.TextBox> control's <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> property to `true`.</span></span> <span data-ttu-id="86ac5-107">Mając właściwość o wartości `true`, użytkownicy mogą nadal przewijać i wyróżniać tekst w polu tekstowym bez zezwalania na wprowadzanie zmian.</span><span class="sxs-lookup"><span data-stu-id="86ac5-107">With the property set to `true`, users can still scroll and highlight text in a text box without allowing changes.</span></span> <span data-ttu-id="86ac5-108">Polecenie **copy** działa w polu tekstowym, ale polecenia **wycinania** i **wklejania** nie są.</span><span class="sxs-lookup"><span data-stu-id="86ac5-108">A **Copy** command is functional in a text box, but **Cut** and **Paste** commands are not.</span></span>

    > [!NOTE]
    > <span data-ttu-id="86ac5-109">Właściwość <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> ma wpływ tylko na interakcję użytkownika w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="86ac5-109">The <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> property only affects user interaction at run time.</span></span> <span data-ttu-id="86ac5-110">Zawartość pola tekstowego można nadal zmieniać programowo w czasie wykonywania, zmieniając właściwość <xref:System.Windows.Forms.TextBox.Text%2A> pola tekstowego.</span><span class="sxs-lookup"><span data-stu-id="86ac5-110">You can still change text box contents programmatically at run time by changing the <xref:System.Windows.Forms.TextBox.Text%2A> property of the text box.</span></span>

## <a name="see-also"></a><span data-ttu-id="86ac5-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="86ac5-111">See also</span></span>

- <xref:System.Windows.Forms.TextBox>
- [<span data-ttu-id="86ac5-112">TextBox, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="86ac5-112">TextBox Control Overview</span></span>](textbox-control-overview-windows-forms.md)
- [<span data-ttu-id="86ac5-113">Instrukcje: kontrolowanie punktu wstawiania w kontrolce TextBox formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="86ac5-113">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [<span data-ttu-id="86ac5-114">Instrukcje: tworzenie pola tekstowego hasła za pomocą kontrolki TextBox formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="86ac5-114">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="86ac5-115">Instrukcje: umieszczanie cudzysłowu w ciągu</span><span class="sxs-lookup"><span data-stu-id="86ac5-115">How to: Put Quotation Marks in a String</span></span>](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [<span data-ttu-id="86ac5-116">Instrukcje: zaznaczanie tekstu w kontrolce TextBox formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="86ac5-116">How to: Select Text in the Windows Forms TextBox Control</span></span>](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="86ac5-117">Instrukcje: wyświetlanie wielu wierszy w kontrolce TextBox formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="86ac5-117">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="86ac5-118">TextBox, kontrolka</span><span class="sxs-lookup"><span data-stu-id="86ac5-118">TextBox Control</span></span>](textbox-control-windows-forms.md)
