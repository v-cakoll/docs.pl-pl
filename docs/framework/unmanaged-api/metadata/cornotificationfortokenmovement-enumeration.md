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
ms.openlocfilehash: 411fad0accb59431f776c5bd66e8bd3027ddd907
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450148"
---
# <a name="cornotificationfortokenmovement-enumeration"></a>CorNotificationForTokenMovement — Wyliczenie
Określa powiadomienia, które będą wysyłane do klienta API metadanych, gdy następuje ponowne mapowanie tokenu.  
  
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
  
## <a name="members"></a>Members  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`MDNotifyDefault`|Powiadamiaj po przeniesieniu tokenów `mdTypeRef`, `mdMethodDef`, `mdMemberRef`lub `mdFieldDef`.|  
|`MDNotifyAll`|Powiadamiaj po przeniesieniu dowolnego tokenu.|  
|`MDNotifyNone`|Nie powiadamiaj, gdy tokeny są przenoszone.|  
|`MDNotifyMethodDef`|Powiadamiaj po przeniesieniu tokenu `mdMethodDef`.|  
|`MDNotifyMemberRef`|Powiadamiaj po przeniesieniu tokenu `mdMemberRef`.|  
|`MDNotifyFieldDef`|Powiadamiaj po przeniesieniu tokenu `mdFieldDef`.|  
|`MDNotifyTypeRef`|Powiadamiaj po przeniesieniu tokenu `mdTypeRef`.|  
|`MDNotifyTypeDef`|Powiadamiaj po przeniesieniu tokenu `mdTypeDef`.|  
|`MDNotifyParamDef`|Powiadamiaj po przeniesieniu tokenu `mdParamDef`.|  
|`MDNotifyInterfaceImpl`|Powiadamiaj po przeniesieniu tokenu `mdInterfaceImpl`.|  
|`MDNotifyProperty`|Powiadamiaj po przeniesieniu tokenu `mdProperty`.|  
|`MDNotifyEvent`|Powiadamiaj po przeniesieniu tokenu `mdEvent`.|  
|`MDNotifySignature`|Powiadamiaj po przeniesieniu tokenu `mdSignature`.|  
|`MDNotifyTypeSpec`|Powiadamiaj po przeniesieniu tokenu `mdTypeSpec`.|  
|`MDNotifyCustomAttribute`|Powiadamiaj po przeniesieniu tokenu `mdCustomAttribute`.|  
|`MDNotifySecurityValue`|Powiadamiaj po przeniesieniu tokenu `mdSecurityValue`.|  
|`MDNotifyPermission`|Powiadamiaj po przeniesieniu tokenu `mdPermission`.|  
|`MDNotifyModuleRef`|Powiadamiaj po przeniesieniu tokenu `mdModuleRef`.|  
|`MDNotifyNameSpace`|Powiadamiaj po przeniesieniu tokenu `mdNameSpace`.|  
|`MDNotifyAssemblyRef`|Powiadamiaj po przeniesieniu tokenu `mdAssemblyRef`.|  
|`MDNotifyFile`|Powiadamiaj po przeniesieniu tokenu `mdFile`.|  
|`MDNotifyExportedType`|Powiadamiaj po przeniesieniu tokenu `mdExportedType`.|  
|`MDNotifyResource`|Powiadamiaj po przeniesieniu tokenu `mdManifestResource`.|  
  
## <a name="remarks"></a>Uwagi  
 Token może być ponownie mapowany (czyli przeniesiony) podczas scalania metadanych.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorHdr. h  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Wyliczenia metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
