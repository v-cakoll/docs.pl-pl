---
title: ICorDebugClass2::GetParameterizedType — Metoda
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1bfc503bfc2b278d7a7344b94cb089cd8e019890
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67747768"
---
# <a name="icordebugclass2getparameterizedtype-method"></a>ICorDebugClass2::GetParameterizedType — Metoda
Pobiera deklaracji typu dla tej klasy.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetParameterizedType (  
    [in] CorElementType                      elementType,  
    [in] ULONG32                             nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType  *ppTypeArgs[],  
    [out] ICorDebugType                    **ppType  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `elementType`  
 [in] Wartość corelementtype — wyliczenie, który określa typ elementu dla tej klasy: Ta wartość ELEMENT_TYPE_VALUETYPE Jeśli ta icordebugclass2 — reprezentuje typ wartości. Ustaw tę wartość na ELEMENT_TYPE_CLASS, jeśli `ICorDebugClass2` reprezentuje typ złożony.  
  
 `nTypeArgs`  
 [in] Liczba parametrów typu, w przypadku typu ogólnego. Liczba parametrów typu (jeśli istnieje) musi być zgodna liczbę wymaganych przez klasę.  
  
 `ppTypeArgs`  
 [in] Tablica wskaźników, z których każdy wskazuje na obiekt ICorDebugType, który reprezentuje parametr typu. Jeśli klasa jest nieogólnego, ta wartość ma wartość null.  
  
 `ppType`  
 [out] Wskaźnik na adres `ICorDebugType` obiekt, który reprezentuje deklaracji typu. Ten obiekt jest odpowiednikiem <xref:System.Type> obiektu w kodzie zarządzanym.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli klasa nieogólnego, oznacza to, jeśli go nie ma parametrów typu, `GetParameterizedType` po prostu pobiera obiekt typu środowiska uruchomieniowego, odpowiadający tej klasy. `elementType` Parametr powinien być ustawiony na typ elementu poprawne dla klasy: ELEMENT_TYPE_VALUETYPE, jeśli klasa jest typem wartości w przeciwnym razie ELEMENT_TYPE_CLASS.  
  
 Jeśli klasa akceptuje parametry typu (na przykład `ArrayList<T>`), możesz użyć `GetParameterizedType` do konstruowania na obiekt typu dla typu wystąpień, takie jak `ArrayList<int>`.  
  
## <a name="background-information"></a>Informacje uzupełniające  
 W wersjach programu .NET Framework 1.0 i 1.1 Każdy typ w metadanych może być bezpośrednio zmapowana do typu w uruchomionego procesu. W związku z tym typ metadanych i typ środowiska uruchomieniowego w kończyły się jednym reprezentacji uruchomionego procesu. Jednak pierwszego typu ogólnego w metadanych można mapować do wielu inne realizacje typu w uruchomionego procesu. Na przykład typ metadanych `SortedList<K,V>` można mapować na `SortedList<String, EmployeeRecord>`, `SortedList<Int32, String>`, `SortedList<String,Array<Int32>>`i tak dalej. Dlatego należy sposób obsługi podczas tworzenia wystąpienia typu.  
  
 .NET Framework w wersji 2.0 wprowadzono `ICorDebugType` interfejsu. Dla typu ogólnego `ICorDebugClass` lub `ICorDebugClass2` obiekt reprezentuje typ bez wystąpień (`SortedList<K,V>`), a `ICorDebugType` obiekt reprezentuje różne typy wystąpień. Biorąc pod uwagę `ICorDebugClass` lub `ICorDebugClass2` obiektu, można utworzyć `ICorDebugType` obiektów dla dowolnego wystąpienia przez wywołanie metody `ICorDebugClass2::GetParameterizedType` metody. Można również utworzyć `ICorDebugType` obiektu dla typu prostego, takie jak Int32, lub dla typu nieogólnego.  
  
 Wprowadzenie `ICorDebugType` obiekt do reprezentowania pojęcie środowiska wykonawczego typu ma falę w interfejsie API. Funkcje, które poprzednio miały `ICorDebugClass` lub `ICorDebugClass2` obiektu, a nawet `CorElementType` wartości zostały uogólnione podjęcie `ICorDebugType` obiektu.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
