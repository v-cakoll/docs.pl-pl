---
title: ICorDebugType — Interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType
helpviewer_keywords:
- ICorDebugType interface [.NET Framework debugging]
ms.assetid: 94e02e31-67ea-4b00-8148-a46740a4571d
topic_type:
- apiref
ms.openlocfilehash: 4f3f553ed5dc93433610365e0dae5bee54863de5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129629"
---
# <a name="icordebugtype-interface"></a>ICorDebugType — Interfejs
Reprezentuje typ, podstawowy lub złożony (to jest zdefiniowany przez użytkownika). Jeśli typ jest ogólny, `ICorDebugType` reprezentuje typ ogólny wystąpienia.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[EnumerateTypeParameters, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-enumeratetypeparameters-method.md)|Pobiera wskaźnik interfejsu do ICorDebugTypeEnum, który odwołuje się do generycznych parametrów <xref:System.Type> klasy, do których odwołuje się ten `ICorDebugType`.|  
|[GetBase, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getbase-method.md)|Pobiera wskaźnik interfejsu do `ICorDebugType`, który odwołuje się do klasy bazowej klasy, do której odwołuje się ten `ICorDebugType`(jeśli taki istnieje).|  
|[GetClass, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getclass-method.md)|Pobiera wskaźnik interfejsu do elementu ICorDebugClass, który odwołuje się do określonego konstruktora tego `ICorDebugType`.|  
|[GetFirstTypeParameter, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getfirsttypeparameter-method.md)|Pobiera wskaźnik interfejsu do `ICorDebugType`, który odwołuje się do pierwszego generycznego parametru <xref:System.Type> dla konstruktora klasy, do której odwołuje się ten `ICorDebugType`.|  
|[GetRank, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getrank-method.md)|Pobiera liczbę wymiarów w typie tablicy.|  
|[GetStaticFieldValue, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getstaticfieldvalue-method.md)|Pobiera wskaźnik interfejsu do ICorDebugValue, który zawiera wartość pola statycznego, do którego odwołuje się określony token pola w określonej ramce stosu.|  
|[GetType, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md)|Pobiera wartość CorElementType —, która opisuje natywny typ środowiska <xref:System.Type> uruchomieniowego języka wspólnego, do którego odwołuje się ten `ICorDebugType`.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli typ jest ogólny, `ICorDebugClass` reprezentuje typ nieskonkretyzowany. Interfejs `ICorDebugType` reprezentuje typ ogólny skonkretyzowany. Na przykład, Hashtable\<K, V > byłaby reprezentowana przez `ICorDebugClass`, natomiast obiekt Hashtable\<Int32, ciąg > będzie reprezentowany przez `ICorDebugType`.  
  
 Typy inne niż ogólne są reprezentowane przez `ICorDebugClass` i `ICorDebugType`. Ten ostatni interfejs został wprowadzony w .NET Framework w wersji 2,0, aby można było zająć się tworzeniem wystąpienia typu.  
  
> [!NOTE]
> Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
