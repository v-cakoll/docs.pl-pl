---
title: COR_PRF_SNAPSHOT_INFO — Wyliczenie
ms.date: 03/30/2017
api_name:
- COR_PRF_SNAPSHOT_INFO
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_SNAPSHOT_INFO
helpviewer_keywords:
- COR_PRF_SNAPSHOT_INFO enumeration [.NET Framework profiling]
ms.assetid: a5906b2a-ad4a-4cc6-a421-2d7d8adf7468
topic_type:
- apiref
ms.openlocfilehash: 6168c5b27868a261871b292e17ca02b04ae89917
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500783"
---
# <a name="cor_prf_snapshot_info-enumeration"></a>COR_PRF_SNAPSHOT_INFO — Wyliczenie
Określa ilość danych, które mają zostać przekazane z migawki stosu w każdym wywołaniu funkcji [StackSnapshotCallback —](stacksnapshotcallback-function.md) profilera.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef enum _COR_PRF_SNAPSHOT_INFO {  
    COR_PRF_SNAPSHOT_DEFAULT = 0x0,  
    COR_PRF_SNAPSHOT_REGISTER_CONTEXT = 0x1,  
    COR_PRF_SNAPSHOT_X86_OPTIMIZED = 0X2  
} COR_PRF_SNAPSHOT_INFO;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Elementy członkowskie|Opis|  
|-------------|-----------------|  
|`COR_PRF_SNAPSHOT_DEFAULT`|Wskazuje, że należy przesłać wartości dla wszystkich `StackSnapshotCallback` parametrów, z wyjątkiem `context` parametru.|  
|`COR_PRF_SNAPSHOT_REGISTER_CONTEXT`|Wskazuje, że należy przesłać wartości dla wszystkich `StackSnapshotCallback` parametrów, łącznie z `context` parametrem.|  
|`COR_PRF_SNAPSHOT_X86_OPTIMIZED`|Wskazuje, że zostanie użyty prostszy, alternatywny algorytm przechodzenia stosu.|  
  
## <a name="remarks"></a>Uwagi  
 Wartości, które są dostarczane przez `COR_PRF_SNAPSHOT_INFO` Wyliczenie, są przekazywane jako parametry do metody [DoStackSnapshot —](icorprofilerinfo2-dostacksnapshot-method.md) .  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [DoStackSnapshot, metoda](icorprofilerinfo2-dostacksnapshot-method.md)
- [Profilowanie — wyliczenia](profiling-enumerations.md)
