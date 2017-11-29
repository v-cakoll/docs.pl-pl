---
title: "ICoreClrDebugTarget — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICoreClrDebugTarget
api_location: mscordbi_macx86.dll
api_type: COM
f1_keywords: ICoreClrDebugTarget
helpviewer_keywords:
- remote debugging API [Silverlight]
- ICorClrDebugTarget interface
- Silverlight, remote debugging
ms.assetid: 7cfaee76-e284-4a66-a431-8e33f0f60038
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e13355078727a55c950bed795d3b01b6c7d52564
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icoreclrdebugtarget-interface"></a><span data-ttu-id="7e206-102">ICoreClrDebugTarget — Interfejs</span><span class="sxs-lookup"><span data-stu-id="7e206-102">ICoreClrDebugTarget Interface</span></span>
<span data-ttu-id="7e206-103">Udostępnia metody, które sterować liczby odwołań, wyliczenie procesów i zwolnić pamięć, skojarzone z debugera, który jest dołączony do docelowego elementu zdalnego Macintosh Silverlight.</span><span class="sxs-lookup"><span data-stu-id="7e206-103">Provides methods that control reference counts, enumerate processes, and free the memory associated with a debugger that is attached to a remote Macintosh Silverlight target.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e206-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7e206-104">Syntax</span></span>  
  
```  
class ICoreClrDebugTarget {  
      HRESULT EnumProcesses (  
          [out] DWORD*                    pcProcs,  
          [out] CoreClrDebugProcInfo**    ppProcs  
      );  
  
      HRESULT EnumRuntimes (  
      [in]  DWORD                      dwInternalProcessID,  
      [out] DWORD*                     pcRuntimes,  
      [out] CoreClrDebugRuntimeInfo**  ppRuntimes  
      );  
  
      void FreeMemory (  
      [in] void*      pMemory  
    );  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="7e206-105">Metody</span><span class="sxs-lookup"><span data-stu-id="7e206-105">Methods</span></span>  
  
|<span data-ttu-id="7e206-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="7e206-106">Method</span></span>|<span data-ttu-id="7e206-107">Opis</span><span class="sxs-lookup"><span data-stu-id="7e206-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7e206-108">ICoreClrDebugTarget::EnumProcesses — metoda</span><span class="sxs-lookup"><span data-stu-id="7e206-108">ICoreClrDebugTarget::EnumProcesses Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-enumprocesses-method.md)|<span data-ttu-id="7e206-109">Wylicza procesów, które są uruchomione na komputerze zdalnym.</span><span class="sxs-lookup"><span data-stu-id="7e206-109">Enumerates the processes that are running on a remote computer.</span></span>|  
|[<span data-ttu-id="7e206-110">ICoreClrDebugTarget::EnumRuntimes — metoda</span><span class="sxs-lookup"><span data-stu-id="7e206-110">ICoreClrDebugTarget::EnumRuntimes Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-enumruntimes-method.md)|<span data-ttu-id="7e206-111">Wylicza wspólnej obsługi language (CLRs) określonego procesu na komputerze zdalnym.</span><span class="sxs-lookup"><span data-stu-id="7e206-111">Enumerates the common language runtimes (CLRs) in the specified process on a remote computer.</span></span>|  
|[<span data-ttu-id="7e206-112">ICoreClrDebugTarget::FreeMemory — metoda</span><span class="sxs-lookup"><span data-stu-id="7e206-112">ICoreClrDebugTarget::FreeMemory Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-freememory-method.md)|<span data-ttu-id="7e206-113">Zwalnia pamięci przydzielonej przez wyliczenie metody tej klasy.</span><span class="sxs-lookup"><span data-stu-id="7e206-113">Frees the memory that is allocated by the enumeration methods in this class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7e206-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7e206-114">Remarks</span></span>  
 <span data-ttu-id="7e206-115">Obecnie ta funkcja jest obsługiwana tylko w przypadku debugowania docelowego aplikacja Silverlight, który jest uruchomiony na komputerze zdalnym Macintosh.</span><span class="sxs-lookup"><span data-stu-id="7e206-115">Currently, this functionality is supported only for debugging a Silverlight-based application target that is running on a remote Macintosh computer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7e206-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7e206-116">Requirements</span></span>  
 <span data-ttu-id="7e206-117">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7e206-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7e206-118">**Nagłówek:** CoreClrRemoteDebuggingInterfaces.h</span><span class="sxs-lookup"><span data-stu-id="7e206-118">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="7e206-119">**Biblioteka:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="7e206-119">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="7e206-120">**Wersje programu .NET framework:** 3.5 z dodatkiem SP1</span><span class="sxs-lookup"><span data-stu-id="7e206-120">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e206-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7e206-121">See Also</span></span>  
 [<span data-ttu-id="7e206-122">ICorDebugRemoteTarget — interfejs</span><span class="sxs-lookup"><span data-stu-id="7e206-122">ICorDebugRemoteTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)  
 [<span data-ttu-id="7e206-123">ICorDebug — interfejs</span><span class="sxs-lookup"><span data-stu-id="7e206-123">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
    
 [<span data-ttu-id="7e206-124">Interfejsy debugowania</span><span class="sxs-lookup"><span data-stu-id="7e206-124">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
