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
ms.openlocfilehash: eb0810a9e0ffce825abecc87eb2698920209d86f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59171811"
---
# <a name="noncomvisiblebaseclass-mda"></a><span data-ttu-id="ef3c3-102">nonComVisibleBaseClass MDA</span><span class="sxs-lookup"><span data-stu-id="ef3c3-102">nonComVisibleBaseClass MDA</span></span>
<span data-ttu-id="ef3c3-103">`nonComVisibleBaseClass` Zarządzanego Asystenta debugowania (MDA) jest aktywowany po `QueryInterface` klasy COM widoczny dla zarządzanych, która pochodzi od klasy podstawowej, która nie jest widoczne dla modelu COM, natywny lub kodowi niezarządzanemu na wywoływana otoka COM (CCW) zostanie nawiązane połączenie.</span><span class="sxs-lookup"><span data-stu-id="ef3c3-103">The `nonComVisibleBaseClass` managed debugging assistant (MDA) is activated when a `QueryInterface` call is made by native or unmanaged code on the COM callable wrapper (CCW) of a COM-visible managed class that derives from a base class that is not COM visible.</span></span>  <span data-ttu-id="ef3c3-104">`QueryInterface` Wywołanie powoduje, że MDA aktywować tylko w przypadkach, w której żądania wywołań interfejsu klasy lub domyślna `IDispatch` COM widoczny dla klas zarządzanych.</span><span class="sxs-lookup"><span data-stu-id="ef3c3-104">The `QueryInterface` call causes the MDA to activate only in cases where call requests the class interface or default `IDispatch` of the COM-visible managed class.</span></span>  <span data-ttu-id="ef3c3-105">MDA jest aktywowane gdy `QueryInterface` jest jawne interfejsu, który ma <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> atrybut zastosowane i jest jawnie implementowane przez klasy widoczne COM.</span><span class="sxs-lookup"><span data-stu-id="ef3c3-105">The MDA is not activated when the `QueryInterface` is for an explicit interface that has the <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> attribute applied and is explicitly implemented by the COM-visible class.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="ef3c3-106">Symptomy</span><span class="sxs-lookup"><span data-stu-id="ef3c3-106">Symptoms</span></span>  
 <span data-ttu-id="ef3c3-107">A `QueryInterface` wywołania z kodu macierzystego, który kończy się niepowodzeniem z COR_E_INVALIDOPERATION HRESULT.</span><span class="sxs-lookup"><span data-stu-id="ef3c3-107">A `QueryInterface` call made from native code that is failing with a COR_E_INVALIDOPERATION HRESULT.</span></span>  <span data-ttu-id="ef3c3-108">HRESULT może wynikać ze środowiska uruchomieniowego nie można przydzielać `QueryInterface` wywołania, które mogą być przyczyną aktywacji to zdarzenie MDA.</span><span class="sxs-lookup"><span data-stu-id="ef3c3-108">The HRESULT might be due to the runtime disallowing `QueryInterface` calls that would cause the activation of this MDA.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="ef3c3-109">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="ef3c3-109">Cause</span></span>  
 <span data-ttu-id="ef3c3-110">Środowisko wykonawcze nie może dopuścić `QueryInterface` wywołania do klasy interfejsu lub domyślne `IDispatch` interfejsu klasy widoczne COM, która pochodzi od klasy, które nie są widoczne dla modelu COM ze względu na potencjalne problemy z wersjonowaniem.</span><span class="sxs-lookup"><span data-stu-id="ef3c3-110">The runtime cannot allow `QueryInterface` calls for the class interface or default `IDispatch` interface of a COM-visible class that derives from a class that is not COM-visible because of potential versioning problems.</span></span>  <span data-ttu-id="ef3c3-111">Na przykład, jeśli wszystkie publiczne elementy członkowskie zostały dodane do klasy bazowej, który nie jest widoczny dla modelu COM, istniejących klientów modelu COM za pomocą klasy pochodnej może potencjalnie uszkodzić ponieważ vtable klasy pochodnej, która zawiera składowe klasy podstawowej, może być zmienione przez takie Zmiana.</span><span class="sxs-lookup"><span data-stu-id="ef3c3-111">For example, if any public members were added to the base class that is not COM-visible, existing COM clients using the derived class could potentially break because the vtable of the derived class, which contains the base class members, would be altered by such a change.</span></span>  <span data-ttu-id="ef3c3-112">Jawne interfejsy widoczne dla modelu COM nie mają tego problemu, ponieważ nie zawierają elementów podstawowych interfejsów w vtable.</span><span class="sxs-lookup"><span data-stu-id="ef3c3-112">Explicit interfaces exposed to COM do not have this problem because they do not include the base members of interfaces in the vtable.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="ef3c3-113">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="ef3c3-113">Resolution</span></span>  
 <span data-ttu-id="ef3c3-114">Nie ujawniaj interfejsu klasy.</span><span class="sxs-lookup"><span data-stu-id="ef3c3-114">Do not expose the class interface.</span></span> <span data-ttu-id="ef3c3-115">Definiowanie interfejsu jawnego i stosowanie <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> atrybutu do niego.</span><span class="sxs-lookup"><span data-stu-id="ef3c3-115">Define an explicit interface and apply the <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> attribute to it.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="ef3c3-116">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="ef3c3-116">Effect on the Runtime</span></span>  
 <span data-ttu-id="ef3c3-117">To zdarzenie MDA nie ma wpływu na środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="ef3c3-117">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="ef3c3-118">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="ef3c3-118">Output</span></span>  
 <span data-ttu-id="ef3c3-119">Poniżej przedstawiono przykładowy komunikat dla `QueryInterface` wywołać klasy widoczne COM `Derived` która jest pochodną klasy COM-niewidocznych `Base`.</span><span class="sxs-lookup"><span data-stu-id="ef3c3-119">The following is an example message for a `QueryInterface` call on a COM-visible class `Derived` that derives from a non-COM-visible class `Base`.</span></span>  
  
```  
A QueryInterface call was made requesting the class interface of COM   
visible managed class 'Derived'. However since this class derives from   
non COM visible class 'Base', the QueryInterface call will fail. This   
is done to prevent the non COM visible base class from being   
constrained by the COM versioning rules.   
```  
  
## <a name="configuration"></a><span data-ttu-id="ef3c3-120">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="ef3c3-120">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <nonComVisibleBaseClass />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ef3c3-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ef3c3-121">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="ef3c3-122">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="ef3c3-122">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="ef3c3-123">Organizowanie międzyoperacyjne</span><span class="sxs-lookup"><span data-stu-id="ef3c3-123">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
