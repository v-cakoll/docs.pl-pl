---
title: ICorDebugEval2::NewParameterizedArray — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.NewParameterizedArray
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::NewParameterizedArray
helpviewer_keywords:
- ICorDebugEval2::NewParameterizedArray method [.NET Framework debugging]
- NewParameterizedArray method [.NET Framework debugging]
ms.assetid: 45efb8ba-c4de-4109-945f-e734d376b43c
topic_type:
- apiref
ms.openlocfilehash: 9d589bfc3093d03d87acb47ade0fc6c972bcd335
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976112"
---
# <a name="icordebugeval2newparameterizedarray-method"></a>ICorDebugEval2::NewParameterizedArray — Metoda
Przypisuje nową tablicę określonego typu elementu i wymiarów.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT NewParameterizedArray(  
    [in] ICorDebugType          *pElementType,  
    [in] ULONG32                rank,  
    [in, size_is(rank)] ULONG32 dims[],  
    [in, size_is(rank)] ULONG32 lowBounds[]  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pElementType`  
 podczas Wskaźnik do obiektu ICorDebugType, który reprezentuje typ elementu przechowywanego w tablicy.  
  
 `rank`  
 podczas Liczba wymiarów tablicy. W .NET Framework w wersji 2,0 ta wartość musi być równa 1.  
  
 `dims`  
 podczas Rozmiar, w bajtach, każdego wymiaru tablicy.  
  
 `lowBounds`  
 podczas Obowiązkowe. Dolna granica każdego wymiaru tablicy. W przypadku pominięcia tej wartości dla każdego wymiaru zostanie przyjęta Dolna granica zero.  
  
## <a name="remarks"></a>Uwagi  
 Elementy tablicy mogą być wystąpieniami typu ogólnego. Tablica jest zawsze tworzona w domenie aplikacji, w której jest aktualnie uruchomiony wątek. W .NET Framework 2,0 wartość `rank` musi być równa 1.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
