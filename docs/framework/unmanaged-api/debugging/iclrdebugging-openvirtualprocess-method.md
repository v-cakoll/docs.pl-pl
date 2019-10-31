---
title: ICLRDebugging::OpenVirtualProcess — Metoda
ms.date: 03/30/2017
api_name:
- ICLRDebugging.OpenVirtualProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDebugging::OpenVirtualProcess
helpviewer_keywords:
- OpenVirtualProcess method [.NET Framework debugging]
- ICLRDebugging::OpenVirtualProcess method [.NET Framework debugging]
ms.assetid: e8ab7c41-d508-4ed9-8a31-ead072b5a314
topic_type:
- apiref
ms.openlocfilehash: cd43dce995c2bc9a45a0c8134a91b20cb1dec26e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73111427"
---
# <a name="iclrdebuggingopenvirtualprocess-method"></a>ICLRDebugging::OpenVirtualProcess — Metoda
Pobiera interfejs ICorDebugProcess, który odnosi się do modułu środowiska uruchomieniowego języka wspólnego (CLR) załadowanego w procesie.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT OpenVirtualProcess(  
    [in] ULONG64 moduleBaseAddress,  
    [in] IUnknown * pDataTarget,  
    [in] ICLRDebuggingLibraryProvider * pLibraryProvider,  
    [in] CLR_DEBUGGING_VERSION * pMaxDebuggerSupportedVersion,  
    [in] REFIID riidProcess,  
    [out, iid_is(riidProcess)] IUnknown ** ppProcess,  
    [in, out] CLR_DEBUGGING_VERSION * pVersion,  
    [out] CLR_DEBUGGING_PROCESS_FLAGS * pdwFlags);  
```  
  
## <a name="parameters"></a>Parametry  
 `moduleBaseAddress`  
 podczas Adres podstawowy modułu w procesie docelowym. COR_E_NOT_CLR zostanie zwrócona, jeśli określony moduł nie jest modułem CLR.  
  
 `pDataTarget`  
 podczas Abstrakcja elementu docelowego danych umożliwiająca zarządzanemu debugerowi sprawdzenie stanu procesu. Debuger musi implementować interfejs [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) . Należy zaimplementować interfejs [ICLRDebuggingLibraryProvider](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md) , aby obsługiwał scenariusze, w których DEBUGOWANE środowisko CLR nie jest zainstalowane lokalnie na komputerze.  
  
 `pLibraryProvider`  
 podczas Interfejs wywołania zwrotnego dostawcy biblioteki, który umożliwia zlokalizowanie i załadowanie bibliotek debugowania specyficznych dla wersji na żądanie. Ten parametr jest wymagany tylko wtedy, gdy nie `null``ppProcess` lub `pFlags`.  
  
 `pMaxDebuggerSupportedVersion`  
 podczas Największa wersja środowiska CLR, którą może debugować ten debuger. Należy określić wersje główne, pomocnicze i kompilacje od najnowszej wersji środowiska CLR obsługiwane przez ten debuger i ustawić numer poprawki na 65535 w celu uwzględnienia przyszłych wydań obsługi środowiska CLR w przyszłości.  
  
 `riidProcess`  
 podczas Identyfikator interfejsu ICorDebugProcess do pobrania. Obecnie Jedyne akceptowane wartości to IID_CORDEBUGPROCESS3, IID_CORDEBUGPROCESS2 i IID_CORDEBUGPROCESS.  
  
 `ppProcess`  
 określoną Wskaźnik do interfejsu COM, który jest identyfikowany przez `riidProcess`.  
  
 `pVersion`  
 [in. out] Wersja środowiska CLR. Na wejściu ta wartość może być `null`. Może również wskazywać na strukturę [CLR_DEBUGGING_VERSION](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-version-structure.md) , w którym przypadku pole `wStructVersion` struktury musi być inicjowane na wartość 0 (zero).  
  
 W danych wyjściowych, zwrócona struktura `CLR_DEBUGGING_VERSION` zostanie wypełniona informacjami o wersji środowiska CLR.  
  
 `pdwFlags`  
 określoną Flagi informacyjne dotyczące określonego środowiska uruchomieniowego. Opis flag można znaleźć w temacie [CLR_DEBUGGING_PROCESS_FLAGS](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-process-flags-enumeration.md) .  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca następujące określone wartości HRESULT oraz błędy HRESULT wskazujące niepowodzenie metody.  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|Metoda została ukończona pomyślnie.|  
|E_POINTER|`pDataTarget` jest `null`.|  
|CORDBG_E_LIBRARY_PROVIDER_ERROR|Wywołanie zwrotne [ICLRDebuggingLibraryProvider](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md) zwraca błąd lub nie zapewnia prawidłowego dojścia.|  
|CORDBG_E_MISSING_DATA_TARGET_INTERFACE|`pDataTarget` nie implementuje wymaganych interfejsów obiektów docelowych danych dla tej wersji środowiska uruchomieniowego.|  
|CORDBG_E_NOT_CLR|Wskazany moduł nie jest modułem CLR. Ten wynik HRESULT jest również zwracany, gdy nie można wykryć modułu CLR, ponieważ pamięć została uszkodzona, moduł jest niedostępny lub wersja środowiska CLR jest nowsza niż wersja podkładki.|  
|CORDBG_E_UNSUPPORTED_DEBUGGING_MODEL|Ta wersja środowiska uruchomieniowego nie obsługuje tego modelu debugowania. Obecnie model debugowania nie jest obsługiwany przez wersje środowiska CLR przed .NET Framework 4. Parametr danych wyjściowych `pwszVersion` nadal jest ustawiany na poprawną wartość po wystąpieniu tego błędu.|  
|CORDBG_E_UNSUPPORTED_FORWARD_COMPAT|Wersja środowiska CLR jest nowsza niż wersja tego debugera do obsługi. Parametr danych wyjściowych `pwszVersion` nadal jest ustawiany na poprawną wartość po wystąpieniu tego błędu.|  
|E_NO_INTERFACE|Interfejs `riidProcess` nie jest dostępny.|  
|CORDBG_E_UNSUPPORTED_VERSION_STRUCT|Struktura `CLR_DEBUGGING_VERSION` nie ma rozpoznawanej wartości dla `wStructVersion`. Jedyną akceptowaną wartością w tym momencie jest 0.|  
  
## <a name="exceptions"></a>Wyjątki  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Debugowanie](../../../../docs/framework/unmanaged-api/debugging/index.md)
