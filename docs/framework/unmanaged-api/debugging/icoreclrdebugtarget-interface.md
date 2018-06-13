---
title: ICoreClrDebugTarget — Interfejs
ms.date: 03/30/2017
api_name:
- ICoreClrDebugTarget
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- ICoreClrDebugTarget
helpviewer_keywords:
- remote debugging API [Silverlight]
- ICorClrDebugTarget interface
- Silverlight, remote debugging
ms.assetid: 7cfaee76-e284-4a66-a431-8e33f0f60038
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 371768a8306c3751e7fc54b91a8583df41ad219b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33422285"
---
# <a name="icoreclrdebugtarget-interface"></a><span data-ttu-id="26072-102">ICoreClrDebugTarget — Interfejs</span><span class="sxs-lookup"><span data-stu-id="26072-102">ICoreClrDebugTarget Interface</span></span>
<span data-ttu-id="26072-103">Udostępnia metody, które sterować liczby odwołań, wyliczenie procesów i zwolnić pamięć, skojarzone z debugera, który jest dołączony do docelowego elementu zdalnego Macintosh Silverlight.</span><span class="sxs-lookup"><span data-stu-id="26072-103">Provides methods that control reference counts, enumerate processes, and free the memory associated with a debugger that is attached to a remote Macintosh Silverlight target.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26072-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="26072-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="26072-105">Metody</span><span class="sxs-lookup"><span data-stu-id="26072-105">Methods</span></span>  
  
|<span data-ttu-id="26072-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="26072-106">Method</span></span>|<span data-ttu-id="26072-107">Opis</span><span class="sxs-lookup"><span data-stu-id="26072-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="26072-108">ICoreClrDebugTarget::EnumProcesses, metoda</span><span class="sxs-lookup"><span data-stu-id="26072-108">ICoreClrDebugTarget::EnumProcesses Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-enumprocesses-method.md)|<span data-ttu-id="26072-109">Wylicza procesów, które są uruchomione na komputerze zdalnym.</span><span class="sxs-lookup"><span data-stu-id="26072-109">Enumerates the processes that are running on a remote computer.</span></span>|  
|[<span data-ttu-id="26072-110">ICoreClrDebugTarget::EnumRuntimes, metoda</span><span class="sxs-lookup"><span data-stu-id="26072-110">ICoreClrDebugTarget::EnumRuntimes Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-enumruntimes-method.md)|<span data-ttu-id="26072-111">Wylicza wspólnej obsługi language (CLRs) określonego procesu na komputerze zdalnym.</span><span class="sxs-lookup"><span data-stu-id="26072-111">Enumerates the common language runtimes (CLRs) in the specified process on a remote computer.</span></span>|  
|[<span data-ttu-id="26072-112">ICoreClrDebugTarget::FreeMemory, metoda</span><span class="sxs-lookup"><span data-stu-id="26072-112">ICoreClrDebugTarget::FreeMemory Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-freememory-method.md)|<span data-ttu-id="26072-113">Zwalnia pamięci przydzielonej przez wyliczenie metody tej klasy.</span><span class="sxs-lookup"><span data-stu-id="26072-113">Frees the memory that is allocated by the enumeration methods in this class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="26072-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="26072-114">Remarks</span></span>  
 <span data-ttu-id="26072-115">Obecnie ta funkcja jest obsługiwana tylko w przypadku debugowania docelowego aplikacja Silverlight, który jest uruchomiony na komputerze zdalnym Macintosh.</span><span class="sxs-lookup"><span data-stu-id="26072-115">Currently, this functionality is supported only for debugging a Silverlight-based application target that is running on a remote Macintosh computer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="26072-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="26072-116">Requirements</span></span>  
 <span data-ttu-id="26072-117">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="26072-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="26072-118">**Nagłówek:** CoreClrRemoteDebuggingInterfaces.h</span><span class="sxs-lookup"><span data-stu-id="26072-118">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="26072-119">**Biblioteka:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="26072-119">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="26072-120">**Wersje programu .NET framework:** 3.5 z dodatkiem SP1</span><span class="sxs-lookup"><span data-stu-id="26072-120">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26072-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="26072-121">See Also</span></span>  
 [<span data-ttu-id="26072-122">ICorDebugRemoteTarget, interfejs</span><span class="sxs-lookup"><span data-stu-id="26072-122">ICorDebugRemoteTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)  
 [<span data-ttu-id="26072-123">ICorDebug, interfejs</span><span class="sxs-lookup"><span data-stu-id="26072-123">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
    
 [<span data-ttu-id="26072-124">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="26072-124">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
