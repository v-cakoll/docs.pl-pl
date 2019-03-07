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
ms.openlocfilehash: 7b8c72a2dde70a93b589181b0cc1bd7824b3f52d
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57496524"
---
# <a name="icordebugremotecreateprocessex-method"></a>ICorDebugRemote::CreateProcessEx — Metoda
Uruchamia proces na komputerze zdalnym w debugerze.  
  
## <a name="syntax"></a>Składnia  
  
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
  
## <a name="parameters"></a>Parametry  
 `pRemoteTarget`  
 [in] Wskaźnik do [icordebugremotetarget — interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md). Używany do określenia komputera zdalnego, na którym zostanie uruchomiony proces.  
  
 `lpApplicationName`  
 [in] Wskaźnik Określa moduł, który ma być wykonane przez uruchomienie procesu ciąg zakończony znakiem null. Moduł jest wykonywany w kontekście zabezpieczeń procesu wywołującego.  
  
 `lpCommandLine`  
 [in] Wskaźnik na ciąg zakończony znakiem null, który określa wiersz poleceń do wykonania przez uruchomienie procesu.  
  
 `lpProcessAttributes`  
 [in] Nieużywane dla zdalnego debugowania.  
  
 `lpThreadAttributes`  
 [in] Nieużywane dla zdalnego debugowania.  
  
 `bInheritHandles`  
 [in] Nieużywane dla zdalnego debugowania.  
  
 `dwCreationFlags`  
 [in] Nieużywane dla zdalnego debugowania.  
  
 `lpEnvironment`  
 [in] Wskaźnik do bloku środowiska dla nowego procesu.  
  
 `lpCurrentDirectory`  
 [in] Wskaźnik na ciąg zakończony znakiem null, który określa pełną ścieżkę do katalogu bieżącego procesu. Jeśli ten parametr ma wartość null, nowy proces, będzie miał ten sam bieżącego dysku i katalogu jako procesu wywołującego.  
  
 `lpStartupInfo`  
 [in] Nieużywane dla zdalnego debugowania.  
  
 `lpProcessInformation`  
 [in] Nieużywane dla zdalnego debugowania.  
  
 `debuggingFlags`  
 [in] Nieużywane dla zdalnego debugowania.  
  
 `ppProcess`  
 [out] Wskaźnik do adresu obiektu "Icordebugprocess — interfejs", który reprezentuje proces.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK  
 Pomyślnie uruchomiono proces na komputerze zdalnym i zwrócony "icordebugprocess — interfejs" do debugowania.  
  
 E_FAIL (lub inne kody powrotne e_)  
 Nie można uruchomić procesu na komputerze zdalnym i zwracają "Interfejs ICorDebugProcess" do debugowania.  
  
## <a name="remarks"></a>Uwagi  
 Debugowanie w trybie mieszanym nie jest obsługiwane w programie Silverlight.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** 4.5, 4, 3.5 Z DODATKIEM SP1  
  
## <a name="see-also"></a>Zobacz także
- [ICorDebugRemote, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugremote-interface.md)
- [ICorDebug, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)

- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
