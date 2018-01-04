---
title: dirtyCastAndCallOnInterface MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managed debugging assistants (MDAs), early bound calls AutoDispatch
- dispatch-only mode
- dirtyCastAndCallOnInterface
- early-bound managed classes
- early bound calls on AutoDispatch
- MDAs (managed debugging assistants), early bound calls AutoDispatch
- EarlyBoundCallOnAutorDispatchClassInteface MDA
ms.assetid: aa388ed3-7e3d-48ea-a0b5-c47ae19cec38
caps.latest.revision: "17"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1dcb3e5088b8dbc5b1d803ff042e363ec6e389a8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="dirtycastandcalloninterface-mda"></a><span data-ttu-id="c0d6d-102">dirtyCastAndCallOnInterface MDA</span><span class="sxs-lookup"><span data-stu-id="c0d6d-102">dirtyCastAndCallOnInterface MDA</span></span>
<span data-ttu-id="c0d6d-103">`dirtyCastAndCallOnInterface` Zarządzany Asystent debugowania (MDA) jest aktywowany, gdy w interfejsie klasy, która została oznaczona jako późnym wiązaniem tylko podejmowane są próby wywołania z wczesnym wiązaniem vtable.</span><span class="sxs-lookup"><span data-stu-id="c0d6d-103">The `dirtyCastAndCallOnInterface` managed debugging assistant (MDA) is activated when an early-bound call through a vtable is attempted on a class interface that has been marked late-bound only.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="c0d6d-104">Symptomy</span><span class="sxs-lookup"><span data-stu-id="c0d6d-104">Symptoms</span></span>  
 <span data-ttu-id="c0d6d-105">Aplikacja zgłasza naruszenie zasad dostępu lub ma nieoczekiwanego zachowania podczas umieszczania wywołania z wczesnym wiązaniem za pośrednictwem modelu COM do środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="c0d6d-105">An application throws an access violation or has unexpected behavior when placing an early-bound call via COM into the CLR.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="c0d6d-106">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="c0d6d-106">Cause</span></span>  
 <span data-ttu-id="c0d6d-107">Kod jest próba wywołania z wczesnym wiązaniem vtable za pośrednictwem interfejsu klasy, które są tylko późnym wiązaniem.</span><span class="sxs-lookup"><span data-stu-id="c0d6d-107">Code is attempting an early-bound call through a vtable via a class interface that is late-bound only.</span></span> <span data-ttu-id="c0d6d-108">Należy pamiętać, że przez domyślną klasę interfejsy są identyfikowane jako trwa późnym wiązaniem tylko.</span><span class="sxs-lookup"><span data-stu-id="c0d6d-108">Note that by default class interfaces are identified as being late-bound only.</span></span> <span data-ttu-id="c0d6d-109">Można również zidentyfikować je jako późnym wiązaniem z <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> atrybutem <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDispatch> wartość (`[ClassInterface(ClassInterfaceType.AutoDispatch)]`).</span><span class="sxs-lookup"><span data-stu-id="c0d6d-109">They can also be identified as late-bound with the <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> attribute with an <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDispatch> value (`[ClassInterface(ClassInterfaceType.AutoDispatch)]`).</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="c0d6d-110">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="c0d6d-110">Resolution</span></span>  
 <span data-ttu-id="c0d6d-111">Zalecane rozwiązanie jest zdefiniować jawnego interfejsu do użycia przez model COM, a wywołania klientów modelu COM za pośrednictwem tego interfejsu zamiast za pomocą interfejsu automatycznie wygenerowana klasa.</span><span class="sxs-lookup"><span data-stu-id="c0d6d-111">The recommended resolution is to define an explicit interface for use by COM and have the COM clients call through this interface instead of through the automatically generated class interface.</span></span> <span data-ttu-id="c0d6d-112">Alternatywnie wywołania z modelu COM może służyć za pośrednictwem wywołania późnym wiązaniem `IDispatch`.</span><span class="sxs-lookup"><span data-stu-id="c0d6d-112">Alternatively, the call from COM can be transformed into a late-bound call via `IDispatch`.</span></span>  
  
 <span data-ttu-id="c0d6d-113">Ponadto istnieje możliwość identyfikowania klasy jako <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual> (`[ClassInterface(ClassInterfaceType.AutoDual)]`) umożliwia wywołania z wczesnym wiązaniem do umieszczenia z modelu COM; jednak za pomocą <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual> jest zalecane z powodu ograniczeń versioning opisanego w <xref:System.Runtime.InteropServices.ClassInterfaceAttribute>.</span><span class="sxs-lookup"><span data-stu-id="c0d6d-113">Finally, it is possible to identify the class as <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual> (`[ClassInterface(ClassInterfaceType.AutoDual)]`) to allow early bound calls to be placed from COM; however, using <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual> is strongly discouraged because of the versioning limitations described in <xref:System.Runtime.InteropServices.ClassInterfaceAttribute>.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="c0d6d-114">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="c0d6d-114">Effect on the Runtime</span></span>  
 <span data-ttu-id="c0d6d-115">To zdarzenie MDA nie ma wpływu na środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="c0d6d-115">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="c0d6d-116">Zwraca tylko dane o wywołania z wczesnym wiązaniem dla interfejsów z późnym wiązaniem.</span><span class="sxs-lookup"><span data-stu-id="c0d6d-116">It only reports data about early-bound calls on late-bound interfaces.</span></span>  
  
## <a name="output"></a><span data-ttu-id="c0d6d-117">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="c0d6d-117">Output</span></span>  
 <span data-ttu-id="c0d6d-118">Nazwa metody lub nazwę pola, do której uzyskuje dostęp z wczesnym wiązaniem.</span><span class="sxs-lookup"><span data-stu-id="c0d6d-118">The name of the method or name of the field being accessed early-bound.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="c0d6d-119">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="c0d6d-119">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dirtyCastAndCallOnInterface />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c0d6d-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c0d6d-120">See Also</span></span>  
 <xref:System.Runtime.InteropServices.ClassInterfaceAttribute>  
 [<span data-ttu-id="c0d6d-121">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="c0d6d-121">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
