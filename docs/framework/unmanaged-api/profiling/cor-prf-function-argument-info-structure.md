---
title: COR_PRF_FUNCTION_ARGUMENT_INFO — Struktura
ms.date: 03/30/2017
api_name:
- COR_PRF_FUNCTION_ARGUMENT_INFO
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_FUNCTION_ARGUMENT_INFO
helpviewer_keywords:
- COR_PRF_FUNCTION_ARGUMENT_INFO structure [.NET Framework profiling]
ms.assetid: 07cf3bab-e193-4991-8205-3f41cf2d67b3
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 293ad30ebf47ca8684d158b1ae1772ab245d7981
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59163120"
---
# <a name="corprffunctionargumentinfo-structure"></a>COR_PRF_FUNCTION_ARGUMENT_INFO — Struktura
Reprezentuje argumenty funkcji, w kolejności od lewej do prawej.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef struct _COR_PRF_FUNCTION_ARGUMENT_INFO {  
    ULONG numRanges;  
    ULONG totalArgumentSize;  
    COR_PRF_FUNCTION_ARGUMENT_RANGE ranges[1];  
} COR_PRF_FUNCTION_ARGUMENT_INFO;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`numRanges`|Liczba bloków argumentów. Ta wartość jest liczbą [cor_prf_function_argument_range —](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md) struktury w `ranges` tablicy.|  
|`totalArgumentSize`|Całkowity rozmiar wszystkich argumentów. Innymi słowy ta wartość jest sumy długości argumentu.|  
|`ranges`|Tablica `COR_PRF_FUNCTION_ARGUMENT_RANGE` struktur, z których każdy reprezentuje jeden blok argumentów funkcji.|  
  
## <a name="remarks"></a>Uwagi  
 Funkcja może mieć wiele argumentów. Tych argumentów nie może być ciągłym przechowywane w pamięci. Może być blokiem trzy argumenty w jednym miejscu, blok dwa argumenty w inne miejsce i blok końcowy jeden argument w innym miejscu. Te argumenty są dostępne dla tej samej funkcji; po prostu są one przechowywane w różnych miejscach.  
  
 `COR_PRF_FUNCTION_ARGUMENT_INFO` Struktury reprezentuje wszystkie argumenty funkcji pojedynczej. Używa tablicy, aby odwoływać się do wszystkich bloków argumentów funkcji. Dlatego dla jednej funkcji, masz jeden `COR_PRF_FUNCTION_ARGUMENT_INFO` struktury, która odwołuje się do wielu `COR_PRF_FUNCTION_ARGUMENT_RANGE` struktur, które wskazuje na jeden lub więcej argumentów funkcji.  
  
 Argumenty, które są przechowywane w rejestrach, są rozrzucone w pamięci, aby skompilować struktur.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Profiling — Struktury](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
