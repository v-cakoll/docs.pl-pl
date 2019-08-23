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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c67ce15175f8667139f99cec1ed17531eab473e1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69935646"
---
# <a name="imethodmalloc-interface"></a>IMethodMalloc — Interfejs
Udostępnia metodę przydzielania pamięci dla nowej treści funkcji języka pośredniego (MSIL) firmy Microsoft.  
  
> [!NOTE]
> `IMethodMalloc` Interfejs jest prostym alokatorem pamięci. Umożliwia przydzielanie pamięci, ale nie zwalnia.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Alloc, metoda](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-alloc-method.md)|Próbuje przydzielić określoną ilość pamięci dla nowej treści funkcji MSIL.|  
  
## <a name="remarks"></a>Uwagi  
 Każdy Alokator jest specyficzny dla modułu i gwarantuje, że treść funkcji będzie naliczona pozytywnie od podstawy modułu. Pamięć powyżej podstawy modułu może być cenna, więc Alokator powinien być używany do przydzielania pamięci tylko dla treści funkcji.  
  
## <a name="requirements"></a>Wymagania  
 **Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówki** CorProf. idl, CorProf. h  
  
 **Biblioteki** CorGuids.lib  
  
 **.NET Framework wersje:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Interfejsy profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
