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
ms.openlocfilehash: 64f5a4425d70974bae8c4f7bec28041e687fe95f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61754326"
---
# <a name="invalidvariant-mda"></a><span data-ttu-id="53b64-102">invalidVariant MDA</span><span class="sxs-lookup"><span data-stu-id="53b64-102">invalidVariant MDA</span></span>
<span data-ttu-id="53b64-103">`invalidVariant` Zarządzanego Asystenta debugowania (MDA) jest uaktywniany podczas nieprawidłową `VARIANT` struktury napotkano podczas wywoływania z kodu natywnego lub niezarządzanego kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="53b64-103">The `invalidVariant` managed debugging assistant (MDA) is activated when an invalid `VARIANT` structure is encountered during a call from native or unmanaged code to managed code.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="53b64-104">Symptomy</span><span class="sxs-lookup"><span data-stu-id="53b64-104">Symptoms</span></span>  
 <span data-ttu-id="53b64-105">Nieoczekiwane zachowanie podczas przejścia między kodu natywnego i zarządzanego obejmujące kierowania `VARIANT` do obiektu.</span><span class="sxs-lookup"><span data-stu-id="53b64-105">Unexpected behavior during a transition between native and managed code involving the marshaling of a `VARIANT` to an object.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="53b64-106">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="53b64-106">Cause</span></span>  
 <span data-ttu-id="53b64-107">Kod natywny jest przekazanie źle sformułowane `VARIANT` strukturę do kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="53b64-107">Native code is passing a malformed `VARIANT` structure to managed code.</span></span>  <span data-ttu-id="53b64-108">Środowisko uruchomieniowe próbuje kierować to `VARIANT` do obiektu i aktywuje MDA, jeśli `VARIANT` jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="53b64-108">The runtime attempts to marshal this `VARIANT` to an object and activates the MDA if the `VARIANT` is not valid.</span></span> <span data-ttu-id="53b64-109">Przykłady nieprawidłowy `VARIANT`obejmują S `VARIANT` z `VARTYPE` VT_EMPTY &#124; VT_BYREF lub `VARIANT` z `VARTYPE` VT_VARIANT.</span><span class="sxs-lookup"><span data-stu-id="53b64-109">Examples of invalid `VARIANT`S include a `VARIANT` with `VARTYPE` VT_EMPTY &#124; VT_BYREF or a `VARIANT` with `VARTYPE` VT_VARIANT.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="53b64-110">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="53b64-110">Resolution</span></span>  
 <span data-ttu-id="53b64-111">Natywny lub kodowi niezarządzanemu przekazywanie `VARIANT` musi zapewnić, że `VARIANT` jest poprawnie sformułowana i zainicjowany.</span><span class="sxs-lookup"><span data-stu-id="53b64-111">The native or unmanaged code passing the `VARIANT` must ensure that the `VARIANT` is correctly formed and initialized.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="53b64-112">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="53b64-112">Effect on the Runtime</span></span>  
 <span data-ttu-id="53b64-113">MDA nie ma wpływu na działanie w środowisku uruchomieniowym.</span><span class="sxs-lookup"><span data-stu-id="53b64-113">The MDA has no effect on the runtime's behavior.</span></span>  
  
## <a name="output"></a><span data-ttu-id="53b64-114">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="53b64-114">Output</span></span>  
 <span data-ttu-id="53b64-115">MDA komunikat wskazujący, że środowisko wykonawcze nie wykryto nieprawidłową `VARIANT` przekazany do kodu zarządzanego przez moduł niezarządzanych.</span><span class="sxs-lookup"><span data-stu-id="53b64-115">An MDA message indicating that the runtime detected an invalid `VARIANT` passed to managed code by an unmanaged module.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="53b64-116">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="53b64-116">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidVariant />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="53b64-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="53b64-117">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="53b64-118">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="53b64-118">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="53b64-119">Marshaling międzyoperacyjny</span><span class="sxs-lookup"><span data-stu-id="53b64-119">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
