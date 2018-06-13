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
ms.openlocfilehash: 06bdc3605d981acad68a97901627f361da4061c7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33423322"
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
  
#### <a name="parameters"></a>Parametry  
 `pRemoteTarget`  
 [in] Wskaźnik do [ICorDebugRemoteTarget — interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md). Używany do określenia komputer zdalny, na którym zostanie uruchomiony proces.  
  
 `lpApplicationName`  
 [in] Wskaźnik do zerem ciąg, który określa moduł, który ma być wykonane przez uruchomionego procesu. Moduł jest wykonywany w kontekście zabezpieczeń procesu wywołującego.  
  
 `lpCommandLine`  
 [in] Wskaźnik do zerem ciąg, który określa wiersz polecenia ma być wykonane przez uruchomionego procesu.  
  
 `lpProcessAttributes`  
 [in] Nieużywane do zdalnego debugowania.  
  
 `lpThreadAttributes`  
 [in] Nieużywane do zdalnego debugowania.  
  
 `bInheritHandles`  
 [in] Nieużywane do zdalnego debugowania.  
  
 `dwCreationFlags`  
 [in] Nieużywane do zdalnego debugowania.  
  
 `lpEnvironment`  
 [in] Wskaźnik do bloku środowiska dla nowego procesu.  
  
 `lpCurrentDirectory`  
 [in] Wskaźnik do zerem ciąg, który określa pełną ścieżkę do katalogu bieżącego procesu. Jeśli ten parametr ma wartość null, nowy proces będzie mieć tego samego bieżącego dysku i katalogu jako proces wywoływania.  
  
 `lpStartupInfo`  
 [in] Nieużywane do zdalnego debugowania.  
  
 `lpProcessInformation`  
 [in] Nieużywane do zdalnego debugowania.  
  
 `debuggingFlags`  
 [in] Nieużywane do zdalnego debugowania.  
  
 `ppProcess`  
 [out] Wskaźnik do obiektu "ICorDebugProcess — interfejs", który reprezentuje proces adres.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK  
 Pomyślne uruchomienie procesu na komputerze zdalnym i zwrócony "ICorDebugProcess — interfejs" do debugowania.  
  
 E_FAIL (lub inne kody powrotu E_)  
 Nie można uruchomić procesu na komputerze zdalnym i wrócić do debugowania "ICorDebugProcess — interfejs".  
  
## <a name="remarks"></a>Uwagi  
 Debugowanie w trybie mieszanym nie jest obsługiwane w programie Silverlight.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** 4.5, 4, 3.5 z dodatkiem SP1  
  
## <a name="see-also"></a>Zobacz też  
 [ICorDebugRemote, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugremote-interface.md)  
 [ICorDebug, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
    
 [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
