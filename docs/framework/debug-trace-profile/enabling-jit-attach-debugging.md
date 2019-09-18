---
title: Włączanie debugowania dołączania JIT
ms.date: 03/30/2017
helpviewer_keywords:
- JIT-attach debugging
- debugging [.NET Framework], JIT-attach debugging
ms.assetid: f91fc5f7-de5a-4f23-b6ac-f450e63c662e
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f4d4e2b3806d2c4d84b59e1cd44eb03ab7b278c9
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052824"
---
# <a name="enabling-jit-attach-debugging"></a><span data-ttu-id="ebee0-102">Włączanie debugowania dołączania JIT</span><span class="sxs-lookup"><span data-stu-id="ebee0-102">Enabling JIT-Attach Debugging</span></span>
<span data-ttu-id="ebee0-103">Debugowanie z dołączaniem JIT jest frazą używaną do opisywania dołączania debugera do procesu w przypadku wystąpienia błędów lub może być wyzwalane przez określone metody lub funkcje.</span><span class="sxs-lookup"><span data-stu-id="ebee0-103">JIT-attach debugging is the phrase used to describe attaching a debugger to a process when you encounter errors, or it can be triggered by specific methods or functions.</span></span>  
  
 <span data-ttu-id="ebee0-104">Debugowanie dołączania JIT jest używane w następujących warunkach błędu:</span><span class="sxs-lookup"><span data-stu-id="ebee0-104">JIT-attach debugging is used under the following fault conditions:</span></span>  
  
- <span data-ttu-id="ebee0-105">Nieobsłużone wyjątki (zarówno w kodzie macierzystym, jak i zarządzanym).</span><span class="sxs-lookup"><span data-stu-id="ebee0-105">Unhandled exceptions (in both native and managed code).</span></span>  
  
- <span data-ttu-id="ebee0-106"><xref:System.Environment.FailFast%2A?displayProperty=nameWithType>Metoda lub funkcja [RaiseFailFastException](https://go.microsoft.com/fwlink/?LinkId=182107) (rodzina systemu Windows 7).</span><span class="sxs-lookup"><span data-stu-id="ebee0-106"><xref:System.Environment.FailFast%2A?displayProperty=nameWithType> method or [RaiseFailFastException](https://go.microsoft.com/fwlink/?LinkId=182107) function (Windows 7 family).</span></span>  
  
- <span data-ttu-id="ebee0-107">Błędy krytyczne środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="ebee0-107">Runtime fatal errors.</span></span>  
  
 <span data-ttu-id="ebee0-108">Debugowanie dołączania JIT jest również wyzwalane przez wywołania następujących metod i funkcji:</span><span class="sxs-lookup"><span data-stu-id="ebee0-108">JIT-attach debugging is also triggered by calls to the following methods and functions:</span></span>  
  
- <span data-ttu-id="ebee0-109"><xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=nameWithType>Method.</span><span class="sxs-lookup"><span data-stu-id="ebee0-109"><xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=nameWithType> method.</span></span>  
  
- <span data-ttu-id="ebee0-110"><xref:System.Diagnostics.Debugger.Break%2A?displayProperty=nameWithType>Method.</span><span class="sxs-lookup"><span data-stu-id="ebee0-110"><xref:System.Diagnostics.Debugger.Break%2A?displayProperty=nameWithType> method.</span></span>  
  
- <span data-ttu-id="ebee0-111">Funkcja [DebugBreak](https://go.microsoft.com/fwlink/?LinkId=182106) (Win32).</span><span class="sxs-lookup"><span data-stu-id="ebee0-111">[DebugBreak](https://go.microsoft.com/fwlink/?LinkId=182106) function (Win32).</span></span>  
  
 <span data-ttu-id="ebee0-112">Przed .NET Framework 4 .NET Framework podano oddzielne klucze rejestru, aby kontrolować zachowanie debugera natywnego i zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="ebee0-112">Before the .NET Framework 4, the .NET Framework provided separate registry keys to control the behavior of native and managed debuggers.</span></span> <span data-ttu-id="ebee0-113">Począwszy od .NET Framework 4, formant jest konsolidowany pod pojedynczym kluczem rejestru: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\Current Version\AeDebug.</span><span class="sxs-lookup"><span data-stu-id="ebee0-113">Starting with the .NET Framework 4, control is consolidated under a single registry key: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\Current Version\AeDebug.</span></span> <span data-ttu-id="ebee0-114">Wartości, które można ustawić dla tego klucza, określają, czy jest wywoływany debuger, i, jeśli tak, to czy jest wywoływany przy użyciu okna dialogowego, które wymaga interakcji z użytkownikiem.</span><span class="sxs-lookup"><span data-stu-id="ebee0-114">The values you can set for that key determine whether a debugger is invoked, and, if so, whether it is invoked with a dialog box that requires user interaction.</span></span> <span data-ttu-id="ebee0-115">Informacje o ustawianiu tego klucza rejestru można znaleźć w temacie [Configuring Automatic Debug](https://go.microsoft.com/fwlink/?LinkId=181767).</span><span class="sxs-lookup"><span data-stu-id="ebee0-115">For information about setting this registry key, see [Configuring Automatic Debugging](https://go.microsoft.com/fwlink/?LinkId=181767).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebee0-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ebee0-116">See also</span></span>

- [<span data-ttu-id="ebee0-117">Debugowanie, śledzenie i profilowanie</span><span class="sxs-lookup"><span data-stu-id="ebee0-117">Debugging, Tracing, and Profiling</span></span>](index.md)
- [<span data-ttu-id="ebee0-118">Ułatwianie debugowania obrazu</span><span class="sxs-lookup"><span data-stu-id="ebee0-118">Making an Image Easier to Debug</span></span>](making-an-image-easier-to-debug.md)
