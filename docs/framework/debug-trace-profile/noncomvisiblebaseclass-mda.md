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
ms.openlocfilehash: 4c16432df201d19b65c91206ec529d07605e979a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181788"
---
# <a name="noncomvisiblebaseclass-mda"></a><span data-ttu-id="9d68b-102">nonComVisibleBaseClass MDA</span><span class="sxs-lookup"><span data-stu-id="9d68b-102">nonComVisibleBaseClass MDA</span></span>
<span data-ttu-id="9d68b-103">Zarządzany `nonComVisibleBaseClass` asystent debugowania (MDA) jest `QueryInterface` aktywowany, gdy wywołanie jest nawiązywane przez kod macierzysty lub niezarządzany na otoce (CCW) wywoływanej przez COM klasy zarządzanej, która wywodzi się z klasy podstawowej, która nie jest widoczna dla modelu COM.</span><span class="sxs-lookup"><span data-stu-id="9d68b-103">The `nonComVisibleBaseClass` managed debugging assistant (MDA) is activated when a `QueryInterface` call is made by native or unmanaged code on the COM callable wrapper (CCW) of a COM-visible managed class that derives from a base class that is not COM visible.</span></span>  <span data-ttu-id="9d68b-104">Wywołanie `QueryInterface` powoduje, że MDA, aby aktywować tylko `IDispatch` w przypadkach, gdy wywołania żąda interfejsu klasy lub domyślnie klasy zarządzanej widoczne com.</span><span class="sxs-lookup"><span data-stu-id="9d68b-104">The `QueryInterface` call causes the MDA to activate only in cases where call requests the class interface or default `IDispatch` of the COM-visible managed class.</span></span>  <span data-ttu-id="9d68b-105">MDA nie jest aktywowany, gdy `QueryInterface` jest dla <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> jawnego interfejsu, który ma atrybut stosowane i jest jawnie implementowane przez klasę widoczne COM.</span><span class="sxs-lookup"><span data-stu-id="9d68b-105">The MDA is not activated when the `QueryInterface` is for an explicit interface that has the <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> attribute applied and is explicitly implemented by the COM-visible class.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="9d68b-106">Objawy</span><span class="sxs-lookup"><span data-stu-id="9d68b-106">Symptoms</span></span>  
 <span data-ttu-id="9d68b-107">Wywołanie `QueryInterface` wykonane z kodu macierzystego, który kończy się niepowodzeniem z COR_E_INVALIDOPERATION HRESULT.</span><span class="sxs-lookup"><span data-stu-id="9d68b-107">A `QueryInterface` call made from native code that is failing with a COR_E_INVALIDOPERATION HRESULT.</span></span>  <span data-ttu-id="9d68b-108">HRESULT może być ze względu na czas `QueryInterface` wykonywania nie zezwalając na wywołania, które mogłyby spowodować aktywację tego MDA.</span><span class="sxs-lookup"><span data-stu-id="9d68b-108">The HRESULT might be due to the runtime disallowing `QueryInterface` calls that would cause the activation of this MDA.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="9d68b-109">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="9d68b-109">Cause</span></span>  
 <span data-ttu-id="9d68b-110">Środowisko wykonawcze `QueryInterface` nie może zezwolić `IDispatch` na wywołania interfejsu klasy lub domyślnego interfejsu klasy widocznej w trybie COM, która pochodzi z klasy, która nie jest widoczna dla środowiska COM z powodu potencjalnych problemów z przechowywaniem wersji.</span><span class="sxs-lookup"><span data-stu-id="9d68b-110">The runtime cannot allow `QueryInterface` calls for the class interface or default `IDispatch` interface of a COM-visible class that derives from a class that is not COM-visible because of potential versioning problems.</span></span>  <span data-ttu-id="9d68b-111">Na przykład jeśli wszystkie elementy publiczne zostały dodane do klasy podstawowej, która nie jest widoczna dla com, istniejących klientów COM przy użyciu klasy pochodnej może potencjalnie przerwać, ponieważ vtable klasy pochodnej, która zawiera elementy członkowskie klasy podstawowej, zostaną zmienione przez takie a Zmienić.</span><span class="sxs-lookup"><span data-stu-id="9d68b-111">For example, if any public members were added to the base class that is not COM-visible, existing COM clients using the derived class could potentially break because the vtable of the derived class, which contains the base class members, would be altered by such a change.</span></span>  <span data-ttu-id="9d68b-112">Jawne interfejsy narażone na COM nie mają tego problemu, ponieważ nie zawierają podstawowych elementów członkowskich interfejsów w vtable.</span><span class="sxs-lookup"><span data-stu-id="9d68b-112">Explicit interfaces exposed to COM do not have this problem because they do not include the base members of interfaces in the vtable.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="9d68b-113">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="9d68b-113">Resolution</span></span>  
 <span data-ttu-id="9d68b-114">Nie należy udostępniać interfejsu klasy.</span><span class="sxs-lookup"><span data-stu-id="9d68b-114">Do not expose the class interface.</span></span> <span data-ttu-id="9d68b-115">Zdefiniuj jawny interfejs i zastosuj do niego <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> atrybut.</span><span class="sxs-lookup"><span data-stu-id="9d68b-115">Define an explicit interface and apply the <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> attribute to it.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="9d68b-116">Wpływ na czas działania</span><span class="sxs-lookup"><span data-stu-id="9d68b-116">Effect on the Runtime</span></span>  
 <span data-ttu-id="9d68b-117">To MDA nie ma wpływu na CLR.</span><span class="sxs-lookup"><span data-stu-id="9d68b-117">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="9d68b-118">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="9d68b-118">Output</span></span>  
 <span data-ttu-id="9d68b-119">Poniżej przedstawiono przykładową `QueryInterface` wiadomość dla wywołania `Derived` klasy widocznej w trybie COM, `Base`która wywodzi się z klasy niewidocznej dla com.</span><span class="sxs-lookup"><span data-stu-id="9d68b-119">The following is an example message for a `QueryInterface` call on a COM-visible class `Derived` that derives from a non-COM-visible class `Base`.</span></span>  
  
```output
A QueryInterface call was made requesting the class interface of COM
visible managed class 'Derived'. However since this class derives from
non COM visible class 'Base', the QueryInterface call will fail. This
is done to prevent the non COM visible base class from being
constrained by the COM versioning rules.
```  
  
## <a name="configuration"></a><span data-ttu-id="9d68b-120">Konfigurowanie</span><span class="sxs-lookup"><span data-stu-id="9d68b-120">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <nonComVisibleBaseClass />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9d68b-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9d68b-121">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="9d68b-122">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="9d68b-122">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="9d68b-123">Organizowanie międzyoperacyjne</span><span class="sxs-lookup"><span data-stu-id="9d68b-123">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
