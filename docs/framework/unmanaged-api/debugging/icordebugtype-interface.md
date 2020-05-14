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
ms.openlocfilehash: 5e88652ff75223e30e6abc454f1e1af91494c7b2
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396700"
---
# <a name="icordebugtype-interface"></a>ICorDebugType, interfejs
Reprezentuje typ, podstawowy lub złożony (to jest zdefiniowany przez użytkownika). Jeśli typ jest ogólny, `ICorDebugType` reprezentuje typ ogólny wystąpienia.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[EnumerateTypeParameters, metoda](icordebugtype-enumeratetypeparameters-method.md)|Pobiera wskaźnik interfejsu do ICorDebugTypeEnum, który odwołuje się do <xref:System.Type> parametrów ogólnych klasy, do których odwołuje się to `ICorDebugType` .|  
|[GetBase, metoda](icordebugtype-getbase-method.md)|Pobiera wskaźnik interfejsu do obiektu `ICorDebugType` , który odwołuje się do klasy bazowej klasy, do której odwołuje się ten element `ICorDebugType` , jeśli taki istnieje.|  
|[GetClass, metoda](icordebugtype-getclass-method.md)|Pobiera wskaźnik interfejsu do ICorDebugClass, który odwołuje się do określonego konstruktora `ICorDebugType` .|  
|[GetFirstTypeParameter, metoda](icordebugtype-getfirsttypeparameter-method.md)|Pobiera wskaźnik interfejsu do obiektu `ICorDebugType` , który odwołuje się do pierwszego parametru generycznego <xref:System.Type> konstruktora klasy, do której odwołuje się to `ICorDebugType` .|  
|[GetRank — Metoda](icordebugtype-getrank-method.md)|Pobiera liczbę wymiarów w typie tablicy.|  
|[GetStaticFieldValue, metoda](icordebugtype-getstaticfieldvalue-method.md)|Pobiera wskaźnik interfejsu do ICorDebugValue, który zawiera wartość pola statycznego, do którego odwołuje się określony token pola w określonej ramce stosu.|  
|[GetType, metoda](icordebugtype-gettype-method.md)|Pobiera wartość CorElementType —, która opisuje typ natywny środowiska uruchomieniowego języka wspólnego, <xref:System.Type> do którego odwołuje się ten element `ICorDebugType` .|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli typ jest ogólny, `ICorDebugClass` reprezentuje typ nieskonkretyzowany. `ICorDebugType`Interfejs reprezentuje typ ogólny skonkretyzowany. Na przykład, obiekt Hashtable \< K,> będzie reprezentowany przez `ICorDebugClass` , natomiast obiekt Hashtable \< Int32, ciąg> być reprezentowany przez `ICorDebugType` .  
  
 Typy inne niż ogólne są reprezentowane przez `ICorDebugClass` i `ICorDebugType` . Ten ostatni interfejs został wprowadzony w .NET Framework w wersji 2,0, aby można było zająć się tworzeniem wystąpienia typu.  
  
> [!NOTE]
> Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie — Interfejsy](debugging-interfaces.md)
