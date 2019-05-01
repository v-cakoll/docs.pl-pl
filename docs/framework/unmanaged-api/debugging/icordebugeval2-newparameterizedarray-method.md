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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8c639204fa207774b0e362f1ba8fe71937494ae2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61988997"
---
# <a name="icordebugeval2newparameterizedarray-method"></a>ICorDebugEval2::NewParameterizedArray — Metoda
Przydziela nową tablicę typu określonego elementu i wymiary.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT NewParameterizedArray(  
    [in] ICorDebugType          *pElementType,  
    [in] ULONG32                rank,  
    [in, size_is(rank)] ULONG32 dims[],  
    [in, size_is(rank)] ULONG32 lowBounds[]  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pElementType`  
 [in] Wskaźnik do obiektu ICorDebugType, który reprezentuje typ elementu przechowywanego w tablicy.  
  
 `rank`  
 [in] Liczba wymiarów tablicy. W programie .NET Framework 2.0 ta wartość musi wynosić 1.  
  
 `dims`  
 [in] Rozmiar w bajtach każdego wymiaru tablicy.  
  
 `lowBounds`  
 [in] Opcjonalnie. Dolna granica każdego wymiaru tablicy. Jeśli ta wartość zostanie pominięty, dolną granicę równą zero zakłada, że dla każdego wymiaru.  
  
## <a name="remarks"></a>Uwagi  
 Elementy tablicy mogą być wystąpień typu ogólnego. Tablica zawsze jest tworzony w domenie aplikacji, w którym wątek jest obecnie uruchomiony. W programie .NET Framework 2.0, wartość `rank` musi mieć wartość 1.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
