---
ms.openlocfilehash: 8b0617d8f021a9534289fd7ae8539cd054684862
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59774421"
---
### <a name="wpf-textboxtext-can-be-out-of-sync-with-databinding"></a><span data-ttu-id="8be65-101">Właściwość WPF TextBox.Text może być niezsynchronizowana z powodu powiązania danych</span><span class="sxs-lookup"><span data-stu-id="8be65-101">WPF TextBox.Text can be out-of-sync with databinding</span></span>

|   |   |
|---|---|
|<span data-ttu-id="8be65-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="8be65-102">Details</span></span>|<span data-ttu-id="8be65-103">W niektórych przypadkach właściwość <xref:System.Windows.Controls.TextBox.Text> odzwierciedla poprzednią wartość właściwości związanej z danymi, jeśli ta właściwość jest modyfikowana podczas operacji zapisu z wiązaniem danych.</span><span class="sxs-lookup"><span data-stu-id="8be65-103">In some cases, the <xref:System.Windows.Controls.TextBox.Text> property reflects a previous value of the databound property value if the property is modified during a databinding write operation.</span></span>|
|<span data-ttu-id="8be65-104">Sugestia</span><span class="sxs-lookup"><span data-stu-id="8be65-104">Suggestion</span></span>|<span data-ttu-id="8be65-105">Nie powinno to mieć żadnego negatywnego wpływu.</span><span class="sxs-lookup"><span data-stu-id="8be65-105">This should have no negative impact.</span></span> <span data-ttu-id="8be65-106">Jednakże można przywrócić poprzednie zachowanie przez ustawienie właściwości <xref:System.Windows.FrameworkCompatibilityPreferences.KeepTextBoxDisplaySynchronizedWithTextProperty> na <code>false</code>.</span><span class="sxs-lookup"><span data-stu-id="8be65-106">However, you can restore the previous behavior by setting the <xref:System.Windows.FrameworkCompatibilityPreferences.KeepTextBoxDisplaySynchronizedWithTextProperty> property to <code>false</code>.</span></span>|
|<span data-ttu-id="8be65-107">Zakres</span><span class="sxs-lookup"><span data-stu-id="8be65-107">Scope</span></span>|<span data-ttu-id="8be65-108">Krawędź</span><span class="sxs-lookup"><span data-stu-id="8be65-108">Edge</span></span>|
|<span data-ttu-id="8be65-109">Wersja</span><span class="sxs-lookup"><span data-stu-id="8be65-109">Version</span></span>|<span data-ttu-id="8be65-110">4.5</span><span class="sxs-lookup"><span data-stu-id="8be65-110">4.5</span></span>|
|<span data-ttu-id="8be65-111">Typ</span><span class="sxs-lookup"><span data-stu-id="8be65-111">Type</span></span>|<span data-ttu-id="8be65-112">Przekierowanie</span><span class="sxs-lookup"><span data-stu-id="8be65-112">Retargeting</span></span>|
|<span data-ttu-id="8be65-113">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="8be65-113">Affected APIs</span></span>|<ul><li><xref:System.Windows.Controls.TextBox.Text?displayProperty=nameWithType></li></ul>|
