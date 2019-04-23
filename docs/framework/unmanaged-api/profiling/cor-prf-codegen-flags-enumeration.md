---
title: COR_PRF_CODEGEN_FLAGS — Wyliczanie
ms.date: 03/30/2017
api_name:
- COR_PRF_CODEGEN_FLAGS
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_CODEGEN_FLAGS
helpviewer_keywords:
- COR_PRF_CODEGEN_FLAGS enumeration [.NET Framework profiling]
ms.assetid: 3e184022-0247-4824-a23d-6b29593d8d01
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 321318b63368ed6e57d235cf97d94485352f8686
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59211364"
---
# <a name="corprfcodegenflags-enumeration"></a>COR_PRF_CODEGEN_FLAGS — Wyliczanie
Określa flagi generowania kodu, które można ustawić za pomocą [icorprofilerfunctioncontrol::setcodegenflags —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md) metody.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef enum {  
    COR_PRF_CODEGEN_DISABLE_INLINING =          0x0001,  
    COR_PRF_CODEGEN_DISABLE_ALL_OPTIMIZATIONS = 0x0002,  
} COR_PRF_CODEGEN_FLAGS;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`COR_PRF_CODEGEN_DISABLE_INLINING`|Żadne funkcje nie będą wbudowana w treści tej funkcji. Jednak ta funkcja może być wbudowana w wywołujące.|  
|`COR_PRF_CODEGEN_DISABLE_ALL_OPTIMIZATIONS`|Wszystkie optymalizacje zostanie wyłączona w treści tej funkcji. Jednak ta funkcja może nadal być wbudowana w wywołujące.|  
  
## <a name="remarks"></a>Uwagi  
 `COR_PRF_CODEGEN_FLAGS` Wyliczenie jest używane przez [icorprofilerfunctioncontrol::setcodegenflags —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md) metodę, aby włączyć narzędzie profiler, aby kontrolować generowanie kodu dla funkcji ponownie skompilowana JIT.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Profilowanie — wyliczenia](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
