---
title: invalidVariant MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MDAs (managed debugging assistants), invalid variant
- VARIANT type errors
- InvalidVariant MDA
- invalid VARIANT types
- managed debugging assistants (MDAs), invalid variant
ms.assetid: d273e070-d1b1-4a53-a9c7-7af837b04a3d
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f97fb7f9bdb144f2b586c387f33211734f664eb0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="invalidvariant-mda"></a><span data-ttu-id="fbd50-102">invalidVariant MDA</span><span class="sxs-lookup"><span data-stu-id="fbd50-102">invalidVariant MDA</span></span>
<span data-ttu-id="fbd50-103">`invalidVariant` Zarządzany Asystent debugowania (MDA) jest aktywowany, gdy nieprawidłową `VARIANT` struktury napotkano podczas wywoływania z kodu natywnego lub niezarządzane do zarządzanego kodu.</span><span class="sxs-lookup"><span data-stu-id="fbd50-103">The `invalidVariant` managed debugging assistant (MDA) is activated when an invalid `VARIANT` structure is encountered during a call from native or unmanaged code to managed code.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="fbd50-104">Symptomy</span><span class="sxs-lookup"><span data-stu-id="fbd50-104">Symptoms</span></span>  
 <span data-ttu-id="fbd50-105">Nieoczekiwane zachowanie podczas przejścia między kodu natywnego i zarządzanego, obejmujące kierowanie `VARIANT` do obiektu.</span><span class="sxs-lookup"><span data-stu-id="fbd50-105">Unexpected behavior during a transition between native and managed code involving the marshaling of a `VARIANT` to an object.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="fbd50-106">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="fbd50-106">Cause</span></span>  
 <span data-ttu-id="fbd50-107">Kod natywny jest przekazanie źle sformułowane `VARIANT` struktury do kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="fbd50-107">Native code is passing a malformed `VARIANT` structure to managed code.</span></span>  <span data-ttu-id="fbd50-108">Środowisko wykonawcze próbuje kierować to `VARIANT` do obiektu i aktywuje MDA, jeśli `VARIANT` jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="fbd50-108">The runtime attempts to marshal this `VARIANT` to an object and activates the MDA if the `VARIANT` is not valid.</span></span> <span data-ttu-id="fbd50-109">Przykłady nieprawidłowy `VARIANT`obejmują S `VARIANT` z `VARTYPE` VT_EMPTY &#124; VT_BYREF lub `VARIANT` z `VARTYPE` VT_VARIANT.</span><span class="sxs-lookup"><span data-stu-id="fbd50-109">Examples of invalid `VARIANT`S include a `VARIANT` with `VARTYPE` VT_EMPTY &#124; VT_BYREF or a `VARIANT` with `VARTYPE` VT_VARIANT.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="fbd50-110">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="fbd50-110">Resolution</span></span>  
 <span data-ttu-id="fbd50-111">Kod natywny lub niezarządzane przekazywanie `VARIANT` upewnij się, że `VARIANT` jest poprawnie sformułowany i zainicjować.</span><span class="sxs-lookup"><span data-stu-id="fbd50-111">The native or unmanaged code passing the `VARIANT` must ensure that the `VARIANT` is correctly formed and initialized.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="fbd50-112">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="fbd50-112">Effect on the Runtime</span></span>  
 <span data-ttu-id="fbd50-113">MDA nie ma wpływu na zachowanie środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="fbd50-113">The MDA has no effect on the runtime's behavior.</span></span>  
  
## <a name="output"></a><span data-ttu-id="fbd50-114">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="fbd50-114">Output</span></span>  
 <span data-ttu-id="fbd50-115">Komunikat MDA wskazujący, że środowisko wykonawcze wykryto nieprawidłową `VARIANT` przekazany do kodu zarządzanego przez moduł niezarządzane.</span><span class="sxs-lookup"><span data-stu-id="fbd50-115">An MDA message indicating that the runtime detected an invalid `VARIANT` passed to managed code by an unmanaged module.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="fbd50-116">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="fbd50-116">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidVariant />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="fbd50-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fbd50-117">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="fbd50-118">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="fbd50-118">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="fbd50-119">Marshaling międzyoperacyjny</span><span class="sxs-lookup"><span data-stu-id="fbd50-119">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
