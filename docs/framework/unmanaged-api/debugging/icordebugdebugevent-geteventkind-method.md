---
title: Metoda ICorDebugDebugEvent::GetEventKind
ms.date: 03/30/2017
ms.assetid: c37aaceb-c948-46bd-a943-08be4cbb76f4
ms.openlocfilehash: 6e3ebdcb5b3e85f6f5a329ed249aa58be903e30f
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976398"
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
 Wskaźnik do elementu członkowskiego wyliczenia [CorDebugDebugEventKind](cordebugdebugeventkind-enumeration.md) , który wskazuje typ zdarzenia.  
  
## <a name="remarks"></a>Uwagi  
 Na podstawie wartości `pDebugEventKind`, można wywołać `QueryInterface` , aby uzyskać dokładniejszy interfejs zdarzenia debugowania, który zawiera dodatkowe dane.  
  
> [!NOTE]
> Ta metoda jest dostępna tylko z .NET Native.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Interfejs ICorDebugDebugEvent](icordebugdebugevent-interface.md)
- [Debugowanie — Interfejsy](debugging-interfaces.md)
