---
title: COR_PRF_FINALIZER_FLAGS — Wyliczenie
ms.date: 03/30/2017
api_name:
- COR_PRF_FINALIZER_FLAGS
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_FINALIZER_FLAGS
helpviewer_keywords:
- COR_PRF_FINALIZER_FLAGS enumeration [.NET Framework profiling]
ms.assetid: 297d7721-3911-4f36-9e34-d9da0c33e22a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d5037f335e8d66c341d70d91d955a1ac7571b823
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61775150"
---
# <a name="corprffinalizerflags-enumeration"></a>COR_PRF_FINALIZER_FLAGS — Wyliczenie
W tym artykule opisano finalizatora obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef enum {  
    COR_PRF_FINALIZER_CRITICAL = 0x1  
} COR_PRF_FINALIZER_FLAGS;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`COR_PRF_FINALIZER_CRITICAL`|Finalizator ma kluczowe znaczenie.|  
  
## <a name="remarks"></a>Uwagi  
 `COR_PRF_FINALIZER_FLAGS` Wyliczenie jest używane przez [icorprofilercallback2::finalizeableobjectqueued —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-finalizeableobjectqueued-method.md) metody do opisania finalizatora obiektu.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Profilowanie — wyliczenia](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
