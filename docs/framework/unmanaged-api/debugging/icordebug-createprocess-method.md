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
 [in] Wskaźnik Określa moduł, który ma być wykonane przez uruchomienie procesu ciąg zakończony znakiem null. Moduł jest wykonywany w kontekście zabezpieczeń procesu wywołującego.  
  
 `lpCommandLine`  
 [in] Wskaźnik na ciąg zakończony znakiem null, który określa wiersz poleceń do wykonania przez uruchomienie procesu. Nazwa aplikacji (na przykład "SomeApp.exe") musi być pierwszym argumentem.  
  
 `lpProcessAttributes`  
 [in] Wskaźnik do systemu Win32 `SECURITY_ATTRIBUTES` strukturę, która określa deskryptora zabezpieczeń dla procesu. Jeśli `lpProcessAttributes` jest wartość null, proces pobiera domyślnego deskryptora zabezpieczeń.  
  
 `lpThreadAttributes`  
 [in] Wskaźnik do systemu Win32 `SECURITY_ATTRIBUTES` strukturę, która określa deskryptora zabezpieczeń dla wątku głównego procesu. Jeśli `lpThreadAttributes` jest wartość null, wątek pobiera domyślnego deskryptora zabezpieczeń.  
  
 `bInheritHandles`  
 [in] Ustaw `true` do wskazania, że każdy dziedziczne uchwytu procesu wywołującego jest dziedziczona przez uruchomienie procesu lub `false` do wskazania, że uchwyty nie są dziedziczone. Uchwyty odziedziczone mają takie same wartości i dostęp prawa jako oryginalnego uchwyty.  
  
 `dwCreationFlags`  
 [in] Bitowa kombinacja [flagi tworzenia procesu Win32](https://go.microsoft.com/fwlink/?linkid=69981) umożliwiające sterowanie priorytet i zachowanie uruchomienie procesu.  
  
 `lpEnvironment`  
 [in] Wskaźnik do bloku środowiska dla nowego procesu.  
  
 `lpCurrentDirectory`  
 [in] Wskaźnik na ciąg zakończony znakiem null, który określa pełną ścieżkę do katalogu bieżącego procesu. Jeśli ten parametr ma wartość null, nowy proces, będzie miał ten sam bieżącego dysku i katalogu jako procesu wywołującego.  
  
 `lpStartupInfo`  
 [in] Wskaźnik do systemu Win32 `STARTUPINFOW` strukturę, która określa stacji okna pulpitu, standardowe uchwyty i wygląd okna głównego dla uruchomionego procesu.  
  
 `lpProcessInformation`  
 [in] Wskaźnik do systemu Win32 `PROCESS_INFORMATION` strukturę, która określa informacje identyfikacyjne dotyczące procesu do uruchomienia.  
  
 `debuggingFlags`  
 [in] Wartość cordebugcreateprocessflags — wyliczenie, który określa opcje debugowania.  
  
 `ppProcess`  
 [out] Wskaźnik do adresu obiektu ICorDebugProcess, który reprezentuje proces.  
  
## <a name="remarks"></a>Uwagi  
 Parametry tej metody są takie same, jak Win32 `CreateProcess` metody.  
  
 Aby włączyć debugowanie niezarządzane trybu mieszanego, ustaw `dwCreationFlags` do DEBUG_PROCESS &#124; DEBUG_ONLY_THIS_PROCESS. Aby użyć tylko debugowania zarządzanego, nie należy ustawiać tych flag.  
  
 Jeśli debuger i proces debugowania (dołączony proces) udostępnianie jednej konsoli, a jeśli debugowania międzyoperacyjnego jest używany, istnieje możliwość dołączony proces konsoli blokady i zatrzyma zdarzeń debugowania. Debuger następnie zablokuje wszelkie próby korzystania z konsoli. Aby uniknąć tego problemu, należy ustawić flagę CREATE_NEW_CONSOLE `dwCreationFlags` parametru.  
  
 Debugowanie międzyoperacyjne nie jest obsługiwane na Win9x i x86 innych platformach, takich jak IA-64 i komputerów z procesorem AMD64 platform.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorDebug, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
