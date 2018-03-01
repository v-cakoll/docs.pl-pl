---
title: "ICorDebugClass2::GetParameterizedType — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugClass2.GetParameterizedType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugClass2::GetParameterizedType
helpviewer_keywords:
- GetParameterizedType method [.NET Framework debugging]
- ICorDebugClass2::GetParameterizedType method [.NET Framework debugging]
ms.assetid: 94b591c4-9302-4af2-a510-089496afb036
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a9cbb755bd8f52482f7eece6e9d236f29cadc419
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugclass2getparameterizedtype-method"></a>ICorDebugClass2::GetParameterizedType — Metoda
Pobiera deklaracji typu dla tej klasy.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetParameterizedType (  
    [in] CorElementType                      elementType,  
    [in] ULONG32                             nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType  *ppTypeArgs[],  
    [out] ICorDebugType                    **ppType  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `elementType`  
 [in] Wartość wyliczenia CorElementType, która określa typ elementu dla tej klasy: Ustaw tę wartość na ELEMENT_TYPE_VALUETYPE, jeśli ta ICorDebugClass2 reprezentuje typ wartości. Ustaw tę wartość po elemencie ELEMENT_TYPE_CLASS, jeśli `ICorDebugClass2` reprezentuje typ złożony.  
  
 `nTypeArgs`  
 [in] Liczba parametrów typu, jeśli typ jest rodzajowy. Liczba parametrów typu (jeśli istnieją) muszą być zgodne numer wymagane przez klasę.  
  
 `ppTypeArgs`  
 [in] Tablicy wskaźników, z których każdy wskazuje obiekt ICorDebugType, który reprezentuje parametr typu. Jeśli klasa jest inny niż ogólny, ta wartość jest pusta.  
  
 `ppType`  
 [out] Wskaźnik do adresu `ICorDebugType` obiekt, który reprezentuje deklaracji typu. Ten obiekt jest odpowiednikiem <xref:System.Type> obiektu w kodzie zarządzanym.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli klasa nie jest ogólna, oznacza to, jeśli go nie ma typu parametrów, `GetParameterizedType` po prostu pobiera obiekt typu środowiska uruchomieniowego odpowiadającą klasę. `elementType` Parametr należy ustawić na typ elementu poprawne dla klasy: ELEMENT_TYPE_VALUETYPE, jeśli klasa jest typ wartości; w przeciwnym razie po elemencie ELEMENT_TYPE_CLASS.  
  
 Jeśli klasa akceptuje parametrów typu (na przykład `ArrayList<T>`), można użyć `GetParameterizedType` do utworzenia obiektu typu dla typu, takich jak `ArrayList<int>`.  
  
## <a name="background-information"></a>Informacje uzupełniające  
 W wersji systemu .NET Framework 1.0 i 1.1 co typ w metadanych można bezpośrednio zmapowana do typu w uruchomionym procesem. W związku z tym typem metadanych i typu środowiska uruchomieniowego miała pojedynczego reprezentacja w uruchomionego procesu. Jednak jeden typ rodzajowy w metadanych mogą być mapowane na wiele różnych wystąpień typu uruchomionego procesu. Na przykład typ metadanych `SortedList<K,V>` można mapować na `SortedList<String, EmployeeRecord>`, `SortedList<Int32, String>`, `SortedList<String,Array<Int32>>`i tak dalej. W związku z tym należy sposób obsługi podczas tworzenia wystąpienia typu.  
  
 .NET Framework w wersji 2.0 wprowadzono `ICorDebugType` interfejsu. Dla typu ogólnego `ICorDebugClass` lub `ICorDebugClass2` obiekt reprezentuje typ bez wystąpień (`SortedList<K,V>`), a `ICorDebugType` obiektu przedstawia różne typy skonkretyzowanym. Podane `ICorDebugClass` lub `ICorDebugClass2` obiektu, można utworzyć `ICorDebugType` obiekt do dowolnego wystąpienia przez wywołanie metody `ICorDebugClass2::GetParameterizedType` metody. Można również utworzyć `ICorDebugType` obiektu typu prostego, takie jak Int32, lub dla typu nieogólnego.  
  
 Wprowadzenie `ICorDebugType` obiekt do reprezentowania wykonawcze pojęcie typu ma wpływ w interfejsie API. Funkcje, które wcześniej miały `ICorDebugClass` lub `ICorDebugClass2` obiektu, a nawet `CorElementType` wartości zostały uogólnione podjęcie `ICorDebugType` obiektu.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
