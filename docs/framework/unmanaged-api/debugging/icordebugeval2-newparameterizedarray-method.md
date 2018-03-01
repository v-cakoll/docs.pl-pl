---
title: "ICorDebugEval2::NewParameterizedArray — Metoda"
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a605276fac66e395d5663bacff727c235981a868
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugeval2newparameterizedarray-method"></a>ICorDebugEval2::NewParameterizedArray — Metoda
Przydziela nowej tablicy o typie określonym elemencie i wymiary.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT NewParameterizedArray(  
    [in] ICorDebugType          *pElementType,  
    [in] ULONG32                rank,  
    [in, size_is(rank)] ULONG32 dims[],  
    [in, size_is(rank)] ULONG32 lowBounds[]  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pElementType`  
 [in] Wskaźnik do obiektu ICorDebugType, który reprezentuje typ elementu przechowywane w tablicy.  
  
 `rank`  
 [in] Liczba wymiarów tablicy. W programie .NET Framework w wersji 2.0 ta wartość musi wynosić 1.  
  
 `dims`  
 [in] Rozmiar w bajtach każdego wymiaru tablicy.  
  
 `lowBounds`  
 [in] Opcjonalne. Dolną granicę każdego wymiaru tablicy. W przypadku pominięcia tej wartości dolna granica zero zakłada, że dla każdego wymiaru.  
  
## <a name="remarks"></a>Uwagi  
 Elementy tablicy można instancji typu ogólnego. Tablicy zawsze jest tworzony w domenie aplikacji, w którym wątek jest uruchomiony. W .NET Framework 2.0, wartość `rank` musi być równa 1.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
