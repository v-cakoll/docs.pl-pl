---
title: "CorCallingConvention — Wyliczenie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorCallingConvention
api_location: mscoree.dll
api_type: COM
f1_keywords: CorCallingConvention
helpviewer_keywords: CorCallingConvention enumeration [.NET Framework metadata]
ms.assetid: 69156fbf-7219-43bf-b4b8-b13f1a2fcb86
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 154fbcc393bb56ab2c249a4928a4451dced9761a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="corcallingconvention-enumeration"></a>CorCallingConvention — Wyliczenie
Zawiera wartości, które opisują typy konwencji wywoływania, które zostały wprowadzone w kodzie zarządzanym.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef enum CorCallingConvention  
{  
    IMAGE_CEE_CS_CALLCONV_DEFAULT       = 0x0,  
  
    IMAGE_CEE_CS_CALLCONV_VARARG        = 0x5,  
    IMAGE_CEE_CS_CALLCONV_FIELD         = 0x6,  
    IMAGE_CEE_CS_CALLCONV_LOCAL_SIG     = 0x7,  
    IMAGE_CEE_CS_CALLCONV_PROPERTY      = 0x8,  
    IMAGE_CEE_CS_CALLCONV_UNMGD         = 0x9,  
    IMAGE_CEE_CS_CALLCONV_GENERICINST   = 0xa,  
    IMAGE_CEE_CS_CALLCONV_NATIVEVARARG  = 0xb,  
    IMAGE_CEE_CS_CALLCONV_MAX           = 0xc,  
  
    IMAGE_CEE_CS_CALLCONV_MASK          = 0x0f,  
    IMAGE_CEE_CS_CALLCONV_HASTHIS       = 0x20,  
    IMAGE_CEE_CS_CALLCONV_EXPLICITTHIS  = 0x40,  
    IMAGE_CEE_CS_CALLCONV_GENERIC       = 0x10  
  
} CorCallingConvention;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`IMAGE_CEE_CS_CALLCONV_DEFAULT`|Wskazuje domyślną konwencję wywoływania.|  
|`IMAGE_CEE_CS_CALLCONV_VARARG`|Wskazuje, że metoda korzysta z różną liczbą parametrów.|  
|`IMAGE_CEE_CS_CALLCONV_FIELD`|Wskazuje, że wywołanie jest do pola.|  
|`IMAGE_CEE_CS_CALLCONV_LOCAL_SIG`|Oznacza wywołania do metody lokalnego.|  
|`IMAGE_CEE_CS_CALLCONV_PROPERTY`|Wskazuje, że wywołanie jest właściwością.|  
|`IMAGE_CEE_CS_CALLCONV_UNMGD`|Wskazuje, że wywołanie jest niezarządzany.|  
|`IMAGE_CEE_CS_CALLCONV_GENERICINST`|Wskazuje wystąpienia metody ogólnej.|  
|`IMAGE_CEE_CS_CALLCONV_NATIVEVARARG`|Wskazuje 64-bitowych wywołanie funkcji PInvoke do metody, która przyjmuje zmienną liczbę parametrów.|  
|`IMAGE_CEE_CS_CALLCONV_MAX`|W tym artykule opisano nieprawidłową wartość 4-bitowy.|  
|`IMAGE_CEE_CS_CALLCONV_MASK`|Wskazuje, czy za pomocą liczby bitów dolnej czterech opisano konwencji wywołania.|  
|`IMAGE_CEE_CS_CALLCONV_HASTHIS`|Wskazuje opisujący top bitu `this` parametru.|  
|`IMAGE_CEE_CS_CALLCONV_EXPLICITTHIS`|Oznacza to, że `this` parametru jest opisana jawnie w podpisie.|  
|`IMAGE_CEE_CS_CALLCONV_GENERIC`|Określa podpis metody ogólnej z jawnym liczby argumentów typu. Liczba parametrów zwykłej to poprzedza.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorHdr.h  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
