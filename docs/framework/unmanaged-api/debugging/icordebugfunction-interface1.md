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
ms.openlocfilehash: 6b7b6969c1f207decbf47217e98b7fee3aa9ce54
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213247"
---
# <a name="icordebugfunction-interface"></a>ICorDebugFunction, interfejs

Reprezentuje zarządzaną funkcję lub metodę.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[CreateBreakpoint — Metoda](icordebugfunction-createbreakpoint-method.md)|Tworzy punkt przerwania na początku tej funkcji.|  
|[GetClass, metoda](icordebugfunction-getclass-method.md)|Pobiera obiekt ICorDebugClass, który reprezentuje klasę, do której należy ta funkcja.|  
|[GetCurrentVersionNumber, metoda](icordebugfunction-getcurrentversionnumber-method.md)|Pobiera numer wersji najnowszej edycji wykonanej w tej funkcji.|  
|[GetILCode, metoda](icordebugfunction-getilcode-method.md)|Pobiera kod języka pośredniego firmy Microsoft (MSIL) dla tej funkcji.|  
|[GetLocalVarSigToken — Metoda](icordebugfunction-getlocalvarsigtoken-method.md)|Pobiera token metadanych dla zmiennej lokalnej sygnatury funkcji reprezentowanej przez to `ICorDebugFunction` wystąpienie.|  
|[GetModule — Metoda](icordebugfunction-getmodule-method.md)|Pobiera moduł, w którym ta funkcja jest zdefiniowana.|  
|[GetNativeCode, metoda](icordebugfunction-getnativecode-method.md)|Pobiera kod natywny dla tej funkcji.|  
|[GetToken — Metoda](icordebugfunction-gettoken-method.md)|Pobiera token metadanych dla tej funkcji.|  
  
## <a name="remarks"></a>Uwagi  
 `ICorDebugFunction`Interfejs nie reprezentuje funkcji z parametrami typu ogólnego. Na przykład `ICorDebugFunction` wystąpienie może reprezentować, `Func<T>` ale nie `Func<string>` . Wywołaj metodę [ICorDebugILFrame2:: EnumerateTypeParameters —](icordebugilframe2-enumeratetypeparameters-method.md) w celu pobrania parametrów typu ogólnego.  
  
 Relacja między tokenem metadanych metody `mdMethodDef` a `ICorDebugFunction` obiektem metody jest zależna od tego, czy funkcja Edytuj i Kontynuuj jest dozwolona dla funkcji:  
  
- Jeśli funkcja Edytuj i Kontynuuj nie jest dozwolona w funkcji, istnieje relacja jeden do jednego między `ICorDebugFunction` obiektem a `mdMethodDef` tokenem. Oznacza to, że funkcja ma jeden `ICorDebugFunction` obiekt i jeden `mdMethodDef` token.  
  
- Jeśli funkcja Edytuj i Kontynuuj jest dozwolona w funkcji, istnieje relacja wiele-do-jednego między `ICorDebugFunction` obiektem a `mdMethodDef` tokenem. Oznacza to, że funkcja może mieć wiele wystąpień `ICorDebugFunction` , jeden dla każdej wersji funkcji, ale tylko jeden `mdMethodDef` token.  
  
> [!NOTE]
> Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:**  CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Debugowanie — Interfejsy](debugging-interfaces.md)
