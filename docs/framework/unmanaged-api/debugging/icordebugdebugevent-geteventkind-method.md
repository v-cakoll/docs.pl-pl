---
title: Metoda ICorDebugDebugEvent::GetEventKind
ms.date: 03/30/2017
ms.assetid: c37aaceb-c948-46bd-a943-08be4cbb76f4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a87dda8d8a263df1989a685d94c5163212f41382
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69911338"
---
# <a name="icordebugdebugeventgeteventkind-method"></a>Metoda ICorDebugDebugEvent::GetEventKind
Wskazuje, jaki rodzaj zdarzenia reprezentuje `ICorDebugDebugEvent` ten obiekt.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetEventKind(  
    [out]CorDebugDebugEventKind *pDebugEventKind  
);  
```  
  
## <a name="parameters"></a>Parametry  
 pDebugEventKind  
 Wskaźnik do elementu członkowskiego wyliczenia [CorDebugDebugEventKind](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) , który wskazuje typ zdarzenia.  
  
## <a name="remarks"></a>Uwagi  
 Na podstawie wartości `pDebugEventKind`, można wywołać `QueryInterface` , aby uzyskać dokładniejszy interfejs zdarzenia debugowania, który zawiera dodatkowe dane.  
  
> [!NOTE]
> Ta metoda jest dostępna tylko z .NET Native.  
  
## <a name="requirements"></a>Wymagania  
 **Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówki** CorDebug.idl, CorDebug.h  
  
 **Biblioteki** CorGuids.lib  
  
 **.NET Framework wersje:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugDebugEvent, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md)
- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
