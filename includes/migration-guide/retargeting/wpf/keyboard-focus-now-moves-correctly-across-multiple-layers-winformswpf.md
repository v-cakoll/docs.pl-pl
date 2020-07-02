---
ms.openlocfilehash: a82b720fd4e771481ea1142a88a095443afa0d5b
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614945"
---
### <a name="keyboard-focus-now-moves-correctly-across-multiple-layers-of-winformswpf-hosting"></a><span data-ttu-id="f451b-101">Fokus klawiatury jest teraz przenoszony prawidłowo między wieloma warstwami WinForms/hostingu WPF</span><span class="sxs-lookup"><span data-stu-id="f451b-101">Keyboard focus now moves correctly across multiple layers of WinForms/WPF hosting</span></span>

#### <a name="details"></a><span data-ttu-id="f451b-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="f451b-102">Details</span></span>

<span data-ttu-id="f451b-103">Rozważmy aplikację WPF hostującym kontrolkę WinForms, która z kolei umożliwia hostowanie formantów WPF.</span><span class="sxs-lookup"><span data-stu-id="f451b-103">Consider a WPF application hosting a WinForms control which in turn hosts WPF controls.</span></span> <span data-ttu-id="f451b-104">Użytkownicy mogą nie być w stanie wystawić karty z warstwy WinForms, jeśli pierwszy lub ostatni formant w tej warstwie jest WPF `System.Windows.Forms.Integration.ElementHost` .</span><span class="sxs-lookup"><span data-stu-id="f451b-104">Users may not be able to tab out of the WinForms layer if the first or last control in that layer is the WPF `System.Windows.Forms.Integration.ElementHost`.</span></span> <span data-ttu-id="f451b-105">Ta zmiana rozwiązuje ten problem, a użytkownicy mogą teraz wystawić kartę z warstwy WinForms. Zautomatyzowane aplikacje, które opierają się na koncentracji, nigdy nie ucieczką warstwy WinForms, mogą przestać działać zgodnie z oczekiwaniami.</span><span class="sxs-lookup"><span data-stu-id="f451b-105">This change fixes this issue, and users are now able to tab out of the WinForms layer.Automated applications that rely on focus never escaping the WinForms layer may no longer work as expected.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="f451b-106">Sugestia</span><span class="sxs-lookup"><span data-stu-id="f451b-106">Suggestion</span></span>

<span data-ttu-id="f451b-107">Deweloperzy, którzy chcą korzystać z tej zmiany podczas określania wersji platformy pod kątem platformy .NET 4.7.2, mogą ustawić dla następujących zestawów flag AppContext wartość false, aby zmiana została włączona.</span><span class="sxs-lookup"><span data-stu-id="f451b-107">A developer who wants to utilize this change while targeting a framework version below .NET 4.7.2 can set the following set of AppContext flags to false for the change to be enabled.</span></span>

<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

<span data-ttu-id="f451b-108">Aplikacje WPF muszą wyrazić zgodę na wszystkie ulepszenia wczesnego dostępu, aby uzyskać dalsze ulepszenia.</span><span class="sxs-lookup"><span data-stu-id="f451b-108">WPF applications must opt in to all early accessibility improvements to get the later improvements.</span></span> <span data-ttu-id="f451b-109">Innymi słowy, zarówno, `Switch.UseLegacyAccessibilityFeatures` jak i `Switch.UseLegacyAccessibilityFeatures.2` przełączników musi być setA Deweloper, który wymaga powyższej funkcjonalności, podczas gdy przeznaczony dla programu .NET 4.7.2 lub nowszego można ustawić dla następującej flagi AppContext wartość true, aby zmiana została wyłączona.</span><span class="sxs-lookup"><span data-stu-id="f451b-109">In other words, both the `Switch.UseLegacyAccessibilityFeatures` and the `Switch.UseLegacyAccessibilityFeatures.2` switches must be setA developer who requires the previous functionality while targeting .NET 4.7.2 or greater can set the following AppContext flag to true for the change to be disabled.</span></span>

<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures.2=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="f451b-110">Nazwa</span><span class="sxs-lookup"><span data-stu-id="f451b-110">Name</span></span>    | <span data-ttu-id="f451b-111">Wartość</span><span class="sxs-lookup"><span data-stu-id="f451b-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="f451b-112">Zakres</span><span class="sxs-lookup"><span data-stu-id="f451b-112">Scope</span></span>   | <span data-ttu-id="f451b-113">Brzeg</span><span class="sxs-lookup"><span data-stu-id="f451b-113">Edge</span></span>        |
| <span data-ttu-id="f451b-114">Wersja</span><span class="sxs-lookup"><span data-stu-id="f451b-114">Version</span></span> | <span data-ttu-id="f451b-115">4.7.2</span><span class="sxs-lookup"><span data-stu-id="f451b-115">4.7.2</span></span>       |
| <span data-ttu-id="f451b-116">Typ</span><span class="sxs-lookup"><span data-stu-id="f451b-116">Type</span></span>    | <span data-ttu-id="f451b-117">Przekierowanie</span><span class="sxs-lookup"><span data-stu-id="f451b-117">Retargeting</span></span> |
