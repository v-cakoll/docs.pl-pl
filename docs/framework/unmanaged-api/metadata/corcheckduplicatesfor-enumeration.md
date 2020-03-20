---
title: CorCheckDuplicatesFor — Wyliczenie
ms.date: 03/30/2017
api_name:
- CorCheckDuplicatesFor
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorCheckDuplicatesFor
helpviewer_keywords:
- CorCheckDuplicatesFor enumeration [.NET Framework metadata]
ms.assetid: d8ec8d3c-70f7-4cc6-9957-68068fd8f49c
topic_type:
- apiref
ms.openlocfilehash: 04dc12ab4d7d178ebf1575a3260f9f4981972782
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176191"
---
# <a name="corcheckduplicatesfor-enumeration"></a>CorCheckDuplicatesFor — Wyliczenie
Określa tokeny metadanych, które będą sprawdzane pod kątem duplikatów.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef enum CorCheckDuplicatesFor {  
  
    MDDupAll                    = 0xffffffff,  
    MDDupENC                    = MDDupAll,  
    MDNoDupChecks               = 0x00000000,  
    MDDupTypeDef                = 0x00000001,  
    MDDupInterfaceImpl          = 0x00000002,  
    MDDupMethodDef              = 0x00000004,  
    MDDupTypeRef                = 0x00000008,  
    MDDupMemberRef              = 0x00000010,  
    MDDupCustomAttribute        = 0x00000020,  
    MDDupParamDef               = 0x00000040,  
    MDDupPermission             = 0x00000080,  
    MDDupProperty               = 0x00000100,  
    MDDupEvent                  = 0x00000200,  
    MDDupFieldDef               = 0x00000400,  
    MDDupSignature              = 0x00000800,  
    MDDupModuleRef              = 0x00001000,  
    MDDupTypeSpec               = 0x00002000,  
    MDDupImplMap                = 0x00004000,  
    MDDupAssemblyRef            = 0x00008000,  
    MDDupFile                   = 0x00010000,  
    MDDupExportedType           = 0x00020000,  
    MDDupManifestResource       = 0x00040000,  
    MDDupGenericParam           = 0x00080000,  
    MDDupMethodSpec             = 0x00100000,  
    MDDupGenericParamConstraint = 0x00200000,  
  
    MDDupAssembly               = 0x10000000,  
  
    MDDupDefault =
        MDNoDupChecks | MDDupTypeRef | MDDupMemberRef |
        MDDupSignature | MDDupTypeSpec | MDDupMethodSpec  
  
} CorCheckDuplicatesFor;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Członek|Opis|  
|------------|-----------------|  
|`MDDupAll`|Sprawdź wszystkie tokeny metadanych pod kątem duplikatów.|  
|`MDDupENC`|Nie używany.|  
|`MDNoDupChecks`|Nie należy sprawdzać tokenów metadanych pod kątem duplikatów.|  
|`MDDupTypeDef`|Sprawdź, czy `mdTypeDef` nie ma duplikatów tokenów.|  
|`MDDupInterfaceImpl`|Sprawdź, czy `mdInterfaceImpl` nie ma duplikatów tokenów.|  
|`MDDupMethodDef`|Sprawdź, czy `mdMethodDef` nie ma duplikatów tokenów.|  
|`MDDupTypeRef`|Sprawdź, czy `mdTypeRef` nie ma duplikatów tokenów.|  
|`MDDupMemberRef`|Sprawdź, czy `mdMemberRef` nie ma duplikatów tokenów.|  
|`MDDupCustomAttribute`|Sprawdź, czy `mdCustomAttribute` nie ma duplikatów tokenów.|  
|`MDDupParamDef`|Sprawdź, czy `mdParamDef` nie ma duplikatów tokenów.|  
|`MDDupPermission`|Sprawdź, czy `mdPermission` nie ma duplikatów tokenów.|  
|`MDDupProperty`|Sprawdź, czy `mdProperty` nie ma duplikatów tokenów.|  
|`MDDupEvent`|Sprawdź, czy `mdEvent` nie ma duplikatów tokenów.|  
|`MDDupFieldDef`|Sprawdź, czy `mdFieldDef` nie ma duplikatów tokenów.|  
|`MDDupSignature`|Sprawdź, czy `mdSignature` nie ma duplikatów tokenów.|  
|`MDDupModuleRef`|Sprawdź, czy `mdModuleRef` nie ma duplikatów tokenów.|  
|`MDDupTypeSpec`|Sprawdź, czy `mdTypeSpec` nie ma duplikatów tokenów.|  
|`MDDupImplMap`|Sprawdź, czy `mdImplMap` nie ma duplikatów tokenów.|  
|`MDDupAssemblyRef`|Sprawdź, czy `mdAssemblyRef` nie ma duplikatów tokenów.|  
|`MDDupFile`|Sprawdź, czy `mdFile` nie ma duplikatów tokenów.|  
|`MDDupExportedType`|Sprawdź, czy `mdExportedType` nie ma duplikatów tokenów.|  
|`MDDupManifestResource`|Sprawdź, czy `mdManifestResource` nie ma duplikatów tokenów.|  
|`MDDupGenericParam`|Sprawdź, czy `mdGenericParam` nie ma duplikatów tokenów.|  
|`MDDupMethodSpec`|Sprawdź, czy `mdMethodSpec` nie ma duplikatów tokenów.|  
|`MDDupGenericParamConstraint`|Sprawdź, czy `mdGenericParamConstraint` nie ma duplikatów tokenów.|  
|`MDDupAssembly`|Sprawdź, czy `mdAssembly` nie ma duplikatów tokenów.|  
|`MDDupDefault`|`mdMemberRef`Sprawdź, czy `mdTypeRef` `mdSignature`nie ma `mdTypeSpec`duplikatów , , i `mdMethodSpec` tokenów.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorHdr.h  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Wyliczenia metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
