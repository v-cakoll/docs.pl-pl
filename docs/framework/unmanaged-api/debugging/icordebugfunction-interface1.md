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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ae65c59efe1d925b5e058e8664d1e093fdfec875
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917209"
---
# <a name="icordebugfunction-interface"></a>ICorDebugFunction, interfejs

Reprezentuje zarządzaną funkcję lub metodę.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[CreateBreakpoint, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-createbreakpoint-method.md)|Tworzy punkt przerwania na początku tej funkcji.|  
|[GetClass, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getclass-method.md)|Pobiera obiekt ICorDebugClass, który reprezentuje klasę, do której należy ta funkcja.|  
|[GetCurrentVersionNumber, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getcurrentversionnumber-method.md)|Pobiera numer wersji najnowszej edycji wykonanej w tej funkcji.|  
|[GetILCode, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getilcode-method.md)|Pobiera kod języka pośredniego firmy Microsoft (MSIL) dla tej funkcji.|  
|[GetLocalVarSigToken, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getlocalvarsigtoken-method.md)|Pobiera token metadanych dla zmiennej lokalnej sygnatury funkcji reprezentowanej przez to `ICorDebugFunction` wystąpienie.|  
|[GetModule, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getmodule-method.md)|Pobiera moduł, w którym ta funkcja jest zdefiniowana.|  
|[GetNativeCode, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getnativecode-method.md)|Pobiera kod natywny dla tej funkcji.|  
|[GetToken, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-gettoken-method.md)|Pobiera token metadanych dla tej funkcji.|  
  
## <a name="remarks"></a>Uwagi  
 `ICorDebugFunction` Interfejs nie reprezentuje funkcji z parametrami typu ogólnego. Na przykład `ICorDebugFunction` wystąpienie może reprezentować `Func<T>` , ale `Func<string>`nie. Wywołaj metodę [ICorDebugILFrame2:: EnumerateTypeParameters —](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-enumeratetypeparameters-method.md) w celu pobrania parametrów typu ogólnego.  
  
 Relacja między tokenem `mdMethodDef`metadanych metody a `ICorDebugFunction` obiektem metody jest zależna od tego, czy funkcja Edytuj i Kontynuuj jest dozwolona dla funkcji:  
  
- Jeśli funkcja Edytuj i Kontynuuj nie jest dozwolona w funkcji, istnieje relacja jeden do jednego między `ICorDebugFunction` obiektem `mdMethodDef` a tokenem. Oznacza to, że funkcja ma jeden `ICorDebugFunction` obiekt i jeden `mdMethodDef` token.  
  
- Jeśli funkcja Edytuj i Kontynuuj jest dozwolona w funkcji, istnieje relacja wiele-do-jednego między `ICorDebugFunction` obiektem `mdMethodDef` a tokenem. Oznacza to, że funkcja może mieć wiele wystąpień `ICorDebugFunction`, jeden dla każdej wersji funkcji, ale tylko jeden `mdMethodDef` token.  
  
> [!NOTE]
> Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.  
  
## <a name="requirements"></a>Wymagania  
 **Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówki** CorDebug.idl, CorDebug.h  
  
 **Biblioteki**  CorGuids.lib  
  
 **.NET Framework wersje:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
