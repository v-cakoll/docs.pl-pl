---
title: invalidVariant MDA
description: Zapoznaj się z asystentem zarządzanego debugowania invalidVariant, który jest wywoływany, jeśli wystąpił nieprawidłowy wariant w wywołaniu z natywnego/niezarządzanego kodu zarządzanego.
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), invalid variant
- VARIANT type errors
- InvalidVariant MDA
- invalid VARIANT types
- managed debugging assistants (MDAs), invalid variant
ms.assetid: d273e070-d1b1-4a53-a9c7-7af837b04a3d
ms.openlocfilehash: ab1233d9faa86ef1508fa8fe2b5af46cb37bd523
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: pl-PL
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051639"
---
# <a name="invalidvariant-mda"></a><span data-ttu-id="7bdc8-103">invalidVariant MDA</span><span class="sxs-lookup"><span data-stu-id="7bdc8-103">invalidVariant MDA</span></span>
<span data-ttu-id="7bdc8-104">`invalidVariant`Asystent debugowania zarządzanego (MDA) jest uaktywniany po napotkaniu nieprawidłowej `VARIANT` struktury podczas wywołania z kodu natywnego lub niezarządzanego do kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="7bdc8-104">The `invalidVariant` managed debugging assistant (MDA) is activated when an invalid `VARIANT` structure is encountered during a call from native or unmanaged code to managed code.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="7bdc8-105">Objawy</span><span class="sxs-lookup"><span data-stu-id="7bdc8-105">Symptoms</span></span>  
 <span data-ttu-id="7bdc8-106">Nieoczekiwane zachowanie podczas przejścia między kodem natywnym i zarządzanym obejmującym kierowanie `VARIANT` do obiektu.</span><span class="sxs-lookup"><span data-stu-id="7bdc8-106">Unexpected behavior during a transition between native and managed code involving the marshaling of a `VARIANT` to an object.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="7bdc8-107">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="7bdc8-107">Cause</span></span>  
 <span data-ttu-id="7bdc8-108">Kod natywny przekazuje nieprawidłowo sformułowaną `VARIANT` strukturę do kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="7bdc8-108">Native code is passing a malformed `VARIANT` structure to managed code.</span></span>  <span data-ttu-id="7bdc8-109">Środowisko uruchomieniowe próbuje zorganizować ten `VARIANT` obiekt w celu aktywowania go, jeśli element `VARIANT` jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="7bdc8-109">The runtime attempts to marshal this `VARIANT` to an object and activates the MDA if the `VARIANT` is not valid.</span></span> <span data-ttu-id="7bdc8-110">Przykłady nieprawidłowych wartości `VARIANT` S `VARIANT` obejmują `VARTYPE` VT_EMPTY &#124; VT_BYREF lub `VARIANT` `VARTYPE` VT_VARIANT.</span><span class="sxs-lookup"><span data-stu-id="7bdc8-110">Examples of invalid `VARIANT`S include a `VARIANT` with `VARTYPE` VT_EMPTY &#124; VT_BYREF or a `VARIANT` with `VARTYPE` VT_VARIANT.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="7bdc8-111">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="7bdc8-111">Resolution</span></span>  
 <span data-ttu-id="7bdc8-112">Kod natywny lub niezarządzany przekazujący `VARIANT` musi mieć pewność, że `VARIANT` jest poprawnie sformułowany i zainicjowany.</span><span class="sxs-lookup"><span data-stu-id="7bdc8-112">The native or unmanaged code passing the `VARIANT` must ensure that the `VARIANT` is correctly formed and initialized.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="7bdc8-113">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="7bdc8-113">Effect on the Runtime</span></span>  
 <span data-ttu-id="7bdc8-114">Zdarzenie MDA nie ma wpływu na zachowanie środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="7bdc8-114">The MDA has no effect on the runtime's behavior.</span></span>  
  
## <a name="output"></a><span data-ttu-id="7bdc8-115">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="7bdc8-115">Output</span></span>  
 <span data-ttu-id="7bdc8-116">Komunikat MDA wskazujący, że środowisko uruchomieniowe wykryło nieprawidłowe `VARIANT` przekazanie do zarządzanego kodu przez moduł niezarządzany.</span><span class="sxs-lookup"><span data-stu-id="7bdc8-116">An MDA message indicating that the runtime detected an invalid `VARIANT` passed to managed code by an unmanaged module.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="7bdc8-117">Konfigurowanie</span><span class="sxs-lookup"><span data-stu-id="7bdc8-117">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidVariant />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7bdc8-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7bdc8-118">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="7bdc8-119">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="7bdc8-119">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="7bdc8-120">Organizowanie międzyoperacyjne</span><span class="sxs-lookup"><span data-stu-id="7bdc8-120">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
