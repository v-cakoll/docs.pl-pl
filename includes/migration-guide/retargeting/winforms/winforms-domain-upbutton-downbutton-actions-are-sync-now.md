---
ms.openlocfilehash: f75a652f15be6b0d184db20dc5cd8aafd80539fe
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614908"
---
### <a name="winforms-domain-upbutton-and-downbutton-actions-are-in-sync-now"></a><span data-ttu-id="18dd3-101">Akcje na przycisku i DownButton domeny WinForm są teraz zsynchronizowane</span><span class="sxs-lookup"><span data-stu-id="18dd3-101">WinForm's Domain upbutton and downbutton actions are in sync now</span></span>

#### <a name="details"></a><span data-ttu-id="18dd3-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="18dd3-102">Details</span></span>

<span data-ttu-id="18dd3-103">W .NET Framework 4.7.1 i poprzednich wersjach <xref:System.Windows.Forms.DomainUpDown> Akcja kontrolki <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> jest ignorowana, gdy jest obecny tekst kontrolki, a deweloper jest zobowiązany do używania <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> akcji na formancie przed użyciem <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> akcji.</span><span class="sxs-lookup"><span data-stu-id="18dd3-103">In the .NET Framework 4.7.1 and previous versions the <xref:System.Windows.Forms.DomainUpDown> control's <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> action is ignored when control text is present, and the developer is required to use <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> action on the control before using <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> action.</span></span> <span data-ttu-id="18dd3-104">Począwszy od .NET Framework 4.7.2 obie <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> akcje i działają niezależnie w tym scenariuszu i pozostają zsynchronizowane.</span><span class="sxs-lookup"><span data-stu-id="18dd3-104">Starting with the .NET Framework 4.7.2 both the <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> and <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> actions work independently in this scenario and remain in sync.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="18dd3-105">Sugestia</span><span class="sxs-lookup"><span data-stu-id="18dd3-105">Suggestion</span></span>

<span data-ttu-id="18dd3-106">Aby aplikacja mogła korzystać z tych zmian, musi ona działać na .NET Framework 4.7.2 lub nowszym.</span><span class="sxs-lookup"><span data-stu-id="18dd3-106">In order for an application to benefit from these changes, it must run on the .NET Framework 4.7.2 or later.</span></span> <span data-ttu-id="18dd3-107">Aplikacja może korzystać z tych zmian w jeden z następujących sposobów:</span><span class="sxs-lookup"><span data-stu-id="18dd3-107">The application can benefit from these changes in either of the following ways:</span></span>

- <span data-ttu-id="18dd3-108">Zostanie ponownie skompilowana w celu przekierowania .NET Framework 4.7.2.</span><span class="sxs-lookup"><span data-stu-id="18dd3-108">It is recompiled to target the .NET Framework 4.7.2.</span></span> <span data-ttu-id="18dd3-109">Ta zmiana jest domyślnie włączona w Windows Forms aplikacjach przeznaczonych dla .NET Framework 4.7.2 lub nowszych.</span><span class="sxs-lookup"><span data-stu-id="18dd3-109">This change is enabled by default on Windows Forms applications that target the .NET Framework 4.7.2 or later.</span></span>
- <span data-ttu-id="18dd3-110">Powoduje to wypróbowanie starszego zachowania przewijania przez dodanie następującego [przełącznika AppContext](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element) do `<runtime>` sekcji pliku konfiguracyjnego aplikacji i ustawienie go na `false` , jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="18dd3-110">It opts out of the legacy scrolling behavior by adding the following [AppContext Switch](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element) to the `<runtime>` section of the app config file and setting it to `false`, as the following example shows.</span></span>

<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="18dd3-111">Nazwa</span><span class="sxs-lookup"><span data-stu-id="18dd3-111">Name</span></span>    | <span data-ttu-id="18dd3-112">Wartość</span><span class="sxs-lookup"><span data-stu-id="18dd3-112">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="18dd3-113">Zakres</span><span class="sxs-lookup"><span data-stu-id="18dd3-113">Scope</span></span>   | <span data-ttu-id="18dd3-114">Brzeg</span><span class="sxs-lookup"><span data-stu-id="18dd3-114">Edge</span></span>        |
| <span data-ttu-id="18dd3-115">Wersja</span><span class="sxs-lookup"><span data-stu-id="18dd3-115">Version</span></span> | <span data-ttu-id="18dd3-116">4.7.2</span><span class="sxs-lookup"><span data-stu-id="18dd3-116">4.7.2</span></span>       |
| <span data-ttu-id="18dd3-117">Typ</span><span class="sxs-lookup"><span data-stu-id="18dd3-117">Type</span></span>    | <span data-ttu-id="18dd3-118">Przekierowanie</span><span class="sxs-lookup"><span data-stu-id="18dd3-118">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="18dd3-119">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="18dd3-119">Affected APIs</span></span>

- <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType>
