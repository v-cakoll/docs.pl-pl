---
title: Włączanie debugowania dołączania JIT
ms.date: 03/30/2017
helpviewer_keywords:
- JIT-attach debugging
- debugging [.NET Framework], JIT-attach debugging
ms.assetid: f91fc5f7-de5a-4f23-b6ac-f450e63c662e
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b92592500f0babf29891710cedf1228b0ddcb0e4
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43563616"
---
# <a name="enabling-jit-attach-debugging"></a><span data-ttu-id="e3257-102">Włączanie debugowania dołączania JIT</span><span class="sxs-lookup"><span data-stu-id="e3257-102">Enabling JIT-Attach Debugging</span></span>
<span data-ttu-id="e3257-103">Debugowania dołączania JIT jest wyrażenie używane do opisywania dołączanie debugera do procesu, gdy wystąpią błędy lub mogą być wyzwalane przez określone metody lub funkcji.</span><span class="sxs-lookup"><span data-stu-id="e3257-103">JIT-attach debugging is the phrase used to describe attaching a debugger to a process when you encounter errors, or it can be triggered by specific methods or functions.</span></span>  
  
 <span data-ttu-id="e3257-104">Debugowania dołączania JIT jest używany w następujących warunkach błędów:</span><span class="sxs-lookup"><span data-stu-id="e3257-104">JIT-attach debugging is used under the following fault conditions:</span></span>  
  
-   <span data-ttu-id="e3257-105">Nieobsługiwane wyjątki (w kodzie natywnych i zarządzanych).</span><span class="sxs-lookup"><span data-stu-id="e3257-105">Unhandled exceptions (in both native and managed code).</span></span>  
  
-   <span data-ttu-id="e3257-106"><xref:System.Environment.FailFast%2A?displayProperty=nameWithType> Metoda lub [RaiseFailFastException](https://go.microsoft.com/fwlink/?LinkId=182107) — funkcja (Windows 7 rodzina).</span><span class="sxs-lookup"><span data-stu-id="e3257-106"><xref:System.Environment.FailFast%2A?displayProperty=nameWithType> method or [RaiseFailFastException](https://go.microsoft.com/fwlink/?LinkId=182107) function (Windows 7 family).</span></span>  
  
-   <span data-ttu-id="e3257-107">Błędy krytyczne środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="e3257-107">Runtime fatal errors.</span></span>  
  
 <span data-ttu-id="e3257-108">Debugowania dołączania JIT jest również wyzwalany przez wywołania do następujących metod i funkcji:</span><span class="sxs-lookup"><span data-stu-id="e3257-108">JIT-attach debugging is also triggered by calls to the following methods and functions:</span></span>  
  
-   <span data-ttu-id="e3257-109"><xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=nameWithType> Metoda.</span><span class="sxs-lookup"><span data-stu-id="e3257-109"><xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=nameWithType> method.</span></span>  
  
-   <span data-ttu-id="e3257-110"><xref:System.Diagnostics.Debugger.Break%2A?displayProperty=nameWithType> Metoda.</span><span class="sxs-lookup"><span data-stu-id="e3257-110"><xref:System.Diagnostics.Debugger.Break%2A?displayProperty=nameWithType> method.</span></span>  
  
-   <span data-ttu-id="e3257-111">[DebugBreak](https://go.microsoft.com/fwlink/?LinkId=182106) — funkcja (Win32).</span><span class="sxs-lookup"><span data-stu-id="e3257-111">[DebugBreak](https://go.microsoft.com/fwlink/?LinkId=182106) function (Win32).</span></span>  
  
 <span data-ttu-id="e3257-112">Przed [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], .NET Framework podane klucze rejestru oddzielne, aby kontrolować zachowanie natywnych i zarządzanych debugerów.</span><span class="sxs-lookup"><span data-stu-id="e3257-112">Before the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], the .NET Framework provided separate registry keys to control the behavior of native and managed debuggers.</span></span> <span data-ttu-id="e3257-113">Począwszy od [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], kontrolki są konsolidowane w kluczu rejestru pojedynczego: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\Current Version\AeDebug.</span><span class="sxs-lookup"><span data-stu-id="e3257-113">Starting with the [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], control is consolidated under a single registry key: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\Current Version\AeDebug.</span></span> <span data-ttu-id="e3257-114">Wartości, które można ustawić dla tego klucza określają, czy debuger jest wywoływany, a jeśli tak, czy jest wywoływana z okna dialogowego wymaga interakcji użytkownika.</span><span class="sxs-lookup"><span data-stu-id="e3257-114">The values you can set for that key determine whether a debugger is invoked, and, if so, whether it is invoked with a dialog box that requires user interaction.</span></span> <span data-ttu-id="e3257-115">Aby uzyskać informacji o ustawieniu tego klucza rejestru, zobacz [Konfigurowanie automatycznego debugowania](https://go.microsoft.com/fwlink/?LinkId=181767).</span><span class="sxs-lookup"><span data-stu-id="e3257-115">For information about setting this registry key, see [Configuring Automatic Debugging](https://go.microsoft.com/fwlink/?LinkId=181767).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3257-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e3257-116">See Also</span></span>  
 [<span data-ttu-id="e3257-117">Debugowanie, śledzenie i profilowanie</span><span class="sxs-lookup"><span data-stu-id="e3257-117">Debugging, Tracing, and Profiling</span></span>](../../../docs/framework/debug-trace-profile/index.md)  
 [<span data-ttu-id="e3257-118">Ułatwianie debugowania obrazu</span><span class="sxs-lookup"><span data-stu-id="e3257-118">Making an Image Easier to Debug</span></span>](../../../docs/framework/debug-trace-profile/making-an-image-easier-to-debug.md)  
 [<span data-ttu-id="e3257-119">Włączanie profilowania</span><span class="sxs-lookup"><span data-stu-id="e3257-119">Enabling Profiling</span></span>](https://msdn.microsoft.com/library/3b669676-f0e0-4ebf-8674-68986dd2020d)
