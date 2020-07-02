---
ms.openlocfilehash: 7c2e80669d9ef27f87cde9442d8eeab0ee31a524
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614978"
---
### <a name="wpf-textboxpasswordbox-text-selection-does-not-follow-system-colors"></a><span data-ttu-id="0ea5f-101">Element TextBox/PasswordBox tekstu WPF nie jest zgodny z kolorami systemu</span><span class="sxs-lookup"><span data-stu-id="0ea5f-101">WPF TextBox/PasswordBox Text Selection Does Not Follow System Colors</span></span>

#### <a name="details"></a><span data-ttu-id="0ea5f-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="0ea5f-102">Details</span></span>

<span data-ttu-id="0ea5f-103">W .NET Framework 4.7.1 i starszych wersjach, WPF `System.Windows.Controls.TextBox` i `System.Windows.Controls.PasswordBox` można renderować tylko zaznaczenie tekstu w warstwie modułu definiowania układu.</span><span class="sxs-lookup"><span data-stu-id="0ea5f-103">In .NET Framework 4.7.1 and earlier versions, WPF `System.Windows.Controls.TextBox` and `System.Windows.Controls.PasswordBox` could only render a text selection in the Adorner layer.</span></span> <span data-ttu-id="0ea5f-104">W niektórych motywach systemu occlude tekstu, co trudno odczytać.</span><span class="sxs-lookup"><span data-stu-id="0ea5f-104">In some system themes this would occlude text, making it hard to read.</span></span>  <span data-ttu-id="0ea5f-105">W .NET Framework 4.7.2 i nowszych deweloperzy mogą korzystać z opcji włączania schematu renderowania wyboru, który pozwala uniknąć tego problemu.</span><span class="sxs-lookup"><span data-stu-id="0ea5f-105">In .NET Framework 4.7.2 and later, developers have an option of enabling a non-Adorner-based selection rendering scheme that alleviates this issue.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="0ea5f-106">Sugestia</span><span class="sxs-lookup"><span data-stu-id="0ea5f-106">Suggestion</span></span>

<span data-ttu-id="0ea5f-107">Deweloperzy, którzy chcą korzystać z tej zmiany, muszą odpowiednio ustawić następującą flagę AppContext.</span><span class="sxs-lookup"><span data-stu-id="0ea5f-107">A developer who wants to utilize this change must set the following AppContext flag appropriately.</span></span>  <span data-ttu-id="0ea5f-108">Aby można było korzystać z tej funkcji, zainstalowana wersja .NET Framework musi być 4.7.2 lub nowsza. Aby włączyć wybór poza modułem definiowania układu, użyj następującej flagi AppContext.</span><span class="sxs-lookup"><span data-stu-id="0ea5f-108">To utilize this feature, the installed .NET Framework version must be 4.7.2 or greater.To enabled the non-adorner-based selection, use the following AppContext flag.</span></span><pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.Text.UseAdornerForTextboxSelectionRendering=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="0ea5f-109">Nazwa</span><span class="sxs-lookup"><span data-stu-id="0ea5f-109">Name</span></span>    | <span data-ttu-id="0ea5f-110">Wartość</span><span class="sxs-lookup"><span data-stu-id="0ea5f-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="0ea5f-111">Zakres</span><span class="sxs-lookup"><span data-stu-id="0ea5f-111">Scope</span></span>   | <span data-ttu-id="0ea5f-112">Brzeg</span><span class="sxs-lookup"><span data-stu-id="0ea5f-112">Edge</span></span>        |
| <span data-ttu-id="0ea5f-113">Wersja</span><span class="sxs-lookup"><span data-stu-id="0ea5f-113">Version</span></span> | <span data-ttu-id="0ea5f-114">4.7.2</span><span class="sxs-lookup"><span data-stu-id="0ea5f-114">4.7.2</span></span>       |
| <span data-ttu-id="0ea5f-115">Typ</span><span class="sxs-lookup"><span data-stu-id="0ea5f-115">Type</span></span>    | <span data-ttu-id="0ea5f-116">Przekierowanie</span><span class="sxs-lookup"><span data-stu-id="0ea5f-116">Retargeting</span></span> |
