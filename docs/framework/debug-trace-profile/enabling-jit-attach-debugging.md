---
title: Włączanie debugowania dołączania JIT
description: Włącz debugowanie w czasie just-in Time (JIT), aby dołączyć debuger do procesu w przypadku wystąpienia błędów. Może być wyzwalane przez niektóre metody lub funkcje.
ms.date: 03/30/2017
helpviewer_keywords:
- JIT-attach debugging
- debugging [.NET Framework], JIT-attach debugging
ms.assetid: f91fc5f7-de5a-4f23-b6ac-f450e63c662e
ms.openlocfilehash: d1190c51a9cc6b5322ec832e0d35bc01dc855b12
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2020
ms.locfileid: "85416047"
---
# <a name="enabling-jit-attach-debugging"></a><span data-ttu-id="c5fd3-104">Włączanie debugowania dołączania JIT</span><span class="sxs-lookup"><span data-stu-id="c5fd3-104">Enabling JIT-Attach Debugging</span></span>
<span data-ttu-id="c5fd3-105">Debugowanie z dołączaniem JIT jest frazą używaną do opisywania dołączania debugera do procesu w przypadku wystąpienia błędów lub może być wyzwalane przez określone metody lub funkcje.</span><span class="sxs-lookup"><span data-stu-id="c5fd3-105">JIT-attach debugging is the phrase used to describe attaching a debugger to a process when you encounter errors, or it can be triggered by specific methods or functions.</span></span>  
  
 <span data-ttu-id="c5fd3-106">Debugowanie dołączania JIT jest używane w następujących warunkach błędu:</span><span class="sxs-lookup"><span data-stu-id="c5fd3-106">JIT-attach debugging is used under the following fault conditions:</span></span>  
  
- <span data-ttu-id="c5fd3-107">Nieobsłużone wyjątki (zarówno w kodzie macierzystym, jak i zarządzanym).</span><span class="sxs-lookup"><span data-stu-id="c5fd3-107">Unhandled exceptions (in both native and managed code).</span></span>  
  
- <span data-ttu-id="c5fd3-108"><xref:System.Environment.FailFast%2A?displayProperty=nameWithType>Metoda lub funkcja [RaiseFailFastException](/windows/win32/api/errhandlingapi/nf-errhandlingapi-raisefailfastexception) (rodzina systemu Windows 7).</span><span class="sxs-lookup"><span data-stu-id="c5fd3-108"><xref:System.Environment.FailFast%2A?displayProperty=nameWithType> method or [RaiseFailFastException](/windows/win32/api/errhandlingapi/nf-errhandlingapi-raisefailfastexception) function (Windows 7 family).</span></span>  
  
- <span data-ttu-id="c5fd3-109">Błędy krytyczne środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="c5fd3-109">Runtime fatal errors.</span></span>  
  
 <span data-ttu-id="c5fd3-110">Debugowanie dołączania JIT jest również wyzwalane przez wywołania następujących metod i funkcji:</span><span class="sxs-lookup"><span data-stu-id="c5fd3-110">JIT-attach debugging is also triggered by calls to the following methods and functions:</span></span>  
  
- <span data-ttu-id="c5fd3-111"><xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=nameWithType>Method.</span><span class="sxs-lookup"><span data-stu-id="c5fd3-111"><xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=nameWithType> method.</span></span>  
  
- <span data-ttu-id="c5fd3-112"><xref:System.Diagnostics.Debugger.Break%2A?displayProperty=nameWithType>Method.</span><span class="sxs-lookup"><span data-stu-id="c5fd3-112"><xref:System.Diagnostics.Debugger.Break%2A?displayProperty=nameWithType> method.</span></span>  
  
- <span data-ttu-id="c5fd3-113">Funkcja [DebugBreak](/windows/win32/api/debugapi/nf-debugapi-debugbreak) (Win32).</span><span class="sxs-lookup"><span data-stu-id="c5fd3-113">[DebugBreak](/windows/win32/api/debugapi/nf-debugapi-debugbreak) function (Win32).</span></span>  
  
 <span data-ttu-id="c5fd3-114">Przed .NET Framework 4 .NET Framework podano oddzielne klucze rejestru, aby kontrolować zachowanie debugera natywnego i zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="c5fd3-114">Before the .NET Framework 4, the .NET Framework provided separate registry keys to control the behavior of native and managed debuggers.</span></span> <span data-ttu-id="c5fd3-115">Począwszy od .NET Framework 4, formant jest konsolidowany pod pojedynczym kluczem rejestru: HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\Windows NT\Current Version\AeDebug.</span><span class="sxs-lookup"><span data-stu-id="c5fd3-115">Starting with the .NET Framework 4, control is consolidated under a single registry key: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\Current Version\AeDebug.</span></span> <span data-ttu-id="c5fd3-116">Wartości, które można ustawić dla tego klucza, określają, czy jest wywoływany debuger, i, jeśli tak, to czy jest wywoływany przy użyciu okna dialogowego, które wymaga interakcji z użytkownikiem.</span><span class="sxs-lookup"><span data-stu-id="c5fd3-116">The values you can set for that key determine whether a debugger is invoked, and, if so, whether it is invoked with a dialog box that requires user interaction.</span></span> <span data-ttu-id="c5fd3-117">Informacje o ustawianiu tego klucza rejestru można znaleźć w temacie [Configuring Automatic Debug](/windows/win32/debug/configuring-automatic-debugging).</span><span class="sxs-lookup"><span data-stu-id="c5fd3-117">For information about setting this registry key, see [Configuring Automatic Debugging](/windows/win32/debug/configuring-automatic-debugging).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5fd3-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c5fd3-118">See also</span></span>

- [<span data-ttu-id="c5fd3-119">Debugowanie, śledzenie i profilowanie</span><span class="sxs-lookup"><span data-stu-id="c5fd3-119">Debugging, Tracing, and Profiling</span></span>](index.md)
- [<span data-ttu-id="c5fd3-120">Ułatwianie debugowania obrazu</span><span class="sxs-lookup"><span data-stu-id="c5fd3-120">Making an Image Easier to Debug</span></span>](making-an-image-easier-to-debug.md)
