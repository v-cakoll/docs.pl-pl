---
title: Metoda ICorDebugProcess6::DecodeEvent
ms.date: 03/30/2017
ms.assetid: 1453bc0c-6e0d-4d5a-b176-22607f8a3e6c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dc5c90cf5006763a84ddc891b9a011dc6cfbe754
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54738290"
---
# <a name="icordebugprocess6decodeevent-method"></a>Metoda ICorDebugProcess6::DecodeEvent
Dekoduje zdarzenia debugowania zarządzanego, które zostały hermetyzowane w ładunku zdarzenia debugowania specjalnie przygotowane natywnych wyjątek.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT DecodeEvent(  
        [in, length_is(countBytes), size_is(countBytes)]  const BYTE pRecord[],  
        [in] DWORD countBytes,  
        [in] CorDebugRecordFormat format,  
        [in] DWORD dwFlags,   
        [in] DWORD dwThreadId,   
        [out] ICorDebugDebugEvent **ppEvent  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pRecord`  
 [in] Wskaźnik do tablicy typu byte ze zdarzenia debugowania natywnych wyjątek zawierającą informacje o zdarzeniu debugowania zarządzanego.  
  
 `countBytes`  
 [in] Liczba elementów w `pRecord` tablicy bajtów.  
  
 `format`  
 [in] A [CorDebugRecordFormat](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md) składowej wyliczenia, która określa format zdarzenia debugowania niezarządzanego.  
  
 `dwFlags`  
 [in] Pole bitowe, która jest zależna od architektury docelowej oraz określa dodatkowe informacje na temat zdarzeń debugowania. Dla systemów Windows, może być członkiem [CorDebugDecodeEventFlagsWindows](../../../../docs/framework/unmanaged-api/debugging/cordebugdecodeeventflagswindows-enumeration.md) wyliczenia.  
  
 `dwThreadId`  
 [in] Identyfikator systemu operacyjnego wątku, na którym wystąpił wyjątek.  
  
 `ppEvent`  
 [out] Wskaźnik na adres [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) obiekt, który reprezentuje zdarzenie zdekodowany debugowania zarządzanego.  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  Ta metoda jest tylko dostępne z architekturą .NET Native.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [ICorDebugProcess6, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)
- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
