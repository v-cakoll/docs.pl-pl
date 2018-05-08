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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 38b00d903fdd7301415a8df7642e12366178fd10
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugevalnewarray-method"></a>ICorDebugEval::NewArray — Metoda
Przydziela nowej tablicy o typie określonym elemencie i wymiary.  
  
 Ta metoda jest przestarzała w programie .NET Framework w wersji 2.0. Użyj [ICorDebugEval2::NewParameterizedArray](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedarray-method.md) zamiast tego.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT NewArray (  
    [in] CorElementType     elementType,  
    [in] ICorDebugClass     *pElementClass,  
    [in] ULONG32            rank,  
    [in, size_is(rank)] ULONG32 dims[],  
    [in, size_is(rank)] ULONG32 lowBounds[]  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `elementType`  
 [in] Wartość wyliczenia CorElementType, która określa typ elementu tablicy.  
  
 `pElementClass`  
 [in] Wskaźnik do obiektu ICorDebugClass, który określa klasę elementu. Ta wartość może mieć wartości zerowej, jeśli typ elementu jest typem pierwotnym.  
  
 `rank`  
 [in] Liczba wymiarów tablicy. W .NET Framework 2.0 ta wartość musi wynosić 1.  
  
 `dims`  
 [in] Rozmiar w bajtach każdego wymiaru tablicy.  
  
 `lowBounds`  
 [in] Opcjonalne. Dolną granicę każdego wymiaru tablicy. W przypadku pominięcia tej wartości dolna granica zero zakłada, że dla każdego wymiaru.  
  
## <a name="remarks"></a>Uwagi  
 Tablicy zawsze jest tworzony w domenie aplikacji, w którym wątek jest aktualnie wykonywany.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** 1.1, 1.0
