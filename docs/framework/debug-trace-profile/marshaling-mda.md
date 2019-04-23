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
ms.openlocfilehash: 463c8e42e76a61eb0820c1af72c20d004161ad25
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59184473"
---
# <a name="marshaling-mda"></a><span data-ttu-id="5344c-102">przekazywanie międzyprocesowe (marshaling) MDA</span><span class="sxs-lookup"><span data-stu-id="5344c-102">marshaling MDA</span></span>
<span data-ttu-id="5344c-103">`marshaling` Zarządzanego Asystenta debugowania (MDA) jest aktywowany, gdy środowisko CLR konfiguruje organizowanie informacji dla parametru metody lub pola struktury.</span><span class="sxs-lookup"><span data-stu-id="5344c-103">The `marshaling` managed debugging assistant (MDA) is activated when the CLR sets up marshaling information for a method parameter or a field of a structure.</span></span> <span data-ttu-id="5344c-104">To zdarzenie MDA nie działa dla zestawów kompilowanego dokładnie na czas.</span><span class="sxs-lookup"><span data-stu-id="5344c-104">This MDA does not work for JIT-compiled assemblies.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="5344c-105">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="5344c-105">Effect on the Runtime</span></span>  
 <span data-ttu-id="5344c-106">To zdarzenie MDA nie ma wpływu na środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="5344c-106">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="5344c-107">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="5344c-107">Output</span></span>  
 <span data-ttu-id="5344c-108">MDA Wyświetla typ parametru lub pola w kontekstach zarządzanych i niezarządzanych i struktury lub metody z typem.</span><span class="sxs-lookup"><span data-stu-id="5344c-108">The MDA displays the type of the parameter or field in the managed and unmanaged contexts, and the structure or method containing the type.</span></span>  <span data-ttu-id="5344c-109">Oto przykład danych wyjściowych dla pola:</span><span class="sxs-lookup"><span data-stu-id="5344c-109">The following is an example of the output for a field:</span></span>  
  
```  
Marshaling from 'Char' to 'ANSI char'  
name="assembly!Namespace.Class::myChar  
```  
  
## <a name="configuration"></a><span data-ttu-id="5344c-110">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="5344c-110">Configuration</span></span>  
 <span data-ttu-id="5344c-111">Konfiguracja MDA pozwala zgłaszane na podstawie związane pola lub nazwy metod organizowania informacji o filtrze.</span><span class="sxs-lookup"><span data-stu-id="5344c-111">The MDA configuration allows you to filter the reported marshaling information based on the involved field or method names.</span></span>  <span data-ttu-id="5344c-112">Poniższy przykład pokazuje użycie `methodFilter`, `fieldFilter`, i `match` elementy, aby określić filtry.</span><span class="sxs-lookup"><span data-stu-id="5344c-112">The following example shows the use of the `methodFilter`, `fieldFilter`, and `match` elements to specify filters.</span></span>  <span data-ttu-id="5344c-113">Ustawienie `name` atrybutu, aby znak gwiazdki (\*) będą zgodne wszystko.</span><span class="sxs-lookup"><span data-stu-id="5344c-113">Setting the `name` attribute to an asterisk (\*) will match everything.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5344c-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5344c-114">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="5344c-115">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="5344c-115">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="5344c-116">Marshaling międzyoperacyjny</span><span class="sxs-lookup"><span data-stu-id="5344c-116">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
