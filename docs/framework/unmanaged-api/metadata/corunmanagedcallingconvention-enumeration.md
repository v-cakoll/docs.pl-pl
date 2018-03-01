---
title: "CorUnmanagedCallingConvention — Wyliczenie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- CorUnmanagedCallingConvention
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorUnmanagedCallingConvention
helpviewer_keywords:
- CorUnmanagedCallingConvention enumeration [.NET Framework metadata]
ms.assetid: 83058790-160b-4703-a5eb-74b66acbdfa9
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 446a948c8809d9f098ede8fbb9b426f6169ce812
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="corunmanagedcallingconvention-enumeration"></a>CorUnmanagedCallingConvention — Wyliczenie
Określa konwencji wywoływania dla niezarządzanego kodu.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef enum CorUnmanagedCallingConvention {  
  
    IMAGE_CEE_UNMANAGED_CALLCONV_C         = 0x1,  
    IMAGE_CEE_UNMANAGED_CALLCONV_STDCALL   = 0x2,  
    IMAGE_CEE_UNMANAGED_CALLCONV_THISCALL  = 0x3,  
    IMAGE_CEE_UNMANAGED_CALLCONV_FASTCALL  = 0x4,  
  
    IMAGE_CEE_CS_CALLCONV_C                = 0x1,  
    IMAGE_CEE_CS_CALLCONV_STDCALL          = 0x2,  
    IMAGE_CEE_CS_CALLCONV_THISCALL         = 0x3,  
    IMAGE_CEE_CS_CALLCONV_FASTCALL         = 0x4  
  
} CorUnmanagedCallingConvention;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_C`|Konwencja wywoływania języka C.|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_STDCALL`|Standardowej konwencji wywoływania.|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_THISCALL`|"This" Konwencji wywołania.|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_FASTCALL`|"Fast" konwencję wywołania.|  
|`IMAGE_CEE_CS_CALLCONV_C`|Nie używany.|  
|`IMAGE_CEE_CS_CALLCONV_STDCALL`|Nie używany.|  
|`IMAGE_CEE_CS_CALLCONV_THISCALL`|Nie używany.|  
|`IMAGE_CEE_CS_CALLCONV_FASTCALL`|Nie używany.|  
  
## <a name="remarks"></a>Uwagi  
 Środowisko CLR nie obsługuje "fast" Konwencja wywoływania w programie .NET Framework w wersji 1.0.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorHdr.h  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
