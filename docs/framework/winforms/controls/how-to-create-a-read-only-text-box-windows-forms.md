---
title: 'Instrukcje: Tworzenie pola tekstowego tylko do odczytu (Windows Forms)'
ms.date: 03/30/2017
helpviewer_keywords:
- TextBox control [Windows Forms], read-only
- read-only text boxes
- text boxes [Windows Forms], read-only
ms.assetid: 60baa9ab-fa57-44ad-bb7c-61b05aa64296
ms.openlocfilehash: 18d2f5ed2530957487ac25c3eb6240f8bc50a938
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/13/2019
ms.locfileid: "68971941"
---
# <a name="how-to-create-a-read-only-text-box-windows-forms"></a><span data-ttu-id="cb70c-102">Instrukcje: Tworzenie pola tekstowego tylko do odczytu (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="cb70c-102">How to: Create a Read-Only Text Box (Windows Forms)</span></span>

<span data-ttu-id="cb70c-103">Możesz przekształcić edytowalne pole tekstowe Windows Forms na kontrolkę tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="cb70c-103">You can transform an editable Windows Forms text box into a read-only control.</span></span> <span data-ttu-id="cb70c-104">Na przykład pole tekstowe może wyświetlać wartość, która jest zwykle edytowana, ale może nie być obecnie ze względu na stan aplikacji.</span><span class="sxs-lookup"><span data-stu-id="cb70c-104">For example, the text box may display a value that is usually edited but may not be currently, due to the state of the application.</span></span>

## <a name="to-create-a-read-only-text-box"></a><span data-ttu-id="cb70c-105">Aby utworzyć pole tekstowe tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="cb70c-105">To create a read-only text box</span></span>

1. <span data-ttu-id="cb70c-106"><xref:System.Windows.Forms.TextBox> Ustaw Właściwość<xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> kontrolki na `true`wartość.</span><span class="sxs-lookup"><span data-stu-id="cb70c-106">Set the <xref:System.Windows.Forms.TextBox> control's <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> property to `true`.</span></span> <span data-ttu-id="cb70c-107">Po ustawieniu właściwości na `true`, użytkownicy mogą nadal przewijać i wyróżniać tekst w polu tekstowym bez zezwalania na wprowadzanie zmian.</span><span class="sxs-lookup"><span data-stu-id="cb70c-107">With the property set to `true`, users can still scroll and highlight text in a text box without allowing changes.</span></span> <span data-ttu-id="cb70c-108">Polecenie **copy** działa w polu tekstowym, ale polecenia wycinania i **wklejania** nie są.</span><span class="sxs-lookup"><span data-stu-id="cb70c-108">A **Copy** command is functional in a text box, but **Cut** and **Paste** commands are not.</span></span>

    > [!NOTE]
    > <span data-ttu-id="cb70c-109"><xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> Właściwość ma wpływ tylko na interakcję użytkownika w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="cb70c-109">The <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> property only affects user interaction at run time.</span></span> <span data-ttu-id="cb70c-110">Zawartość pola tekstowego można nadal zmieniać programowo w czasie wykonywania, zmieniając <xref:System.Windows.Forms.TextBox.Text%2A> właściwość pola tekstowego.</span><span class="sxs-lookup"><span data-stu-id="cb70c-110">You can still change text box contents programmatically at run time by changing the <xref:System.Windows.Forms.TextBox.Text%2A> property of the text box.</span></span>

## <a name="see-also"></a><span data-ttu-id="cb70c-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cb70c-111">See also</span></span>

- <xref:System.Windows.Forms.TextBox>
- [<span data-ttu-id="cb70c-112">TextBox, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="cb70c-112">TextBox Control Overview</span></span>](textbox-control-overview-windows-forms.md)
- [<span data-ttu-id="cb70c-113">Instrukcje: Kontrolowanie punktu wstawiania w kontrolce TextBox Windows Forms</span><span class="sxs-lookup"><span data-stu-id="cb70c-113">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [<span data-ttu-id="cb70c-114">Instrukcje: Tworzenie pola tekstowego hasła za pomocą kontrolki TextBox Windows Forms</span><span class="sxs-lookup"><span data-stu-id="cb70c-114">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="cb70c-115">Instrukcje: Umieszczanie cudzysłowu w ciągu</span><span class="sxs-lookup"><span data-stu-id="cb70c-115">How to: Put Quotation Marks in a String</span></span>](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [<span data-ttu-id="cb70c-116">Instrukcje: Zaznacz tekst w kontrolce TextBox Windows Forms</span><span class="sxs-lookup"><span data-stu-id="cb70c-116">How to: Select Text in the Windows Forms TextBox Control</span></span>](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="cb70c-117">Instrukcje: Wyświetl wiele wierszy w kontrolce TextBox Windows Forms</span><span class="sxs-lookup"><span data-stu-id="cb70c-117">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="cb70c-118">TextBox, kontrolka</span><span class="sxs-lookup"><span data-stu-id="cb70c-118">TextBox Control</span></span>](textbox-control-windows-forms.md)
