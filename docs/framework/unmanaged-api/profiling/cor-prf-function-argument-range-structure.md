---
title: COR_PRF_FUNCTION_ARGUMENT_RANGE — Struktura
ms.date: 03/30/2017
api_name:
- COR_PRF_FUNCTION_ARGUMENT_RANGE
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_FUNCTION_ARGUMENT_RANGE
helpviewer_keywords:
- COR_PRF_FUNCTION_ARGUMENT_RANGE structure [.NET Framework profiling'
ms.assetid: 9f469eac-ac66-419b-8668-fe705bc1a51f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 92e3a0a930a4e4b91cac27cbed1b745dea4207a9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33450027"
---
# <a name="corprffunctionargumentrange-structure"></a>COR_PRF_FUNCTION_ARGUMENT_RANGE — Struktura
Reprezentuje blok argumentów funkcji ciągłym przechowywane w kolejności od lewej do prawej w pamięci.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef struct _COR_PRF_FUNCTION_ARGUMENT_RANGE {  
    UINT_PTR startAddress;  
    ULONG length;  
} COR_PRF_FUNCTION_ARGUMENT_RANGE;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Elementy członkowskie|Opis|  
|-------------|-----------------|  
|`startAddress`|Adres początkowy bloku.|  
|`length`|Długość ciągłego bloku.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Profiling — struktury](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
