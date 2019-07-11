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
ms.openlocfilehash: 9597d05e46c2d41ab1f24a073c028561e944fb59
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67753029"
---
# <a name="icordebugevalnewarray-method"></a>ICorDebugEval::NewArray — Metoda
Przydziela nową tablicę typu określonego elementu i wymiary.  
  
 Ta metoda jest przestarzała w programie .NET Framework 2.0. Użyj [ICorDebugEval2::NewParameterizedArray](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedarray-method.md) zamiast tego.  
  
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
 [in] Wartość corelementtype — wyliczenie, który określa typ elementu tablicy.  
  
 `pElementClass`  
 [in] Wskaźnik do obiektu ICorDebugClass, który określa klasę elementu. Ta wartość może być zerowy, jeśli typ elementu to typ pierwotny.  
  
 `rank`  
 [in] Liczba wymiarów tablicy. W programie .NET Framework 2.0 ta wartość musi wynosić 1.  
  
 `dims`  
 [in] Rozmiar w bajtach każdego wymiaru tablicy.  
  
 `lowBounds`  
 [in] Opcjonalnie. Dolna granica każdego wymiaru tablicy. Jeśli ta wartość zostanie pominięty, dolną granicę równą zero zakłada, że dla każdego wymiaru.  
  
## <a name="remarks"></a>Uwagi  
 Tablica zawsze jest tworzony w domenie aplikacji, w którym wątek jest w trakcie wykonywania.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** 1.1, 1.0
