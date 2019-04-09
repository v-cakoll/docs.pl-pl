---
title: ICorDebugTypeEnum::Next — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugTypeEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugTypeEnum::Next
helpviewer_keywords:
- ICorDebugTypeEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugTypeEnum interface [.NET Framework debugging]
ms.assetid: d0fdeba3-c195-4ece-8caf-79b1f40025d2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d47f14ff2adb37fca16cf6774a2b80cb2e074b17
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59157316"
---
# <a name="icordebugtypeenumnext-method"></a>ICorDebugTypeEnum::Next — Metoda
Pobiera liczbę wystąpień "ICorDebugType" określonego przez `celt` z wyliczenia, zaczynając od bieżącej pozycji.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT Next (  
    [in]  ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugType *values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `celt`  
 [in] Liczba `ICorDebugType` wystąpienia mają zostać pobrane.  
  
 `values`  
 [out] Tablica wskaźników, z których każdy wskazuje `ICorDebugType` obiektu.  
  
 `pceltFetched`  
 [out] Wskaźnik do liczby `ICorDebugType` wystąpień rzeczywistego zwrotu. Ta wartość może mieć wartości null Jeśli `celt` jeden.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
