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
ms.openlocfilehash: 4dd4e39c9092d018f13e3bd2822e9492d71141ad
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76867298"
---
# <a name="cor_prf_codegen_flags-enumeration"></a>COR_PRF_CODEGEN_FLAGS — Wyliczanie
Definiuje flagi generowania kodu, które można ustawić za pomocą metody [ICorProfilerFunctionControl:: SetCodegenFlags —](icorprofilerfunctioncontrol-setcodegenflags-method.md) .  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef enum {  
    COR_PRF_CODEGEN_DISABLE_INLINING =          0x0001,  
    COR_PRF_CODEGEN_DISABLE_ALL_OPTIMIZATIONS = 0x0002,  
} COR_PRF_CODEGEN_FLAGS;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`COR_PRF_CODEGEN_DISABLE_INLINING`|Żadna funkcja nie zostanie zakreślona w treści tej funkcji. Jednak sama funkcja może być wbudowana w jej obiekty wywołujące.|  
|`COR_PRF_CODEGEN_DISABLE_ALL_OPTIMIZATIONS`|Wszystkie optymalizacje zostaną wyłączone dla treści tej funkcji. Jednak sama funkcja może być w dalszym ciągu zakreślona w jego wywołaniach.|  
  
## <a name="remarks"></a>Uwagi  
 Wyliczenie `COR_PRF_CODEGEN_FLAGS` jest używane przez metodę [ICorProfilerFunctionControl:: SetCodegenFlags —](icorprofilerfunctioncontrol-setcodegenflags-method.md) w celu umożliwienia profilerowi sterowania generowaniem kodu dla funkcji ponownie skompilowanej JIT.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Profilowanie — wyliczenia](profiling-enumerations.md)
