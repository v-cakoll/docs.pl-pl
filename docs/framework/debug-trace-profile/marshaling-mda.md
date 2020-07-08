---
title: przekazywanie międzyprocesowe (marshaling) MDA
description: Przejrzyj zarządzany Asystent debugowania (MDA), który jest wywoływany, jeśli środowisko CLR skonfiguruje informacje kierujące dla parametru metody lub pola struktury.
ms.date: 03/30/2017
helpviewer_keywords:
- marshaling, run-time errors
- marshaling MDA
- managed debugging assistants (MDAs), marshaling
- MDAs (managed debugging assistants), marshaling
ms.assetid: 5433b1f8-b0e5-40c9-a49a-0e5bd213363d
ms.openlocfilehash: 77811c526d1770b91b14aa1199dfc7b3177e6c59
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: pl-PL
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051158"
---
# <a name="marshaling-mda"></a><span data-ttu-id="266ad-103">przekazywanie międzyprocesowe (marshaling) MDA</span><span class="sxs-lookup"><span data-stu-id="266ad-103">marshaling MDA</span></span>
<span data-ttu-id="266ad-104">`marshaling`Asystent debugowania zarządzanego (MDA) jest uaktywniany, gdy środowisko CLR konfiguruje informacje kierujące dla parametru metody lub pola struktury.</span><span class="sxs-lookup"><span data-stu-id="266ad-104">The `marshaling` managed debugging assistant (MDA) is activated when the CLR sets up marshaling information for a method parameter or a field of a structure.</span></span> <span data-ttu-id="266ad-105">To zdarzenie MDA nie działa w przypadku zestawów skompilowanych w trybie JIT.</span><span class="sxs-lookup"><span data-stu-id="266ad-105">This MDA does not work for JIT-compiled assemblies.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="266ad-106">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="266ad-106">Effect on the Runtime</span></span>  
 <span data-ttu-id="266ad-107">To zdarzenie MDA nie ma wpływu na środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="266ad-107">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="266ad-108">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="266ad-108">Output</span></span>  
 <span data-ttu-id="266ad-109">MDA Wyświetla typ parametru lub pola w kontekstach zarządzanych i niezarządzanych, a także strukturę lub metodę zawierającą typ.</span><span class="sxs-lookup"><span data-stu-id="266ad-109">The MDA displays the type of the parameter or field in the managed and unmanaged contexts, and the structure or method containing the type.</span></span>  <span data-ttu-id="266ad-110">Poniżej znajduje się przykład danych wyjściowych dla pola:</span><span class="sxs-lookup"><span data-stu-id="266ad-110">The following is an example of the output for a field:</span></span>  
  
```output
Marshaling from 'Char' to 'ANSI char'  
name="assembly!Namespace.Class::myChar  
```  
  
## <a name="configuration"></a><span data-ttu-id="266ad-111">Konfigurowanie</span><span class="sxs-lookup"><span data-stu-id="266ad-111">Configuration</span></span>  
 <span data-ttu-id="266ad-112">Konfiguracja MDA umożliwia filtrowanie raportowanych informacji o kierowaniu na podstawie nazw pól lub metod.</span><span class="sxs-lookup"><span data-stu-id="266ad-112">The MDA configuration allows you to filter the reported marshaling information based on the involved field or method names.</span></span>  <span data-ttu-id="266ad-113">W poniższym przykładzie pokazano użycie `methodFilter` , `fieldFilter` , i `match` elementów do określenia filtrów.</span><span class="sxs-lookup"><span data-stu-id="266ad-113">The following example shows the use of the `methodFilter`, `fieldFilter`, and `match` elements to specify filters.</span></span>  <span data-ttu-id="266ad-114">Ustawienie `name` atrybutu na gwiazdkę ( \* ) będzie pasować do wszystkiego.</span><span class="sxs-lookup"><span data-stu-id="266ad-114">Setting the `name` attribute to an asterisk (\*) will match everything.</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <marshaling>  
      <methodFilter>  
        <match name="Method1"/>  
        <match name="Method2"/>  
      </methodFilter>  
      <fieldFilter>  
        <match name="Field1"/>  
        <match name="Field2"/>  
       </fieldFilter>  
    </marshaling>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="266ad-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="266ad-115">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="266ad-116">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="266ad-116">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="266ad-117">Organizowanie międzyoperacyjne</span><span class="sxs-lookup"><span data-stu-id="266ad-117">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
