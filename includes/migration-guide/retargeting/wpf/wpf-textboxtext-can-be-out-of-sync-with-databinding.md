---
ms.openlocfilehash: d0de1a262d57c67dd4dfb258d5ac013af5d8783d
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617294"
---
### <a name="wpf-textboxtext-can-be-out-of-sync-with-databinding"></a><span data-ttu-id="03525-101">Właściwość WPF TextBox.Text może być niezsynchronizowana z powodu powiązania danych</span><span class="sxs-lookup"><span data-stu-id="03525-101">WPF TextBox.Text can be out-of-sync with databinding</span></span>

#### <a name="details"></a><span data-ttu-id="03525-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="03525-102">Details</span></span>

<span data-ttu-id="03525-103">W niektórych przypadkach właściwość <xref:System.Windows.Controls.TextBox.Text> odzwierciedla poprzednią wartość właściwości związanej z danymi, jeśli ta właściwość jest modyfikowana podczas operacji zapisu z wiązaniem danych.</span><span class="sxs-lookup"><span data-stu-id="03525-103">In some cases, the <xref:System.Windows.Controls.TextBox.Text> property reflects a previous value of the databound property value if the property is modified during a databinding write operation.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="03525-104">Sugestia</span><span class="sxs-lookup"><span data-stu-id="03525-104">Suggestion</span></span>

<span data-ttu-id="03525-105">Nie powinno to mieć żadnego negatywnego wpływu.</span><span class="sxs-lookup"><span data-stu-id="03525-105">This should have no negative impact.</span></span> <span data-ttu-id="03525-106">Jednakże można przywrócić poprzednie zachowanie przez ustawienie właściwości <xref:System.Windows.FrameworkCompatibilityPreferences.KeepTextBoxDisplaySynchronizedWithTextProperty> na `false`.</span><span class="sxs-lookup"><span data-stu-id="03525-106">However, you can restore the previous behavior by setting the <xref:System.Windows.FrameworkCompatibilityPreferences.KeepTextBoxDisplaySynchronizedWithTextProperty> property to `false`.</span></span>

| <span data-ttu-id="03525-107">Nazwa</span><span class="sxs-lookup"><span data-stu-id="03525-107">Name</span></span>    | <span data-ttu-id="03525-108">Wartość</span><span class="sxs-lookup"><span data-stu-id="03525-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="03525-109">Zakres</span><span class="sxs-lookup"><span data-stu-id="03525-109">Scope</span></span>   | <span data-ttu-id="03525-110">Brzeg</span><span class="sxs-lookup"><span data-stu-id="03525-110">Edge</span></span>        |
| <span data-ttu-id="03525-111">Wersja</span><span class="sxs-lookup"><span data-stu-id="03525-111">Version</span></span> | <span data-ttu-id="03525-112">4.5</span><span class="sxs-lookup"><span data-stu-id="03525-112">4.5</span></span>         |
|<span data-ttu-id="03525-113">Typ</span><span class="sxs-lookup"><span data-stu-id="03525-113">Type</span></span>|<span data-ttu-id="03525-114">Przekierowanie</span><span class="sxs-lookup"><span data-stu-id="03525-114">Retargeting</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="03525-115">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="03525-115">Affected APIs</span></span>

- <xref:System.Windows.Controls.TextBox.Text?displayProperty=nameWithType>
