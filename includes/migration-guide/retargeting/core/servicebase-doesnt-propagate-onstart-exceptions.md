---
ms.openlocfilehash: 519de92ca4201d199941afe6382ddf9fc480fbbd
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614778"
---
### <a name="servicebase-doesnt-propagate-onstart-exceptions"></a><span data-ttu-id="85ad9-101">ServiceBase nie propaguje wyjątków OnStart</span><span class="sxs-lookup"><span data-stu-id="85ad9-101">ServiceBase doesn't propagate OnStart exceptions</span></span>

#### <a name="details"></a><span data-ttu-id="85ad9-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="85ad9-102">Details</span></span>

<span data-ttu-id="85ad9-103">W .NET Framework 4,7 i wcześniejszych wersjach wyjątki zgłoszone podczas uruchamiania usługi nie są propagowane do obiektu wywołującego <xref:System.ServiceProcess.ServiceBase.Run%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="85ad9-103">In the .NET Framework 4.7 and earlier versions, exceptions thrown on service startup are not propagated to the caller of <xref:System.ServiceProcess.ServiceBase.Run%2A?displayProperty=nameWithType>.</span></span><br/><span data-ttu-id="85ad9-104">Począwszy od aplikacji przeznaczonych dla .NET Framework 4.7.1, środowisko uruchomieniowe propaguje wyjątki do <xref:System.ServiceProcess.ServiceBase.Run%2A?displayProperty=nameWithType> usług, których uruchomienie nie powiodło się.</span><span class="sxs-lookup"><span data-stu-id="85ad9-104">Starting with applications that target the .NET Framework 4.7.1, the runtime propagates exceptions to <xref:System.ServiceProcess.ServiceBase.Run%2A?displayProperty=nameWithType> for services that fail to start.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="85ad9-105">Sugestia</span><span class="sxs-lookup"><span data-stu-id="85ad9-105">Suggestion</span></span>

<span data-ttu-id="85ad9-106">W przypadku uruchomienia usługi, jeśli wystąpi wyjątek, ten wyjątek zostanie rozpropagowany.</span><span class="sxs-lookup"><span data-stu-id="85ad9-106">On service start, if there is an exception, that exception will be propagated.</span></span> <span data-ttu-id="85ad9-107">Powinno to pomóc zdiagnozować przypadki, w których nie można uruchomić usług.</span><span class="sxs-lookup"><span data-stu-id="85ad9-107">This should help diagnose cases where services fail to start.</span></span> <br/><span data-ttu-id="85ad9-108">Jeśli takie zachowanie jest niepożądane, można zrezygnować z niego, dodając następujący &lt; element AppContextSwitchOverrides &gt; do &lt; sekcji środowiska uruchomieniowego w &gt; pliku konfiguracyjnym aplikacji:</span><span class="sxs-lookup"><span data-stu-id="85ad9-108">If this behavior is undesirable, you can opt out of it by adding the following &lt;AppContextSwitchOverrides&gt; element to the &lt;runtime&gt; section of your application configuration file:</span></span>

```xml
<AppContextSwitchOverrides value="Switch.System.ServiceProcess.DontThrowExceptionsOnStart=true" />
```

<span data-ttu-id="85ad9-109">Jeśli aplikacja jest przeznaczona dla starszej wersji niż 4.7.1, ale chcesz mieć to zachowanie, Dodaj następujący &lt; element AppContextSwitchOverrides &gt; do &lt; sekcji środowiska uruchomieniowego w &gt; pliku konfiguracyjnym aplikacji:</span><span class="sxs-lookup"><span data-stu-id="85ad9-109">If your application targets an earlier version than 4.7.1 but you want to have this behavior, add the following &lt;AppContextSwitchOverrides&gt; element to the &lt;runtime&gt; section of your application configuration file:</span></span>

```xml
<AppContextSwitchOverrides value="Switch.System.ServiceProcess.DontThrowExceptionsOnStart=false" />
```

| <span data-ttu-id="85ad9-110">Nazwa</span><span class="sxs-lookup"><span data-stu-id="85ad9-110">Name</span></span>    | <span data-ttu-id="85ad9-111">Wartość</span><span class="sxs-lookup"><span data-stu-id="85ad9-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="85ad9-112">Zakres</span><span class="sxs-lookup"><span data-stu-id="85ad9-112">Scope</span></span>   | <span data-ttu-id="85ad9-113">Mały</span><span class="sxs-lookup"><span data-stu-id="85ad9-113">Minor</span></span>       |
| <span data-ttu-id="85ad9-114">Wersja</span><span class="sxs-lookup"><span data-stu-id="85ad9-114">Version</span></span> | <span data-ttu-id="85ad9-115">4.7.1</span><span class="sxs-lookup"><span data-stu-id="85ad9-115">4.7.1</span></span>       |
| <span data-ttu-id="85ad9-116">Typ</span><span class="sxs-lookup"><span data-stu-id="85ad9-116">Type</span></span>    | <span data-ttu-id="85ad9-117">Przekierowanie</span><span class="sxs-lookup"><span data-stu-id="85ad9-117">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="85ad9-118">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="85ad9-118">Affected APIs</span></span>

- <xref:System.ServiceProcess.ServiceBase.Run(System.ServiceProcess.ServiceBase)?displayProperty=nameWithType>
- <xref:System.ServiceProcess.ServiceBase.Run(System.ServiceProcess.ServiceBase[])?displayProperty=nameWithType>
