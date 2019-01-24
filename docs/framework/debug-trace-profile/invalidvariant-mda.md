---
title: invalidVariant MDA
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), invalid variant
- VARIANT type errors
- InvalidVariant MDA
- invalid VARIANT types
- managed debugging assistants (MDAs), invalid variant
ms.assetid: d273e070-d1b1-4a53-a9c7-7af837b04a3d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7d29d3f3638b3dae4381524fcaf55e1afeddc9f8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54730805"
---
# <a name="invalidvariant-mda"></a><span data-ttu-id="a6089-102">invalidVariant MDA</span><span class="sxs-lookup"><span data-stu-id="a6089-102">invalidVariant MDA</span></span>
<span data-ttu-id="a6089-103">`invalidVariant` Zarządzanego Asystenta debugowania (MDA) jest uaktywniany podczas nieprawidłową `VARIANT` struktury napotkano podczas wywoływania z kodu natywnego lub niezarządzanego kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="a6089-103">The `invalidVariant` managed debugging assistant (MDA) is activated when an invalid `VARIANT` structure is encountered during a call from native or unmanaged code to managed code.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="a6089-104">Symptomy</span><span class="sxs-lookup"><span data-stu-id="a6089-104">Symptoms</span></span>  
 <span data-ttu-id="a6089-105">Nieoczekiwane zachowanie podczas przejścia między kodu natywnego i zarządzanego obejmujące kierowania `VARIANT` do obiektu.</span><span class="sxs-lookup"><span data-stu-id="a6089-105">Unexpected behavior during a transition between native and managed code involving the marshaling of a `VARIANT` to an object.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="a6089-106">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="a6089-106">Cause</span></span>  
 <span data-ttu-id="a6089-107">Kod natywny jest przekazanie źle sformułowane `VARIANT` strukturę do kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="a6089-107">Native code is passing a malformed `VARIANT` structure to managed code.</span></span>  <span data-ttu-id="a6089-108">Środowisko uruchomieniowe próbuje kierować to `VARIANT` do obiektu i aktywuje MDA, jeśli `VARIANT` jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="a6089-108">The runtime attempts to marshal this `VARIANT` to an object and activates the MDA if the `VARIANT` is not valid.</span></span> <span data-ttu-id="a6089-109">Przykłady nieprawidłowy `VARIANT`obejmują S `VARIANT` z `VARTYPE` VT_EMPTY &#124; VT_BYREF lub `VARIANT` z `VARTYPE` VT_VARIANT.</span><span class="sxs-lookup"><span data-stu-id="a6089-109">Examples of invalid `VARIANT`S include a `VARIANT` with `VARTYPE` VT_EMPTY &#124; VT_BYREF or a `VARIANT` with `VARTYPE` VT_VARIANT.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="a6089-110">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="a6089-110">Resolution</span></span>  
 <span data-ttu-id="a6089-111">Natywny lub kodowi niezarządzanemu przekazywanie `VARIANT` musi zapewnić, że `VARIANT` jest poprawnie sformułowana i zainicjowany.</span><span class="sxs-lookup"><span data-stu-id="a6089-111">The native or unmanaged code passing the `VARIANT` must ensure that the `VARIANT` is correctly formed and initialized.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="a6089-112">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="a6089-112">Effect on the Runtime</span></span>  
 <span data-ttu-id="a6089-113">MDA nie ma wpływu na działanie w środowisku uruchomieniowym.</span><span class="sxs-lookup"><span data-stu-id="a6089-113">The MDA has no effect on the runtime's behavior.</span></span>  
  
## <a name="output"></a><span data-ttu-id="a6089-114">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="a6089-114">Output</span></span>  
 <span data-ttu-id="a6089-115">MDA komunikat wskazujący, że środowisko wykonawcze nie wykryto nieprawidłową `VARIANT` przekazany do kodu zarządzanego przez moduł niezarządzanych.</span><span class="sxs-lookup"><span data-stu-id="a6089-115">An MDA message indicating that the runtime detected an invalid `VARIANT` passed to managed code by an unmanaged module.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="a6089-116">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="a6089-116">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidVariant />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a6089-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a6089-117">See also</span></span>
- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="a6089-118">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="a6089-118">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="a6089-119">Marshaling międzyoperacyjny</span><span class="sxs-lookup"><span data-stu-id="a6089-119">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
