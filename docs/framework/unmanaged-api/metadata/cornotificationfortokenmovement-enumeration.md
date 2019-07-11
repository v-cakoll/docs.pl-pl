---
title: CorNotificationForTokenMovement — Wyliczenie
ms.date: 03/30/2017
api_name:
- CorNotificationForTokenMovement
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorNotificationForTokenMovement
helpviewer_keywords:
- CorNotificationForTokenMovement enumeration [.NET Framework metadata]
ms.assetid: 1edd1670-976a-4fc8-bef7-7c41e60ad989
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7a7859bd890a2ecc10b5117f697ff8b06ad569f6
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781697"
---
# <a name="cornotificationfortokenmovement-enumeration"></a>CorNotificationForTokenMovement — Wyliczenie
Określa powiadomień, które będą wysyłane do klienta metadanych interfejsu API, gdy wystąpi tokenu ponowne mapowanie.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef enum CorNotificationForTokenMovement {  
  
    MDNotifyDefault             = 0x0000000f,  
    MDNotifyAll                 = 0xffffffff,  
    MDNotifyNone                = 0x00000000,  
    MDNotifyMethodDef           = 0x00000001,  
    MDNotifyMemberRef           = 0x00000002,  
    MDNotifyFieldDef            = 0x00000004,  
    MDNotifyTypeRef             = 0x00000008,  
  
    MDNotifyTypeDef             = 0x00000010,  
    MDNotifyParamDef            = 0x00000020,  
    MDNotifyInterfaceImpl       = 0x00000040,  
    MDNotifyProperty            = 0x00000080,  
    MDNotifyEvent               = 0x00000100,  
    MDNotifySignature           = 0x00000200,  
    MDNotifyTypeSpec            = 0x00000400,  
    MDNotifyCustomAttribute     = 0x00000800,  
    MDNotifySecurityValue       = 0x00001000,  
    MDNotifyPermission          = 0x00002000,  
    MDNotifyModuleRef           = 0x00004000,  
  
    MDNotifyNameSpace           = 0x00008000,  
  
    MDNotifyAssemblyRef         = 0x01000000,  
    MDNotifyFile                = 0x02000000,  
    MDNotifyExportedType        = 0x04000000,  
    MDNotifyResource            = 0x08000000  
  
} CorNotificationForTokenMovement;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`MDNotifyDefault`|Powiadom mnie, kiedy `mdTypeRef`, `mdMethodDef`, `mdMemberRef`, lub `mdFieldDef` przenoszenia tokenów.|  
|`MDNotifyAll`|Powiadomienie, gdy dowolny token.|  
|`MDNotifyNone`|Nie powiadamiaj podczas przenoszenia tokenów.|  
|`MDNotifyMethodDef`|Powiadom mnie, kiedy `mdMethodDef` przenosi tokenu.|  
|`MDNotifyMemberRef`|Powiadom mnie, kiedy `mdMemberRef` przenosi tokenu.|  
|`MDNotifyFieldDef`|Powiadom mnie, kiedy `mdFieldDef` przenosi tokenu.|  
|`MDNotifyTypeRef`|Powiadom mnie, kiedy `mdTypeRef` przenosi tokenu.|  
|`MDNotifyTypeDef`|Powiadom mnie, kiedy `mdTypeDef` przenosi tokenu.|  
|`MDNotifyParamDef`|Powiadom mnie, kiedy `mdParamDef` przenosi tokenu.|  
|`MDNotifyInterfaceImpl`|Powiadom mnie, kiedy `mdInterfaceImpl` przenosi tokenu.|  
|`MDNotifyProperty`|Powiadom mnie, kiedy `mdProperty` przenosi tokenu.|  
|`MDNotifyEvent`|Powiadom mnie, kiedy `mdEvent` przenosi tokenu.|  
|`MDNotifySignature`|Powiadom mnie, kiedy `mdSignature` przenosi tokenu.|  
|`MDNotifyTypeSpec`|Powiadom mnie, kiedy `mdTypeSpec` przenosi tokenu.|  
|`MDNotifyCustomAttribute`|Powiadom mnie, kiedy `mdCustomAttribute` przenosi tokenu.|  
|`MDNotifySecurityValue`|Powiadom mnie, kiedy `mdSecurityValue` przenosi tokenu.|  
|`MDNotifyPermission`|Powiadom mnie, kiedy `mdPermission` przenosi tokenu.|  
|`MDNotifyModuleRef`|Powiadom mnie, kiedy `mdModuleRef` przenosi tokenu.|  
|`MDNotifyNameSpace`|Powiadom mnie, kiedy `mdNameSpace` przenosi tokenu.|  
|`MDNotifyAssemblyRef`|Powiadom mnie, kiedy `mdAssemblyRef` przenosi tokenu.|  
|`MDNotifyFile`|Powiadom mnie, kiedy `mdFile` przenosi tokenu.|  
|`MDNotifyExportedType`|Powiadom mnie, kiedy `mdExportedType` przenosi tokenu.|  
|`MDNotifyResource`|Powiadom mnie, kiedy `mdManifestResource` przenosi tokenu.|  
  
## <a name="remarks"></a>Uwagi  
 Tokenu można ponownie zamapować (który poruszyły) podczas scalania metadanych.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorHdr.h  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Wyliczenia metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
