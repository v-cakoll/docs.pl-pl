---
title: "ICorDebugRemote — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugRemote
api_location:
- CorDebug.dll
api_type:
- COM
f1_keywords:
- ICorDebugRemote
helpviewer_keywords:
- ICorDebugRemote interface [.NET Framework debugging]
ms.assetid: 53d073c6-fa02-40d2-82e1-b9452bb6abaa
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: cc34c3a1049a24a27fae4d13288efbd5a98a4dc9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugremote-interface"></a><span data-ttu-id="a85cd-102">ICorDebugRemote — Interfejs</span><span class="sxs-lookup"><span data-stu-id="a85cd-102">ICorDebugRemote Interface</span></span>
<span data-ttu-id="a85cd-103">Zapewnia zdalnemu procesowi docelowemu możliwość uruchamiania lub dołączenia zarządzanych debugerów.</span><span class="sxs-lookup"><span data-stu-id="a85cd-103">Provides the ability to launch or attach a managed debugger to a remote target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a85cd-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a85cd-104">Syntax</span></span>  
  
```  
interface ICorDebugRemote : IUnknown  
{  
    HRESULT CreateProcessEx  
      (  
      [in] ICorDebugRemoteTarget *     pRemoteTarget,  
      [in] LPCWSTR                     lpApplicationName,  
      [in] LPWSTR                      lpCommandLine,  
      [in] LPSECURITY_ATTRIBUTES       lpProcessAttributes,  
      [in] LPSECURITY_ATTRIBUTES       lpThreadAttributes,  
      [in] BOOL                        bInheritHandles,  
      [in] DWORD                       dwCreationFlags,  
      [in] PVOID                       lpEnvironment,  
      [in] LPCWSTR                     lpCurrentDirectory,  
      [in] LPSTARTUPINFOW              lpStartupInfo,  
      [in] LPPROCESS_INFORMATION       lpProcessInformation,  
      [in] CorDebugCreateProcessFlags  debuggingFlags,  
      [out] ICorDebugProcess **        ppProcess  
      );  
  
    HRESULT DebugActiveProcessEx  
      (  
      [in] ICorDebugRemoteTarget *   pRemoteTarget,  
      [in] DWORD                     dwProcessId,  
      [in] BOOL                      fWin32Attach,  
      [out] ICorDebugProcess **      ppProcess  
      );  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="a85cd-105">Metody</span><span class="sxs-lookup"><span data-stu-id="a85cd-105">Methods</span></span>  
  
|<span data-ttu-id="a85cd-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="a85cd-106">Method</span></span>|<span data-ttu-id="a85cd-107">Opis</span><span class="sxs-lookup"><span data-stu-id="a85cd-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a85cd-108">ICorDebugRemote::CreateProcessEx, metoda</span><span class="sxs-lookup"><span data-stu-id="a85cd-108">ICorDebugRemote::CreateProcessEx Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremote-createprocessex-method.md)|<span data-ttu-id="a85cd-109">Tworzy proces na komputerze zdalnym do debugowania zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="a85cd-109">Creates a process on a remote machine for managed debugging.</span></span>|  
|[<span data-ttu-id="a85cd-110">ICorDebugRemote::DebugActiveProcessEx, metoda</span><span class="sxs-lookup"><span data-stu-id="a85cd-110">ICorDebugRemote::DebugActiveProcessEx Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremote-debugactiveprocessex-method.md)|<span data-ttu-id="a85cd-111">Uruchamia proces na komputerze zdalnym w debugerze.</span><span class="sxs-lookup"><span data-stu-id="a85cd-111">Launches a process on a remote machine under the debugger.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a85cd-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a85cd-112">Remarks</span></span>  
 <span data-ttu-id="a85cd-113">Obecnie ta funkcja jest obsługiwana tylko w przypadku debugowania docelowego aplikacja Silverlight, który działa na maszynie zdalnej dla komputerów Macintosh.</span><span class="sxs-lookup"><span data-stu-id="a85cd-113">Currently, this functionality is supported only for debugging a Silverlight-based application target that is running on a remote Macintosh machine.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a85cd-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a85cd-114">Requirements</span></span>  
 <span data-ttu-id="a85cd-115">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a85cd-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a85cd-116">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a85cd-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a85cd-117">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a85cd-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a85cd-118">**Wersje programu .NET framework:** 4.5, 4, 3.5 z dodatkiem SP1</span><span class="sxs-lookup"><span data-stu-id="a85cd-118">**.NET Framework Versions:** 4.5, 4, 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a85cd-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a85cd-119">See Also</span></span>  
 [<span data-ttu-id="a85cd-120">ICorDebugRemoteTarget, interfejs</span><span class="sxs-lookup"><span data-stu-id="a85cd-120">ICorDebugRemoteTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)  
 [<span data-ttu-id="a85cd-121">ICorDebug, interfejs</span><span class="sxs-lookup"><span data-stu-id="a85cd-121">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
    
 [<span data-ttu-id="a85cd-122">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="a85cd-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
