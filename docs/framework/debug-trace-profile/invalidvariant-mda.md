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
ms.openlocfilehash: ee537dcb03dc76968b829f827c73542c07922a3b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="invalidvariant-mda"></a><span data-ttu-id="6d236-102">invalidVariant MDA</span><span class="sxs-lookup"><span data-stu-id="6d236-102">invalidVariant MDA</span></span>
<span data-ttu-id="6d236-103">`invalidVariant` Zarządzany Asystent debugowania (MDA) jest aktywowany, gdy nieprawidłową `VARIANT` struktury napotkano podczas wywoływania z kodu natywnego lub niezarządzane do zarządzanego kodu.</span><span class="sxs-lookup"><span data-stu-id="6d236-103">The `invalidVariant` managed debugging assistant (MDA) is activated when an invalid `VARIANT` structure is encountered during a call from native or unmanaged code to managed code.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="6d236-104">Symptomy</span><span class="sxs-lookup"><span data-stu-id="6d236-104">Symptoms</span></span>  
 <span data-ttu-id="6d236-105">Nieoczekiwane zachowanie podczas przejścia między kodu natywnego i zarządzanego, obejmujące kierowanie `VARIANT` do obiektu.</span><span class="sxs-lookup"><span data-stu-id="6d236-105">Unexpected behavior during a transition between native and managed code involving the marshaling of a `VARIANT` to an object.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="6d236-106">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="6d236-106">Cause</span></span>  
 <span data-ttu-id="6d236-107">Kod natywny jest przekazanie źle sformułowane `VARIANT` struktury do kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="6d236-107">Native code is passing a malformed `VARIANT` structure to managed code.</span></span>  <span data-ttu-id="6d236-108">Środowisko wykonawcze próbuje kierować to `VARIANT` do obiektu i aktywuje MDA, jeśli `VARIANT` jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="6d236-108">The runtime attempts to marshal this `VARIANT` to an object and activates the MDA if the `VARIANT` is not valid.</span></span> <span data-ttu-id="6d236-109">Przykłady nieprawidłowy `VARIANT`obejmują S `VARIANT` z `VARTYPE` VT_EMPTY &#124; VT_BYREF lub `VARIANT` z `VARTYPE` VT_VARIANT.</span><span class="sxs-lookup"><span data-stu-id="6d236-109">Examples of invalid `VARIANT`S include a `VARIANT` with `VARTYPE` VT_EMPTY &#124; VT_BYREF or a `VARIANT` with `VARTYPE` VT_VARIANT.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="6d236-110">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="6d236-110">Resolution</span></span>  
 <span data-ttu-id="6d236-111">Kod natywny lub niezarządzane przekazywanie `VARIANT` upewnij się, że `VARIANT` jest poprawnie sformułowany i zainicjować.</span><span class="sxs-lookup"><span data-stu-id="6d236-111">The native or unmanaged code passing the `VARIANT` must ensure that the `VARIANT` is correctly formed and initialized.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="6d236-112">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="6d236-112">Effect on the Runtime</span></span>  
 <span data-ttu-id="6d236-113">MDA nie ma wpływu na zachowanie środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="6d236-113">The MDA has no effect on the runtime's behavior.</span></span>  
  
## <a name="output"></a><span data-ttu-id="6d236-114">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="6d236-114">Output</span></span>  
 <span data-ttu-id="6d236-115">Komunikat MDA wskazujący, że środowisko wykonawcze wykryto nieprawidłową `VARIANT` przekazany do kodu zarządzanego przez moduł niezarządzane.</span><span class="sxs-lookup"><span data-stu-id="6d236-115">An MDA message indicating that the runtime detected an invalid `VARIANT` passed to managed code by an unmanaged module.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="6d236-116">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="6d236-116">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidVariant />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6d236-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6d236-117">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="6d236-118">Diagnozowanie błędów przy użyciu Asystenci zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="6d236-118">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="6d236-119">Przekazywanie międzyoperacyjne</span><span class="sxs-lookup"><span data-stu-id="6d236-119">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
