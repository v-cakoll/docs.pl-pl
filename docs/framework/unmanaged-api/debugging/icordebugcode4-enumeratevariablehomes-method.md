---
title: 'ICorDebugCode4:: EnumerateVariableHomes, Metoda'
ms.date: 03/30/2017
api_name:
- ICorDebugCode4.EnumerateVariableHomes
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode4::EnumerateVariableHomes
helpviewer_keywords:
- EnumerateVariableHomes method [.NET Framework debugging]
- ICorDebugCode4::EnumerateVariableHomes method [.NET Framework debugging]
ms.assetid: 802c01ff-8b80-4733-b6dd-03ab6ff7fa11
topic_type:
- apiref
ms.openlocfilehash: ca452b230e2508f2d69c9aa38f274db506f3a906
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76784088"
---
# <a name="icordebugcode4enumeratevariablehomes-method"></a>ICorDebugCode4:: EnumerateVariableHomes, Metoda
Pobiera moduł wyliczający do zmiennych lokalnych i argumentów w funkcji.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT EnumerateVariableHomes(  
    [out] ICorDebugVariableHomeEnum **ppEnum  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppEnum`  
 Wskaźnik do adresu obiektu interfejsu [ICorDebugVariableHomeEnum](icordebugvariablehomeenum-interface.md) , który jest modułem wyliczającym dla zmiennych lokalnych i argumentów w funkcji.  
  
## <a name="remarks"></a>Uwagi  
 Obiekt interfejsu [ICorDebugVariableHomeEnum](icordebugvariablehomeenum-interface.md) to standardowy moduł wyliczający pochodzący z interfejsu "ICorDebugEnum", który umożliwia Wyliczenie obiektów [ICorDebugVariableHome](icordebugvariablehome-interface.md) . Kolekcja może zawierać wiele obiektów [ICorDebugVariableHome](icordebugvariablehome-interface.md) dla tego samego miejsca lub indeksu argumentów, jeśli mają różne domy w różnych punktach w funkcji.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugCode4, interfejs](icordebugcode4-interface.md)
- [Debugowanie, interfejsy](debugging-interfaces.md)
