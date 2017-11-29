---
title: "ICorDebugCodeEnum::Next — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugCodeEnum.Next
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugCodeEnum::Next
helpviewer_keywords:
- ICorDebugCodeEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugEnum interface [.NET Framework debugging]
ms.assetid: 644ece86-384d-4c63-9fba-52c789616ff7
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0260f52a32d5cd6d2862927bb0938c90bc430440
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugcodeenumnext-method"></a>ICorDebugCodeEnum::Next — Metoda
Pobiera określoną liczbę wystąpień "ICorDebugCode" z wyliczenia, zaczynając od bieżącego położenia.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugCode *values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `celt`  
 [in] Liczba `ICorDebugCode` wystąpienia mają zostać pobrane.  
  
 `values`  
 [out] Tablicy wskaźników, z których każdy wskazuje `ICorDebugCode` obiektu.  
  
 `pceltFetched`  
 [out] Wskaźnik do liczby `ICorDebugCode` wystąpienia faktycznie zwracane. Ta wartość może mieć wartości zerowej Jeśli `celt` jeden.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
    
 
