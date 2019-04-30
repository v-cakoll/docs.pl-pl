---
title: ICorDebugCodeEnum::Next — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugCodeEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCodeEnum::Next
helpviewer_keywords:
- ICorDebugCodeEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugEnum interface [.NET Framework debugging]
ms.assetid: 644ece86-384d-4c63-9fba-52c789616ff7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5db87cd4ad965654b63a68828cd088b8d2f7d07c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61749790"
---
# <a name="icordebugcodeenumnext-method"></a>ICorDebugCodeEnum::Next — Metoda
Pobiera określoną liczbę wystąpień "ICorDebugCode" z wyliczenia, zaczynając od bieżącej pozycji.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugCode *values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `celt`  
 [in] Liczba `ICorDebugCode` wystąpienia mają zostać pobrane.  
  
 `values`  
 [out] Tablica wskaźników, z których każdy wskazuje `ICorDebugCode` obiektu.  
  
 `pceltFetched`  
 [out] Wskaźnik do liczby `ICorDebugCode` wystąpień rzeczywistego zwrotu. Ta wartość może mieć wartości null Jeśli `celt` jeden.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
