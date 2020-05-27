---
title: CorCallingConvention — Wyliczenie
ms.date: 03/30/2017
api_name:
- CorCallingConvention
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorCallingConvention
helpviewer_keywords:
- CorCallingConvention enumeration [.NET Framework metadata]
ms.assetid: 69156fbf-7219-43bf-b4b8-b13f1a2fcb86
topic_type:
- apiref
ms.openlocfilehash: 310319e8fefe80017c58706e2beaee5eb1e78422
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007913"
---
# <a name="corcallingconvention-enumeration"></a>CorCallingConvention — Wyliczenie
Zawiera wartości opisujące typy konwencji wywoływania, które są wykonywane w kodzie zarządzanym.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
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
  
|Członek|Opis|  
|------------|-----------------|  
|`IMAGE_CEE_CS_CALLCONV_DEFAULT`|Wskazuje domyślną konwencję wywoływania.|  
|`IMAGE_CEE_CS_CALLCONV_VARARG`|Wskazuje, że metoda przyjmuje zmienną liczbę parametrów.|  
|`IMAGE_CEE_CS_CALLCONV_FIELD`|Wskazuje, że wywołanie należy do pola.|  
|`IMAGE_CEE_CS_CALLCONV_LOCAL_SIG`|Wskazuje, że wywołanie jest metodą lokalną.|  
|`IMAGE_CEE_CS_CALLCONV_PROPERTY`|Wskazuje, że wywołanie jest właściwością.|  
|`IMAGE_CEE_CS_CALLCONV_UNMGD`|Wskazuje, że wywołanie jest niezarządzane.|  
|`IMAGE_CEE_CS_CALLCONV_GENERICINST`|Wskazuje na tworzenie wystąpienia metody ogólnej.|  
|`IMAGE_CEE_CS_CALLCONV_NATIVEVARARG`|Wskazuje 64-bitowego wywołania PInvoke do metody, która przyjmuje zmienną liczbę parametrów.|  
|`IMAGE_CEE_CS_CALLCONV_MAX`|Opisuje nieprawidłową wartość 4-bitową.|  
|`IMAGE_CEE_CS_CALLCONV_MASK`|Wskazuje, że Konwencja wywoływania jest opisana przez cztery ostatnie bity.|  
|`IMAGE_CEE_CS_CALLCONV_HASTHIS`|Wskazuje, że górny bit opisuje `this` parametr.|  
|`IMAGE_CEE_CS_CALLCONV_EXPLICITTHIS`|Wskazuje, że `this` parametr jest jawnie opisany w podpisie.|  
|`IMAGE_CEE_CS_CALLCONV_GENERIC`|Wskazuje sygnaturę metody ogólnej z jawną liczbą argumentów typu. Poprzedza to zwykłą liczbę parametrów.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorHdr. h  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Wyliczenia metadanych](metadata-enumerations.md)
