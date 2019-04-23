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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d04f5589ecffbcde59a6ffbe4f3d6c5f0b1040cd
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59074875"
---
# <a name="corcheckduplicatesfor-enumeration"></a>CorCheckDuplicatesFor — Wyliczenie
Określa tokeny metadanych, które będą sprawdzane duplikatów.  
  
## <a name="syntax"></a>Składnia  
  
```  
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
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`MDDupAll`|Sprawdź wszystkie tokeny metadanych dla duplikatów.|  
|`MDDupENC`|Nie używany.|  
|`MDNoDupChecks`|Nie zaznaczaj tokeny metadanych dla duplikatów.|  
|`MDDupTypeDef`|Sprawdź duplikaty z `mdTypeDef` tokenów.|  
|`MDDupInterfaceImpl`|Sprawdź duplikaty z `mdInterfaceImpl` tokenów.|  
|`MDDupMethodDef`|Sprawdź duplikaty z `mdMethodDef` tokenów.|  
|`MDDupTypeRef`|Sprawdź duplikaty z `mdTypeRef` tokenów.|  
|`MDDupMemberRef`|Sprawdź duplikaty z `mdMemberRef` tokenów.|  
|`MDDupCustomAttribute`|Sprawdź duplikaty z `mdCustomAttribute` tokenów.|  
|`MDDupParamDef`|Sprawdź duplikaty z `mdParamDef` tokenów.|  
|`MDDupPermission`|Sprawdź duplikaty z `mdPermission` tokenów.|  
|`MDDupProperty`|Sprawdź duplikaty z `mdProperty` tokenów.|  
|`MDDupEvent`|Sprawdź duplikaty z `mdEvent` tokenów.|  
|`MDDupFieldDef`|Sprawdź duplikaty z `mdFieldDef` tokenów.|  
|`MDDupSignature`|Sprawdź duplikaty z `mdSignature` tokenów.|  
|`MDDupModuleRef`|Sprawdź duplikaty z `mdModuleRef` tokenów.|  
|`MDDupTypeSpec`|Sprawdź duplikaty z `mdTypeSpec` tokenów.|  
|`MDDupImplMap`|Sprawdź duplikaty z `mdImplMap` tokenów.|  
|`MDDupAssemblyRef`|Sprawdź duplikaty z `mdAssemblyRef` tokenów.|  
|`MDDupFile`|Sprawdź duplikaty z `mdFile` tokenów.|  
|`MDDupExportedType`|Sprawdź duplikaty z `mdExportedType` tokenów.|  
|`MDDupManifestResource`|Sprawdź duplikaty z `mdManifestResource` tokenów.|  
|`MDDupGenericParam`|Sprawdź duplikaty z `mdGenericParam` tokenów.|  
|`MDDupMethodSpec`|Sprawdź duplikaty z `mdMethodSpec` tokenów.|  
|`MDDupGenericParamConstraint`|Sprawdź duplikaty z `mdGenericParamConstraint` tokenów.|  
|`MDDupAssembly`|Sprawdź duplikaty z `mdAssembly` tokenów.|  
|`MDDupDefault`|Sprawdź duplikaty z `mdMemberRef`, `mdTypeRef`, `mdSignature`, `mdTypeSpec`, i `mdMethodSpec` tokenów.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorHdr.h  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Wyliczenia metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
