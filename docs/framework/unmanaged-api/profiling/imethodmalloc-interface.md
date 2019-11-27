---
title: IMethodMalloc — Interfejs
ms.date: 03/30/2017
api_name:
- IMethodMalloc
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- IMethodMalloc
helpviewer_keywords:
- IMethodMalloc interface [.NET Framework profiling]
ms.assetid: 8c8ab5dc-557c-473a-82f2-6e403eca7dac
topic_type:
- apiref
ms.openlocfilehash: 3f840154d472dbcea7dfef7ba93e38c80b836734
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447549"
---
# <a name="imethodmalloc-interface"></a>IMethodMalloc — Interfejs
Udostępnia metodę przydzielania pamięci dla nowej treści funkcji języka pośredniego (MSIL) firmy Microsoft.  
  
> [!NOTE]
> Interfejs `IMethodMalloc` jest prostym alokatorem pamięci. Umożliwia przydzielanie pamięci, ale nie zwalnia.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Alloc, metoda](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-alloc-method.md)|Próbuje przydzielić określoną ilość pamięci dla nowej treści funkcji MSIL.|  
  
## <a name="remarks"></a>Uwagi  
 Każdy Alokator jest specyficzny dla modułu i gwarantuje, że treść funkcji będzie naliczona pozytywnie od podstawy modułu. Pamięć powyżej podstawy modułu może być cenna, więc Alokator powinien być używany do przydzielania pamięci tylko dla treści funkcji.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Interfejsy profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
