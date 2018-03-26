---
title: MDA marshalingu
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- marshaling, run-time errors
- marshaling MDA
- managed debugging assistants (MDAs), marshaling
- MDAs (managed debugging assistants), marshaling
ms.assetid: 5433b1f8-b0e5-40c9-a49a-0e5bd213363d
caps.latest.revision: ''
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 83b621f78e3ba4641540f6125ed14d600cc292d1
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/26/2018
---
# <a name="marshaling-mda"></a><span data-ttu-id="d76df-102">MDA marshalingu</span><span class="sxs-lookup"><span data-stu-id="d76df-102">marshaling MDA</span></span>
<span data-ttu-id="d76df-103">`marshaling` Zarządzany Asystent debugowania (MDA) została aktywowana po skonfigurowaniu informacje dla parametru metody lub pola struktury organizacyjne środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="d76df-103">The `marshaling` managed debugging assistant (MDA) is activated when the CLR sets up marshaling information for a method parameter or a field of a structure.</span></span> <span data-ttu-id="d76df-104">To zdarzenie MDA nie działa w przypadku zestawów kompilacji JIT.</span><span class="sxs-lookup"><span data-stu-id="d76df-104">This MDA does not work for JIT-compiled assemblies.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="d76df-105">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="d76df-105">Effect on the Runtime</span></span>  
 <span data-ttu-id="d76df-106">To zdarzenie MDA nie ma wpływu na środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="d76df-106">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="d76df-107">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="d76df-107">Output</span></span>  
 <span data-ttu-id="d76df-108">MDA Wyświetla typ parametru lub pola w kontekstach zarządzane i niezarządzane oraz struktury lub metody z typem.</span><span class="sxs-lookup"><span data-stu-id="d76df-108">The MDA displays the type of the parameter or field in the managed and unmanaged contexts, and the structure or method containing the type.</span></span>  <span data-ttu-id="d76df-109">Poniżej przedstawiono przykład danych wyjściowych dla pola:</span><span class="sxs-lookup"><span data-stu-id="d76df-109">The following is an example of the output for a field:</span></span>  
  
```  
Marshaling from 'Char' to 'ANSI char'  
name="assembly!Namespace.Class::myChar  
```  
  
## <a name="configuration"></a><span data-ttu-id="d76df-110">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="d76df-110">Configuration</span></span>  
 <span data-ttu-id="d76df-111">Konfiguracja MDA umożliwia zgłoszony na podstawie związane pola lub nazwy metod organizowania informacji o filtrze.</span><span class="sxs-lookup"><span data-stu-id="d76df-111">The MDA configuration allows you to filter the reported marshaling information based on the involved field or method names.</span></span>  <span data-ttu-id="d76df-112">W poniższym przykładzie przedstawiono użycie `methodFilter`, `fieldFilter`, i `match` elementy, aby określić filtrów.</span><span class="sxs-lookup"><span data-stu-id="d76df-112">The following example shows the use of the `methodFilter`, `fieldFilter`, and `match` elements to specify filters.</span></span>  <span data-ttu-id="d76df-113">Ustawienie `name` atrybutu znak gwiazdki (\*) będą zgodne wszystko.</span><span class="sxs-lookup"><span data-stu-id="d76df-113">Setting the `name` attribute to an asterisk (\*) will match everything.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d76df-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d76df-114">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="d76df-115">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="d76df-115">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="d76df-116">Marshaling międzyoperacyjny</span><span class="sxs-lookup"><span data-stu-id="d76df-116">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
