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
ms.openlocfilehash: ee825da1f3f0fd72a3b47b48783f0f344af99b65
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59077787"
---
# <a name="imethodmalloc-interface"></a>IMethodMalloc — Interfejs
Udostępnia metodę można przydzielić pamięci dla nowej treści funkcji Microsoft intermediate language (MSIL).  
  
> [!NOTE]
>  `IMethodMalloc` Interfejs jest alokatora pamięci proste. Można przydzielić pamięci, ale nie można go bezpłatnie.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Alloc, metoda](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-alloc-method.md)|Próbuje przydzielić określonej ilości pamięci dla nowej treści funkcji MSIL.|  
  
## <a name="remarks"></a>Uwagi  
 Każdy alokatora jest specyficzny dla modułu i gwarantuje, że treści funkcji będzie przesunięciem dodatnią od podstawy modułu. Pamięć od podstawy modułu mogą być cenne, alokator powinien być używany do przydzielania pamięci tylko w przypadku treści funkcji.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Interfejsy profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
