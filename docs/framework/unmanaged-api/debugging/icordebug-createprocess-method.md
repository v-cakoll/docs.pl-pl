---
title: ICorDebug::CreateProcess — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebug.CreateProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::CreateProcess
helpviewer_keywords:
- ICorDebug::CreateProcess method [.NET Framework debugging]
- CreateProcess method, ICorDebugProcess interface [.NET Framework debugging]
ms.assetid: b6128694-11ed-46e7-bd4e-49ea1914c46a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dfda61706af3e1043d271c0aa74264bd99a4076c
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43386594"
---
# <a name="icordebugcreateprocess-method"></a><span data-ttu-id="edb2d-102">ICorDebug::CreateProcess — Metoda</span><span class="sxs-lookup"><span data-stu-id="edb2d-102">ICorDebug::CreateProcess Method</span></span>
<span data-ttu-id="edb2d-103">Uruchamia proces i jego podstawowym wątku pod kontrolą debugera.</span><span class="sxs-lookup"><span data-stu-id="edb2d-103">Launches a process and its primary thread under the control of the debugger.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="edb2d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="edb2d-104">Syntax</span></span>  
  
```  
HRESULT CreateProcess (  
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
    [out] ICorDebugProcess            **ppProcess  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="edb2d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="edb2d-105">Parameters</span></span>  
 `lpApplicationName`  
 <span data-ttu-id="edb2d-106">[in] Wskaźnik Określa moduł, który ma być wykonane przez uruchomienie procesu ciąg zakończony znakiem null.</span><span class="sxs-lookup"><span data-stu-id="edb2d-106">[in] Pointer to a null-terminated string that specifies the module to be executed by the launched process.</span></span> <span data-ttu-id="edb2d-107">Moduł jest wykonywany w kontekście zabezpieczeń procesu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="edb2d-107">The module is executed in the security context of the calling process.</span></span>  
  
 `lpCommandLine`  
 <span data-ttu-id="edb2d-108">[in] Wskaźnik na ciąg zakończony znakiem null, który określa wiersz poleceń do wykonania przez uruchomienie procesu.</span><span class="sxs-lookup"><span data-stu-id="edb2d-108">[in] Pointer to a null-terminated string that specifies the command line to be executed by the launched process.</span></span> <span data-ttu-id="edb2d-109">Nazwa aplikacji (na przykład "SomeApp.exe") musi być pierwszym argumentem.</span><span class="sxs-lookup"><span data-stu-id="edb2d-109">The application name (for example, "SomeApp.exe") must be the first argument.</span></span>  
  
 `lpProcessAttributes`  
 <span data-ttu-id="edb2d-110">[in] Wskaźnik do systemu Win32 `SECURITY_ATTRIBUTES` strukturę, która określa deskryptora zabezpieczeń dla procesu.</span><span class="sxs-lookup"><span data-stu-id="edb2d-110">[in] Pointer to a Win32 `SECURITY_ATTRIBUTES` structure that specifies the security descriptor for the process.</span></span> <span data-ttu-id="edb2d-111">Jeśli `lpProcessAttributes` jest wartość null, proces pobiera domyślnego deskryptora zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="edb2d-111">If `lpProcessAttributes` is null, the process gets a default security descriptor.</span></span>  
  
 `lpThreadAttributes`  
 <span data-ttu-id="edb2d-112">[in] Wskaźnik do systemu Win32 `SECURITY_ATTRIBUTES` strukturę, która określa deskryptora zabezpieczeń dla wątku głównego procesu.</span><span class="sxs-lookup"><span data-stu-id="edb2d-112">[in] Pointer to a Win32 `SECURITY_ATTRIBUTES` structure that specifies the security descriptor for the primary thread of the process.</span></span> <span data-ttu-id="edb2d-113">Jeśli `lpThreadAttributes` jest wartość null, wątek pobiera domyślnego deskryptora zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="edb2d-113">If `lpThreadAttributes` is null, the thread gets a default security descriptor.</span></span>  
  
 `bInheritHandles`  
 <span data-ttu-id="edb2d-114">[in] Ustaw `true` do wskazania, że każdy dziedziczne uchwytu procesu wywołującego jest dziedziczona przez uruchomienie procesu lub `false` do wskazania, że uchwyty nie są dziedziczone.</span><span class="sxs-lookup"><span data-stu-id="edb2d-114">[in] Set to `true` to indicate that each inheritable handle in the calling process is inherited by the launched process, or `false` to indicate that the handles are not inherited.</span></span> <span data-ttu-id="edb2d-115">Uchwyty odziedziczone mają takie same wartości i dostęp prawa jako oryginalnego uchwyty.</span><span class="sxs-lookup"><span data-stu-id="edb2d-115">The inherited handles have the same value and access rights as the original handles.</span></span>  
  
 `dwCreationFlags`  
 <span data-ttu-id="edb2d-116">[in] Bitowa kombinacja [flagi tworzenia procesu Win32](https://go.microsoft.com/fwlink/?linkid=69981) umożliwiające sterowanie priorytet i zachowanie uruchomienie procesu.</span><span class="sxs-lookup"><span data-stu-id="edb2d-116">[in] A bitwise combination of the [Win32 Process Creation Flags](https://go.microsoft.com/fwlink/?linkid=69981) that control the priority class and the behavior of the launched process.</span></span>  
  
 `lpEnvironment`  
 <span data-ttu-id="edb2d-117">[in] Wskaźnik do bloku środowiska dla nowego procesu.</span><span class="sxs-lookup"><span data-stu-id="edb2d-117">[in] Pointer to an environment block for the new process.</span></span>  
  
 `lpCurrentDirectory`  
 <span data-ttu-id="edb2d-118">[in] Wskaźnik na ciąg zakończony znakiem null, który określa pełną ścieżkę do katalogu bieżącego procesu.</span><span class="sxs-lookup"><span data-stu-id="edb2d-118">[in] Pointer to a null-terminated string that specifies the full path to the current directory for the process.</span></span> <span data-ttu-id="edb2d-119">Jeśli ten parametr ma wartość null, nowy proces, będzie miał ten sam bieżącego dysku i katalogu jako procesu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="edb2d-119">If this parameter is null, the new process will have the same current drive and directory as the calling process.</span></span>  
  
 `lpStartupInfo`  
 <span data-ttu-id="edb2d-120">[in] Wskaźnik do systemu Win32 `STARTUPINFOW` strukturę, która określa stacji okna pulpitu, standardowe uchwyty i wygląd okna głównego dla uruchomionego procesu.</span><span class="sxs-lookup"><span data-stu-id="edb2d-120">[in] Pointer to a Win32 `STARTUPINFOW` structure that specifies the window station, desktop, standard handles, and appearance of the main window for the launched process.</span></span>  
  
 `lpProcessInformation`  
 <span data-ttu-id="edb2d-121">[in] Wskaźnik do systemu Win32 `PROCESS_INFORMATION` strukturę, która określa informacje identyfikacyjne dotyczące procesu do uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="edb2d-121">[in] Pointer to a Win32 `PROCESS_INFORMATION` structure that specifies the identification information about the process to be launched.</span></span>  
  
 `debuggingFlags`  
 <span data-ttu-id="edb2d-122">[in] Wartość cordebugcreateprocessflags — wyliczenie, który określa opcje debugowania.</span><span class="sxs-lookup"><span data-stu-id="edb2d-122">[in] A value of the CorDebugCreateProcessFlags enumeration that specifies the debugging options.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="edb2d-123">[out] Wskaźnik do adresu obiektu ICorDebugProcess, który reprezentuje proces.</span><span class="sxs-lookup"><span data-stu-id="edb2d-123">[out] A pointer to the address of a ICorDebugProcess object that represents the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="edb2d-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="edb2d-124">Remarks</span></span>  
 <span data-ttu-id="edb2d-125">Parametry tej metody są takie same, jak Win32 `CreateProcess` metody.</span><span class="sxs-lookup"><span data-stu-id="edb2d-125">The parameters of this method are the same as those of the Win32 `CreateProcess` method.</span></span>  
  
 <span data-ttu-id="edb2d-126">Aby włączyć debugowanie niezarządzane trybu mieszanego, ustaw `dwCreationFlags` do DEBUG_PROCESS &#124; DEBUG_ONLY_THIS_PROCESS.</span><span class="sxs-lookup"><span data-stu-id="edb2d-126">To enable unmanaged mixed-mode debugging, set `dwCreationFlags` to DEBUG_PROCESS &#124; DEBUG_ONLY_THIS_PROCESS.</span></span> <span data-ttu-id="edb2d-127">Aby użyć tylko debugowania zarządzanego, nie należy ustawiać tych flag.</span><span class="sxs-lookup"><span data-stu-id="edb2d-127">If you want to use only managed debugging, do not set these flags.</span></span>  
  
 <span data-ttu-id="edb2d-128">Jeśli debuger i proces debugowania (dołączony proces) udostępnianie jednej konsoli, a jeśli debugowania międzyoperacyjnego jest używany, istnieje możliwość dołączony proces konsoli blokady i zatrzyma zdarzeń debugowania.</span><span class="sxs-lookup"><span data-stu-id="edb2d-128">If the debugger and the process to be debugged (the attached process) share a single console, and if interop debugging is used, it is possible for the attached process to hold console locks and stop at a debug event.</span></span> <span data-ttu-id="edb2d-129">Debuger następnie zablokuje wszelkie próby korzystania z konsoli.</span><span class="sxs-lookup"><span data-stu-id="edb2d-129">The debugger will then block any attempt to use the console.</span></span> <span data-ttu-id="edb2d-130">Aby uniknąć tego problemu, należy ustawić flagę CREATE_NEW_CONSOLE `dwCreationFlags` parametru.</span><span class="sxs-lookup"><span data-stu-id="edb2d-130">To avoid this problem, set the CREATE_NEW_CONSOLE flag in the `dwCreationFlags` parameter.</span></span>  
  
 <span data-ttu-id="edb2d-131">Debugowanie międzyoperacyjne nie jest obsługiwane na Win9x i x86 innych platformach, takich jak IA-64 i komputerów z procesorem AMD64 platform.</span><span class="sxs-lookup"><span data-stu-id="edb2d-131">Interop debugging is not supported on Win9x and non-x86 platforms such as IA-64-based and AMD64-based platforms.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="edb2d-132">Wymagania</span><span class="sxs-lookup"><span data-stu-id="edb2d-132">Requirements</span></span>  
 <span data-ttu-id="edb2d-133">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="edb2d-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="edb2d-134">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="edb2d-134">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="edb2d-135">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="edb2d-135">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="edb2d-136">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="edb2d-136">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="edb2d-137">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="edb2d-137">See Also</span></span>  
 [<span data-ttu-id="edb2d-138">ICorDebug, interfejs</span><span class="sxs-lookup"><span data-stu-id="edb2d-138">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
