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
ms.openlocfilehash: e8065a5492884a4b7f5d662737e4beddc6fca5b3
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007601"
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
  
## <a name="members"></a>Elementy członkowskie  
  
|Członek|Opis|  
|------------|-----------------|  
|`MDNotifyDefault`|Powiadamiaj `mdTypeRef` o `mdMethodDef` `mdMemberRef` `mdFieldDef` przeniesieniu tokenów,, lub.|  
|`MDNotifyAll`|Powiadamiaj po przeniesieniu dowolnego tokenu.|  
|`MDNotifyNone`|Nie powiadamiaj, gdy tokeny są przenoszone.|  
|`MDNotifyMethodDef`|Powiadamiaj o `mdMethodDef` przeniesieniu tokenu.|  
|`MDNotifyMemberRef`|Powiadamiaj o `mdMemberRef` przeniesieniu tokenu.|  
|`MDNotifyFieldDef`|Powiadamiaj o `mdFieldDef` przeniesieniu tokenu.|  
|`MDNotifyTypeRef`|Powiadamiaj o `mdTypeRef` przeniesieniu tokenu.|  
|`MDNotifyTypeDef`|Powiadamiaj o `mdTypeDef` przeniesieniu tokenu.|  
|`MDNotifyParamDef`|Powiadamiaj o `mdParamDef` przeniesieniu tokenu.|  
|`MDNotifyInterfaceImpl`|Powiadamiaj o `mdInterfaceImpl` przeniesieniu tokenu.|  
|`MDNotifyProperty`|Powiadamiaj o `mdProperty` przeniesieniu tokenu.|  
|`MDNotifyEvent`|Powiadamiaj o `mdEvent` przeniesieniu tokenu.|  
|`MDNotifySignature`|Powiadamiaj o `mdSignature` przeniesieniu tokenu.|  
|`MDNotifyTypeSpec`|Powiadamiaj o `mdTypeSpec` przeniesieniu tokenu.|  
|`MDNotifyCustomAttribute`|Powiadamiaj o `mdCustomAttribute` przeniesieniu tokenu.|  
|`MDNotifySecurityValue`|Powiadamiaj o `mdSecurityValue` przeniesieniu tokenu.|  
|`MDNotifyPermission`|Powiadamiaj o `mdPermission` przeniesieniu tokenu.|  
|`MDNotifyModuleRef`|Powiadamiaj o `mdModuleRef` przeniesieniu tokenu.|  
|`MDNotifyNameSpace`|Powiadamiaj o `mdNameSpace` przeniesieniu tokenu.|  
|`MDNotifyAssemblyRef`|Powiadamiaj o `mdAssemblyRef` przeniesieniu tokenu.|  
|`MDNotifyFile`|Powiadamiaj o `mdFile` przeniesieniu tokenu.|  
|`MDNotifyExportedType`|Powiadamiaj o `mdExportedType` przeniesieniu tokenu.|  
|`MDNotifyResource`|Powiadamiaj o `mdManifestResource` przeniesieniu tokenu.|  
  
## <a name="remarks"></a>Uwagi  
 Token może być ponownie mapowany (czyli przeniesiony) podczas scalania metadanych.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorHdr. h  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Wyliczenia metadanych](metadata-enumerations.md)
