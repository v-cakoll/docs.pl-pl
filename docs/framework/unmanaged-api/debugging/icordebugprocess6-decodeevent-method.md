---
title: Metoda ICorDebugProcess6::DecodeEvent
ms.date: 03/30/2017
ms.assetid: 1453bc0c-6e0d-4d5a-b176-22607f8a3e6c
ms.openlocfilehash: be30b1ff79c2aceb97eb4ad42052da7dd162f5d3
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792282"
---
# <a name="icordebugprocess6decodeevent-method"></a>Metoda ICorDebugProcess6::DecodeEvent
Dekoduje zarządzane zdarzenia debugowania, które zostały hermetyzowane w ładunku specjalnie spreparowanych zdarzeń debugowania wyjątku natywnego.  
  
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
 podczas Wskaźnik do tablicy bajtów z natywnego zdarzenia debugowania wyjątku, który zawiera informacje o zarządzanym zdarzeniu debugowania.  
  
 `countBytes`  
 podczas Liczba elementów w tablicy `pRecord` bajtowej.  
  
 `format`  
 podczas Element członkowski wyliczenia [CorDebugRecordFormat](cordebugrecordformat-enumeration.md) , który określa format niezarządzanego zdarzenia debugowania.  
  
 `dwFlags`  
 podczas Pole bitowe, które zależy od architektury docelowej i określające dodatkowe informacje o zdarzeniu debugowania. W przypadku systemów Windows może być elementem członkowskim wyliczenia [CorDebugDecodeEventFlagsWindows](cordebugdecodeeventflagswindows-enumeration.md) .  
  
 `dwThreadId`  
 podczas Identyfikator systemu operacyjnego wątku, w którym został zgłoszony wyjątek.  
  
 `ppEvent`  
 określoną Wskaźnik do adresu obiektu [ICorDebugDebugEvent](icordebugdebugevent-interface.md) , który reprezentuje zdekodowane zdarzenie debugowania zarządzane.  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
> Ta metoda jest dostępna tylko z .NET Native.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugProcess6, interfejs](icordebugprocess6-interface.md)
- [Debugowanie, interfejsy](debugging-interfaces.md)
