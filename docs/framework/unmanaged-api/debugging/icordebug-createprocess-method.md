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
ms.openlocfilehash: 044f94a567dc4bc2b169ba2a5f2a5d7b4f98e516
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugcreateprocess-method"></a>ICorDebug::CreateProcess — Metoda
Uruchamia proces i jego podstawowym wątku pod kontrolą debugera.  
  
## <a name="syntax"></a>Składnia  
  
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
  
#### <a name="parameters"></a>Parametry  
 `lpApplicationName`  
 [in] Wskaźnik do zerem ciąg, który określa moduł, który ma być wykonane przez uruchomionego procesu. Moduł jest wykonywany w kontekście zabezpieczeń procesu wywołującego.  
  
 `lpCommandLine`  
 [in] Wskaźnik do zerem ciąg, który określa wiersz polecenia ma być wykonane przez uruchomionego procesu. Nazwa aplikacji (na przykład "SomeApp.exe") musi być pierwszym argumentem.  
  
 `lpProcessAttributes`  
 [in] Wskaźnik do Win32 `SECURITY_ATTRIBUTES` strukturę, która określa deskryptora zabezpieczeń dla procesu. Jeśli `lpProcessAttributes` jest wartość null, proces pobiera domyślnego deskryptora zabezpieczeń.  
  
 `lpThreadAttributes`  
 [in] Wskaźnik do Win32 `SECURITY_ATTRIBUTES` strukturę, która określa deskryptora zabezpieczeń dla podstawowego wątków procesu. Jeśli `lpThreadAttributes` jest wartość null, wątek pobiera domyślnego deskryptora zabezpieczeń.  
  
 `bInheritHandles`  
 [in] Ustaw `true` aby wskazać, że każdego dziedziczne uchwytu procesu wywołującego jest dziedziczona przez uruchomionego procesu lub `false` aby wskazać, że uchwyty nie są dziedziczone. Uchwyty odziedziczone mają te same prawa dostępu i wartość jako oryginalnego uchwytów.  
  
 `dwCreationFlags`  
 [in] Bitowe połączenie [flagi tworzenia procesu Win32](http://go.microsoft.com/fwlink/?linkid=69981) umożliwiające sterowanie priorytet i działanie uruchomionego procesu.  
  
 `lpEnvironment`  
 [in] Wskaźnik do bloku środowiska dla nowego procesu.  
  
 `lpCurrentDirectory`  
 [in] Wskaźnik do zerem ciąg, który określa pełną ścieżkę do katalogu bieżącego procesu. Jeśli ten parametr ma wartość null, nowy proces będzie mieć tego samego bieżącego dysku i katalogu jako proces wywoływania.  
  
 `lpStartupInfo`  
 [in] Wskaźnik do Win32 `STARTUPINFOW` strukturę, która określa stacja pulpitu, standardowe dojść i wyglądu głównego okna procesu uruchomionego.  
  
 `lpProcessInformation`  
 [in] Wskaźnik do Win32 `PROCESS_INFORMATION` strukturę, która określa informacje identyfikacyjne dotyczące procesu, które mają zostać uruchomione.  
  
 `debuggingFlags`  
 [in] Wartość wyliczenia CorDebugCreateProcessFlags, która określa opcje debugowania.  
  
 `ppProcess`  
 [out] Wskaźnik do adres obiektu ICorDebugProcess, który reprezentuje procesu.  
  
## <a name="remarks"></a>Uwagi  
 Parametry tej metody są takie same jak Win32 `CreateProcess` metody.  
  
 Aby włączyć debugowanie w trybie mieszanym niezarządzane, ustaw `dwCreationFlags` do DEBUG_PROCESS &#124; DEBUG_ONLY_THIS_PROCESS. Jeśli chcesz używać, tylko debugowanie zarządzane nie należy ustawiać te flagi.  
  
 Jeśli debugera i procesu, aby było debugowania (dołączony proces) udostępnianie jednej konsoli, a jeśli używany jest debugowania międzyoperacyjnego, istnieje możliwość dołączony proces do przechowywania blokad konsoli i zatrzymać w zdarzeniu debugowania. Debuger następnie blokuje wszelkie próby korzystania z konsoli. Aby uniknąć tego problemu, należy ustawić flagę CREATE_NEW_CONSOLE `dwCreationFlags` parametru.  
  
 Debugowanie międzyoperacyjne nie jest obsługiwane na platformach Win9x i z systemem innym niż x86, takich jak IA-64 i procesorem AMD64 platformy.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorDebug, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
