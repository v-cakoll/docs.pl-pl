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
ms.openlocfilehash: 0cc79c0a93fa4f05b8c793a8b7fb0b9b3f031b1a
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791956"
---
# <a name="icordebugremote-interface"></a><span data-ttu-id="b4c80-102">ICorDebugRemote — Interfejs</span><span class="sxs-lookup"><span data-stu-id="b4c80-102">ICorDebugRemote Interface</span></span>
<span data-ttu-id="b4c80-103">Zapewnia zdalnemu procesowi docelowemu możliwość uruchamiania lub dołączenia zarządzanych debugerów.</span><span class="sxs-lookup"><span data-stu-id="b4c80-103">Provides the ability to launch or attach a managed debugger to a remote target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4c80-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b4c80-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="methods"></a><span data-ttu-id="b4c80-105">Metody</span><span class="sxs-lookup"><span data-stu-id="b4c80-105">Methods</span></span>  
  
|<span data-ttu-id="b4c80-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="b4c80-106">Method</span></span>|<span data-ttu-id="b4c80-107">Opis</span><span class="sxs-lookup"><span data-stu-id="b4c80-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b4c80-108">ICorDebugRemote::CreateProcessEx, metoda</span><span class="sxs-lookup"><span data-stu-id="b4c80-108">ICorDebugRemote::CreateProcessEx Method</span></span>](icordebugremote-createprocessex-method.md)|<span data-ttu-id="b4c80-109">Tworzy proces na maszynie zdalnej na potrzeby debugowania zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="b4c80-109">Creates a process on a remote machine for managed debugging.</span></span>|  
|[<span data-ttu-id="b4c80-110">ICorDebugRemote::DebugActiveProcessEx, metoda</span><span class="sxs-lookup"><span data-stu-id="b4c80-110">ICorDebugRemote::DebugActiveProcessEx Method</span></span>](icordebugremote-debugactiveprocessex-method.md)|<span data-ttu-id="b4c80-111">Uruchamia proces na maszynie zdalnej pod debugerem.</span><span class="sxs-lookup"><span data-stu-id="b4c80-111">Launches a process on a remote machine under the debugger.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b4c80-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b4c80-112">Remarks</span></span>  
 <span data-ttu-id="b4c80-113">Obecnie ta funkcja jest obsługiwana tylko w przypadku debugowania obiektu docelowego aplikacji opartego na technologii Silverlight, który jest uruchomiony na komputerze zdalnym Macintosh.</span><span class="sxs-lookup"><span data-stu-id="b4c80-113">Currently, this functionality is supported only for debugging a Silverlight-based application target that is running on a remote Macintosh machine.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b4c80-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b4c80-114">Requirements</span></span>  
 <span data-ttu-id="b4c80-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b4c80-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b4c80-116">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b4c80-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b4c80-117">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="b4c80-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b4c80-118">**.NET Framework wersje:** 4,5, 4, 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="b4c80-118">**.NET Framework Versions:** 4.5, 4, 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4c80-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b4c80-119">See also</span></span>

- [<span data-ttu-id="b4c80-120">ICorDebugRemoteTarget, interfejs</span><span class="sxs-lookup"><span data-stu-id="b4c80-120">ICorDebugRemoteTarget Interface</span></span>](icordebugremotetarget-interface.md)
- [<span data-ttu-id="b4c80-121">ICorDebug, interfejs</span><span class="sxs-lookup"><span data-stu-id="b4c80-121">ICorDebug Interface</span></span>](icordebug-interface.md)

- [<span data-ttu-id="b4c80-122">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="b4c80-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
