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
ms.openlocfilehash: 5f731b1459542c3f5378790b21f2ea576e89ad97
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82893341"
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
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [ICorDebugCode4, interfejs](icordebugcode4-interface.md)
- [Debugowanie — Interfejsy](debugging-interfaces.md)
