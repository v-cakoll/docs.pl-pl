---
title: ICorDebugRemote — Interfejs
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a50a799c625c647aa275994bc92738b8a4267eec
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59135580"
---
# <a name="icordebugremote-interface"></a><span data-ttu-id="996d2-102">ICorDebugRemote — Interfejs</span><span class="sxs-lookup"><span data-stu-id="996d2-102">ICorDebugRemote Interface</span></span>
<span data-ttu-id="996d2-103">Zapewnia zdalnemu procesowi docelowemu możliwość uruchamiania lub dołączenia zarządzanych debugerów.</span><span class="sxs-lookup"><span data-stu-id="996d2-103">Provides the ability to launch or attach a managed debugger to a remote target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="996d2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="996d2-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="996d2-105">Metody</span><span class="sxs-lookup"><span data-stu-id="996d2-105">Methods</span></span>  
  
|<span data-ttu-id="996d2-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="996d2-106">Method</span></span>|<span data-ttu-id="996d2-107">Opis</span><span class="sxs-lookup"><span data-stu-id="996d2-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="996d2-108">ICorDebugRemote::CreateProcessEx, metoda</span><span class="sxs-lookup"><span data-stu-id="996d2-108">ICorDebugRemote::CreateProcessEx Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremote-createprocessex-method.md)|<span data-ttu-id="996d2-109">Tworzy proces na komputerze zdalnym, do debugowania zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="996d2-109">Creates a process on a remote machine for managed debugging.</span></span>|  
|[<span data-ttu-id="996d2-110">ICorDebugRemote::DebugActiveProcessEx, metoda</span><span class="sxs-lookup"><span data-stu-id="996d2-110">ICorDebugRemote::DebugActiveProcessEx Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremote-debugactiveprocessex-method.md)|<span data-ttu-id="996d2-111">Uruchamia proces na komputerze zdalnym w debugerze.</span><span class="sxs-lookup"><span data-stu-id="996d2-111">Launches a process on a remote machine under the debugger.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="996d2-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="996d2-112">Remarks</span></span>  
 <span data-ttu-id="996d2-113">Obecnie ta funkcja jest obsługiwana tylko w przypadku debugowania element docelowy aplikacji opartych na technologii Silverlight, który jest uruchomiony na maszynie zdalnej dla komputerów Macintosh.</span><span class="sxs-lookup"><span data-stu-id="996d2-113">Currently, this functionality is supported only for debugging a Silverlight-based application target that is running on a remote Macintosh machine.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="996d2-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="996d2-114">Requirements</span></span>  
 <span data-ttu-id="996d2-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="996d2-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="996d2-116">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="996d2-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="996d2-117">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="996d2-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="996d2-118">**Wersje programu .NET framework:** 4.5, 4, 3.5 Z DODATKIEM SP1</span><span class="sxs-lookup"><span data-stu-id="996d2-118">**.NET Framework Versions:** 4.5, 4, 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="996d2-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="996d2-119">See also</span></span>

- [<span data-ttu-id="996d2-120">ICorDebugRemoteTarget, interfejs</span><span class="sxs-lookup"><span data-stu-id="996d2-120">ICorDebugRemoteTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)
- [<span data-ttu-id="996d2-121">ICorDebug, interfejs</span><span class="sxs-lookup"><span data-stu-id="996d2-121">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)

- [<span data-ttu-id="996d2-122">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="996d2-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
