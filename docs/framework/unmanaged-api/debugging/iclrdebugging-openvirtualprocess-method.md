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
ms.openlocfilehash: a313ea62455067fb36b94d942b0ce21589677e3b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61698164"
---
# <a name="iclrdebuggingopenvirtualprocess-method"></a>ICLRDebugging::OpenVirtualProcess — Metoda
Pobiera icordebugprocess — interfejs, który odnosi się do wspólnego języka wspólnego (CLR) moduł załadowany w procesie.  
  
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
  
## <a name="parameters"></a>Parametry  
 `moduleBaseAddress`  
 [in] Adres podstawowy moduł w procesie docelowym. COR_E_NOT_CLR zostanie zwrócona, jeśli określony moduł nie jest modułem środowiska CLR.  
  
 `pDataTarget`  
 [in] Abstrakcja docelowego danych, umożliwiająca zarządzanego debugera sprawdzić stan procesu. Debuger musi implementować [icordebugdatatarget —](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interfejsu. Należy zaimplementować [iclrdebugginglibraryprovider —](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md) interfejsu do obsługi scenariuszy, w których CLR, która jest debugowana nie zainstalowano lokalnie na komputerze.  
  
 `pLibraryProvider`  
 [in] Biblioteka dostawcy interfejs wywołania zwrotnego, która umożliwia bibliotekom debudowania określonych wersji lokalizowanie i ładowanie na żądanie. Ten parametr jest wymagany tylko wtedy, gdy `ppProcess` lub `pFlags` nie `null`.  
  
 `pMaxDebuggerSupportedVersion`  
 [in] Najnowsza wersja środowiska CLR, który można debugować ten debuger. Należy określić głównych i pomocniczych i tworzenia wersji z najnowszej wersji środowiska CLR, który obsługuje ten debuger i ustawić numer poprawki do 65535, aby pomieścić przyszłych CLR w miejscu, obsługi wersji.  
  
 `riidProcess`  
 [in] Identyfikator icordebugprocess — interfejs do pobrania. Obecnie tylko akceptowane wartości są IID_CORDEBUGPROCESS3 IID_CORDEBUGPROCESS2 i IID_CORDEBUGPROCESS.  
  
 `ppProcess`  
 [out] Wskaźnik do interfejsu COM, który jest identyfikowany przez `riidProcess`.  
  
 `pVersion`  
 [out w] Wersja środowiska CLR. W danych wejściowych, ta wartość może być `null`. Może też wskazywać na [clr_debugging_version —](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-version-structure.md) strukturę, w którym to przypadku struktury `wStructVersion` pola musi zostać zainicjowany do 0 (zero).  
  
 W danych wyjściowych, zwrócony `CLR_DEBUGGING_VERSION` struktury zostanie wypełniona informacje o wersji dla środowiska CLR.  
  
 `pdwFlags`  
 [out] Flagi informacyjne dotyczące określonego środowiska uruchomieniowego. Zobacz [clr_debugging_process_flags —](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-process-flags-enumeration.md) tematu, aby uzyskać opis flag.  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca następujące specyficzne wyniki HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|Metoda została ukończona pomyślnie.|  
|E_POINTER|`pDataTarget` jest `null`.|  
|CORDBG_E_LIBRARY_PROVIDER_ERROR|[Iclrdebugginglibraryprovider —](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md) wywołania zwrotnego zwraca błąd lub nie zawiera prawidłowego uchwytu.|  
|CORDBG_E_MISSING_DATA_TARGET_INTERFACE|`pDataTarget` nie implementuje interfejsy docelowym wymagane dane dla tej wersji środowiska uruchomieniowego.|  
|CORDBG_E_NOT_CLR|Wskazany modułu nie jest modułem środowiska CLR. Ta wartość HRESULT jest także zwracany, jeśli nie można wykryć moduł CLR, ponieważ została uszkodzona pamięć, moduł nie jest dostępna lub wersja środowiska CLR jest nowsza niż wersja podkładki.|  
|CORDBG_E_UNSUPPORTED_DEBUGGING_MODEL|Ta wersja środowiska uruchomieniowego nie obsługuje debugowania modelu. Obecnie debugowania model nie jest obsługiwany przez wersje środowiska CLR przed [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]. `pwszVersion` Parametru wyjściowego nadal jest ustawione na prawidłową wartość po tym błędzie.|  
|CORDBG_E_UNSUPPORTED_FORWARD_COMPAT|Wersja środowiska CLR jest nowsza niż wersja, ten debuger oświadczenia do obsługi. `pwszVersion` Parametru wyjściowego nadal jest ustawione na prawidłową wartość po tym błędzie.|  
|E_NO_INTERFACE|`riidProcess` Interfejs nie jest dostępny.|  
|CORDBG_E_UNSUPPORTED_VERSION_STRUCT|`CLR_DEBUGGING_VERSION` Struktura ma rozpoznawaną wartością dla `wStructVersion`. To jedyna wartość zaakceptowane w tej chwili to 0.|  
  
## <a name="exceptions"></a>Wyjątki  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Debugowanie](../../../../docs/framework/unmanaged-api/debugging/index.md)
