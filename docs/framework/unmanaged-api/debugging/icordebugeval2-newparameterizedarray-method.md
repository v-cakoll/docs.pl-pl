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
ms.openlocfilehash: 9476bcc9706e89fd3d7e0abc14031f70a0aa0ad0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73084838"
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
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
