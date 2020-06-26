---
title: dirtyCastAndCallOnInterface MDA
description: Zapoznaj się z asystentem debugowania zarządzanego dirtyCastAndCallOnInterface, który jest wywoływany, gdy wczesne wywołania tablic wirtualnych są wykonywane na interfejsach klas z późnym wiązaniem.
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
ms.openlocfilehash: 2ed5589909915a261a22c48490e469ae52659c8c
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2020
ms.locfileid: "85416073"
---
# <a name="dirtycastandcalloninterface-mda"></a><span data-ttu-id="3f6fa-103">dirtyCastAndCallOnInterface MDA</span><span class="sxs-lookup"><span data-stu-id="3f6fa-103">dirtyCastAndCallOnInterface MDA</span></span>
<span data-ttu-id="3f6fa-104">`dirtyCastAndCallOnInterface`Asystent debugowania zarządzanego (MDA) jest uaktywniany, gdy podejmowana jest próba wywołania wczesnego za pośrednictwem tablicy tablicowej interfejsu klasy, który został oznaczony jako późny.</span><span class="sxs-lookup"><span data-stu-id="3f6fa-104">The `dirtyCastAndCallOnInterface` managed debugging assistant (MDA) is activated when an early-bound call through a vtable is attempted on a class interface that has been marked late-bound only.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="3f6fa-105">Objawy</span><span class="sxs-lookup"><span data-stu-id="3f6fa-105">Symptoms</span></span>  
 <span data-ttu-id="3f6fa-106">Aplikacja zgłasza naruszenie zasad dostępu lub ma nieoczekiwane zachowanie podczas umieszczania na wczesnym połączeniu wywołania przy użyciu modelu COM do środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="3f6fa-106">An application throws an access violation or has unexpected behavior when placing an early-bound call via COM into the CLR.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="3f6fa-107">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="3f6fa-107">Cause</span></span>  
 <span data-ttu-id="3f6fa-108">Kod próbuje nawiązać połączenie z wczesnym wiązaniem przez tablicę czasową za pośrednictwem interfejsu klasy, który jest tylko z późnym wiązaniem.</span><span class="sxs-lookup"><span data-stu-id="3f6fa-108">Code is attempting an early-bound call through a vtable via a class interface that is late-bound only.</span></span> <span data-ttu-id="3f6fa-109">Należy zauważyć, że domyślnie interfejsy klasy są identyfikowane jako późne wiązanie.</span><span class="sxs-lookup"><span data-stu-id="3f6fa-109">Note that by default class interfaces are identified as being late-bound only.</span></span> <span data-ttu-id="3f6fa-110">Mogą być również identyfikowane jako późne powiązania z <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> atrybutem o <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDispatch> wartości ( `[ClassInterface(ClassInterfaceType.AutoDispatch)]` ).</span><span class="sxs-lookup"><span data-stu-id="3f6fa-110">They can also be identified as late-bound with the <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> attribute with an <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDispatch> value (`[ClassInterface(ClassInterfaceType.AutoDispatch)]`).</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="3f6fa-111">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="3f6fa-111">Resolution</span></span>  
 <span data-ttu-id="3f6fa-112">Zalecanym rozwiązaniem jest zdefiniowanie jawnego interfejsu do użycia przez model COM i zadzwonienie klientów modelu COM za pomocą tego interfejsu zamiast za pomocą automatycznie wygenerowanego interfejsu klasy.</span><span class="sxs-lookup"><span data-stu-id="3f6fa-112">The recommended resolution is to define an explicit interface for use by COM and have the COM clients call through this interface instead of through the automatically generated class interface.</span></span> <span data-ttu-id="3f6fa-113">Alternatywnie wywołanie z modelu COM może być przekształcone w wywołanie z późnym wiązaniem za pośrednictwem `IDispatch` .</span><span class="sxs-lookup"><span data-stu-id="3f6fa-113">Alternatively, the call from COM can be transformed into a late-bound call via `IDispatch`.</span></span>  
  
 <span data-ttu-id="3f6fa-114">Na koniec istnieje możliwość zidentyfikowania klasy jako <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual> ( `[ClassInterface(ClassInterfaceType.AutoDual)]` ) w celu umożliwienia umieszczenia wywołań wczesnego wiązania z modelu COM, jednak użycie <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual> jest zdecydowanie odradzane ze względu na ograniczenia wersji opisane w temacie <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> .</span><span class="sxs-lookup"><span data-stu-id="3f6fa-114">Finally, it is possible to identify the class as <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual> (`[ClassInterface(ClassInterfaceType.AutoDual)]`) to allow early bound calls to be placed from COM; however, using <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual> is strongly discouraged because of the versioning limitations described in <xref:System.Runtime.InteropServices.ClassInterfaceAttribute>.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="3f6fa-115">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="3f6fa-115">Effect on the Runtime</span></span>  
 <span data-ttu-id="3f6fa-116">To zdarzenie MDA nie ma wpływu na środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="3f6fa-116">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="3f6fa-117">Raportuje tylko dane dotyczące wczesnych wywołań w interfejsach z późnym wiązaniem.</span><span class="sxs-lookup"><span data-stu-id="3f6fa-117">It only reports data about early-bound calls on late-bound interfaces.</span></span>  
  
## <a name="output"></a><span data-ttu-id="3f6fa-118">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="3f6fa-118">Output</span></span>  
 <span data-ttu-id="3f6fa-119">Nazwa metody lub nazwy pola, do którego uzyskuje się wczesne powiązanie.</span><span class="sxs-lookup"><span data-stu-id="3f6fa-119">The name of the method or name of the field being accessed early-bound.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="3f6fa-120">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="3f6fa-120">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dirtyCastAndCallOnInterface />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3f6fa-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3f6fa-121">See also</span></span>

- <xref:System.Runtime.InteropServices.ClassInterfaceAttribute>
- [<span data-ttu-id="3f6fa-122">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="3f6fa-122">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
