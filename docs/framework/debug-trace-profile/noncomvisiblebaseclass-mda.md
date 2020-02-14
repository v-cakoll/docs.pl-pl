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
ms.openlocfilehash: b46d5c6ffbf12efbae113a95bbfccd5742ec9ec9
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217304"
---
# <a name="noncomvisiblebaseclass-mda"></a><span data-ttu-id="57c45-102">nonComVisibleBaseClass MDA</span><span class="sxs-lookup"><span data-stu-id="57c45-102">nonComVisibleBaseClass MDA</span></span>
<span data-ttu-id="57c45-103">Asystent debugowania zarządzanego `nonComVisibleBaseClass` (MDA) jest uaktywniany, gdy wywołanie `QueryInterface` odbywa się przy użyciu kodu natywnego lub niezarządzanego w przypadku niewidocznej otoki COM (CCW) klasy zarządzanej w modelu COM, która dziedziczy z klasy podstawowej, która nie jest widoczna dla modelu COM.</span><span class="sxs-lookup"><span data-stu-id="57c45-103">The `nonComVisibleBaseClass` managed debugging assistant (MDA) is activated when a `QueryInterface` call is made by native or unmanaged code on the COM callable wrapper (CCW) of a COM-visible managed class that derives from a base class that is not COM visible.</span></span>  <span data-ttu-id="57c45-104">Wywołanie `QueryInterface` powoduje aktywację elementu MDA tylko w przypadkach, gdy wywołania żądają interfejsu klasy lub domyślnej `IDispatch` klasy zarządzanej widocznej dla modelu COM.</span><span class="sxs-lookup"><span data-stu-id="57c45-104">The `QueryInterface` call causes the MDA to activate only in cases where call requests the class interface or default `IDispatch` of the COM-visible managed class.</span></span>  <span data-ttu-id="57c45-105">Zdarzenie MDA nie jest aktywowane, gdy `QueryInterface` dotyczy jawnego interfejsu, do którego zastosowano atrybut <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> i jest on jawnie zaimplementowany przez klasę widoczną dla modelu COM.</span><span class="sxs-lookup"><span data-stu-id="57c45-105">The MDA is not activated when the `QueryInterface` is for an explicit interface that has the <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> attribute applied and is explicitly implemented by the COM-visible class.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="57c45-106">Objawy</span><span class="sxs-lookup"><span data-stu-id="57c45-106">Symptoms</span></span>  
 <span data-ttu-id="57c45-107">Wywołanie `QueryInterface` wykonane z kodu natywnego, który kończy się niepowodzeniem z COR_E_INVALIDOPERATION HRESULT.</span><span class="sxs-lookup"><span data-stu-id="57c45-107">A `QueryInterface` call made from native code that is failing with a COR_E_INVALIDOPERATION HRESULT.</span></span>  <span data-ttu-id="57c45-108">WYNIK HRESULT może być spowodowany tym, że środowisko uruchomieniowe nie zezwoli na `QueryInterface` wywołań, które mogłyby spowodować aktywację tego elementu MDA.</span><span class="sxs-lookup"><span data-stu-id="57c45-108">The HRESULT might be due to the runtime disallowing `QueryInterface` calls that would cause the activation of this MDA.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="57c45-109">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="57c45-109">Cause</span></span>  
 <span data-ttu-id="57c45-110">Środowisko wykonawcze nie może zezwalać na `QueryInterface` wywołań interfejsu klasy ani domyślnego interfejsu `IDispatch` klasy widocznej dla modelu COM, która dziedziczy z klasy, która nie jest widoczna dla modelu COM ze względu na potencjalne problemy z wersjami.</span><span class="sxs-lookup"><span data-stu-id="57c45-110">The runtime cannot allow `QueryInterface` calls for the class interface or default `IDispatch` interface of a COM-visible class that derives from a class that is not COM-visible because of potential versioning problems.</span></span>  <span data-ttu-id="57c45-111">Na przykład, jeśli jakikolwiek publiczny element członkowski został dodany do klasy podstawowej, która nie jest widoczna dla modelu COM, istniejący klienci COM korzystający z klasy pochodnej mogą potencjalnie przerwać, ponieważ tablice metod pochodnych klasy pochodnej, która zawiera składowe klasy bazowej, zostałyby zmienione przez takie stąp.</span><span class="sxs-lookup"><span data-stu-id="57c45-111">For example, if any public members were added to the base class that is not COM-visible, existing COM clients using the derived class could potentially break because the vtable of the derived class, which contains the base class members, would be altered by such a change.</span></span>  <span data-ttu-id="57c45-112">Jawne interfejsy uwidocznione dla modelu COM nie mają tego problemu, ponieważ nie obejmują podstawowych elementów członkowskich interfejsów w tablicy bazowej.</span><span class="sxs-lookup"><span data-stu-id="57c45-112">Explicit interfaces exposed to COM do not have this problem because they do not include the base members of interfaces in the vtable.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="57c45-113">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="57c45-113">Resolution</span></span>  
 <span data-ttu-id="57c45-114">Nie ujawniaj interfejsu klasy.</span><span class="sxs-lookup"><span data-stu-id="57c45-114">Do not expose the class interface.</span></span> <span data-ttu-id="57c45-115">Zdefiniuj jawny interfejs i Zastosuj do niego atrybut <xref:System.Runtime.InteropServices.ClassInterfaceAttribute>.</span><span class="sxs-lookup"><span data-stu-id="57c45-115">Define an explicit interface and apply the <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> attribute to it.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="57c45-116">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="57c45-116">Effect on the Runtime</span></span>  
 <span data-ttu-id="57c45-117">To zdarzenie MDA nie ma wpływu na środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="57c45-117">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="57c45-118">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="57c45-118">Output</span></span>  
 <span data-ttu-id="57c45-119">Poniżej znajduje się przykładowy komunikat dla wywołania `QueryInterface` na klasie widocznej dla modelu COM `Derived`, który pochodzi z klasy niewidocznej dla modelu COM, `Base`.</span><span class="sxs-lookup"><span data-stu-id="57c45-119">The following is an example message for a `QueryInterface` call on a COM-visible class `Derived` that derives from a non-COM-visible class `Base`.</span></span>  
  
```output
A QueryInterface call was made requesting the class interface of COM   
visible managed class 'Derived'. However since this class derives from   
non COM visible class 'Base', the QueryInterface call will fail. This   
is done to prevent the non COM visible base class from being   
constrained by the COM versioning rules.   
```  
  
## <a name="configuration"></a><span data-ttu-id="57c45-120">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="57c45-120">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <nonComVisibleBaseClass />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="57c45-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="57c45-121">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="57c45-122">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="57c45-122">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="57c45-123">Marshaling międzyoperacyjny</span><span class="sxs-lookup"><span data-stu-id="57c45-123">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
