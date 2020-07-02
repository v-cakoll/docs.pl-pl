---
ms.openlocfilehash: 811b1a91169eeebfa056d9ecdb07d342d3b32d85
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615712"
---
### <a name="icontobitmap-successfully-converts-icons-with-png-frames-into-bitmap-objects"></a><span data-ttu-id="f8925-101">Ikona. ToBitmap pomyślnie konwertuje ikony z ramkami PNG na obiekty map bitowych</span><span class="sxs-lookup"><span data-stu-id="f8925-101">Icon.ToBitmap successfully converts icons with PNG frames into Bitmap objects</span></span>

#### <a name="details"></a><span data-ttu-id="f8925-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="f8925-102">Details</span></span>

<span data-ttu-id="f8925-103">Począwszy od aplikacji przeznaczonych dla .NET Framework 4,6, <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> metoda pomyślnie konwertuje ikony z ramkami PNG na obiekty map bitowych.</span><span class="sxs-lookup"><span data-stu-id="f8925-103">Starting with the apps that target the .NET Framework 4.6, the <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> method successfully converts icons with PNG frames into Bitmap objects.</span></span><p/><span data-ttu-id="f8925-104">W aplikacjach przeznaczonych dla .NET Framework 4.5.2 i starszych wersji <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> Metoda zgłasza <xref:System.ArgumentOutOfRangeException> wyjątek, jeśli obiekt ikony ma ramki PNG.</span><span class="sxs-lookup"><span data-stu-id="f8925-104">In apps that target the .NET Framework 4.5.2 and earlier versions, the  <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> method throws an <xref:System.ArgumentOutOfRangeException> exception if the Icon object has PNG frames.</span></span><p/><span data-ttu-id="f8925-105">Ta zmiana ma wpływ na aplikacje, które są ponownie kompilowane pod kątem .NET Framework 4,6 i implementowanie specjalnej obsługi dla <xref:System.ArgumentOutOfRangeException> , która jest generowany, gdy obiekt ikony ma ramki PNG.</span><span class="sxs-lookup"><span data-stu-id="f8925-105">This change affects apps that are recompiled to target the .NET Framework 4.6 and that implement special handling for the <xref:System.ArgumentOutOfRangeException> that is thrown when an Icon object has PNG frames.</span></span> <span data-ttu-id="f8925-106">W przypadku uruchamiania w .NET Framework 4,6, konwersja kończy się powodzeniem, <xref:System.ArgumentOutOfRangeException> nie jest już zgłaszane i w związku z tym program obsługi wyjątków nie jest już wywoływany.</span><span class="sxs-lookup"><span data-stu-id="f8925-106">When running under the .NET Framework 4.6, the conversion is successful, an <xref:System.ArgumentOutOfRangeException> is no longer thrown, and therefore the exception handler is no longer invoked.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="f8925-107">Sugestia</span><span class="sxs-lookup"><span data-stu-id="f8925-107">Suggestion</span></span>

<span data-ttu-id="f8925-108">Jeśli takie zachowanie jest niepożądane, można zachować poprzednie zachowanie, dodając następujący element do `<runtime>` sekcji pliku app.config:</span><span class="sxs-lookup"><span data-stu-id="f8925-108">If this behavior is undesirable, you can retain the previous behavior by adding the following element to the `<runtime>` section of your app.config file:</span></span>

<pre><code class="lang-xml">&lt;AppContextSwitchOverrides&#13;&#10;value=&quot;Switch.System.Drawing.DontSupportPngFramesInIcons=true&quot; /&gt;&#13;&#10;</code></pre>

<span data-ttu-id="f8925-109">Jeśli plik app.config zawiera już `AppContextSwitchOverrides` element, Nowa wartość powinna zostać scalona z atrybutem Value w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="f8925-109">If the app.config file already contains the `AppContextSwitchOverrides` element, the new value should be merged with the value attribute like this:</span></span>

<pre><code class="lang-xml">&lt;AppContextSwitchOverrides&#13;&#10;value=&quot;Switch.System.Drawing.DontSupportPngFramesInIcons=true;&lt;previous key&gt;=&lt;previous value&gt;&quot; /&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="f8925-110">Nazwa</span><span class="sxs-lookup"><span data-stu-id="f8925-110">Name</span></span>    | <span data-ttu-id="f8925-111">Wartość</span><span class="sxs-lookup"><span data-stu-id="f8925-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="f8925-112">Zakres</span><span class="sxs-lookup"><span data-stu-id="f8925-112">Scope</span></span>   | <span data-ttu-id="f8925-113">Mały</span><span class="sxs-lookup"><span data-stu-id="f8925-113">Minor</span></span>       |
| <span data-ttu-id="f8925-114">Wersja</span><span class="sxs-lookup"><span data-stu-id="f8925-114">Version</span></span> | <span data-ttu-id="f8925-115">4.6</span><span class="sxs-lookup"><span data-stu-id="f8925-115">4.6</span></span>         |
| <span data-ttu-id="f8925-116">Typ</span><span class="sxs-lookup"><span data-stu-id="f8925-116">Type</span></span>    | <span data-ttu-id="f8925-117">Przekierowanie</span><span class="sxs-lookup"><span data-stu-id="f8925-117">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="f8925-118">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="f8925-118">Affected APIs</span></span>

- <xref:System.Drawing.Icon.ToBitmap?displayProperty=nameWithType>
