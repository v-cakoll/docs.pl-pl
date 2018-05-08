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
ms.openlocfilehash: 96ab659e6ab6cc9601c0e9a1ab511da92905c242
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="cornotificationfortokenmovement-enumeration"></a>CorNotificationForTokenMovement — Wyliczenie
Określa powiadomień, które zostaną wysłane do klienta metadanych interfejsu API po wystąpieniu tokenu ponownego mapowania.  
  
## <a name="syntax"></a>Składnia  
  
```  
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
|`MDNotifyDefault`|Powiadom `mdTypeRef`, `mdMethodDef`, `mdMemberRef`, lub `mdFieldDef` przenoszenia tokenów.|  
|`MDNotifyAll`|Powiadamianie Przenosi dowolny token.|  
|`MDNotifyNone`|Nie powiadamiaj przenoszenia tokenów.|  
|`MDNotifyMethodDef`|Powiadom `mdMethodDef` token przenosi.|  
|`MDNotifyMemberRef`|Powiadom `mdMemberRef` token przenosi.|  
|`MDNotifyFieldDef`|Powiadom `mdFieldDef` token przenosi.|  
|`MDNotifyTypeRef`|Powiadom `mdTypeRef` token przenosi.|  
|`MDNotifyTypeDef`|Powiadom `mdTypeDef` token przenosi.|  
|`MDNotifyParamDef`|Powiadom `mdParamDef` token przenosi.|  
|`MDNotifyInterfaceImpl`|Powiadom `mdInterfaceImpl` token przenosi.|  
|`MDNotifyProperty`|Powiadom `mdProperty` token przenosi.|  
|`MDNotifyEvent`|Powiadom `mdEvent` token przenosi.|  
|`MDNotifySignature`|Powiadom `mdSignature` token przenosi.|  
|`MDNotifyTypeSpec`|Powiadom `mdTypeSpec` token przenosi.|  
|`MDNotifyCustomAttribute`|Powiadom `mdCustomAttribute` token przenosi.|  
|`MDNotifySecurityValue`|Powiadom `mdSecurityValue` token przenosi.|  
|`MDNotifyPermission`|Powiadom `mdPermission` token przenosi.|  
|`MDNotifyModuleRef`|Powiadom `mdModuleRef` token przenosi.|  
|`MDNotifyNameSpace`|Powiadom `mdNameSpace` token przenosi.|  
|`MDNotifyAssemblyRef`|Powiadom `mdAssemblyRef` token przenosi.|  
|`MDNotifyFile`|Powiadom `mdFile` token przenosi.|  
|`MDNotifyExportedType`|Powiadom `mdExportedType` token przenosi.|  
|`MDNotifyResource`|Powiadom `mdManifestResource` token przenosi.|  
  
## <a name="remarks"></a>Uwagi  
 Tokenu można ponownie zamapować (który przeniesiona) podczas scalania metadanych.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorHdr.h  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
