---
title: "Włączanie debugowania dołączania JIT"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- JIT-attach debugging
- debugging [.NET Framework], JIT-attach debugging
ms.assetid: f91fc5f7-de5a-4f23-b6ac-f450e63c662e
caps.latest.revision: "17"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 71b2e95076edbda3a67a84c9185d8b689c158e12
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="enabling-jit-attach-debugging"></a><span data-ttu-id="495b0-102">Włączanie debugowania dołączania JIT</span><span class="sxs-lookup"><span data-stu-id="495b0-102">Enabling JIT-Attach Debugging</span></span>
<span data-ttu-id="495b0-103">Debugowanie dołączania JIT jest hasło używane do opisywania dołączanie debugera do procesu, gdy wystąpią błędy, lub mogą być wyzwalane przez określone metody lub funkcji.</span><span class="sxs-lookup"><span data-stu-id="495b0-103">JIT-attach debugging is the phrase used to describe attaching a debugger to a process when you encounter errors, or it can be triggered by specific methods or functions.</span></span>  
  
 <span data-ttu-id="495b0-104">Debugowanie dołączania JIT jest używany w następujących warunkach błędów:</span><span class="sxs-lookup"><span data-stu-id="495b0-104">JIT-attach debugging is used under the following fault conditions:</span></span>  
  
-   <span data-ttu-id="495b0-105">Nieobsługiwane wyjątki (w kodzie natywnych i zarządzanych).</span><span class="sxs-lookup"><span data-stu-id="495b0-105">Unhandled exceptions (in both native and managed code).</span></span>  
  
-   <span data-ttu-id="495b0-106"><xref:System.Environment.FailFast%2A?displayProperty=nameWithType>Metoda lub [RaiseFailFastException](http://go.microsoft.com/fwlink/?LinkId=182107) — funkcja (rodziny Windows 7).</span><span class="sxs-lookup"><span data-stu-id="495b0-106"><xref:System.Environment.FailFast%2A?displayProperty=nameWithType> method or [RaiseFailFastException](http://go.microsoft.com/fwlink/?LinkId=182107) function (Windows 7 family).</span></span>  
  
-   <span data-ttu-id="495b0-107">Błędy krytyczne podczas wykonywania.</span><span class="sxs-lookup"><span data-stu-id="495b0-107">Runtime fatal errors.</span></span>  
  
 <span data-ttu-id="495b0-108">Debugowanie dołączania JIT również jest wyzwalany przez wywołania z funkcji i następujących metod:</span><span class="sxs-lookup"><span data-stu-id="495b0-108">JIT-attach debugging is also triggered by calls to the following methods and functions:</span></span>  
  
-   <span data-ttu-id="495b0-109"><xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=nameWithType>Metoda.</span><span class="sxs-lookup"><span data-stu-id="495b0-109"><xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=nameWithType> method.</span></span>  
  
-   <span data-ttu-id="495b0-110"><xref:System.Diagnostics.Debugger.Break%2A?displayProperty=nameWithType>Metoda.</span><span class="sxs-lookup"><span data-stu-id="495b0-110"><xref:System.Diagnostics.Debugger.Break%2A?displayProperty=nameWithType> method.</span></span>  
  
-   <span data-ttu-id="495b0-111">[Debugbreak —](http://go.microsoft.com/fwlink/?LinkId=182106) — funkcja (Win32).</span><span class="sxs-lookup"><span data-stu-id="495b0-111">[DebugBreak](http://go.microsoft.com/fwlink/?LinkId=182106) function (Win32).</span></span>  
  
 <span data-ttu-id="495b0-112">Przed [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], .NET Framework podane klucze rejestru oddzielne do sterowania zachowaniem debugery natywnych i zarządzanych.</span><span class="sxs-lookup"><span data-stu-id="495b0-112">Before the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], the .NET Framework provided separate registry keys to control the behavior of native and managed debuggers.</span></span> <span data-ttu-id="495b0-113">Począwszy od [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], sterowania są konsolidowane w kluczu rejestru pojedynczego: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\Current Version\AeDebug.</span><span class="sxs-lookup"><span data-stu-id="495b0-113">Starting with the [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], control is consolidated under a single registry key: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\Current Version\AeDebug.</span></span> <span data-ttu-id="495b0-114">Wartości, które można ustawić dla tego klucza określają, czy debuger jest wywoływany, a jeśli tak, czy jest wywoływana z okna dialogowego wymaga interakcji użytkownika.</span><span class="sxs-lookup"><span data-stu-id="495b0-114">The values you can set for that key determine whether a debugger is invoked, and, if so, whether it is invoked with a dialog box that requires user interaction.</span></span> <span data-ttu-id="495b0-115">Aby uzyskać informacje o ustawieniu tego klucza rejestru, zobacz [Konfigurowanie automatycznego debugowania](http://go.microsoft.com/fwlink/?LinkId=181767).</span><span class="sxs-lookup"><span data-stu-id="495b0-115">For information about setting this registry key, see [Configuring Automatic Debugging](http://go.microsoft.com/fwlink/?LinkId=181767).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="495b0-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="495b0-116">See Also</span></span>  
 [<span data-ttu-id="495b0-117">Debugowanie, śledzenie i profilowanie</span><span class="sxs-lookup"><span data-stu-id="495b0-117">Debugging, Tracing, and Profiling</span></span>](../../../docs/framework/debug-trace-profile/index.md)  
 [<span data-ttu-id="495b0-118">Ułatwianie debugowania obrazu</span><span class="sxs-lookup"><span data-stu-id="495b0-118">Making an Image Easier to Debug</span></span>](../../../docs/framework/debug-trace-profile/making-an-image-easier-to-debug.md)  
 [<span data-ttu-id="495b0-119">Włączenie profilowania</span><span class="sxs-lookup"><span data-stu-id="495b0-119">Enabling Profiling</span></span>](http://msdn.microsoft.com/library/3b669676-f0e0-4ebf-8674-68986dd2020d)
