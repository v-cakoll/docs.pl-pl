---
title: ICorDebugType Interface1
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
ms.openlocfilehash: d29ab3c67e0788b15850b7dfb8b55914c1d1e369
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54694532"
---
# <a name="icordebugtype-interface1"></a>ICorDebugType Interface1
Reprezentuje typ podstawowy lub złożony (zdefiniowany przez użytkownika). Jeśli typ ogólny, `ICorDebugType` reprezentuje typ ogólny z wystąpieniami.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[EnumerateTypeParameters, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-enumeratetypeparameters-method.md)|Pobiera wskaźnik interfejsu do icordebugtypeenum —, który odwołuje się do ogólnego <xref:System.Type> parametrów klasy przywoływane przez to `ICorDebugType`.|  
|[GetBase, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getbase-method.md)|Pobiera wskaźnik interfejsu do `ICorDebugType` odwołujący się klasę bazową klasy przywoływane przez to `ICorDebugType`, jeśli taka istnieje.|  
|[GetClass, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getclass-method.md)|Pobiera wskaźnik interfejsu do ICorDebugClass, który odwołuje się do konstruktora wpisane `ICorDebugType`.|  
|[GetFirstTypeParameter, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getfirsttypeparameter-method.md)|Pobiera wskaźnik interfejsu do `ICorDebugType` odwołujący się pierwszy ogólny <xref:System.Type> parametr dla konstruktora klasy przywoływane przez to `ICorDebugType`.|  
|[GetRank, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getrank-method.md)|Pobiera liczbę wymiarów typu tablicowego.|  
|[GetStaticFieldValue, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getstaticfieldvalue-method.md)|Pobiera token w ramce stosu określony wskaźnik interfejsu do ICorDebugValue, który zawiera wartość pola statycznego odwołuje się określone pole.|  
|[GetType, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md)|Pobiera wartość corelementtype —, która opisuje typ macierzysty środowiska uruchomieniowego języka wspólnego <xref:System.Type> przywoływane przez to `ICorDebugType`.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli typ ogólny, `ICorDebugClass` reprezentuje typ bez wystąpień. `ICorDebugType` Interfejs reprezentuje typ ogólny. Na przykład tablica skrótów\<K, V > jest przedstawiany przez `ICorDebugClass`, podczas gdy tabela skrótów\<Int32, String > jest przedstawiany przez `ICorDebugType`.  
  
 Typy nieuniwersalne są reprezentowane przez oba `ICorDebugClass` i `ICorDebugType`. Ostatnie interfejsu została wprowadzona w .NET Framework w wersji 2.0 radzenia sobie z podczas tworzenia wystąpienia typu.  
  
> [!NOTE]
>  Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
