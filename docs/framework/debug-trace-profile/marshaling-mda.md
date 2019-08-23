---
title: przekazywanie międzyprocesowe (marshaling) MDA
ms.date: 03/30/2017
helpviewer_keywords:
- marshaling, run-time errors
- marshaling MDA
- managed debugging assistants (MDAs), marshaling
- MDAs (managed debugging assistants), marshaling
ms.assetid: 5433b1f8-b0e5-40c9-a49a-0e5bd213363d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1e1583ba8ecfa461958f96bea6cb2b9d3313349b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69967283"
---
# <a name="marshaling-mda"></a><span data-ttu-id="22ce0-102">przekazywanie międzyprocesowe (marshaling) MDA</span><span class="sxs-lookup"><span data-stu-id="22ce0-102">marshaling MDA</span></span>
<span data-ttu-id="22ce0-103">Asystent `marshaling` debugowania zarządzanego (MDA) jest uaktywniany, gdy środowisko CLR konfiguruje informacje kierujące dla parametru metody lub pola struktury.</span><span class="sxs-lookup"><span data-stu-id="22ce0-103">The `marshaling` managed debugging assistant (MDA) is activated when the CLR sets up marshaling information for a method parameter or a field of a structure.</span></span> <span data-ttu-id="22ce0-104">To zdarzenie MDA nie działa w przypadku zestawów skompilowanych w trybie JIT.</span><span class="sxs-lookup"><span data-stu-id="22ce0-104">This MDA does not work for JIT-compiled assemblies.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="22ce0-105">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="22ce0-105">Effect on the Runtime</span></span>  
 <span data-ttu-id="22ce0-106">To zdarzenie MDA nie ma wpływu na środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="22ce0-106">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="22ce0-107">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="22ce0-107">Output</span></span>  
 <span data-ttu-id="22ce0-108">MDA Wyświetla typ parametru lub pola w kontekstach zarządzanych i niezarządzanych, a także strukturę lub metodę zawierającą typ.</span><span class="sxs-lookup"><span data-stu-id="22ce0-108">The MDA displays the type of the parameter or field in the managed and unmanaged contexts, and the structure or method containing the type.</span></span>  <span data-ttu-id="22ce0-109">Poniżej znajduje się przykład danych wyjściowych dla pola:</span><span class="sxs-lookup"><span data-stu-id="22ce0-109">The following is an example of the output for a field:</span></span>  
  
```  
Marshaling from 'Char' to 'ANSI char'  
name="assembly!Namespace.Class::myChar  
```  
  
## <a name="configuration"></a><span data-ttu-id="22ce0-110">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="22ce0-110">Configuration</span></span>  
 <span data-ttu-id="22ce0-111">Konfiguracja MDA umożliwia filtrowanie raportowanych informacji o kierowaniu na podstawie nazw pól lub metod.</span><span class="sxs-lookup"><span data-stu-id="22ce0-111">The MDA configuration allows you to filter the reported marshaling information based on the involved field or method names.</span></span>  <span data-ttu-id="22ce0-112">W poniższym przykładzie pokazano użycie `methodFilter`, `fieldFilter`, i `match` elementów do określenia filtrów.</span><span class="sxs-lookup"><span data-stu-id="22ce0-112">The following example shows the use of the `methodFilter`, `fieldFilter`, and `match` elements to specify filters.</span></span>  <span data-ttu-id="22ce0-113">Ustawienie atrybutu na gwiazdkę (\*) będzie pasować do wszystkiego. `name`</span><span class="sxs-lookup"><span data-stu-id="22ce0-113">Setting the `name` attribute to an asterisk (\*) will match everything.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="22ce0-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="22ce0-114">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="22ce0-115">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="22ce0-115">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="22ce0-116">Marshaling międzyoperacyjny</span><span class="sxs-lookup"><span data-stu-id="22ce0-116">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
