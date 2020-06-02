---
title: Optymalizacja udostępnionej usługi hostingu sieci Web
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- garbage collection, Web hosting
- garbage collection, optimizing
- garbage collection, shared Web hosting
ms.assetid: be98c0ab-7ef8-409f-8a0d-cb6e5b75ff20
ms.openlocfilehash: ccaacd44f8aaed9c3178cb94f98b0f58d4d3c7d4
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84285992"
---
# <a name="optimization-for-shared-web-hosting"></a><span data-ttu-id="ff88b-102">Optymalizacja udostępnionej usługi hostingu sieci Web</span><span class="sxs-lookup"><span data-stu-id="ff88b-102">Optimization for Shared Web Hosting</span></span>
<span data-ttu-id="ff88b-103">Jeśli jesteś administratorem serwera, który jest udostępniany przez hosting kilku małych witryn sieci Web, możesz zoptymalizować wydajność i zwiększyć pojemność lokacji, dodając następujące `gcTrimCommitOnLowMemory` ustawienie do `runtime` węzła w pliku aspnet. config w katalogu .NET:</span><span class="sxs-lookup"><span data-stu-id="ff88b-103">If you are the administrator for a server that is shared by hosting several small Web sites, you can optimize performance and increase site capacity by adding the following `gcTrimCommitOnLowMemory` setting to the `runtime` node in the Aspnet.config file in the .NET directory:</span></span>  
  
 `<gcTrimCommitOnLowMemory enabled="true|false"/>`  
  
> [!NOTE]
> <span data-ttu-id="ff88b-104">To ustawienie jest zalecane tylko w scenariuszach hostingu w sieci Web.</span><span class="sxs-lookup"><span data-stu-id="ff88b-104">This setting is recommended only for shared Web hosting scenarios.</span></span>  
  
 <span data-ttu-id="ff88b-105">Ponieważ moduł wyrzucania elementów bezużytecznych zachowuje pamięć dla przyszłych przydziałów, jego zatwierdzone miejsce może być większe niż to, co jest absolutnie wymagane.</span><span class="sxs-lookup"><span data-stu-id="ff88b-105">Because the garbage collector retains memory for future allocations, its committed space can be more than what is strictly needed.</span></span> <span data-ttu-id="ff88b-106">Można zmniejszyć to miejsce do czasu, gdy występuje duże obciążenie pamięci systemowej.</span><span class="sxs-lookup"><span data-stu-id="ff88b-106">You can reduce this space to accommodate times when there is a heavy load on system memory.</span></span> <span data-ttu-id="ff88b-107">Zmniejszenie ilości tego zajmowanego miejsca zwiększa wydajność i zwiększa możliwości hostowania większej liczby lokacji.</span><span class="sxs-lookup"><span data-stu-id="ff88b-107">Reducing this committed space improves performance and expands the capacity to host more sites.</span></span>  
  
 <span data-ttu-id="ff88b-108">Gdy to `gcTrimCommitOnLowMemory` ustawienie jest włączone, moduł zbierający elementy bezużyteczne szacuje obciążenie pamięci systemowej i przechodzi do trybu przycinania, gdy obciążenie osiągnie 90%.</span><span class="sxs-lookup"><span data-stu-id="ff88b-108">When the `gcTrimCommitOnLowMemory` setting is enabled, the garbage collector evaluates the system memory load and enters a trimming mode when the load reaches 90%.</span></span> <span data-ttu-id="ff88b-109">Utrzymuje tryb przycinania do momentu spadku obciążenia poniżej 85%.</span><span class="sxs-lookup"><span data-stu-id="ff88b-109">It maintains the trimming mode until the load drops under 85%.</span></span>  
  
 <span data-ttu-id="ff88b-110">Gdy warunki zezwalają, Moduł wyrzucania elementów bezużytecznych może zdecydować, że to `gcTrimCommitOnLowMemory` ustawienie nie będzie pomocne dla bieżącej aplikacji i nie zostanie zignorowane.</span><span class="sxs-lookup"><span data-stu-id="ff88b-110">When conditions permit, the garbage collector can decide that the `gcTrimCommitOnLowMemory` setting will not help the current application and ignore it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ff88b-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="ff88b-111">Example</span></span>  
 <span data-ttu-id="ff88b-112">Poniższy fragment kodu XML pokazuje, jak włączyć `gcTrimCommitOnLowMemory` ustawienie.</span><span class="sxs-lookup"><span data-stu-id="ff88b-112">The following XML fragment shows how to enable the `gcTrimCommitOnLowMemory` setting.</span></span> <span data-ttu-id="ff88b-113">Elipsy wskazują inne ustawienia, które mogą znajdować się w `runtime` węźle.</span><span class="sxs-lookup"><span data-stu-id="ff88b-113">Ellipses indicate other settings that would be in the `runtime` node.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ff88b-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ff88b-114">See also</span></span>

- [<span data-ttu-id="ff88b-115">Odzyskiwanie pamięci</span><span class="sxs-lookup"><span data-stu-id="ff88b-115">Garbage Collection</span></span>](index.md)
