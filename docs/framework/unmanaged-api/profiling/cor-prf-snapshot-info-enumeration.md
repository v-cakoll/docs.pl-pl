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
ms.openlocfilehash: 97bf3e69a8ea155d53479ba6f61988e56e3bd396
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76867027"
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
|`COR_PRF_SNAPSHOT_DEFAULT`|Wskazuje, że należy przesłać wartości dla wszystkich parametrów `StackSnapshotCallback`, z wyjątkiem parametru `context`.|  
|`COR_PRF_SNAPSHOT_REGISTER_CONTEXT`|Wskazuje, że należy przesłać wartości dla wszystkich parametrów `StackSnapshotCallback`, łącznie z parametrem `context`.|  
|`COR_PRF_SNAPSHOT_X86_OPTIMIZED`|Wskazuje, że zostanie użyty prostszy, alternatywny algorytm przechodzenia stosu.|  
  
## <a name="remarks"></a>Uwagi  
 Wartości, które są dostarczane przez Wyliczenie `COR_PRF_SNAPSHOT_INFO` są przekazywane jako parametry do metody [DoStackSnapshot —](icorprofilerinfo2-dostacksnapshot-method.md) .  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [DoStackSnapshot, metoda](icorprofilerinfo2-dostacksnapshot-method.md)
- [Profilowanie — wyliczenia](profiling-enumerations.md)
