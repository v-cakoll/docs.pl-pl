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
# <a name="icordebugcreateprocess-method"></a>ICorDebug::CreateProcess — Metoda
Uruchamia proces i jego główny wątek pod kontrolą debugera.  
  
## <a name="syntax"></a>Składnia  
  
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
  
## <a name="parameters"></a>Parametry  
 `lpApplicationName`  
 podczas Wskaźnik na ciąg zakończony znakiem null, który określa moduł, który ma zostać wykonany przez uruchomiony proces. Moduł jest wykonywany w kontekście zabezpieczeń procesu wywołującego.  
  
 `lpCommandLine`  
 podczas Wskaźnik na ciąg zakończony znakiem null, który określa wiersz polecenia, który ma zostać wykonany przez uruchomiony proces. Nazwa aplikacji (na przykład "SomeApp. exe") musi być pierwszym argumentem.  
  
 `lpProcessAttributes`  
 podczas Wskaźnik do struktury `SECURITY_ATTRIBUTES` Win32, który określa deskryptor zabezpieczeń dla procesu. Jeśli `lpProcessAttributes` ma wartość null, proces Pobiera domyślny deskryptor zabezpieczeń.  
  
 `lpThreadAttributes`  
 podczas Wskaźnik do struktury `SECURITY_ATTRIBUTES` Win32, który określa deskryptor zabezpieczeń dla wątku podstawowego procesu. Jeśli `lpThreadAttributes` ma wartość null, wątek Pobiera domyślny deskryptor zabezpieczeń.  
  
 `bInheritHandles`  
 podczas Ustaw na `true`, aby wskazać, że każdy dziedziczny uchwyt w procesie wywołującym jest dziedziczony przez uruchomiony proces lub `false`, aby wskazać, że uchwyty nie są dziedziczone. Dziedziczone dojścia mają takie same prawa wartości i dostępu jak oryginalne dojścia.  
  
 `dwCreationFlags`  
 podczas Bitowa kombinacja [flag tworzenia procesów Win32](https://go.microsoft.com/fwlink/?linkid=69981) kontrolujących klasę priorytetu i zachowanie uruchomionego procesu.  
  
 `lpEnvironment`  
 podczas Wskaźnik do bloku środowiska dla nowego procesu.  
  
 `lpCurrentDirectory`  
 podczas Wskaźnik na ciąg zakończony znakiem null, który określa pełną ścieżkę do bieżącego katalogu dla procesu. Jeśli ten parametr ma wartość null, nowy proces będzie miał ten sam bieżący dysk i katalog co proces wywołujący.  
  
 `lpStartupInfo`  
 podczas Wskaźnik do struktury `STARTUPINFOW` Win32, który określa stacji okna, pulpitu, standardowych dojść i wyglądu okna głównego dla uruchomionego procesu.  
  
 `lpProcessInformation`  
 podczas Wskaźnik do struktury `PROCESS_INFORMATION` Win32, który określa informacje identyfikacyjne procesu, który ma zostać uruchomiony.  
  
 `debuggingFlags`  
 podczas Wartość wyliczenia CorDebugCreateProcessFlags —, która określa opcje debugowania.  
  
 `ppProcess`  
 określoną Wskaźnik do adresu obiektu ICorDebugProcess, który reprezentuje proces.  
  
## <a name="remarks"></a>Uwagi  
 Parametry tej metody są takie same jak w przypadku metody Win32 `CreateProcess`.  
  
 Aby włączyć debugowanie w trybie mieszanym, ustaw `dwCreationFlags` na DEBUG_PROCESS &#124; DEBUG_ONLY_THIS_PROCESS. Jeśli chcesz używać tylko debugowania zarządzanego, nie ustawiaj tych flag.  
  
 Jeśli debuger i proces mają być debugowane (dołączone procesy) współużytkują pojedynczą konsolę, a jeśli jest używane debugowanie międzyoperacyjności, istnieje możliwość, że podłączony proces będzie przetrzymywać blokady i zatrzymać przy zdarzeniu debugowania. Debuger spowoduje zablokowanie wszelkich prób korzystania z konsoli programu. Aby uniknąć tego problemu, Ustaw flagę CREATE_NEW_CONSOLE w parametrze `dwCreationFlags`.  
  
 Debugowanie międzyoperacyjności nie jest obsługiwane w przypadku platform systemów Win9x i innych niż x86, takich jak platformy oparte na architekturze IA-64 i AMD64.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebug, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
