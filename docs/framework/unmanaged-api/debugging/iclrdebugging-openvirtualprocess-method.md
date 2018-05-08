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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 51b5a9ecd85f0d40ac2fe2826cbbe7a56a6228d1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="iclrdebuggingopenvirtualprocess-method"></a>ICLRDebugging::OpenVirtualProcess — Metoda
Pobiera interfejs ICorDebugProcess, który odpowiada wspólny języka wspólnego (CLR) moduł załadowany w procesie.  
  
## <a name="syntax"></a>Składnia  
  
```  
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
  
#### <a name="parameters"></a>Parametry  
 `moduleBaseAddress`  
 [in] Adres podstawowy modułu w procesie docelowym. COR_E_NOT_CLR zostanie zwrócony, jeśli określony moduł nie jest modułem CLR.  
  
 `pDataTarget`  
 [in] Abstrakcja docelowego danych, umożliwiający zarządzanego debugera sprawdzić stan procesu. Debuger musi implementować [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interfejsu. Należy zaimplementować [iclrdebugginglibraryprovider —](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md) interfejs na potrzeby obsługi scenariuszy, których CLR, która jest debugowany nie zainstalowano lokalnie na komputerze.  
  
 `pLibraryProvider`  
 [in] Biblioteka dostawcy wywołanie zwrotne interfejsu, który umożliwia bibliotek debugowania określonej wersji, należy odnaleźć i załadować na żądanie. Ten parametr jest wymagany tylko wtedy, gdy `ppProcess` lub `pFlags` nie jest `null`.  
  
 `pMaxDebuggerSupportedVersion`  
 [in] Najwyższa wersja środowiska CLR, która może debugować ten debuger. Należy określić głównych i pomocniczych i kompilacji wersji z najnowszej wersji środowiska CLR, który obsługuje ten debuger i ustawiony numer poprawki do 65535, aby zmieścił się w przyszłości CLR w miejscu obsługi wersji.  
  
 `riidProcess`  
 [in] Identyfikator interfejsu ICorDebugProcess do pobrania. Obecnie akceptowane wartości to wyłącznie są IID_CORDEBUGPROCESS3, IID_CORDEBUGPROCESS2 i IID_CORDEBUGPROCESS.  
  
 `ppProcess`  
 [out] Wskaźnik do interfejsu COM, który jest identyfikowany przez `riidProcess`.  
  
 `pVersion`  
 [w, out] Wersja środowiska CLR. W danych wejściowych, ta wartość może być `null`. Może także wskazywać [clr_debugging_version —](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-version-structure.md) struktury, w którym to przypadku struktury `wStructVersion` pola musi zostać zainicjowany jako 0 (zero).  
  
 W danych wyjściowych, zwracana `CLR_DEBUGGING_VERSION` struktury zostaną wypełnione informacje o wersji dla środowiska CLR.  
  
 `pdwFlags`  
 [out] Informacyjny flagi informacje o określonym środowisku uruchomieniowym. Zobacz [clr_debugging_process_flags —](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-process-flags-enumeration.md) temacie opis flag.  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca następujące określonych wyników HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|Metoda została ukończona pomyślnie.|  
|E_POINTER|`pDataTarget` jest `null`.|  
|CORDBG_E_LIBRARY_PROVIDER_ERROR|[Iclrdebugginglibraryprovider —](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md) wywołania zwrotnego zwraca błąd lub nie ma prawidłowego dojścia.|  
|CORDBG_E_MISSING_DATA_TARGET_INTERFACE|`pDataTarget` nie implementuje interfejsów docelowy wymagane dane dla tej wersji środowiska uruchomieniowego.|  
|CORDBG_E_NOT_CLR|Wskazany modułu nie jest modułem CLR. Ta wartość HRESULT jest także zwracany, jeśli nie można wykryć modułu CLR, ponieważ uszkodzona pamięć, moduł nie jest dostępna lub wersja środowiska CLR jest nowsza niż wersja podkładki.|  
|CORDBG_E_UNSUPPORTED_DEBUGGING_MODEL|Ta wersja środowiska uruchomieniowego nie obsługuje ten model debugowania. Obecnie model debugowania nie jest obsługiwany przez wersje CLR przed [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]. `pwszVersion` Parametr wyjściowy nadal jest ustawione na prawidłową wartość po tym błędzie.|  
|CORDBG_E_UNSUPPORTED_FORWARD_COMPAT|Wersja środowiska CLR jest nowsza niż wersja, ten debuger oświadczenia do obsługi. `pwszVersion` Parametr wyjściowy nadal jest ustawione na prawidłową wartość po tym błędzie.|  
|E_NO_INTERFACE|`riidProcess` Interfejs nie jest dostępny.|  
|CORDBG_E_UNSUPPORTED_VERSION_STRUCT|`CLR_DEBUGGING_VERSION` Struktury nie ma rozpoznawaną wartością dla `wStructVersion`. Wartość akceptowane tylko w tej chwili jest 0.|  
  
## <a name="exceptions"></a>Wyjątki  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Debugowanie](../../../../docs/framework/unmanaged-api/debugging/index.md)
