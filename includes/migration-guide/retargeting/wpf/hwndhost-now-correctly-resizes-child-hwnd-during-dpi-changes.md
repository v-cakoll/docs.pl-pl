---
ms.openlocfilehash: 3d1dc8dec18212afd815aa3de7fc82c8a1f680dc
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616313"
---
### <a name="hwndhost-now-correctly-resizes-child-hwnd-during-dpi-changes"></a><span data-ttu-id="486ad-101">HwndHost teraz prawidłowo zmienia rozmiar elementu podrzędnego (HWND) podczas zmiany DPI</span><span class="sxs-lookup"><span data-stu-id="486ad-101">HwndHost now correctly resizes child-HWND during DPI changes</span></span>

#### <a name="details"></a><span data-ttu-id="486ad-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="486ad-102">Details</span></span>

<span data-ttu-id="486ad-103">W .NET Framework 4.7.2 i starszych wersjach, gdy WPF była uruchamiana w trybie z uwzględnieniem monitora, formanty hostowane w ramach <xref:System.Windows.Interop.HwndHost> nie zostały poprawnie dopasowane po zmianie dpi, na przykład podczas przesuwania aplikacji z jednego monitora na inny.</span><span class="sxs-lookup"><span data-stu-id="486ad-103">In .NET Framework 4.7.2 and earlier versions, when WPF was run in Per-Monitor Aware mode, controls hosted within <xref:System.Windows.Interop.HwndHost> were not sized correctly after DPI changes, such as when moving applications from one monitor to another.</span></span> <span data-ttu-id="486ad-104">Ta poprawka zapewnia odpowiednie rozmiary formantów hostowanych.</span><span class="sxs-lookup"><span data-stu-id="486ad-104">This fix ensures that hosted controls are sized appropriately.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="486ad-105">Sugestia</span><span class="sxs-lookup"><span data-stu-id="486ad-105">Suggestion</span></span>

<span data-ttu-id="486ad-106">Aby aplikacja mogła korzystać z tych zmian, musi ona zostać uruchomiona w .NET Framework 4.7.2 lub nowszym, a następnie musi wybrać następujący [przełącznik AppContext](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element) w `<runtime>` sekcji pliku konfiguracji aplikacji do `false` , jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="486ad-106">In order for the application to benefit from these changes, it must run on the .NET Framework 4.7.2 or later, and it must opt-in to this behavior by setting the following [AppContext Switch](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element) in the `<runtime>` section of the app config file to `false`, as the following example shows.</span></span>

<pre><code class="lang-xml">&lt;?xml version=&quot;1.0&quot; encoding=&quot;utf-8&quot;?&gt;&#13;&#10;&lt;configuration&gt;&#13;&#10;&lt;startup&gt;&#13;&#10;&lt;supportedRuntime version=&quot;v4.0&quot; sku=&quot;.NETFramework,Version=v4.7&quot;/&gt;&#13;&#10;&lt;/startup&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;!-- AppContextSwitchOverrides value attribute is in the form of &#39;key1=true/false;key2=true/false  --&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.DoNotUsePresentationDpiCapabilityTier2OrGreater=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="486ad-107">Nazwa</span><span class="sxs-lookup"><span data-stu-id="486ad-107">Name</span></span>    | <span data-ttu-id="486ad-108">Wartość</span><span class="sxs-lookup"><span data-stu-id="486ad-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="486ad-109">Zakres</span><span class="sxs-lookup"><span data-stu-id="486ad-109">Scope</span></span>   | <span data-ttu-id="486ad-110">Duży</span><span class="sxs-lookup"><span data-stu-id="486ad-110">Major</span></span>       |
| <span data-ttu-id="486ad-111">Wersja</span><span class="sxs-lookup"><span data-stu-id="486ad-111">Version</span></span> | <span data-ttu-id="486ad-112">4,8</span><span class="sxs-lookup"><span data-stu-id="486ad-112">4.8</span></span>         |
| <span data-ttu-id="486ad-113">Typ</span><span class="sxs-lookup"><span data-stu-id="486ad-113">Type</span></span>    | <span data-ttu-id="486ad-114">Przekierowanie</span><span class="sxs-lookup"><span data-stu-id="486ad-114">Retargeting</span></span> |
