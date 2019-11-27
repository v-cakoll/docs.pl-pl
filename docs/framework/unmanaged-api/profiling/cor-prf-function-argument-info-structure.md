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
ms.openlocfilehash: 2b01acbd617b13a64ef3dca6c8661f1e6bb067ac
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447386"
---
# <a name="cor_prf_function_argument_info-structure"></a>COR_PRF_FUNCTION_ARGUMENT_INFO — Struktura
Reprezentuje argumenty funkcji w kolejności od lewej do prawej.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef struct _COR_PRF_FUNCTION_ARGUMENT_INFO {  
    ULONG numRanges;  
    ULONG totalArgumentSize;  
    COR_PRF_FUNCTION_ARGUMENT_RANGE ranges[1];  
} COR_PRF_FUNCTION_ARGUMENT_INFO;  
```  
  
## <a name="members"></a>Members  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`numRanges`|Liczba bloków argumentów. Oznacza to, że ta wartość jest liczbą struktur [COR_PRF_FUNCTION_ARGUMENT_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md) w tablicy `ranges`.|  
|`totalArgumentSize`|Łączny rozmiar wszystkich argumentów. Innymi słowy, ta wartość jest sumą argumentów długości.|  
|`ranges`|Tablica struktur `COR_PRF_FUNCTION_ARGUMENT_RANGE`, z których każdy reprezentuje jeden blok argumentów funkcji.|  
  
## <a name="remarks"></a>Uwagi  
 Funkcja może mieć wiele argumentów. Te argumenty mogą nie być przechowywane w sposób ciągły w pamięci. Może istnieć blok trzech argumentów w jednym miejscu, blok dwóch argumentów w innym miejscu i końcowy blok jednego argumentu w innym miejscu. Te argumenty są wszystkie dla tej samej funkcji; są one po prostu przechowywane w różnych miejscach.  
  
 Struktura `COR_PRF_FUNCTION_ARGUMENT_INFO` reprezentuje wszystkie argumenty pojedynczej funkcji. Używa tablicy do odwoływania się do wszystkich bloków argumentów funkcji. Dlatego w przypadku pojedynczej funkcji istnieje jedna struktura `COR_PRF_FUNCTION_ARGUMENT_INFO`, która odwołuje się do wielu struktur `COR_PRF_FUNCTION_ARGUMENT_RANGE`, z których każdy wskazuje jeden lub więcej argumentów funkcji.  
  
 Argumenty, które są przechowywane w rejestrach, są rozlane do pamięci, aby kompilować struktury.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Profiling — struktury](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
