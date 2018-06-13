---
title: 'Ograniczenie: renderowanie okien WPF'
ms.date: 03/30/2017
ms.assetid: 28ed6bf8-141b-4b73-a4e3-44a99fae5084
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8a91839ff12109b84c563dcd3fabd078f75dad9f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33389571"
---
# <a name="mitigation-wpf-window-rendering"></a><span data-ttu-id="e4bb9-102">Ograniczenie: renderowanie okien WPF</span><span class="sxs-lookup"><span data-stu-id="e4bb9-102">Mitigation: WPF Window Rendering</span></span>
<span data-ttu-id="e4bb9-103">W [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] działa w systemie Windows 8 i nowszym, całe okno jest renderowany bez przycinania, gdy wykraczał poza pojedynczy wyświetlana w przypadku wielu monitora.</span><span class="sxs-lookup"><span data-stu-id="e4bb9-103">In the [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] running on Windows 8 and above, the entire window is rendered without clipping when it extends outside of single display in a multi-monitor scenario.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="e4bb9-104">Wpływ</span><span class="sxs-lookup"><span data-stu-id="e4bb9-104">Impact</span></span>  
 <span data-ttu-id="e4bb9-105">Ogólnie rzecz biorąc renderowania całe okno na wiele monitorów bez wycinka jest oczekiwane zachowanie.</span><span class="sxs-lookup"><span data-stu-id="e4bb9-105">In general, rendering an entire window across multiple monitors without clipping is the expected behavior.</span></span> <span data-ttu-id="e4bb9-106">Jednak na system Windows 7 i wcześniejsze wersje systemu windows WPF są kadrowane, gdy one wykraczać poza pojedynczy wyświetlania, ponieważ renderowanie części okna na drugim monitorze ma wpływ na wydajność znaczących.</span><span class="sxs-lookup"><span data-stu-id="e4bb9-106">However, on Windows 7 and earlier versions, WPF windows are clipped when they extend beyond a single display because rendering a portion of the window on the second monitor has a significant performance impact.</span></span>  
  
 <span data-ttu-id="e4bb9-107">Dokładne wpływ renderowanie okien WPF na monitorów w systemie Windows 8 lub nowszym nie jest dokładnie wymierne, ponieważ zależy od wielu czynników.</span><span class="sxs-lookup"><span data-stu-id="e4bb9-107">The precise impact of rendering WPF windows across monitors on Windows 8 and above is not precisely quantifiable since it depends on a large number of factors.</span></span> <span data-ttu-id="e4bb9-108">W niektórych przypadkach mogą go nadal dawać niekorzystny wpływ na wydajność, szczególnie w przypadku użytkowników, którzy uruchamiania aplikacji z dużą ilością grafiki i czy masz system windows międzystrefowymi monitorów.</span><span class="sxs-lookup"><span data-stu-id="e4bb9-108">In some cases, it may still produce an undesirable impact on performance, particularly for users who run graphics-intensive applications and have windows straddling monitors.</span></span> <span data-ttu-id="e4bb9-109">W pozostałych przypadkach po prostu można zachowanie spójności między wersje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e4bb9-109">In other cases, you may simply want a consistent behavior across .NET Framework versions.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="e4bb9-110">Ograniczenie</span><span class="sxs-lookup"><span data-stu-id="e4bb9-110">Mitigation</span></span>  
 <span data-ttu-id="e4bb9-111">Można wyłączyć tę zmianę i powrócić do poprzedniej zachowanie wycinka okna WPF, gdy wykraczał poza jednym wyświetlania.</span><span class="sxs-lookup"><span data-stu-id="e4bb9-111">You can disable this change and revert to the previous behavior of clipping a WPF window when it extends beyond a single display.</span></span> <span data-ttu-id="e4bb9-112">Istnieją dwa sposoby wykonania tej czynności:</span><span class="sxs-lookup"><span data-stu-id="e4bb9-112">There are two ways to do this:</span></span>  
  
-   <span data-ttu-id="e4bb9-113">Dodając `<EnableMultiMonitorDisplayClipping>` elementu `<appSettings>` sekcji pliku konfiguracji aplikacji, można wyłączyć lub włączyć to zachowanie na aplikacje działające w systemie Windows 8 lub nowszym.</span><span class="sxs-lookup"><span data-stu-id="e4bb9-113">By adding the `<EnableMultiMonitorDisplayClipping>` element to the `<appSettings>` section of your application configuration file, you can disable or enable this behavior on apps running on Windows 8 or later.</span></span> <span data-ttu-id="e4bb9-114">Na przykład następującą sekcję konfiguracji wyłącza renderowanie bez wycinka:</span><span class="sxs-lookup"><span data-stu-id="e4bb9-114">For example, the following configuration section disables rendering without clipping:</span></span>  
  
    ```xml  
    <appSettings>  
        <add key="EnableMultiMonitorDisplayClipping" value="true"/>  
      </appSettings>  
    ```  
  
     <span data-ttu-id="e4bb9-115">`<EnableMultiMonitorDisplayClipping>` Ustawienie konfiguracji może mieć jedną z dwóch wartości:</span><span class="sxs-lookup"><span data-stu-id="e4bb9-115">The `<EnableMultiMonitorDisplayClipping>` configuration setting can have either of two values:</span></span>  
  
    -   <span data-ttu-id="e4bb9-116">`true`, aby włączyć wycinka systemu windows do monitorowania granic podczas renderowania.</span><span class="sxs-lookup"><span data-stu-id="e4bb9-116">`true`, to enable clipping of windows to monitor bounds during rendering.</span></span>  
  
    -   <span data-ttu-id="e4bb9-117">`false`, aby wyłączyć obcinanie do systemu windows do monitorowania granic podczas renderowania.</span><span class="sxs-lookup"><span data-stu-id="e4bb9-117">`false`, to disable clipping of windows to monitor bounds during rendering.</span></span>  
  
-   <span data-ttu-id="e4bb9-118">Przez ustawienie <xref:System.Windows.CoreCompatibilityPreferences.EnableMultiMonitorDisplayClipping%2A> właściwości `true` podczas uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e4bb9-118">By setting the <xref:System.Windows.CoreCompatibilityPreferences.EnableMultiMonitorDisplayClipping%2A> property to `true` at app startup.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4bb9-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e4bb9-119">See Also</span></span>  
 [<span data-ttu-id="e4bb9-120">Zmiany środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="e4bb9-120">Runtime Changes</span></span>](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-6.md)
