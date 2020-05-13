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
ms.openlocfilehash: 4b2689f04228c9ecbbbb18531a0aefd3c40e3072
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/13/2020
ms.locfileid: "83377983"
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
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK  
 Pomyślnie uruchomiono proces na maszynie zdalnej i zwróciło "interfejs ICorDebugProcess" do debugowania.  
  
 E_FAIL (lub inne kody powrotne E_)  
 Nie można uruchomić procesu na maszynie zdalnej i zwrócić "ICorDebugProcess Interface" w celu debugowania.  
  
## <a name="remarks"></a>Uwagi  
 Debugowanie w trybie mieszanym nie jest obsługiwane w programie Silverlight.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:** 4,5, 4, 3,5 SP1  
  
## <a name="see-also"></a>Zobacz też

- [ICorDebugRemote — Interfejs](icordebugremote-interface.md)
- [ICorDebug — Interfejs](icordebug-interface.md)

- [Debugowanie — Interfejsy](debugging-interfaces.md)
