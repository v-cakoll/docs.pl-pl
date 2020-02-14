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
ms.openlocfilehash: 8d686621ae4aa087e1b4f4bea9df7fc3de758d40
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216276"
---
# <a name="invalidvariant-mda"></a><span data-ttu-id="9c3e1-102">invalidVariant MDA</span><span class="sxs-lookup"><span data-stu-id="9c3e1-102">invalidVariant MDA</span></span>
<span data-ttu-id="9c3e1-103">Asystent debugowania zarządzanego `invalidVariant` (MDA) jest uaktywniany po napotkaniu nieprawidłowej struktury `VARIANT` podczas wywołania z kodu natywnego lub niezarządzanego do kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="9c3e1-103">The `invalidVariant` managed debugging assistant (MDA) is activated when an invalid `VARIANT` structure is encountered during a call from native or unmanaged code to managed code.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="9c3e1-104">Objawy</span><span class="sxs-lookup"><span data-stu-id="9c3e1-104">Symptoms</span></span>  
 <span data-ttu-id="9c3e1-105">Nieoczekiwane zachowanie podczas przejścia między kodem natywnym i zarządzanym obejmującym kierowanie `VARIANT` do obiektu.</span><span class="sxs-lookup"><span data-stu-id="9c3e1-105">Unexpected behavior during a transition between native and managed code involving the marshaling of a `VARIANT` to an object.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="9c3e1-106">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="9c3e1-106">Cause</span></span>  
 <span data-ttu-id="9c3e1-107">Kod natywny przekazuje nieprawidłowo sformułowaną strukturę `VARIANT` do kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="9c3e1-107">Native code is passing a malformed `VARIANT` structure to managed code.</span></span>  <span data-ttu-id="9c3e1-108">Środowisko uruchomieniowe próbuje zorganizować ten `VARIANT` do obiektu i aktywuje zdarzenie MDA, jeśli `VARIANT` jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="9c3e1-108">The runtime attempts to marshal this `VARIANT` to an object and activates the MDA if the `VARIANT` is not valid.</span></span> <span data-ttu-id="9c3e1-109">Przykłady nieprawidłowych `VARIANT`S obejmują `VARIANT` z `VARTYPE` VT_EMPTY &#124; VT_BYREF lub `VARIANT` z `VARTYPE` VT_VARIANT.</span><span class="sxs-lookup"><span data-stu-id="9c3e1-109">Examples of invalid `VARIANT`S include a `VARIANT` with `VARTYPE` VT_EMPTY &#124; VT_BYREF or a `VARIANT` with `VARTYPE` VT_VARIANT.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="9c3e1-110">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="9c3e1-110">Resolution</span></span>  
 <span data-ttu-id="9c3e1-111">Kod natywny lub niezarządzany przekazanie `VARIANT` musi mieć pewność, że `VARIANT` jest poprawnie sformułowany i zainicjowany.</span><span class="sxs-lookup"><span data-stu-id="9c3e1-111">The native or unmanaged code passing the `VARIANT` must ensure that the `VARIANT` is correctly formed and initialized.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="9c3e1-112">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="9c3e1-112">Effect on the Runtime</span></span>  
 <span data-ttu-id="9c3e1-113">Zdarzenie MDA nie ma wpływu na zachowanie środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="9c3e1-113">The MDA has no effect on the runtime's behavior.</span></span>  
  
## <a name="output"></a><span data-ttu-id="9c3e1-114">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="9c3e1-114">Output</span></span>  
 <span data-ttu-id="9c3e1-115">Komunikat MDA wskazujący, że środowisko uruchomieniowe wykryło nieprawidłową `VARIANT` przekazaną do kodu zarządzanego przez moduł niezarządzany.</span><span class="sxs-lookup"><span data-stu-id="9c3e1-115">An MDA message indicating that the runtime detected an invalid `VARIANT` passed to managed code by an unmanaged module.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="9c3e1-116">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="9c3e1-116">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidVariant />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9c3e1-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9c3e1-117">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="9c3e1-118">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="9c3e1-118">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="9c3e1-119">Marshaling międzyoperacyjny</span><span class="sxs-lookup"><span data-stu-id="9c3e1-119">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
