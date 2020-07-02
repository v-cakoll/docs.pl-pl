---
title: 'Porady: tworzenie pola tekstowego tylko do odczytu'
description: Dowiedz się więcej na temat przekształcania edytowalnego pola tekstowego Windows Forms w pole tekstowe tylko do odczytu Windows Forms.
ms.date: 03/30/2017
helpviewer_keywords:
- TextBox control [Windows Forms], read-only
- read-only text boxes
- text boxes [Windows Forms], read-only
ms.assetid: 60baa9ab-fa57-44ad-bb7c-61b05aa64296
ms.openlocfilehash: 5baa7c66d5f16560a4ea23861d563b099592957f
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619367"
---
# <a name="how-to-create-a-read-only-text-box-windows-forms"></a><span data-ttu-id="b037c-103">Porady: tworzenie pola tekstowego tylko do odczytu (Formularze systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="b037c-103">How to: Create a Read-Only Text Box (Windows Forms)</span></span>

<span data-ttu-id="b037c-104">Możesz przekształcić edytowalne pole tekstowe Windows Forms na kontrolkę tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="b037c-104">You can transform an editable Windows Forms text box into a read-only control.</span></span> <span data-ttu-id="b037c-105">Na przykład pole tekstowe może wyświetlać wartość, która jest zwykle edytowana, ale może nie być obecnie ze względu na stan aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b037c-105">For example, the text box may display a value that is usually edited but may not be currently, due to the state of the application.</span></span>

## <a name="to-create-a-read-only-text-box"></a><span data-ttu-id="b037c-106">Aby utworzyć pole tekstowe tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="b037c-106">To create a read-only text box</span></span>

1. <span data-ttu-id="b037c-107">Ustaw <xref:System.Windows.Forms.TextBox> Właściwość kontrolki <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> na wartość `true` .</span><span class="sxs-lookup"><span data-stu-id="b037c-107">Set the <xref:System.Windows.Forms.TextBox> control's <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> property to `true`.</span></span> <span data-ttu-id="b037c-108">Po ustawieniu właściwości na `true` , użytkownicy mogą nadal przewijać i wyróżniać tekst w polu tekstowym bez zezwalania na wprowadzanie zmian.</span><span class="sxs-lookup"><span data-stu-id="b037c-108">With the property set to `true`, users can still scroll and highlight text in a text box without allowing changes.</span></span> <span data-ttu-id="b037c-109">Polecenie **copy** działa w polu tekstowym, ale polecenia **wycinania** i **wklejania** nie są.</span><span class="sxs-lookup"><span data-stu-id="b037c-109">A **Copy** command is functional in a text box, but **Cut** and **Paste** commands are not.</span></span>

    > [!NOTE]
    > <span data-ttu-id="b037c-110"><xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A>Właściwość ma wpływ tylko na interakcję użytkownika w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="b037c-110">The <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> property only affects user interaction at run time.</span></span> <span data-ttu-id="b037c-111">Zawartość pola tekstowego można nadal zmieniać programowo w czasie wykonywania, zmieniając <xref:System.Windows.Forms.TextBox.Text%2A> Właściwość pola tekstowego.</span><span class="sxs-lookup"><span data-stu-id="b037c-111">You can still change text box contents programmatically at run time by changing the <xref:System.Windows.Forms.TextBox.Text%2A> property of the text box.</span></span>

## <a name="see-also"></a><span data-ttu-id="b037c-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b037c-112">See also</span></span>

- <xref:System.Windows.Forms.TextBox>
- [<span data-ttu-id="b037c-113">TextBox, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="b037c-113">TextBox Control Overview</span></span>](textbox-control-overview-windows-forms.md)
- [<span data-ttu-id="b037c-114">Instrukcje: kontrolowanie punktu wstawiania w kontrolce TextBox formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b037c-114">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [<span data-ttu-id="b037c-115">Instrukcje: tworzenie pola tekstowego hasła za pomocą kontrolki TextBox formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b037c-115">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="b037c-116">Instrukcje: umieszczanie cudzysłowu w ciągu</span><span class="sxs-lookup"><span data-stu-id="b037c-116">How to: Put Quotation Marks in a String</span></span>](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [<span data-ttu-id="b037c-117">Porady: zaznaczanie tekstu w formancie TextBox formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="b037c-117">How to: Select Text in the Windows Forms TextBox Control</span></span>](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="b037c-118">Instrukcje: wyświetlanie wielu wierszy w kontrolce TextBox formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b037c-118">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="b037c-119">TextBox — Formant</span><span class="sxs-lookup"><span data-stu-id="b037c-119">TextBox Control</span></span>](textbox-control-windows-forms.md)
