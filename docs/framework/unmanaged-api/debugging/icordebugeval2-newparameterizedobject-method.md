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
ms.openlocfilehash: f6ede42ac90f65f934e285f879bcef62d13b65cb
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976099"
---
# <a name="icordebugeval2newparameterizedobject-method"></a>ICorDebugEval2::NewParameterizedObject — Metoda
Tworzy wystąpienie nowego obiektu typu sparametryzowanego i wywołuje metodę konstruktora obiektu.  
  
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
 podczas Wskaźnik do obiektu ICorDebugFunction, który reprezentuje konstruktora obiektu do wystąpienia.  
  
 `nTypeArgs`  
 podczas Liczba przezakończonych argumentów typu.  
  
 `ppTypeArgs`  
 podczas Tablica wskaźników, z których każdy wskazuje obiekt ICorDebugType, który reprezentuje argument typu dla obiektu, który jest tworzony.  
  
 `nArgs`  
 podczas Liczba argumentów przeniesiona do konstruktora.  
  
 `ppArgs`  
 podczas Tablica wskaźników, z których każdy wskazuje obiekt ICorDebugValue, który reprezentuje wartość argumentu, który jest przesyłany do konstruktora.  
  
## <a name="remarks"></a>Uwagi  
 Konstruktor obiektu może przyjmować <xref:System.Type> parametry.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
