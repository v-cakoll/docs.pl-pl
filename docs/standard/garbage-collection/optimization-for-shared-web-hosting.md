---
title: Optymalizacja udostępnionej usługi hostingu sieci Web
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- garbage collection, Web hosting
- garbage collection, optimizing
- garbage collection, shared Web hosting
ms.assetid: be98c0ab-7ef8-409f-8a0d-cb6e5b75ff20
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7831e383a3048523909b79ac5a4706f3c1c48371
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/26/2018
ms.locfileid: "47216136"
---
# <a name="optimization-for-shared-web-hosting"></a><span data-ttu-id="bb5d2-102">Optymalizacja udostępnionej usługi hostingu sieci Web</span><span class="sxs-lookup"><span data-stu-id="bb5d2-102">Optimization for Shared Web Hosting</span></span>
<span data-ttu-id="bb5d2-103">Jeśli jesteś administratorem serwera, który jest współużytkowany przez kilka małych witryn sieci Web hostingu, można zoptymalizować wydajność i zwiększyć wydajność witryny, dodając następujące `gcTrimCommitOnLowMemory` ustawienie `runtime` węzeł w pliku konfigurację Aspnet.config na platformie .NET katalog:</span><span class="sxs-lookup"><span data-stu-id="bb5d2-103">If you are the administrator for a server that is shared by hosting several small Web sites, you can optimize performance and increase site capacity by adding the following `gcTrimCommitOnLowMemory` setting to the `runtime` node in the Aspnet.config file in the .NET directory:</span></span>  
  
 `<gcTrimCommitOnLowMemory enabled="true|false"/>`  
  
> [!NOTE]
>  <span data-ttu-id="bb5d2-104">To ustawienie jest zalecane tylko dla udostępnionych w sieci Web w scenariuszach hostingu.</span><span class="sxs-lookup"><span data-stu-id="bb5d2-104">This setting is recommended only for shared Web hosting scenarios.</span></span>  
  
 <span data-ttu-id="bb5d2-105">Ponieważ moduł odśmiecania pamięci zachowuje pamięć dla przyszłej alokacji, może być jej przydzielonych miejsc, więcej niż ściśle potrzebne.</span><span class="sxs-lookup"><span data-stu-id="bb5d2-105">Because the garbage collector retains memory for future allocations, its committed space can be more than what is strictly needed.</span></span> <span data-ttu-id="bb5d2-106">Można zmniejszyć tego miejsca, aby pomieścić godziny po duże obciążenie pamięci systemowej.</span><span class="sxs-lookup"><span data-stu-id="bb5d2-106">You can reduce this space to accommodate times when there is a heavy load on system memory.</span></span> <span data-ttu-id="bb5d2-107">Zmniejszenie tego przydzielone miejsce zapewnia lepszą wydajność i rozwija zdolności do hostowania więcej witryn.</span><span class="sxs-lookup"><span data-stu-id="bb5d2-107">Reducing this committed space improves performance and expands the capacity to host more sites.</span></span>  
  
 <span data-ttu-id="bb5d2-108">Gdy `gcTrimCommitOnLowMemory` ustawienie jest włączone, moduł zbierający elementy bezużyteczne ocenia obciążenia pamięci systemu i przechodzi trybie przycinania, gdy obciążenie osiągnie 90%.</span><span class="sxs-lookup"><span data-stu-id="bb5d2-108">When the `gcTrimCommitOnLowMemory` setting is enabled, the garbage collector evaluates the system memory load and enters a trimming mode when the load reaches 90%.</span></span> <span data-ttu-id="bb5d2-109">Dopóki obciążenie spadnie poniżej 85%, obsługuje tryb przycinania.</span><span class="sxs-lookup"><span data-stu-id="bb5d2-109">It maintains the trimming mode until the load drops under 85%.</span></span>  
  
 <span data-ttu-id="bb5d2-110">Gdy warunki na to pozwalają, wyrzucanie elementów bezużytecznych może zdecydować, że `gcTrimCommitOnLowMemory` ustawienie nie zostanie pomocy bieżącej aplikacji i go zignorować.</span><span class="sxs-lookup"><span data-stu-id="bb5d2-110">When conditions permit, the garbage collector can decide that the `gcTrimCommitOnLowMemory` setting will not help the current application and ignore it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bb5d2-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="bb5d2-111">Example</span></span>  
 <span data-ttu-id="bb5d2-112">Poniższy fragment XML przedstawiono sposób włączania `gcTrimCommitOnLowMemory` ustawienie.</span><span class="sxs-lookup"><span data-stu-id="bb5d2-112">The following XML fragment shows how to enable the `gcTrimCommitOnLowMemory` setting.</span></span> <span data-ttu-id="bb5d2-113">Wielokropek wskazywać inne ustawienia, które będą miały `runtime` węzła.</span><span class="sxs-lookup"><span data-stu-id="bb5d2-113">Ellipses indicate other settings that would be in the `runtime` node.</span></span>  
  
```xml  
<?xml version="1.0" encoding="UTF-8"?>  
<configuration>  
    <runtime>  
    . . .  
    <gcTrimCommitOnLowMemory enabled="true"/>  
    </runtime>  
    . . .  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="bb5d2-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bb5d2-114">See also</span></span>

- [<span data-ttu-id="bb5d2-115">Odzyskiwanie pamięci</span><span class="sxs-lookup"><span data-stu-id="bb5d2-115">Garbage Collection</span></span>](../../../docs/standard/garbage-collection/index.md)
