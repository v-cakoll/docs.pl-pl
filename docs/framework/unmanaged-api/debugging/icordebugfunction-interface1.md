---
title: ICorDebugFunction — Interfejs
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
ms.openlocfilehash: eb2b1e218314be01898ce90c4378fb713f9bf6ba
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137852"
---
# <a name="icordebugfunction-interface"></a>ICorDebugFunction — Interfejs

Reprezentuje zarządzaną funkcję lub metodę.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[CreateBreakpoint, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-createbreakpoint-method.md)|Tworzy punkt przerwania na początku tej funkcji.|  
|[GetClass, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getclass-method.md)|Pobiera obiekt ICorDebugClass, który reprezentuje klasę, do której należy ta funkcja.|  
|[GetCurrentVersionNumber, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getcurrentversionnumber-method.md)|Pobiera numer wersji najnowszej edycji wykonanej w tej funkcji.|  
|[GetILCode, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getilcode-method.md)|Pobiera kod języka pośredniego firmy Microsoft (MSIL) dla tej funkcji.|  
|[GetLocalVarSigToken, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getlocalvarsigtoken-method.md)|Pobiera token metadanych dla zmiennej lokalnej sygnatury funkcji reprezentowanej przez to wystąpienie `ICorDebugFunction`.|  
|[GetModule, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getmodule-method.md)|Pobiera moduł, w którym ta funkcja jest zdefiniowana.|  
|[GetNativeCode, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getnativecode-method.md)|Pobiera kod natywny dla tej funkcji.|  
|[GetToken, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-gettoken-method.md)|Pobiera token metadanych dla tej funkcji.|  
  
## <a name="remarks"></a>Uwagi  
 Interfejs `ICorDebugFunction` nie reprezentuje funkcji z parametrami typu ogólnego. Na przykład wystąpienie `ICorDebugFunction` reprezentuje `Func<T>`, ale nie `Func<string>`. Wywołaj metodę [ICorDebugILFrame2:: EnumerateTypeParameters —](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-enumeratetypeparameters-method.md) w celu pobrania parametrów typu ogólnego.  
  
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

- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
