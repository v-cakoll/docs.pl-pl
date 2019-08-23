---
title: ICorDebugType, interfejs
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b830af5d59c0eb177d815451ecedbdc14121aaad
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964762"
---
# <a name="icordebugtype-interface"></a>ICorDebugType, interfejs
Reprezentuje typ, podstawowy lub złożony (to jest zdefiniowany przez użytkownika). Jeśli typ jest ogólny, `ICorDebugType` reprezentuje typ ogólny wystąpienia.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[EnumerateTypeParameters, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-enumeratetypeparameters-method.md)|Pobiera wskaźnik interfejsu do ICorDebugTypeEnum, który odwołuje się do <xref:System.Type> parametrów ogólnych klasy, do których odwołuje się to. `ICorDebugType`|  
|[GetBase, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getbase-method.md)|Pobiera wskaźnik interfejsu do obiektu `ICorDebugType` , który odwołuje się do klasy bazowej klasy, do której odwołuje się ten `ICorDebugType`element, jeśli taki istnieje.|  
|[GetClass, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getclass-method.md)|Pobiera wskaźnik interfejsu do ICorDebugClass, który odwołuje się do określonego konstruktora `ICorDebugType`.|  
|[GetFirstTypeParameter, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getfirsttypeparameter-method.md)|Pobiera wskaźnik interfejsu do obiektu `ICorDebugType` , który odwołuje się do pierwszego parametru generycznego <xref:System.Type> konstruktora klasy, do której odwołuje się to `ICorDebugType`.|  
|[GetRank, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getrank-method.md)|Pobiera liczbę wymiarów w typie tablicy.|  
|[GetStaticFieldValue, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getstaticfieldvalue-method.md)|Pobiera wskaźnik interfejsu do ICorDebugValue, który zawiera wartość pola statycznego, do którego odwołuje się określony token pola w określonej ramce stosu.|  
|[GetType, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md)|Pobiera wartość CorElementType —, która opisuje typ natywny środowiska uruchomieniowego <xref:System.Type> języka wspólnego, do którego odwołuje się ten `ICorDebugType`element.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli typ jest ogólny, `ICorDebugClass` reprezentuje typ nieskonkretyzowany. `ICorDebugType` Interfejs reprezentuje typ ogólny skonkretyzowany. Na przykład, obiekt\<Hashtable K, > będzie reprezentowany przez `ICorDebugClass`, natomiast obiekt Hashtable\<Int32, ciąg > być reprezentowany przez `ICorDebugType`.  
  
 Typy inne niż ogólne są reprezentowane przez `ICorDebugClass` i. `ICorDebugType` Ten ostatni interfejs został wprowadzony w .NET Framework w wersji 2,0, aby można było zająć się tworzeniem wystąpienia typu.  
  
> [!NOTE]
> Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.  
  
## <a name="requirements"></a>Wymagania  
 **Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówki** CorDebug.idl, CorDebug.h  
  
 **Biblioteki** CorGuids.lib  
  
 **.NET Framework wersje:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
