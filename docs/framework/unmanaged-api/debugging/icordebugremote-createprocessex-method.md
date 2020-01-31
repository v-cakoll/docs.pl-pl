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
ms.openlocfilehash: cfec84483d387630623f77c176c668171303dd0f
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791991"
---
# <a name="icordebugremotecreateprocessex-method"></a>ICorDebugRemote::CreateProcessEx — Metoda
Uruchamia proces na maszynie zdalnej pod debugerem.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
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
 podczas Wskaźnik do [interfejsu ICorDebugRemoteTarget](icordebugremotetarget-interface.md). Służy do określania komputera zdalnego, na którym zostanie uruchomiony proces.  
  
 `lpApplicationName`  
 podczas Wskaźnik na ciąg zakończony znakiem null, który określa moduł, który ma zostać wykonany przez uruchomiony proces. Moduł jest wykonywany w kontekście zabezpieczeń procesu wywołującego.  
  
 `lpCommandLine`  
 podczas Wskaźnik na ciąg zakończony znakiem null, który określa wiersz polecenia, który ma zostać wykonany przez uruchomiony proces.  
  
 `lpProcessAttributes`  
 podczas Nieużywane na potrzeby debugowania zdalnego.  
  
 `lpThreadAttributes`  
 podczas Nieużywane na potrzeby debugowania zdalnego.  
  
 `bInheritHandles`  
 podczas Nieużywane na potrzeby debugowania zdalnego.  
  
 `dwCreationFlags`  
 podczas Nieużywane na potrzeby debugowania zdalnego.  
  
 `lpEnvironment`  
 podczas Wskaźnik do bloku środowiska dla nowego procesu.  
  
 `lpCurrentDirectory`  
 podczas Wskaźnik na ciąg zakończony znakiem null, który określa pełną ścieżkę do bieżącego katalogu dla procesu. Jeśli ten parametr ma wartość null, nowy proces będzie miał ten sam bieżący dysk i katalog co proces wywołujący.  
  
 `lpStartupInfo`  
 podczas Nieużywane na potrzeby debugowania zdalnego.  
  
 `lpProcessInformation`  
 podczas Nieużywane na potrzeby debugowania zdalnego.  
  
 `debuggingFlags`  
 podczas Nieużywane na potrzeby debugowania zdalnego.  
  
 `ppProcess`  
 określoną Wskaźnik do adresu obiektu "ICorDebugProcess Interface", który reprezentuje proces.  
  
## <a name="return-value"></a>Wartość zwrócona  
 S_OK  
 Pomyślnie uruchomiono proces na maszynie zdalnej i zwróciło "interfejs ICorDebugProcess" do debugowania.  
  
 E_FAIL (lub inne kody powrotne E_)  
 Nie można uruchomić procesu na maszynie zdalnej i zwrócić "ICorDebugProcess Interface" w celu debugowania.  
  
## <a name="remarks"></a>Uwagi  
 Debugowanie w trybie mieszanym nie jest obsługiwane w programie Silverlight.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:** 4,5, 4, 3,5 SP1  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugRemote, interfejs](icordebugremote-interface.md)
- [ICorDebug, interfejs](icordebug-interface.md)

- [Debugowanie, interfejsy](debugging-interfaces.md)
