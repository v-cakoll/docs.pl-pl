---
title: "COR_PRF_FUNCTION_ARGUMENT_INFO — Struktura"
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e26377fe3c5cfbae68f90087e3fb624ae4db0dc8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="corprffunctionargumentinfo-structure"></a>COR_PRF_FUNCTION_ARGUMENT_INFO — Struktura
Reprezentuje argumenty funkcji w kolejności od lewej do prawej.  
  
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
|`numRanges`|Liczba bloków argumentów. Oznacza to, że ta wartość jest liczbą [COR_PRF_FUNCTION_ARGUMENT_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md) struktury w `ranges` tablicy.|  
|`totalArgumentSize`|Całkowity rozmiar wszystkich argumentów. Innymi słowy ta wartość jest suma długości argumentu.|  
|`ranges`|Tablica `COR_PRF_FUNCTION_ARGUMENT_RANGE` struktury, z których każdy reprezentuje jeden blok argumentów funkcji.|  
  
## <a name="remarks"></a>Uwagi  
 Funkcja może mieć wiele argumentów. Tych argumentów nie może być połączone ze sobą przechowywane w pamięci. Może być blokiem trzech argumentów w jednym miejscu, blok dwa argumenty w innym miejscu i bloku końcowego jeden argument w innym miejscu. Wyświetlane są wszystkie argumenty dla tej samej funkcji; po prostu są one przechowywane w różnych miejscach.  
  
 `COR_PRF_FUNCTION_ARGUMENT_INFO` Struktury reprezentuje wszystkie argumenty funkcji pojedynczego. Aby odwołać wszystkie bloki argumentów funkcji używa tablicy. Tak, dla jednej funkcji, należy mieć pojedynczy `COR_PRF_FUNCTION_ARGUMENT_INFO` struktury, która odwołuje się do wielu `COR_PRF_FUNCTION_ARGUMENT_RANGE` struktury, z których każdy wskazuje co najmniej jeden z argumentów funkcji.  
  
 Argumenty, które są przechowywane w rejestrach są rozrzucone w pamięci, aby skompilować struktur.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Profiling — struktury](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
