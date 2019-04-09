---
title: Metoda ICorDebugDebugEvent::GetEventKind
ms.date: 03/30/2017
ms.assetid: c37aaceb-c948-46bd-a943-08be4cbb76f4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 62eede48eea01563dbc3e170720694a24343d0a5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59150530"
---
# <a name="icordebugdebugeventgeteventkind-method"></a>Metoda ICorDebugDebugEvent::GetEventKind
Wskazuje rodzaj zdarzeń, to `ICorDebugDebugEvent` obiekt reprezentuje.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetEventKind(  
    [out]CorDebugDebugEventKind *pDebugEventKind  
);  
```  
  
## <a name="parameters"></a>Parametry  
 pDebugEventKind  
 Wskaźnik do [CorDebugDebugEventKind](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) składowej wyliczenia, która określa typ zdarzenia.  
  
## <a name="remarks"></a>Uwagi  
 Na podstawie wartości z `pDebugEventKind`, można wywołać `QueryInterface` uzyskanie bardziej precyzyjne interfejsu zdarzenia debugowania, która zawiera dane dodatkowe.  
  
> [!NOTE]
>  Ta metoda jest tylko dostępne z architekturą .NET Native.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Interfejs ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md)
- [Debugowanie — Interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
