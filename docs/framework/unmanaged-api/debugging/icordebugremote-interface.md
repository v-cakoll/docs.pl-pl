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
ms.openlocfilehash: ef11aa48f679592126f736c2877c697f02cb5e62
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379247"
---
# <a name="icordebugremote-interface"></a><span data-ttu-id="66267-102">ICorDebugRemote — Interfejs</span><span class="sxs-lookup"><span data-stu-id="66267-102">ICorDebugRemote Interface</span></span>
<span data-ttu-id="66267-103">Zapewnia zdalnemu procesowi docelowemu możliwość uruchamiania lub dołączenia zarządzanych debugerów.</span><span class="sxs-lookup"><span data-stu-id="66267-103">Provides the ability to launch or attach a managed debugger to a remote target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66267-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="66267-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="66267-105">Metody</span><span class="sxs-lookup"><span data-stu-id="66267-105">Methods</span></span>  
  
|<span data-ttu-id="66267-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="66267-106">Method</span></span>|<span data-ttu-id="66267-107">Opis</span><span class="sxs-lookup"><span data-stu-id="66267-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="66267-108">ICorDebugRemote::CreateProcessEx — Metoda</span><span class="sxs-lookup"><span data-stu-id="66267-108">ICorDebugRemote::CreateProcessEx Method</span></span>](icordebugremote-createprocessex-method.md)|<span data-ttu-id="66267-109">Tworzy proces na maszynie zdalnej na potrzeby debugowania zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="66267-109">Creates a process on a remote machine for managed debugging.</span></span>|  
|[<span data-ttu-id="66267-110">ICorDebugRemote::DebugActiveProcessEx — Metoda</span><span class="sxs-lookup"><span data-stu-id="66267-110">ICorDebugRemote::DebugActiveProcessEx Method</span></span>](icordebugremote-debugactiveprocessex-method.md)|<span data-ttu-id="66267-111">Uruchamia proces na maszynie zdalnej pod debugerem.</span><span class="sxs-lookup"><span data-stu-id="66267-111">Launches a process on a remote machine under the debugger.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="66267-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="66267-112">Remarks</span></span>  
 <span data-ttu-id="66267-113">Obecnie ta funkcja jest obsługiwana tylko w przypadku debugowania obiektu docelowego aplikacji opartego na technologii Silverlight, który jest uruchomiony na komputerze zdalnym Macintosh.</span><span class="sxs-lookup"><span data-stu-id="66267-113">Currently, this functionality is supported only for debugging a Silverlight-based application target that is running on a remote Macintosh machine.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="66267-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="66267-114">Requirements</span></span>  
 <span data-ttu-id="66267-115">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="66267-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="66267-116">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="66267-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="66267-117">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="66267-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="66267-118">**.NET Framework wersje:** 4,5, 4, 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="66267-118">**.NET Framework Versions:** 4.5, 4, 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66267-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="66267-119">See also</span></span>

- [<span data-ttu-id="66267-120">ICorDebugRemoteTarget — Interfejs</span><span class="sxs-lookup"><span data-stu-id="66267-120">ICorDebugRemoteTarget Interface</span></span>](icordebugremotetarget-interface.md)
- [<span data-ttu-id="66267-121">ICorDebug — Interfejs</span><span class="sxs-lookup"><span data-stu-id="66267-121">ICorDebug Interface</span></span>](icordebug-interface.md)

- [<span data-ttu-id="66267-122">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="66267-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
