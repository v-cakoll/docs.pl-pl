---
title: nonComVisibleBaseClass MDA
ms.date: 03/30/2017
helpviewer_keywords:
- visible classes
- managed debugging assistants (MDAs), COM visible classes
- nonComVisibleBaseClass MDA
- COM visible classes
- QueryInterface call failures
- MDAs (managed debugging assistants), COM visible classes
ms.assetid: 9ec1af27-604b-477e-9ee2-e833eb10d3ce
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a52460bbbf2b5f65f5c15d2cd06be7d3917f68bd
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854054"
---
# <a name="noncomvisiblebaseclass-mda"></a><span data-ttu-id="80a50-102">nonComVisibleBaseClass MDA</span><span class="sxs-lookup"><span data-stu-id="80a50-102">nonComVisibleBaseClass MDA</span></span>
<span data-ttu-id="80a50-103">Asystent debugowania `QueryInterface` zarządzanego (MDA) jest uaktywniany, gdy wywołanie jest wykonywane przez kod natywny lub niezarządzany w przypadku niezarządzanej otoki COM (CCW) klasy zarządzanej com, która dziedziczy z klasy podstawowej, która nie jest widoczna dla modelu com. `nonComVisibleBaseClass`</span><span class="sxs-lookup"><span data-stu-id="80a50-103">The `nonComVisibleBaseClass` managed debugging assistant (MDA) is activated when a `QueryInterface` call is made by native or unmanaged code on the COM callable wrapper (CCW) of a COM-visible managed class that derives from a base class that is not COM visible.</span></span>  <span data-ttu-id="80a50-104">Wywołanie powoduje aktywację elementu MDA tylko w przypadkach, gdy wywołania żądają interfejsu klasy lub domyślnej `IDispatch` klasy zarządzanej przez com. `QueryInterface`</span><span class="sxs-lookup"><span data-stu-id="80a50-104">The `QueryInterface` call causes the MDA to activate only in cases where call requests the class interface or default `IDispatch` of the COM-visible managed class.</span></span>  <span data-ttu-id="80a50-105">Zdarzenie MDA nie jest uaktywniane, `QueryInterface` gdy jest przeznaczony dla jawnego interfejsu, <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> który ma atrybut zastosowany i jest jawnie zaimplementowany przez klasę widoczną dla modelu com.</span><span class="sxs-lookup"><span data-stu-id="80a50-105">The MDA is not activated when the `QueryInterface` is for an explicit interface that has the <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> attribute applied and is explicitly implemented by the COM-visible class.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="80a50-106">Symptomy</span><span class="sxs-lookup"><span data-stu-id="80a50-106">Symptoms</span></span>  
 <span data-ttu-id="80a50-107">Wykonano `QueryInterface` wywołanie z kodu natywnego, który kończy się niepowodzeniem z COR_E_INVALIDOPERATION HRESULT.</span><span class="sxs-lookup"><span data-stu-id="80a50-107">A `QueryInterface` call made from native code that is failing with a COR_E_INVALIDOPERATION HRESULT.</span></span>  <span data-ttu-id="80a50-108">Wynik HRESULT może być spowodowany tym, że środowisko uruchomieniowe nie zezwoli `QueryInterface` na wywołania, które mogłyby spowodować aktywację tego elementu MDA.</span><span class="sxs-lookup"><span data-stu-id="80a50-108">The HRESULT might be due to the runtime disallowing `QueryInterface` calls that would cause the activation of this MDA.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="80a50-109">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="80a50-109">Cause</span></span>  
 <span data-ttu-id="80a50-110">Środowisko uruchomieniowe nie `QueryInterface` może zezwolić na wywołania interfejsu klasy lub `IDispatch` domyślnego interfejsu klasy widocznej dla modelu COM, która dziedziczy z klasy, która nie jest widoczna dla modelu COM ze względu na potencjalne problemy z wersjami.</span><span class="sxs-lookup"><span data-stu-id="80a50-110">The runtime cannot allow `QueryInterface` calls for the class interface or default `IDispatch` interface of a COM-visible class that derives from a class that is not COM-visible because of potential versioning problems.</span></span>  <span data-ttu-id="80a50-111">Na przykład, jeśli jakikolwiek publiczny element członkowski został dodany do klasy podstawowej, która nie jest widoczna dla modelu COM, istniejący klienci COM korzystający z klasy pochodnej mogą potencjalnie przerwać, ponieważ tablice metod pochodnych klasy pochodnej, która zawiera składowe klasy bazowej, zostałyby zmienione przez takie stąp.</span><span class="sxs-lookup"><span data-stu-id="80a50-111">For example, if any public members were added to the base class that is not COM-visible, existing COM clients using the derived class could potentially break because the vtable of the derived class, which contains the base class members, would be altered by such a change.</span></span>  <span data-ttu-id="80a50-112">Jawne interfejsy uwidocznione dla modelu COM nie mają tego problemu, ponieważ nie obejmują podstawowych elementów członkowskich interfejsów w tablicy bazowej.</span><span class="sxs-lookup"><span data-stu-id="80a50-112">Explicit interfaces exposed to COM do not have this problem because they do not include the base members of interfaces in the vtable.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="80a50-113">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="80a50-113">Resolution</span></span>  
 <span data-ttu-id="80a50-114">Nie ujawniaj interfejsu klasy.</span><span class="sxs-lookup"><span data-stu-id="80a50-114">Do not expose the class interface.</span></span> <span data-ttu-id="80a50-115">Zdefiniuj jawny interfejs i Zastosuj <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> do niego atrybut.</span><span class="sxs-lookup"><span data-stu-id="80a50-115">Define an explicit interface and apply the <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> attribute to it.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="80a50-116">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="80a50-116">Effect on the Runtime</span></span>  
 <span data-ttu-id="80a50-117">To zdarzenie MDA nie ma wpływu na środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="80a50-117">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="80a50-118">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="80a50-118">Output</span></span>  
 <span data-ttu-id="80a50-119">Poniżej znajduje się przykładowy komunikat dla `QueryInterface` wywołania klasy `Derived` widocznej dla modelu COM, która dziedziczy z klasy `Base`niewidocznej dla modelu com.</span><span class="sxs-lookup"><span data-stu-id="80a50-119">The following is an example message for a `QueryInterface` call on a COM-visible class `Derived` that derives from a non-COM-visible class `Base`.</span></span>  
  
```output
A QueryInterface call was made requesting the class interface of COM   
visible managed class 'Derived'. However since this class derives from   
non COM visible class 'Base', the QueryInterface call will fail. This   
is done to prevent the non COM visible base class from being   
constrained by the COM versioning rules.   
```  
  
## <a name="configuration"></a><span data-ttu-id="80a50-120">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="80a50-120">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <nonComVisibleBaseClass />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="80a50-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="80a50-121">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="80a50-122">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="80a50-122">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="80a50-123">Marshaling międzyoperacyjny</span><span class="sxs-lookup"><span data-stu-id="80a50-123">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
