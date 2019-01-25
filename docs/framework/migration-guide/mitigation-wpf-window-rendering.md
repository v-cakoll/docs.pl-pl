---
title: 'Środki zaradcze: Renderowanie okien WPF'
ms.date: 03/30/2017
ms.assetid: 28ed6bf8-141b-4b73-a4e3-44a99fae5084
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 71e1829716e0a9d5fc63692ca84c8bfefe4cefef
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54663469"
---
# <a name="mitigation-wpf-window-rendering"></a><span data-ttu-id="fdd11-102">Środki zaradcze: Renderowanie okien WPF</span><span class="sxs-lookup"><span data-stu-id="fdd11-102">Mitigation: WPF Window Rendering</span></span>
<span data-ttu-id="fdd11-103">W [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] działa w systemie Windows 8 i nowszych, całe okno jest renderowany bez przycinania, gdy wykraczał poza jednym wyświetlana w przypadku wielu monitorów.</span><span class="sxs-lookup"><span data-stu-id="fdd11-103">In the [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] running on Windows 8 and above, the entire window is rendered without clipping when it extends outside of single display in a multi-monitor scenario.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="fdd11-104">Wpływ</span><span class="sxs-lookup"><span data-stu-id="fdd11-104">Impact</span></span>  
 <span data-ttu-id="fdd11-105">Ogólnie rzecz biorąc renderowanie całe okno na wiele monitorów bez przycinania to oczekiwane zachowanie.</span><span class="sxs-lookup"><span data-stu-id="fdd11-105">In general, rendering an entire window across multiple monitors without clipping is the expected behavior.</span></span> <span data-ttu-id="fdd11-106">Jednak na Windows 7 i starszych wersjach, WPF, windows powoduje ich rozszerzania poza pojedynczy ekran, ponieważ renderowanie części okna na drugim monitorze ma wpływ na wydajność znaczące.</span><span class="sxs-lookup"><span data-stu-id="fdd11-106">However, on Windows 7 and earlier versions, WPF windows are clipped when they extend beyond a single display because rendering a portion of the window on the second monitor has a significant performance impact.</span></span>  
  
 <span data-ttu-id="fdd11-107">Dokładne wpływ renderowanie okien WPF na monitorów w systemie Windows 8 lub nowszym nie jest dokładnie wymierne, ponieważ zależy od wielu czynników.</span><span class="sxs-lookup"><span data-stu-id="fdd11-107">The precise impact of rendering WPF windows across monitors on Windows 8 and above is not precisely quantifiable since it depends on a large number of factors.</span></span> <span data-ttu-id="fdd11-108">W niektórych przypadkach go może dać nadal niekorzystny wpływ na wydajność, szczególnie w przypadku użytkowników, którzy uruchamiania aplikacji intensywnie korzystających z grafiki i czy masz system windows międzystrefowymi monitorów.</span><span class="sxs-lookup"><span data-stu-id="fdd11-108">In some cases, it may still produce an undesirable impact on performance, particularly for users who run graphics-intensive applications and have windows straddling monitors.</span></span> <span data-ttu-id="fdd11-109">W innych przypadkach może po prostu chcesz spójne zachowanie różnych wersji programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="fdd11-109">In other cases, you may simply want a consistent behavior across .NET Framework versions.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="fdd11-110">Ograniczenie</span><span class="sxs-lookup"><span data-stu-id="fdd11-110">Mitigation</span></span>  
 <span data-ttu-id="fdd11-111">Można wyłączyć tej zmiany i powrócić do poprzedniego zachowania przycinania okna WPF, gdy wykraczał poza pojedynczy ekran.</span><span class="sxs-lookup"><span data-stu-id="fdd11-111">You can disable this change and revert to the previous behavior of clipping a WPF window when it extends beyond a single display.</span></span> <span data-ttu-id="fdd11-112">Istnieją dwa sposoby wykonania tej czynności:</span><span class="sxs-lookup"><span data-stu-id="fdd11-112">There are two ways to do this:</span></span>  
  
-   <span data-ttu-id="fdd11-113">Dodając `<EnableMultiMonitorDisplayClipping>` elementu `<appSettings>` sekcję pliku konfiguracji aplikacji można wyłączyć lub włączyć to zachowanie w aplikacje działające w systemie Windows 8 lub nowszym.</span><span class="sxs-lookup"><span data-stu-id="fdd11-113">By adding the `<EnableMultiMonitorDisplayClipping>` element to the `<appSettings>` section of your application configuration file, you can disable or enable this behavior on apps running on Windows 8 or later.</span></span> <span data-ttu-id="fdd11-114">Na przykład w poniższej sekcji konfiguracji wyłącza renderowanie, bez przycinania:</span><span class="sxs-lookup"><span data-stu-id="fdd11-114">For example, the following configuration section disables rendering without clipping:</span></span>  
  
    ```xml  
    <appSettings>  
        <add key="EnableMultiMonitorDisplayClipping" value="true"/>  
      </appSettings>  
    ```  
  
     <span data-ttu-id="fdd11-115">`<EnableMultiMonitorDisplayClipping>` Ustawienie konfiguracji może mieć jedną z dwóch wartości:</span><span class="sxs-lookup"><span data-stu-id="fdd11-115">The `<EnableMultiMonitorDisplayClipping>` configuration setting can have either of two values:</span></span>  
  
    -   <span data-ttu-id="fdd11-116">`true`, aby umożliwić wycinka monitorowania granic podczas renderowania w systemie windows.</span><span class="sxs-lookup"><span data-stu-id="fdd11-116">`true`, to enable clipping of windows to monitor bounds during rendering.</span></span>  
  
    -   <span data-ttu-id="fdd11-117">`false`, aby wyłączyć obcinanie do systemu windows do monitorowania granic podczas renderowania.</span><span class="sxs-lookup"><span data-stu-id="fdd11-117">`false`, to disable clipping of windows to monitor bounds during rendering.</span></span>  
  
-   <span data-ttu-id="fdd11-118">Ustawiając <xref:System.Windows.CoreCompatibilityPreferences.EnableMultiMonitorDisplayClipping%2A> właściwości `true` przy uruchamianiu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="fdd11-118">By setting the <xref:System.Windows.CoreCompatibilityPreferences.EnableMultiMonitorDisplayClipping%2A> property to `true` at app startup.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fdd11-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fdd11-119">See also</span></span>
- [<span data-ttu-id="fdd11-120">Zmiany środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="fdd11-120">Runtime Changes</span></span>](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-6.md)
