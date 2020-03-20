---
title: COR_PRF_REJIT_FLAGS — Wyliczenie
ms.date: 08/06/2019
api_name:
- COR_PRF_REJIT_FLAGS Enumeration
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_REJIT_FLAGS
helpviewer_keywords:
- COR_PRF_REJIT_FLAGS enumeration [.NET Framework profiling]
topic_type:
- apiref
author: davmason
ms.author: davmason
ms.openlocfilehash: 8fc5f1a488826d8adc6aecb8ef122609bebbe813
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177102"
---
# <a name="cor_prf_rejit_flags-enumeration"></a>COR_PRF_REJIT_FLAGS — Wyliczenie
Zawiera wartości, które wskazują, jak [ICorProfilerInfo10::RequestReJITWithInliners](icorprofilerinfo10-requestrejitwithinliners-method.md) api powinien zachowywać.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef enum  
{
    COR_PRF_REJIT_BLOCK_INLINING = 0x1,
    COR_PRF_REJIT_INLINING_CALLBACKS    = 0x2
} COR_PRF_REJIT_FLAGS;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Członek|Opis|  
|------------|-----------------|  
|`COR_PRF_REJIT_BLOCK_INLINING`| Metody ReJITted zostaną zablokowane przed inlined w innych metodach. |  
|`COR_PRF_REJIT_INLINING_CALLBACKS`| Odbieranie `GetFunctionParameters` wywołań zwrotnych dla wszelkich metod, które wbudowane metody wymagane do ReJITted. |  

## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [.NET Core obsługiwane systemy operacyjne](../../../core/install/dependencies.md?pivots=os-windows).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]
  
## <a name="see-also"></a>Zobacz też

- [Profilowanie — wyliczenia](profiling-enumerations.md)
