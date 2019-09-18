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
ms.openlocfilehash: 6ac43f6b92198fec03e722b6cf5e12b86df6f4b8
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052869"
---
# <a name="dirtycastandcalloninterface-mda"></a><span data-ttu-id="45339-102">dirtyCastAndCallOnInterface MDA</span><span class="sxs-lookup"><span data-stu-id="45339-102">dirtyCastAndCallOnInterface MDA</span></span>
<span data-ttu-id="45339-103">Asystent `dirtyCastAndCallOnInterface` debugowania zarządzanego (MDA) jest uaktywniany, gdy podejmowana jest próba wywołania wczesnego za pośrednictwem tablicy tablicowej interfejsu klasy, który został oznaczony jako późny.</span><span class="sxs-lookup"><span data-stu-id="45339-103">The `dirtyCastAndCallOnInterface` managed debugging assistant (MDA) is activated when an early-bound call through a vtable is attempted on a class interface that has been marked late-bound only.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="45339-104">Symptomy</span><span class="sxs-lookup"><span data-stu-id="45339-104">Symptoms</span></span>  
 <span data-ttu-id="45339-105">Aplikacja zgłasza naruszenie zasad dostępu lub ma nieoczekiwane zachowanie podczas umieszczania na wczesnym połączeniu wywołania przy użyciu modelu COM do środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="45339-105">An application throws an access violation or has unexpected behavior when placing an early-bound call via COM into the CLR.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="45339-106">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="45339-106">Cause</span></span>  
 <span data-ttu-id="45339-107">Kod próbuje nawiązać połączenie z wczesnym wiązaniem przez tablicę czasową za pośrednictwem interfejsu klasy, który jest tylko z późnym wiązaniem.</span><span class="sxs-lookup"><span data-stu-id="45339-107">Code is attempting an early-bound call through a vtable via a class interface that is late-bound only.</span></span> <span data-ttu-id="45339-108">Należy zauważyć, że domyślnie interfejsy klasy są identyfikowane jako późne wiązanie.</span><span class="sxs-lookup"><span data-stu-id="45339-108">Note that by default class interfaces are identified as being late-bound only.</span></span> <span data-ttu-id="45339-109">Mogą być również identyfikowane jako późne powiązania z <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> atrybutem <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDispatch> o wartości (`[ClassInterface(ClassInterfaceType.AutoDispatch)]`).</span><span class="sxs-lookup"><span data-stu-id="45339-109">They can also be identified as late-bound with the <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> attribute with an <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDispatch> value (`[ClassInterface(ClassInterfaceType.AutoDispatch)]`).</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="45339-110">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="45339-110">Resolution</span></span>  
 <span data-ttu-id="45339-111">Zalecanym rozwiązaniem jest zdefiniowanie jawnego interfejsu do użycia przez model COM i zadzwonienie klientów modelu COM za pomocą tego interfejsu zamiast za pomocą automatycznie wygenerowanego interfejsu klasy.</span><span class="sxs-lookup"><span data-stu-id="45339-111">The recommended resolution is to define an explicit interface for use by COM and have the COM clients call through this interface instead of through the automatically generated class interface.</span></span> <span data-ttu-id="45339-112">Alternatywnie wywołanie z modelu COM może być przekształcone w wywołanie z późnym wiązaniem za pośrednictwem `IDispatch`.</span><span class="sxs-lookup"><span data-stu-id="45339-112">Alternatively, the call from COM can be transformed into a late-bound call via `IDispatch`.</span></span>  
  
 <span data-ttu-id="45339-113">Na koniec istnieje <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual> możliwość zidentyfikowania klasy jako (`[ClassInterface(ClassInterfaceType.AutoDual)]`) w celu umożliwienia umieszczenia wywołań wczesnego wiązania z modelu COM, jednak użycie <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual> jest zdecydowanie odradzane ze względu na ograniczenia wersji opisane w <xref:System.Runtime.InteropServices.ClassInterfaceAttribute>temacie.</span><span class="sxs-lookup"><span data-stu-id="45339-113">Finally, it is possible to identify the class as <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual> (`[ClassInterface(ClassInterfaceType.AutoDual)]`) to allow early bound calls to be placed from COM; however, using <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual> is strongly discouraged because of the versioning limitations described in <xref:System.Runtime.InteropServices.ClassInterfaceAttribute>.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="45339-114">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="45339-114">Effect on the Runtime</span></span>  
 <span data-ttu-id="45339-115">To zdarzenie MDA nie ma wpływu na środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="45339-115">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="45339-116">Raportuje tylko dane dotyczące wczesnych wywołań w interfejsach z późnym wiązaniem.</span><span class="sxs-lookup"><span data-stu-id="45339-116">It only reports data about early-bound calls on late-bound interfaces.</span></span>  
  
## <a name="output"></a><span data-ttu-id="45339-117">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="45339-117">Output</span></span>  
 <span data-ttu-id="45339-118">Nazwa metody lub nazwy pola, do którego uzyskuje się wczesne powiązanie.</span><span class="sxs-lookup"><span data-stu-id="45339-118">The name of the method or name of the field being accessed early-bound.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="45339-119">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="45339-119">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dirtyCastAndCallOnInterface />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="45339-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="45339-120">See also</span></span>

- <xref:System.Runtime.InteropServices.ClassInterfaceAttribute>
- [<span data-ttu-id="45339-121">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="45339-121">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
