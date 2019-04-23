---
title: dirtyCastAndCallOnInterface MDA
ms.date: 03/30/2017
helpviewer_keywords:
- managed debugging assistants (MDAs), early bound calls AutoDispatch
- dispatch-only mode
- dirtyCastAndCallOnInterface
- early-bound managed classes
- early bound calls on AutoDispatch
- MDAs (managed debugging assistants), early bound calls AutoDispatch
- EarlyBoundCallOnAutorDispatchClassInteface MDA
ms.assetid: aa388ed3-7e3d-48ea-a0b5-c47ae19cec38
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5a28820479ca15ad72475ae9a7754bbbf99ce5c5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59108592"
---
# <a name="dirtycastandcalloninterface-mda"></a><span data-ttu-id="e5935-102">dirtyCastAndCallOnInterface MDA</span><span class="sxs-lookup"><span data-stu-id="e5935-102">dirtyCastAndCallOnInterface MDA</span></span>
<span data-ttu-id="e5935-103">`dirtyCastAndCallOnInterface` Zarządzanego Asystenta debugowania (MDA) jest aktywowany, gdy próba zostanie podjęta na interfejs klasy, która została oznaczona z późnym wiązaniem tylko wywołanie wczesnym wiązaniem przy użyciu wartości vtable.</span><span class="sxs-lookup"><span data-stu-id="e5935-103">The `dirtyCastAndCallOnInterface` managed debugging assistant (MDA) is activated when an early-bound call through a vtable is attempted on a class interface that has been marked late-bound only.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="e5935-104">Symptomy</span><span class="sxs-lookup"><span data-stu-id="e5935-104">Symptoms</span></span>  
 <span data-ttu-id="e5935-105">Aplikacja zgłasza naruszenie zasad dostępu lub ma nieoczekiwane zachowanie podczas umieszczania wywołania z wczesnym wiązaniem za pośrednictwem modelu COM do środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="e5935-105">An application throws an access violation or has unexpected behavior when placing an early-bound call via COM into the CLR.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="e5935-106">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="e5935-106">Cause</span></span>  
 <span data-ttu-id="e5935-107">Kod próbuje wywołania wczesnym wiązaniem vtable za pośrednictwem interfejsu klasy, która jest tylko z późnym wiązaniem.</span><span class="sxs-lookup"><span data-stu-id="e5935-107">Code is attempting an early-bound call through a vtable via a class interface that is late-bound only.</span></span> <span data-ttu-id="e5935-108">Należy pamiętać, że przez domyślną klasę interfejsy są identyfikowane jako trwa z późnym wiązaniem tylko.</span><span class="sxs-lookup"><span data-stu-id="e5935-108">Note that by default class interfaces are identified as being late-bound only.</span></span> <span data-ttu-id="e5935-109">Można również zidentyfikować jako z późnym wiązaniem przy użyciu <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> atrybutem <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDispatch> wartość (`[ClassInterface(ClassInterfaceType.AutoDispatch)]`).</span><span class="sxs-lookup"><span data-stu-id="e5935-109">They can also be identified as late-bound with the <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> attribute with an <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDispatch> value (`[ClassInterface(ClassInterfaceType.AutoDispatch)]`).</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="e5935-110">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="e5935-110">Resolution</span></span>  
 <span data-ttu-id="e5935-111">Zalecane rozwiązanie jest zdefiniowanie interfejsu jawnego do użycia przez model COM i mieć wywołania klientów modelu COM za pośrednictwem tego interfejsu, zamiast za pośrednictwem interfejsu automatycznie wygenerowana klasa.</span><span class="sxs-lookup"><span data-stu-id="e5935-111">The recommended resolution is to define an explicit interface for use by COM and have the COM clients call through this interface instead of through the automatically generated class interface.</span></span> <span data-ttu-id="e5935-112">Alternatywnie wywołania z modelu COM mogą zostać przekształcone do wywołania późnego wiązania za pośrednictwem `IDispatch`.</span><span class="sxs-lookup"><span data-stu-id="e5935-112">Alternatively, the call from COM can be transformed into a late-bound call via `IDispatch`.</span></span>  
  
 <span data-ttu-id="e5935-113">Na koniec jest możliwe zidentyfikować klasę jako <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual> (`[ClassInterface(ClassInterfaceType.AutoDual)]`) umożliwia wywołania z wczesnym wiązaniem do umieszczenia z modelu COM; jednak za pomocą <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual> jest zdecydowanie odradzane ze względu na ograniczenia wersji opisanego w <xref:System.Runtime.InteropServices.ClassInterfaceAttribute>.</span><span class="sxs-lookup"><span data-stu-id="e5935-113">Finally, it is possible to identify the class as <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual> (`[ClassInterface(ClassInterfaceType.AutoDual)]`) to allow early bound calls to be placed from COM; however, using <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual> is strongly discouraged because of the versioning limitations described in <xref:System.Runtime.InteropServices.ClassInterfaceAttribute>.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="e5935-114">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="e5935-114">Effect on the Runtime</span></span>  
 <span data-ttu-id="e5935-115">To zdarzenie MDA nie ma wpływu na środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="e5935-115">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="e5935-116">Informuje jedynie dane o wywołaniach wczesnym wiązaniem dla interfejsów z późnym wiązaniem.</span><span class="sxs-lookup"><span data-stu-id="e5935-116">It only reports data about early-bound calls on late-bound interfaces.</span></span>  
  
## <a name="output"></a><span data-ttu-id="e5935-117">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="e5935-117">Output</span></span>  
 <span data-ttu-id="e5935-118">Nazwa metody lub nazwę pola, którego uzyskiwany jest dostęp wczesnym wiązaniem.</span><span class="sxs-lookup"><span data-stu-id="e5935-118">The name of the method or name of the field being accessed early-bound.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="e5935-119">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="e5935-119">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dirtyCastAndCallOnInterface />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e5935-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e5935-120">See also</span></span>

- <xref:System.Runtime.InteropServices.ClassInterfaceAttribute>
- [<span data-ttu-id="e5935-121">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="e5935-121">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
