---
title: przekazywanie międzyprocesowe (marshaling) MDA
ms.date: 03/30/2017
helpviewer_keywords:
- marshaling, run-time errors
- marshaling MDA
- managed debugging assistants (MDAs), marshaling
- MDAs (managed debugging assistants), marshaling
ms.assetid: 5433b1f8-b0e5-40c9-a49a-0e5bd213363d
ms.openlocfilehash: f7bb630d3a1e832cf6bf083ce4cf603034248ceb
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217318"
---
# <a name="marshaling-mda"></a><span data-ttu-id="ea446-102">przekazywanie międzyprocesowe (marshaling) MDA</span><span class="sxs-lookup"><span data-stu-id="ea446-102">marshaling MDA</span></span>
<span data-ttu-id="ea446-103">Asystent debugowania zarządzanego `marshaling` (MDA) jest uaktywniany, gdy środowisko CLR konfiguruje informacje kierujące dla parametru metody lub pola struktury.</span><span class="sxs-lookup"><span data-stu-id="ea446-103">The `marshaling` managed debugging assistant (MDA) is activated when the CLR sets up marshaling information for a method parameter or a field of a structure.</span></span> <span data-ttu-id="ea446-104">To zdarzenie MDA nie działa w przypadku zestawów skompilowanych w trybie JIT.</span><span class="sxs-lookup"><span data-stu-id="ea446-104">This MDA does not work for JIT-compiled assemblies.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="ea446-105">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="ea446-105">Effect on the Runtime</span></span>  
 <span data-ttu-id="ea446-106">To zdarzenie MDA nie ma wpływu na środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="ea446-106">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="ea446-107">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="ea446-107">Output</span></span>  
 <span data-ttu-id="ea446-108">MDA Wyświetla typ parametru lub pola w kontekstach zarządzanych i niezarządzanych, a także strukturę lub metodę zawierającą typ.</span><span class="sxs-lookup"><span data-stu-id="ea446-108">The MDA displays the type of the parameter or field in the managed and unmanaged contexts, and the structure or method containing the type.</span></span>  <span data-ttu-id="ea446-109">Poniżej znajduje się przykład danych wyjściowych dla pola:</span><span class="sxs-lookup"><span data-stu-id="ea446-109">The following is an example of the output for a field:</span></span>  
  
```output
Marshaling from 'Char' to 'ANSI char'  
name="assembly!Namespace.Class::myChar  
```  
  
## <a name="configuration"></a><span data-ttu-id="ea446-110">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="ea446-110">Configuration</span></span>  
 <span data-ttu-id="ea446-111">Konfiguracja MDA umożliwia filtrowanie raportowanych informacji o kierowaniu na podstawie nazw pól lub metod.</span><span class="sxs-lookup"><span data-stu-id="ea446-111">The MDA configuration allows you to filter the reported marshaling information based on the involved field or method names.</span></span>  <span data-ttu-id="ea446-112">Poniższy przykład ilustruje użycie elementów `methodFilter`, `fieldFilter`i `match` do określenia filtrów.</span><span class="sxs-lookup"><span data-stu-id="ea446-112">The following example shows the use of the `methodFilter`, `fieldFilter`, and `match` elements to specify filters.</span></span>  <span data-ttu-id="ea446-113">Ustawienie atrybutu `name` na gwiazdkę (\*) będzie pasować do wszystkiego.</span><span class="sxs-lookup"><span data-stu-id="ea446-113">Setting the `name` attribute to an asterisk (\*) will match everything.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ea446-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ea446-114">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="ea446-115">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="ea446-115">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="ea446-116">Marshaling międzyoperacyjny</span><span class="sxs-lookup"><span data-stu-id="ea446-116">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
