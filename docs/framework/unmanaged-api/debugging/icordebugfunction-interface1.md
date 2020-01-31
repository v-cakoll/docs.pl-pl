---
title: ICorDebugFunction, interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugFunction
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction
helpviewer_keywords:
- ICorDebugFunction interface [.NET Framework debugging]
ms.assetid: 783faea9-8083-41c1-b04a-51a81ac4c8f3
topic_type:
- apiref
ms.openlocfilehash: ba0e0b1b2bac785e28f41e09dda74841121a748d
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794503"
---
# <a name="icordebugfunction-interface"></a>ICorDebugFunction, interfejs

Reprezentuje zarządzaną funkcję lub metodę.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[CreateBreakpoint, metoda](icordebugfunction-createbreakpoint-method.md)|Tworzy punkt przerwania na początku tej funkcji.|  
|[GetClass, metoda](icordebugfunction-getclass-method.md)|Pobiera obiekt ICorDebugClass, który reprezentuje klasę, do której należy ta funkcja.|  
|[GetCurrentVersionNumber, metoda](icordebugfunction-getcurrentversionnumber-method.md)|Pobiera numer wersji najnowszej edycji wykonanej w tej funkcji.|  
|[GetILCode, metoda](icordebugfunction-getilcode-method.md)|Pobiera kod języka pośredniego firmy Microsoft (MSIL) dla tej funkcji.|  
|[GetLocalVarSigToken, metoda](icordebugfunction-getlocalvarsigtoken-method.md)|Pobiera token metadanych dla zmiennej lokalnej sygnatury funkcji reprezentowanej przez to wystąpienie `ICorDebugFunction`.|  
|[GetModule, metoda](icordebugfunction-getmodule-method.md)|Pobiera moduł, w którym ta funkcja jest zdefiniowana.|  
|[GetNativeCode, metoda](icordebugfunction-getnativecode-method.md)|Pobiera kod natywny dla tej funkcji.|  
|[GetToken, metoda](icordebugfunction-gettoken-method.md)|Pobiera token metadanych dla tej funkcji.|  
  
## <a name="remarks"></a>Uwagi  
 Interfejs `ICorDebugFunction` nie reprezentuje funkcji z parametrami typu ogólnego. Na przykład wystąpienie `ICorDebugFunction` reprezentuje `Func<T>`, ale nie `Func<string>`. Wywołaj metodę [ICorDebugILFrame2:: EnumerateTypeParameters —](icordebugilframe2-enumeratetypeparameters-method.md) w celu pobrania parametrów typu ogólnego.  
  
 Relacja między tokenem metadanych metody, `mdMethodDef`i obiektem `ICorDebugFunction` metody jest zależna od tego, czy funkcja Edytuj i Kontynuuj jest dozwolona dla funkcji:  
  
- Jeśli funkcja Edytuj i Kontynuuj nie jest dozwolona w funkcji, istnieje relacja jeden do jednego między obiektem `ICorDebugFunction` a tokenem `mdMethodDef`. Oznacza to, że funkcja ma jeden `ICorDebugFunction` obiektu i jeden token `mdMethodDef`.  
  
- Jeśli funkcja Edytuj i Kontynuuj jest dozwolona w funkcji, istnieje relacja wiele-do-jednego między obiektem `ICorDebugFunction` a tokenem `mdMethodDef`. Oznacza to, że funkcja może mieć wiele wystąpień `ICorDebugFunction`, jeden dla każdej wersji funkcji, ale tylko jeden token `mdMethodDef`.  
  
> [!NOTE]
> Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:**  CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, interfejsy](debugging-interfaces.md)
