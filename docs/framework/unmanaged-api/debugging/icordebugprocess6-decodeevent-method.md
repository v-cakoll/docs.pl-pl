---
title: Metoda ICorDebugProcess6::DecodeEvent
ms.date: 03/30/2017
ms.assetid: 1453bc0c-6e0d-4d5a-b176-22607f8a3e6c
ms.openlocfilehash: a0b77724a5a70461073d554a9794c5a904f6a363
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178580"
---
# <a name="icordebugprocess6decodeevent-method"></a>Metoda ICorDebugProcess6::DecodeEvent
Dekoduje zarządzane zdarzenia debugowania, które zostały zhermetyzowane w ładunku specjalnie spreparowanych zdarzeń debugowania wyjątków natywnych.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT DecodeEvent(  
        [in, length_is(countBytes), size_is(countBytes)]  const BYTE pRecord[],  
        [in] DWORD countBytes,  
        [in] CorDebugRecordFormat format,  
        [in] DWORD dwFlags,
        [in] DWORD dwThreadId,
        [out] ICorDebugDebugEvent **ppEvent  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pRecord`  
 [w] Wskaźnik do tablicy bajtów ze zdarzenia debugowania wyjątku macierzystego, który zawiera informacje o zdarzeniu zarządzanym debugowania.  
  
 `countBytes`  
 [w] Liczba elementów w `pRecord` tablicy bajtów.  
  
 `format`  
 [w] A [CorDebugRecordFormat](cordebugrecordformat-enumeration.md) element członkowski wyliczenia, który określa format zdarzenia debugowania niezarządzane.  
  
 `dwFlags`  
 [w] Pole bitowe, które zależy od architektury docelowej i które określa dodatkowe informacje o zdarzeniu debugowania. W przypadku systemów Windows może być członkiem [wyliczenia CorDebugDecodeEventFlagsWindows.](cordebugdecodeeventflagswindows-enumeration.md)  
  
 `dwThreadId`  
 [w] Identyfikator systemu operacyjnego wątku, w którym został zgłoszony wyjątek.  
  
 `ppEvent`  
 [na zewnątrz] Wskaźnik do adresu obiektu [ICorDebugDebugEvent,](icordebugdebugevent-interface.md) który reprezentuje zdekodowane zdarzenie debugowania zarządzanego.  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
> Ta metoda jest dostępna tylko w przypadku platformy .NET Native.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [ICorDebugProcess6, interfejs](icordebugprocess6-interface.md)
- [Debugowanie — Interfejsy](debugging-interfaces.md)
