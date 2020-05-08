---
title: ICorDebugEval::NewArray — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugEval.NewArray
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::NewArray
helpviewer_keywords:
- NewArray method [.NET Framework debugging]
- ICorDebugEval::NewArray method [.NET Framework debugging]
ms.assetid: cc79a67d-5368-434d-a943-209db90491b9
topic_type:
- apiref
ms.openlocfilehash: 496a6a7e01dec8aa90ba4e849c431ccd499ef53d
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976203"
---
# <a name="icordebugevalnewarray-method"></a>ICorDebugEval::NewArray — Metoda
Przypisuje nową tablicę określonego typu elementu i wymiarów.  
  
 Ta metoda jest przestarzała w .NET Framework w wersji 2,0. Zamiast tego użyj [ICorDebugEval2:: NewParameterizedArray —](icordebugeval2-newparameterizedarray-method.md) .  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT NewArray (  
    [in] CorElementType     elementType,  
    [in] ICorDebugClass     *pElementClass,  
    [in] ULONG32            rank,  
    [in, size_is(rank)] ULONG32 dims[],  
    [in, size_is(rank)] ULONG32 lowBounds[]  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `elementType`  
 podczas Wartość wyliczenia CorElementType —, która określa typ elementu tablicy.  
  
 `pElementClass`  
 podczas Wskaźnik do obiektu ICorDebugClass, który określa klasę elementu. Ta wartość może być równa null, jeśli typ elementu jest typem pierwotnym.  
  
 `rank`  
 podczas Liczba wymiarów tablicy. W .NET Framework 2,0 ta wartość musi być równa 1.  
  
 `dims`  
 podczas Rozmiar, w bajtach, każdego wymiaru tablicy.  
  
 `lowBounds`  
 podczas Obowiązkowe. Dolna granica każdego wymiaru tablicy. W przypadku pominięcia tej wartości dla każdego wymiaru zostanie przyjęta Dolna granica zero.  
  
## <a name="remarks"></a>Uwagi  
 Tablica jest zawsze tworzona w domenie aplikacji, w której jest aktualnie wykonywany wątek.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:** 1,1, 1,0
