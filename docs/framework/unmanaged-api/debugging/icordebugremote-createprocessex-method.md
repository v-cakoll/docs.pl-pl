---
title: ICorDebugRemote::CreateProcessEx — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugRemote.CreateProcessEx
api_location:
- CorDebug.dll
api_type:
- COM
f1_keywords:
- ICorDebugRemoteTarget::CreateProcessEx
helpviewer_keywords:
- CreateProcessEx method, ICorDebugRemote interface [.NET Framework debugging]
- ICorDebugRemote::CreateProcessEx method [.NET Framework debugging]
ms.assetid: 41af93c7-e448-4251-8d4d-413d38c635f2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a38812803127857281f9766fa3ed551971ec0330
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59093535"
---
# <a name="icordebugremotecreateprocessex-method"></a><span data-ttu-id="b9dbe-102">ICorDebugRemote::CreateProcessEx — Metoda</span><span class="sxs-lookup"><span data-stu-id="b9dbe-102">ICorDebugRemote::CreateProcessEx Method</span></span>
<span data-ttu-id="b9dbe-103">Uruchamia proces na komputerze zdalnym w debugerze.</span><span class="sxs-lookup"><span data-stu-id="b9dbe-103">Launches a process on a remote machine under the debugger.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9dbe-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b9dbe-104">Syntax</span></span>  
  
```  
HRESULT CreateProcessEx (  
    [in]  ICorDebugRemoteTarget*      pRemoteTarget,  
    [in]  LPCWSTR                     lpApplicationName,  
    [in]  LPWSTR                      lpCommandLine,  
    [in]  LPSECURITY_ATTRIBUTES       lpProcessAttributes,  
    [in]  LPSECURITY_ATTRIBUTES       lpThreadAttributes,  
    [in]  BOOL                        bInheritHandles,  
    [in]  DWORD                       dwCreationFlags,  
    [in]  PVOID                       lpEnvironment,  
    [in]  LPCWSTR                     lpCurrentDirectory,  
    [in]  LPSTARTUPINFOW              lpStartupInfo,  
    [in]  LPPROCESS_INFORMATION       lpProcessInformation,  
    [in]  CorDebugCreateProcessFlags  debuggingFlags,  
    [out] ICorDebugProcess**          ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b9dbe-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b9dbe-105">Parameters</span></span>  
 `pRemoteTarget`  
 <span data-ttu-id="b9dbe-106">[in] Wskaźnik do [icordebugremotetarget — interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md).</span><span class="sxs-lookup"><span data-stu-id="b9dbe-106">[in] Pointer to an [ICorDebugRemoteTarget Interface](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md).</span></span> <span data-ttu-id="b9dbe-107">Używany do określenia komputera zdalnego, na którym zostanie uruchomiony proces.</span><span class="sxs-lookup"><span data-stu-id="b9dbe-107">Used to determine the remote machine on which the process will be launched.</span></span>  
  
 `lpApplicationName`  
 <span data-ttu-id="b9dbe-108">[in] Wskaźnik Określa moduł, który ma być wykonane przez uruchomienie procesu ciąg zakończony znakiem null.</span><span class="sxs-lookup"><span data-stu-id="b9dbe-108">[in] Pointer to a null-terminated string that specifies the module to be executed by the launched process.</span></span> <span data-ttu-id="b9dbe-109">Moduł jest wykonywany w kontekście zabezpieczeń procesu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="b9dbe-109">The module is executed in the security context of the calling process.</span></span>  
  
 `lpCommandLine`  
 <span data-ttu-id="b9dbe-110">[in] Wskaźnik na ciąg zakończony znakiem null, który określa wiersz poleceń do wykonania przez uruchomienie procesu.</span><span class="sxs-lookup"><span data-stu-id="b9dbe-110">[in] Pointer to a null-terminated string that specifies the command line to be executed by the launched process.</span></span>  
  
 `lpProcessAttributes`  
 <span data-ttu-id="b9dbe-111">[in] Nieużywane dla zdalnego debugowania.</span><span class="sxs-lookup"><span data-stu-id="b9dbe-111">[in] Unused for remote debugging.</span></span>  
  
 `lpThreadAttributes`  
 <span data-ttu-id="b9dbe-112">[in] Nieużywane dla zdalnego debugowania.</span><span class="sxs-lookup"><span data-stu-id="b9dbe-112">[in] Unused for remote debugging.</span></span>  
  
 `bInheritHandles`  
 <span data-ttu-id="b9dbe-113">[in] Nieużywane dla zdalnego debugowania.</span><span class="sxs-lookup"><span data-stu-id="b9dbe-113">[in] Unused for remote debugging.</span></span>  
  
 `dwCreationFlags`  
 <span data-ttu-id="b9dbe-114">[in] Nieużywane dla zdalnego debugowania.</span><span class="sxs-lookup"><span data-stu-id="b9dbe-114">[in] Unused for remote debugging.</span></span>  
  
 `lpEnvironment`  
 <span data-ttu-id="b9dbe-115">[in] Wskaźnik do bloku środowiska dla nowego procesu.</span><span class="sxs-lookup"><span data-stu-id="b9dbe-115">[in] Pointer to an environment block for the new process.</span></span>  
  
 `lpCurrentDirectory`  
 <span data-ttu-id="b9dbe-116">[in] Wskaźnik na ciąg zakończony znakiem null, który określa pełną ścieżkę do katalogu bieżącego procesu.</span><span class="sxs-lookup"><span data-stu-id="b9dbe-116">[in] Pointer to a null-terminated string that specifies the full path to the current directory for the process.</span></span> <span data-ttu-id="b9dbe-117">Jeśli ten parametr ma wartość null, nowy proces, będzie miał ten sam bieżącego dysku i katalogu jako procesu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="b9dbe-117">If this parameter is null, the new process will have the same current drive and directory as the calling process.</span></span>  
  
 `lpStartupInfo`  
 <span data-ttu-id="b9dbe-118">[in] Nieużywane dla zdalnego debugowania.</span><span class="sxs-lookup"><span data-stu-id="b9dbe-118">[in] Unused for remote debugging.</span></span>  
  
 `lpProcessInformation`  
 <span data-ttu-id="b9dbe-119">[in] Nieużywane dla zdalnego debugowania.</span><span class="sxs-lookup"><span data-stu-id="b9dbe-119">[in] Unused for remote debugging.</span></span>  
  
 `debuggingFlags`  
 <span data-ttu-id="b9dbe-120">[in] Nieużywane dla zdalnego debugowania.</span><span class="sxs-lookup"><span data-stu-id="b9dbe-120">[in] Unused for remote debugging.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="b9dbe-121">[out] Wskaźnik do adresu obiektu "Icordebugprocess — interfejs", który reprezentuje proces.</span><span class="sxs-lookup"><span data-stu-id="b9dbe-121">[out] A pointer to the address of a"ICorDebugProcess Interface" object that represents the process.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b9dbe-122">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="b9dbe-122">Return Value</span></span>  
 <span data-ttu-id="b9dbe-123">S_OK</span><span class="sxs-lookup"><span data-stu-id="b9dbe-123">S_OK</span></span>  
 <span data-ttu-id="b9dbe-124">Pomyślnie uruchomiono proces na komputerze zdalnym i zwrócony "icordebugprocess — interfejs" do debugowania.</span><span class="sxs-lookup"><span data-stu-id="b9dbe-124">Successfully launched the process on the remote machine and returned an "ICorDebugProcess Interface" for debugging.</span></span>  
  
 <span data-ttu-id="b9dbe-125">E_FAIL (lub inne kody powrotne e_)</span><span class="sxs-lookup"><span data-stu-id="b9dbe-125">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="b9dbe-126">Nie można uruchomić procesu na komputerze zdalnym i zwracają "Interfejs ICorDebugProcess" do debugowania.</span><span class="sxs-lookup"><span data-stu-id="b9dbe-126">Unable to launch the process on the remote machine and return an "ICorDebugProcess Interface" for debugging.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b9dbe-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b9dbe-127">Remarks</span></span>  
 <span data-ttu-id="b9dbe-128">Debugowanie w trybie mieszanym nie jest obsługiwane w programie Silverlight.</span><span class="sxs-lookup"><span data-stu-id="b9dbe-128">Mixed-mode debugging is not supported in Silverlight.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b9dbe-129">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b9dbe-129">Requirements</span></span>  
 <span data-ttu-id="b9dbe-130">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b9dbe-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b9dbe-131">**Nagłówek:** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="b9dbe-131">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="b9dbe-132">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b9dbe-132">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b9dbe-133">**Wersje programu .NET framework:** 4.5, 4, 3.5 Z DODATKIEM SP1</span><span class="sxs-lookup"><span data-stu-id="b9dbe-133">**.NET Framework Versions:** 4.5, 4, 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9dbe-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b9dbe-134">See also</span></span>

- [<span data-ttu-id="b9dbe-135">ICorDebugRemote — Interfejs</span><span class="sxs-lookup"><span data-stu-id="b9dbe-135">ICorDebugRemote Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremote-interface.md)
- [<span data-ttu-id="b9dbe-136">ICorDebug — Interfejs</span><span class="sxs-lookup"><span data-stu-id="b9dbe-136">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)

- [<span data-ttu-id="b9dbe-137">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="b9dbe-137">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
