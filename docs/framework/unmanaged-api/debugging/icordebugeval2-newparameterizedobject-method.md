---
title: ICorDebugEval2::NewParameterizedObject — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.NewParameterizedObject
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::NewParameterizedObject
helpviewer_keywords:
- NewParameterizedObject method [.NET Framework debugging]
- ICorDebugEval2::NewParameterizedObject method [.NET Framework debugging]
ms.assetid: 3d705463-e640-4249-8036-4e8206d03cfe
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: aae5f4c79acd6f92d42c2890ba64fa66e1b4bfbe
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67753590"
---
# <a name="icordebugeval2newparameterizedobject-method"></a>ICorDebugEval2::NewParameterizedObject — Metoda
Tworzy nowy obiekt typ sparametryzowany i wywołuje metodę do konstruktora obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT NewParameterizedObject (  
    [in] ICorDebugFunction     *pConstructor,  
    [in] ULONG32               nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType *ppTypeArgs[],  
    [in] ULONG32               nArgs,  
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pConstructor`  
 [in] Wskaźnik do obiektu ICorDebugFunction, który reprezentuje konstruktora obiektu, który ma zostać utworzona.  
  
 `nTypeArgs`  
 [in] Przekazany liczby argumentów typu.  
  
 `ppTypeArgs`  
 [in] Tablica wskaźników, z których każdy wskazuje na obiekt ICorDebugType, który reprezentuje argument typu obiektu, który zostanie on uruchomiony.  
  
 `nArgs`  
 [in] Liczba argumentów przekazana do konstruktora.  
  
 `ppArgs`  
 [in] Tablica wskaźników, z których każdy wskazuje na obiekt ICorDebugValue, który reprezentuje wartość argumentu, który jest przekazywany do konstruktora.  
  
## <a name="remarks"></a>Uwagi  
 Konstruktor obiektu może potrwać <xref:System.Type> parametrów.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
