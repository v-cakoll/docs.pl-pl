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
ms.openlocfilehash: 2985c419b25b8bf76df8fee0f0f37ba9ebee3df7
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007907"
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
|`MDDupAll`|Sprawdź wszystkie tokeny metadanych dla duplikatów.|  
|`MDDupENC`|Nie używany.|  
|`MDNoDupChecks`|Nie sprawdzaj tokenów metadanych dla duplikatów.|  
|`MDDupTypeDef`|Sprawdź duplikaty `mdTypeDef` tokenów.|  
|`MDDupInterfaceImpl`|Sprawdź duplikaty `mdInterfaceImpl` tokenów.|  
|`MDDupMethodDef`|Sprawdź duplikaty `mdMethodDef` tokenów.|  
|`MDDupTypeRef`|Sprawdź duplikaty `mdTypeRef` tokenów.|  
|`MDDupMemberRef`|Sprawdź duplikaty `mdMemberRef` tokenów.|  
|`MDDupCustomAttribute`|Sprawdź duplikaty `mdCustomAttribute` tokenów.|  
|`MDDupParamDef`|Sprawdź duplikaty `mdParamDef` tokenów.|  
|`MDDupPermission`|Sprawdź duplikaty `mdPermission` tokenów.|  
|`MDDupProperty`|Sprawdź duplikaty `mdProperty` tokenów.|  
|`MDDupEvent`|Sprawdź duplikaty `mdEvent` tokenów.|  
|`MDDupFieldDef`|Sprawdź duplikaty `mdFieldDef` tokenów.|  
|`MDDupSignature`|Sprawdź duplikaty `mdSignature` tokenów.|  
|`MDDupModuleRef`|Sprawdź duplikaty `mdModuleRef` tokenów.|  
|`MDDupTypeSpec`|Sprawdź duplikaty `mdTypeSpec` tokenów.|  
|`MDDupImplMap`|Sprawdź duplikaty `mdImplMap` tokenów.|  
|`MDDupAssemblyRef`|Sprawdź duplikaty `mdAssemblyRef` tokenów.|  
|`MDDupFile`|Sprawdź duplikaty `mdFile` tokenów.|  
|`MDDupExportedType`|Sprawdź duplikaty `mdExportedType` tokenów.|  
|`MDDupManifestResource`|Sprawdź duplikaty `mdManifestResource` tokenów.|  
|`MDDupGenericParam`|Sprawdź duplikaty `mdGenericParam` tokenów.|  
|`MDDupMethodSpec`|Sprawdź duplikaty `mdMethodSpec` tokenów.|  
|`MDDupGenericParamConstraint`|Sprawdź duplikaty `mdGenericParamConstraint` tokenów.|  
|`MDDupAssembly`|Sprawdź duplikaty `mdAssembly` tokenów.|  
|`MDDupDefault`|Sprawdź duplikaty `mdMemberRef` `mdTypeRef` tokenów,, `mdSignature` , `mdTypeSpec` i `mdMethodSpec` .|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorHdr. h  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Wyliczenia metadanych](metadata-enumerations.md)
