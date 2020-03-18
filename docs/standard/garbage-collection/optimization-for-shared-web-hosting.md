---
title: Optymalizacja udostępnionej usługi hostingu sieci Web
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- garbage collection, Web hosting
- garbage collection, optimizing
- garbage collection, shared Web hosting
ms.assetid: be98c0ab-7ef8-409f-8a0d-cb6e5b75ff20
ms.openlocfilehash: 07a100e2cd6aaff2b54b99144c9d762c8979fb47
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73140273"
---
# <a name="optimization-for-shared-web-hosting"></a><span data-ttu-id="06123-102">Optymalizacja udostępnionej usługi hostingu sieci Web</span><span class="sxs-lookup"><span data-stu-id="06123-102">Optimization for Shared Web Hosting</span></span>
<span data-ttu-id="06123-103">Jeśli jesteś administratorem serwera współdzielonego przez hostowanie kilku małych witryn sieci Web, możesz `gcTrimCommitOnLowMemory` zoptymalizować wydajność i zwiększyć pojemność lokacji, dodając następujące ustawienie do `runtime` węzła w pliku Aspnet.config w katalogu .NET:</span><span class="sxs-lookup"><span data-stu-id="06123-103">If you are the administrator for a server that is shared by hosting several small Web sites, you can optimize performance and increase site capacity by adding the following `gcTrimCommitOnLowMemory` setting to the `runtime` node in the Aspnet.config file in the .NET directory:</span></span>  
  
 `<gcTrimCommitOnLowMemory enabled="true|false"/>`  
  
> [!NOTE]
> <span data-ttu-id="06123-104">To ustawienie jest zalecane tylko w przypadku scenariuszy hostingu udostępnionego sieci Web.</span><span class="sxs-lookup"><span data-stu-id="06123-104">This setting is recommended only for shared Web hosting scenarios.</span></span>  
  
 <span data-ttu-id="06123-105">Ponieważ moduł zbierający elementy bezużyteczne zachowuje pamięć dla przyszłych alokacji, jego zatwierdzone miejsce może być więcej niż to, co jest ściśle potrzebne.</span><span class="sxs-lookup"><span data-stu-id="06123-105">Because the garbage collector retains memory for future allocations, its committed space can be more than what is strictly needed.</span></span> <span data-ttu-id="06123-106">Można zmniejszyć to miejsce, aby pomieścić razy, gdy istnieje duże obciążenie pamięci systemowej.</span><span class="sxs-lookup"><span data-stu-id="06123-106">You can reduce this space to accommodate times when there is a heavy load on system memory.</span></span> <span data-ttu-id="06123-107">Zmniejszenie tej zaangażowanej przestrzeni zwiększa wydajność i zwiększa pojemność hostowania większej liczby witryn.</span><span class="sxs-lookup"><span data-stu-id="06123-107">Reducing this committed space improves performance and expands the capacity to host more sites.</span></span>  
  
 <span data-ttu-id="06123-108">Gdy `gcTrimCommitOnLowMemory` ustawienie jest włączone, moduł zbierający elementy bezużyteczne ocenia obciążenie pamięci systemowej i przechodzi w tryb przycinania, gdy obciążenie osiągnie 90%.</span><span class="sxs-lookup"><span data-stu-id="06123-108">When the `gcTrimCommitOnLowMemory` setting is enabled, the garbage collector evaluates the system memory load and enters a trimming mode when the load reaches 90%.</span></span> <span data-ttu-id="06123-109">Utrzymuje tryb przycinania, aż obciążenie spadnie poniżej 85%.</span><span class="sxs-lookup"><span data-stu-id="06123-109">It maintains the trimming mode until the load drops under 85%.</span></span>  
  
 <span data-ttu-id="06123-110">Gdy pozwalają na to warunki, moduł `gcTrimCommitOnLowMemory` zbierający elementy bezużyteczne może zdecydować, że ustawienie nie pomoże bieżącej aplikacji i zignorować go.</span><span class="sxs-lookup"><span data-stu-id="06123-110">When conditions permit, the garbage collector can decide that the `gcTrimCommitOnLowMemory` setting will not help the current application and ignore it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="06123-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="06123-111">Example</span></span>  
 <span data-ttu-id="06123-112">Poniższy fragment XML pokazuje, `gcTrimCommitOnLowMemory` jak włączyć ustawienie.</span><span class="sxs-lookup"><span data-stu-id="06123-112">The following XML fragment shows how to enable the `gcTrimCommitOnLowMemory` setting.</span></span> <span data-ttu-id="06123-113">Elipsy wskazują inne ustawienia, `runtime` które byłyby w węźle.</span><span class="sxs-lookup"><span data-stu-id="06123-113">Ellipses indicate other settings that would be in the `runtime` node.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="06123-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="06123-114">See also</span></span>

- [<span data-ttu-id="06123-115">Odzyskiwanie pamięci</span><span class="sxs-lookup"><span data-stu-id="06123-115">Garbage Collection</span></span>](../../../docs/standard/garbage-collection/index.md)
