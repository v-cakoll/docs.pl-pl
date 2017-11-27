---
title: "Optymalizacja udostępnionej usługi hostingu sieci Web"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- garbage collection, Web hosting
- garbage collection, optimizing
- garbage collection, shared Web hosting
ms.assetid: be98c0ab-7ef8-409f-8a0d-cb6e5b75ff20
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1f423d867d4fada075800650627c94f9d09e9e7a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="optimization-for-shared-web-hosting"></a><span data-ttu-id="16aa2-102">Optymalizacja udostępnionej usługi hostingu sieci Web</span><span class="sxs-lookup"><span data-stu-id="16aa2-102">Optimization for Shared Web Hosting</span></span>
<span data-ttu-id="16aa2-103">Jeśli jesteś administratorem serwera, który jest współużytkowany przez hosting kilka małych witryn sieci Web można zoptymalizować wydajność i zwiększyć wydajność witryny, dodając następujące `gcTrimCommitOnLowMemory` ustawienie `runtime` węzeł w pliku konfigurację Aspnet.config w ramach platformy .NET katalog:</span><span class="sxs-lookup"><span data-stu-id="16aa2-103">If you are the administrator for a server that is shared by hosting several small Web sites, you can optimize performance and increase site capacity by adding the following `gcTrimCommitOnLowMemory` setting to the `runtime` node in the Aspnet.config file in the .NET directory:</span></span>  
  
 `<gcTrimCommitOnLowMemory enabled="true|false"/>`  
  
> [!NOTE]
>  <span data-ttu-id="16aa2-104">To ustawienie jest zalecane tylko dla udostępnionych w sieci Web w scenariuszach hostingu.</span><span class="sxs-lookup"><span data-stu-id="16aa2-104">This setting is recommended only for shared Web hosting scenarios.</span></span>  
  
 <span data-ttu-id="16aa2-105">Ponieważ moduł garbage collector zachowuje pamięć dla przyszłych alokacji, jego przydzielone miejsce może być więcej niż ściśle potrzebna.</span><span class="sxs-lookup"><span data-stu-id="16aa2-105">Because the garbage collector retains memory for future allocations, its committed space can be more than what is strictly needed.</span></span> <span data-ttu-id="16aa2-106">Zmniejsza to miejsce, by uwzględnić czas po duże obciążenie pamięci systemowej.</span><span class="sxs-lookup"><span data-stu-id="16aa2-106">You can reduce this space to accommodate times when there is a heavy load on system memory.</span></span> <span data-ttu-id="16aa2-107">Zmniejsza to przydzielone miejsce poprawia wydajność i rozwija zdolności do obsługi więcej witryn.</span><span class="sxs-lookup"><span data-stu-id="16aa2-107">Reducing this committed space improves performance and expands the capacity to host more sites.</span></span>  
  
 <span data-ttu-id="16aa2-108">Gdy `gcTrimCommitOnLowMemory` ustawienie jest włączone, moduł zbierający elementy bezużyteczne ocenia obciążenia pamięci systemu i przejdzie do trybu przycinanie podczas obciążenia wynosi 90%.</span><span class="sxs-lookup"><span data-stu-id="16aa2-108">When the `gcTrimCommitOnLowMemory` setting is enabled, the garbage collector evaluates the system memory load and enters a trimming mode when the load reaches 90%.</span></span> <span data-ttu-id="16aa2-109">Ta funkcja obsługuje tryb przycinanie dopóki obciążenia spadnie poniżej 85%.</span><span class="sxs-lookup"><span data-stu-id="16aa2-109">It maintains the trimming mode until the load drops under 85%.</span></span>  
  
 <span data-ttu-id="16aa2-110">Gdy zezwolenie na warunki, moduł zbierający elementy bezużyteczne można zdecydować, że `gcTrimCommitOnLowMemory` ustawienie nie zostanie pomocy bieżącej aplikacji i go zignorować.</span><span class="sxs-lookup"><span data-stu-id="16aa2-110">When conditions permit, the garbage collector can decide that the `gcTrimCommitOnLowMemory` setting will not help the current application and ignore it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="16aa2-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="16aa2-111">Example</span></span>  
 <span data-ttu-id="16aa2-112">Poniższy fragment XML pokazano, jak włączyć `gcTrimCommitOnLowMemory` ustawienie.</span><span class="sxs-lookup"><span data-stu-id="16aa2-112">The following XML fragment shows how to enable the `gcTrimCommitOnLowMemory` setting.</span></span> <span data-ttu-id="16aa2-113">Wielokropek wskazywać inne ustawienia, które byłyby w `runtime` węzła.</span><span class="sxs-lookup"><span data-stu-id="16aa2-113">Ellipses indicate other settings that would be in the `runtime` node.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="16aa2-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="16aa2-114">See Also</span></span>  
 [<span data-ttu-id="16aa2-115">Wyrzucanie elementów bezużytecznych</span><span class="sxs-lookup"><span data-stu-id="16aa2-115">Garbage Collection</span></span>](../../../docs/standard/garbage-collection/index.md)
