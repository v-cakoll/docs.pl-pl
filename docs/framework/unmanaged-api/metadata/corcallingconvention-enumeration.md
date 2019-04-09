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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 44a4b5903cec2249eb1e176381fe3d8e600dd5e6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59145876"
---
# <a name="corcallingconvention-enumeration"></a>CorCallingConvention — Wyliczenie
Zawiera wartości, które opisują rodzaje konwencji wywoływania, które zostały wprowadzone w kodzie zarządzanym.  
  
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
|`IMAGE_CEE_CS_CALLCONV_VARARG`|Wskazuje, że ta metoda przyjmuje zmienną liczbę parametrów.|  
|`IMAGE_CEE_CS_CALLCONV_FIELD`|Wskazuje, że wywołanie się do pola.|  
|`IMAGE_CEE_CS_CALLCONV_LOCAL_SIG`|Wskazuje wywołanie do metody lokalnej.|  
|`IMAGE_CEE_CS_CALLCONV_PROPERTY`|Wskazuje, że wywołanie jest właściwością.|  
|`IMAGE_CEE_CS_CALLCONV_UNMGD`|Wskazuje, że wywołanie jest niezarządzany.|  
|`IMAGE_CEE_CS_CALLCONV_GENERICINST`|Wskazuje wystąpienia metody rodzajowej.|  
|`IMAGE_CEE_CS_CALLCONV_NATIVEVARARG`|Wskazuje wywołania metody, która przyjmuje zmienną liczbę parametrów funkcji PInvoke 64-bitowych.|  
|`IMAGE_CEE_CS_CALLCONV_MAX`|W tym artykule opisano nieprawidłową wartość 4-bitowy.|  
|`IMAGE_CEE_CS_CALLCONV_MASK`|Wskazuje, że Konwencja wywołania jest opisana przez dolnej cztery bity.|  
|`IMAGE_CEE_CS_CALLCONV_HASTHIS`|Wskazuje, który opisuje bitu najwyższego `this` parametru.|  
|`IMAGE_CEE_CS_CALLCONV_EXPLICITTHIS`|Oznacza to, że `this` parametr jest jawnie opisany w podpisie.|  
|`IMAGE_CEE_CS_CALLCONV_GENERIC`|Wskazuje sygnaturę metody ogólnej przy użyciu jawne liczby argumentów typu. To poprzedza liczba zwykłych parametrów.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorHdr.h  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Wyliczenia metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
