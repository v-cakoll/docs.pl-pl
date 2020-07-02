---
ms.openlocfilehash: 9c9c4ec55143ef991e9b69a389e0f3368263bb4e
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614847"
---
### <a name="nullreferenceexception-in-exception-handling-code-from-imagesourceconverterconvertfrom"></a><span data-ttu-id="c14e0-101">NullReferenceException w kodzie obsługującym wyjątek z ImageSourceConverter. ConvertFrom</span><span class="sxs-lookup"><span data-stu-id="c14e0-101">NullReferenceException in exception handling code from ImageSourceConverter.ConvertFrom</span></span>

#### <a name="details"></a><span data-ttu-id="c14e0-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="c14e0-102">Details</span></span>

<span data-ttu-id="c14e0-103">Błąd w kodzie obsługi wyjątku dla <xref:System.Windows.Media.ImageSourceConverter.ConvertFrom(System.ComponentModel.ITypeDescriptorContext,System.Globalization.CultureInfo,System.Object)> spowodowany błędem <xref:System.NullReferenceException?displayProperty=fullName> został zgłoszony, zamiast zamierzonego wyjątku ( <xref:System.IO.DirectoryNotFoundException?displayProperty=fullName> lub <xref:System.IO.FileNotFoundException?displayProperty=fullName> ).</span><span class="sxs-lookup"><span data-stu-id="c14e0-103">An error in the exception handling code for <xref:System.Windows.Media.ImageSourceConverter.ConvertFrom(System.ComponentModel.ITypeDescriptorContext,System.Globalization.CultureInfo,System.Object)> caused an incorrect <xref:System.NullReferenceException?displayProperty=fullName> to be thrown instead of the intended exception ( <xref:System.IO.DirectoryNotFoundException?displayProperty=fullName> or <xref:System.IO.FileNotFoundException?displayProperty=fullName>).</span></span> <span data-ttu-id="c14e0-104">Ta zmiana koryguje ten błąd, aby Metoda teraz wyrzucał właściwy wyjątek.</span><span class="sxs-lookup"><span data-stu-id="c14e0-104">This change corrects that error so that the method now throws the right exception.</span></span> <p/><span data-ttu-id="c14e0-105">Domyślnie wszystkie aplikacje ukierunkowane na .NET Framework 4.6.2 i poprzednie nadal generują <xref:System.NullReferenceException?displayProperty=fullName> zgodność.</span><span class="sxs-lookup"><span data-stu-id="c14e0-105">By default all applications targeting .NET Framework 4.6.2 and earlier continue to throw <xref:System.NullReferenceException?displayProperty=fullName> for compatibility.</span></span> <span data-ttu-id="c14e0-106">Deweloperzy ukierunkowani na .NET Framework 4,7 i nowsze powinny zobaczyć właściwe wyjątki.</span><span class="sxs-lookup"><span data-stu-id="c14e0-106">Developers targeting .NET Framework 4.7 and above should see the right exceptions.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="c14e0-107">Sugestia</span><span class="sxs-lookup"><span data-stu-id="c14e0-107">Suggestion</span></span>

<span data-ttu-id="c14e0-108">Deweloperzy, którzy chcą wrócić do uzyskania, <xref:System.NullReferenceException?displayProperty=fullName> gdy celem .NET Framework 4,7 lub nowszym będzie Dodawanie/scalanie następujących elementów w pliku App.config aplikacji:</span><span class="sxs-lookup"><span data-stu-id="c14e0-108">Developers who wish to revert to getting <xref:System.NullReferenceException?displayProperty=fullName> when targeting .NET Framework 4.7 or later can add/merge the following to their application's App.config file:</span></span>

<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Media.ImageSourceConverter.OverrideExceptionWithNullReferenceException=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="c14e0-109">Nazwa</span><span class="sxs-lookup"><span data-stu-id="c14e0-109">Name</span></span>    | <span data-ttu-id="c14e0-110">Wartość</span><span class="sxs-lookup"><span data-stu-id="c14e0-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="c14e0-111">Zakres</span><span class="sxs-lookup"><span data-stu-id="c14e0-111">Scope</span></span>   | <span data-ttu-id="c14e0-112">Brzeg</span><span class="sxs-lookup"><span data-stu-id="c14e0-112">Edge</span></span>        |
| <span data-ttu-id="c14e0-113">Wersja</span><span class="sxs-lookup"><span data-stu-id="c14e0-113">Version</span></span> | <span data-ttu-id="c14e0-114">4,7</span><span class="sxs-lookup"><span data-stu-id="c14e0-114">4.7</span></span>         |
| <span data-ttu-id="c14e0-115">Typ</span><span class="sxs-lookup"><span data-stu-id="c14e0-115">Type</span></span>    | <span data-ttu-id="c14e0-116">Przekierowanie</span><span class="sxs-lookup"><span data-stu-id="c14e0-116">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="c14e0-117">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="c14e0-117">Affected APIs</span></span>

- <xref:System.Windows.Media.ImageSourceConverter.ConvertFrom(System.ComponentModel.ITypeDescriptorContext,System.Globalization.CultureInfo,System.Object)?displayProperty=nameWithType>
