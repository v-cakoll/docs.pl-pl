---
title: nonComVisibleBaseClass MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- visible classes
- managed debugging assistants (MDAs), COM visible classes
- nonComVisibleBaseClass MDA
- COM visible classes
- QueryInterface call failures
- MDAs (managed debugging assistants), COM visible classes
ms.assetid: 9ec1af27-604b-477e-9ee2-e833eb10d3ce
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4b00d8396b07eb445414fb85cd830d595a513be0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="noncomvisiblebaseclass-mda"></a><span data-ttu-id="1f780-102">nonComVisibleBaseClass MDA</span><span class="sxs-lookup"><span data-stu-id="1f780-102">nonComVisibleBaseClass MDA</span></span>
<span data-ttu-id="1f780-103">`nonComVisibleBaseClass` Zarządzany Asystent debugowania (MDA) została aktywowana po `QueryInterface` kod natywny lub niezarządzane w wywoływana otoka COM (CCW) wywołanie, widoczny dla modelu COM zarządzane klasy, która pochodzi z klasy podstawowej, która nie jest widoczne dla modelu COM.</span><span class="sxs-lookup"><span data-stu-id="1f780-103">The `nonComVisibleBaseClass` managed debugging assistant (MDA) is activated when a `QueryInterface` call is made by native or unmanaged code on the COM callable wrapper (CCW) of a COM-visible managed class that derives from a base class that is not COM visible.</span></span>  <span data-ttu-id="1f780-104">`QueryInterface` MDA aktywować tylko w przypadkach, gdy wywołanie zażąda klasy interfejsu lub domyślnej powoduje, że wywołanie `IDispatch` widoczny dla modelu COM klasy zarządzane.</span><span class="sxs-lookup"><span data-stu-id="1f780-104">The `QueryInterface` call causes the MDA to activate only in cases where call requests the class interface or default `IDispatch` of the COM-visible managed class.</span></span>  <span data-ttu-id="1f780-105">MDA nie jest aktywowany, gdy `QueryInterface` dotyczy jawnego interfejsu, który ma <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> atrybut stosowane i jest jawnie implementowana przez widoczny dla modelu COM klasy.</span><span class="sxs-lookup"><span data-stu-id="1f780-105">The MDA is not activated when the `QueryInterface` is for an explicit interface that has the <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> attribute applied and is explicitly implemented by the COM-visible class.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="1f780-106">Symptomy</span><span class="sxs-lookup"><span data-stu-id="1f780-106">Symptoms</span></span>  
 <span data-ttu-id="1f780-107">A `QueryInterface` wywołania z kodu macierzystego, który kończy się niepowodzeniem z COR_E_INVALIDOPERATION HRESULT.</span><span class="sxs-lookup"><span data-stu-id="1f780-107">A `QueryInterface` call made from native code that is failing with a COR_E_INVALIDOPERATION HRESULT.</span></span>  <span data-ttu-id="1f780-108">HRESULT może wynikać ze środowiska uruchomieniowego, brak zezwolenia `QueryInterface` wywołania, które mogłyby spowodować aktywacji to zdarzenie MDA.</span><span class="sxs-lookup"><span data-stu-id="1f780-108">The HRESULT might be due to the runtime disallowing `QueryInterface` calls that would cause the activation of this MDA.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="1f780-109">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="1f780-109">Cause</span></span>  
 <span data-ttu-id="1f780-110">Środowisko uruchomieniowe nie może dopuścić `QueryInterface` odwołuje się do klasy interfejsu lub domyślna `IDispatch` interfejsu widoczny dla modelu COM klasy, która pochodzi z klasy, która nie jest widoczny dla modelu COM ze względu na potencjalne problemy przechowywania wersji.</span><span class="sxs-lookup"><span data-stu-id="1f780-110">The runtime cannot allow `QueryInterface` calls for the class interface or default `IDispatch` interface of a COM-visible class that derives from a class that is not COM-visible because of potential versioning problems.</span></span>  <span data-ttu-id="1f780-111">Na przykład, jeśli wszystkie publiczne elementy członkowskie zostały dodane do klasy podstawowej, która nie jest widoczny dla modelu COM, istniejących klientów modelu COM za pomocą klasy pochodnej może potencjalnie spowodować przerwanie ponieważ vtable klasy pochodnej, która zawiera elementów członkowskich klasy podstawowej, czy można zmienić takie Zmiana.</span><span class="sxs-lookup"><span data-stu-id="1f780-111">For example, if any public members were added to the base class that is not COM-visible, existing COM clients using the derived class could potentially break because the vtable of the derived class, which contains the base class members, would be altered by such a change.</span></span>  <span data-ttu-id="1f780-112">Jawne interfejsy ujawniony dla modelu COM nie mają ten problem, ponieważ nie zawierają podstawowe elementy członkowskie interfejsów w vtable.</span><span class="sxs-lookup"><span data-stu-id="1f780-112">Explicit interfaces exposed to COM do not have this problem because they do not include the base members of interfaces in the vtable.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="1f780-113">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="1f780-113">Resolution</span></span>  
 <span data-ttu-id="1f780-114">Nie ujawniaj interfejsu klasy.</span><span class="sxs-lookup"><span data-stu-id="1f780-114">Do not expose the class interface.</span></span> <span data-ttu-id="1f780-115">Zdefiniuj jawnego interfejsu i zastosować <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> do niej atrybut.</span><span class="sxs-lookup"><span data-stu-id="1f780-115">Define an explicit interface and apply the <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> attribute to it.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="1f780-116">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="1f780-116">Effect on the Runtime</span></span>  
 <span data-ttu-id="1f780-117">To zdarzenie MDA nie ma wpływu na środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="1f780-117">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="1f780-118">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="1f780-118">Output</span></span>  
 <span data-ttu-id="1f780-119">Poniżej przedstawiono przykładowy komunikat dla `QueryInterface` wywoływać dla klasy widoczne COM `Derived` który dziedziczy z klasy niewidoczne COM `Base`.</span><span class="sxs-lookup"><span data-stu-id="1f780-119">The following is an example message for a `QueryInterface` call on a COM-visible class `Derived` that derives from a non-COM-visible class `Base`.</span></span>  
  
```  
A QueryInterface call was made requesting the class interface of COM   
visible managed class 'Derived'. However since this class derives from   
non COM visible class 'Base', the QueryInterface call will fail. This   
is done to prevent the non COM visible base class from being   
constrained by the COM versioning rules.   
```  
  
## <a name="configuration"></a><span data-ttu-id="1f780-120">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="1f780-120">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <nonComVisibleBaseClass />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1f780-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1f780-121">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="1f780-122">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="1f780-122">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="1f780-123">Marshaling międzyoperacyjny</span><span class="sxs-lookup"><span data-stu-id="1f780-123">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
