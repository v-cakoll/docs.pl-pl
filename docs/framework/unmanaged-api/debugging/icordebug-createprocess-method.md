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
ms.openlocfilehash: 8812a98b0f28dd1336903dc34682f638a291f53b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73110992"
---
# <a name="icordebugcreateprocess-method"></a><span data-ttu-id="5ce88-102">ICorDebug::CreateProcess — Metoda</span><span class="sxs-lookup"><span data-stu-id="5ce88-102">ICorDebug::CreateProcess Method</span></span>
<span data-ttu-id="5ce88-103">Uruchamia proces i jego główny wątek pod kontrolą debugera.</span><span class="sxs-lookup"><span data-stu-id="5ce88-103">Launches a process and its primary thread under the control of the debugger.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ce88-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5ce88-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="5ce88-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5ce88-105">Parameters</span></span>  
 `lpApplicationName`  
 <span data-ttu-id="5ce88-106">podczas Wskaźnik na ciąg zakończony znakiem null, który określa moduł, który ma zostać wykonany przez uruchomiony proces.</span><span class="sxs-lookup"><span data-stu-id="5ce88-106">[in] Pointer to a null-terminated string that specifies the module to be executed by the launched process.</span></span> <span data-ttu-id="5ce88-107">Moduł jest wykonywany w kontekście zabezpieczeń procesu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="5ce88-107">The module is executed in the security context of the calling process.</span></span>  
  
 `lpCommandLine`  
 <span data-ttu-id="5ce88-108">podczas Wskaźnik na ciąg zakończony znakiem null, który określa wiersz polecenia, który ma zostać wykonany przez uruchomiony proces.</span><span class="sxs-lookup"><span data-stu-id="5ce88-108">[in] Pointer to a null-terminated string that specifies the command line to be executed by the launched process.</span></span> <span data-ttu-id="5ce88-109">Nazwa aplikacji (na przykład "SomeApp. exe") musi być pierwszym argumentem.</span><span class="sxs-lookup"><span data-stu-id="5ce88-109">The application name (for example, "SomeApp.exe") must be the first argument.</span></span>  
  
 `lpProcessAttributes`  
 <span data-ttu-id="5ce88-110">podczas Wskaźnik do struktury `SECURITY_ATTRIBUTES` Win32, który określa deskryptor zabezpieczeń dla procesu.</span><span class="sxs-lookup"><span data-stu-id="5ce88-110">[in] Pointer to a Win32 `SECURITY_ATTRIBUTES` structure that specifies the security descriptor for the process.</span></span> <span data-ttu-id="5ce88-111">Jeśli `lpProcessAttributes` ma wartość null, proces Pobiera domyślny deskryptor zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="5ce88-111">If `lpProcessAttributes` is null, the process gets a default security descriptor.</span></span>  
  
 `lpThreadAttributes`  
 <span data-ttu-id="5ce88-112">podczas Wskaźnik do struktury `SECURITY_ATTRIBUTES` Win32, który określa deskryptor zabezpieczeń dla wątku podstawowego procesu.</span><span class="sxs-lookup"><span data-stu-id="5ce88-112">[in] Pointer to a Win32 `SECURITY_ATTRIBUTES` structure that specifies the security descriptor for the primary thread of the process.</span></span> <span data-ttu-id="5ce88-113">Jeśli `lpThreadAttributes` ma wartość null, wątek Pobiera domyślny deskryptor zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="5ce88-113">If `lpThreadAttributes` is null, the thread gets a default security descriptor.</span></span>  
  
 `bInheritHandles`  
 <span data-ttu-id="5ce88-114">podczas Ustaw na `true`, aby wskazać, że każdy dziedziczny uchwyt w procesie wywołującym jest dziedziczony przez uruchomiony proces lub `false`, aby wskazać, że uchwyty nie są dziedziczone.</span><span class="sxs-lookup"><span data-stu-id="5ce88-114">[in] Set to `true` to indicate that each inheritable handle in the calling process is inherited by the launched process, or `false` to indicate that the handles are not inherited.</span></span> <span data-ttu-id="5ce88-115">Dziedziczone dojścia mają takie same prawa wartości i dostępu jak oryginalne dojścia.</span><span class="sxs-lookup"><span data-stu-id="5ce88-115">The inherited handles have the same value and access rights as the original handles.</span></span>  
  
 `dwCreationFlags`  
 <span data-ttu-id="5ce88-116">podczas Bitowa kombinacja [flag tworzenia procesów Win32](https://go.microsoft.com/fwlink/?linkid=69981) kontrolujących klasę priorytetu i zachowanie uruchomionego procesu.</span><span class="sxs-lookup"><span data-stu-id="5ce88-116">[in] A bitwise combination of the [Win32 Process Creation Flags](https://go.microsoft.com/fwlink/?linkid=69981) that control the priority class and the behavior of the launched process.</span></span>  
  
 `lpEnvironment`  
 <span data-ttu-id="5ce88-117">podczas Wskaźnik do bloku środowiska dla nowego procesu.</span><span class="sxs-lookup"><span data-stu-id="5ce88-117">[in] Pointer to an environment block for the new process.</span></span>  
  
 `lpCurrentDirectory`  
 <span data-ttu-id="5ce88-118">podczas Wskaźnik na ciąg zakończony znakiem null, który określa pełną ścieżkę do bieżącego katalogu dla procesu.</span><span class="sxs-lookup"><span data-stu-id="5ce88-118">[in] Pointer to a null-terminated string that specifies the full path to the current directory for the process.</span></span> <span data-ttu-id="5ce88-119">Jeśli ten parametr ma wartość null, nowy proces będzie miał ten sam bieżący dysk i katalog co proces wywołujący.</span><span class="sxs-lookup"><span data-stu-id="5ce88-119">If this parameter is null, the new process will have the same current drive and directory as the calling process.</span></span>  
  
 `lpStartupInfo`  
 <span data-ttu-id="5ce88-120">podczas Wskaźnik do struktury `STARTUPINFOW` Win32, który określa stacji okna, pulpitu, standardowych dojść i wyglądu okna głównego dla uruchomionego procesu.</span><span class="sxs-lookup"><span data-stu-id="5ce88-120">[in] Pointer to a Win32 `STARTUPINFOW` structure that specifies the window station, desktop, standard handles, and appearance of the main window for the launched process.</span></span>  
  
 `lpProcessInformation`  
 <span data-ttu-id="5ce88-121">podczas Wskaźnik do struktury `PROCESS_INFORMATION` Win32, który określa informacje identyfikacyjne procesu, który ma zostać uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="5ce88-121">[in] Pointer to a Win32 `PROCESS_INFORMATION` structure that specifies the identification information about the process to be launched.</span></span>  
  
 `debuggingFlags`  
 <span data-ttu-id="5ce88-122">podczas Wartość wyliczenia CorDebugCreateProcessFlags —, która określa opcje debugowania.</span><span class="sxs-lookup"><span data-stu-id="5ce88-122">[in] A value of the CorDebugCreateProcessFlags enumeration that specifies the debugging options.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="5ce88-123">określoną Wskaźnik do adresu obiektu ICorDebugProcess, który reprezentuje proces.</span><span class="sxs-lookup"><span data-stu-id="5ce88-123">[out] A pointer to the address of a ICorDebugProcess object that represents the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5ce88-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5ce88-124">Remarks</span></span>  
 <span data-ttu-id="5ce88-125">Parametry tej metody są takie same jak w przypadku metody Win32 `CreateProcess`.</span><span class="sxs-lookup"><span data-stu-id="5ce88-125">The parameters of this method are the same as those of the Win32 `CreateProcess` method.</span></span>  
  
 <span data-ttu-id="5ce88-126">Aby włączyć debugowanie w trybie mieszanym, ustaw `dwCreationFlags` na DEBUG_PROCESS &#124; DEBUG_ONLY_THIS_PROCESS.</span><span class="sxs-lookup"><span data-stu-id="5ce88-126">To enable unmanaged mixed-mode debugging, set `dwCreationFlags` to DEBUG_PROCESS &#124; DEBUG_ONLY_THIS_PROCESS.</span></span> <span data-ttu-id="5ce88-127">Jeśli chcesz używać tylko debugowania zarządzanego, nie ustawiaj tych flag.</span><span class="sxs-lookup"><span data-stu-id="5ce88-127">If you want to use only managed debugging, do not set these flags.</span></span>  
  
 <span data-ttu-id="5ce88-128">Jeśli debuger i proces mają być debugowane (dołączone procesy) współużytkują pojedynczą konsolę, a jeśli jest używane debugowanie międzyoperacyjności, istnieje możliwość, że podłączony proces będzie przetrzymywać blokady i zatrzymać przy zdarzeniu debugowania.</span><span class="sxs-lookup"><span data-stu-id="5ce88-128">If the debugger and the process to be debugged (the attached process) share a single console, and if interop debugging is used, it is possible for the attached process to hold console locks and stop at a debug event.</span></span> <span data-ttu-id="5ce88-129">Debuger spowoduje zablokowanie wszelkich prób korzystania z konsoli programu.</span><span class="sxs-lookup"><span data-stu-id="5ce88-129">The debugger will then block any attempt to use the console.</span></span> <span data-ttu-id="5ce88-130">Aby uniknąć tego problemu, Ustaw flagę CREATE_NEW_CONSOLE w parametrze `dwCreationFlags`.</span><span class="sxs-lookup"><span data-stu-id="5ce88-130">To avoid this problem, set the CREATE_NEW_CONSOLE flag in the `dwCreationFlags` parameter.</span></span>  
  
 <span data-ttu-id="5ce88-131">Debugowanie międzyoperacyjności nie jest obsługiwane w przypadku platform systemów Win9x i innych niż x86, takich jak platformy oparte na architekturze IA-64 i AMD64.</span><span class="sxs-lookup"><span data-stu-id="5ce88-131">Interop debugging is not supported on Win9x and non-x86 platforms such as IA-64-based and AMD64-based platforms.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5ce88-132">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5ce88-132">Requirements</span></span>  
 <span data-ttu-id="5ce88-133">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5ce88-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5ce88-134">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="5ce88-134">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5ce88-135">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="5ce88-135">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5ce88-136">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5ce88-136">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ce88-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5ce88-137">See also</span></span>

- [<span data-ttu-id="5ce88-138">ICorDebug, interfejs</span><span class="sxs-lookup"><span data-stu-id="5ce88-138">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
