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
ms.openlocfilehash: 6b551743227dc1c6069796038782a515e6dbe8c4
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74443784"
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
  
## <a name="members"></a>Members  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`MDDupAll`|Sprawdź wszystkie tokeny metadanych dla duplikatów.|  
|`MDDupENC`|Nie jest używany.|  
|`MDNoDupChecks`|Nie sprawdzaj tokenów metadanych dla duplikatów.|  
|`MDDupTypeDef`|Sprawdź duplikaty tokenów `mdTypeDef`.|  
|`MDDupInterfaceImpl`|Sprawdź duplikaty tokenów `mdInterfaceImpl`.|  
|`MDDupMethodDef`|Sprawdź duplikaty tokenów `mdMethodDef`.|  
|`MDDupTypeRef`|Sprawdź duplikaty tokenów `mdTypeRef`.|  
|`MDDupMemberRef`|Sprawdź duplikaty tokenów `mdMemberRef`.|  
|`MDDupCustomAttribute`|Sprawdź duplikaty tokenów `mdCustomAttribute`.|  
|`MDDupParamDef`|Sprawdź duplikaty tokenów `mdParamDef`.|  
|`MDDupPermission`|Sprawdź duplikaty tokenów `mdPermission`.|  
|`MDDupProperty`|Sprawdź duplikaty tokenów `mdProperty`.|  
|`MDDupEvent`|Sprawdź duplikaty tokenów `mdEvent`.|  
|`MDDupFieldDef`|Sprawdź duplikaty tokenów `mdFieldDef`.|  
|`MDDupSignature`|Sprawdź duplikaty tokenów `mdSignature`.|  
|`MDDupModuleRef`|Sprawdź duplikaty tokenów `mdModuleRef`.|  
|`MDDupTypeSpec`|Sprawdź duplikaty tokenów `mdTypeSpec`.|  
|`MDDupImplMap`|Sprawdź duplikaty tokenów `mdImplMap`.|  
|`MDDupAssemblyRef`|Sprawdź duplikaty tokenów `mdAssemblyRef`.|  
|`MDDupFile`|Sprawdź duplikaty tokenów `mdFile`.|  
|`MDDupExportedType`|Sprawdź duplikaty tokenów `mdExportedType`.|  
|`MDDupManifestResource`|Sprawdź duplikaty tokenów `mdManifestResource`.|  
|`MDDupGenericParam`|Sprawdź duplikaty tokenów `mdGenericParam`.|  
|`MDDupMethodSpec`|Sprawdź duplikaty tokenów `mdMethodSpec`.|  
|`MDDupGenericParamConstraint`|Sprawdź duplikaty tokenów `mdGenericParamConstraint`.|  
|`MDDupAssembly`|Sprawdź duplikaty tokenów `mdAssembly`.|  
|`MDDupDefault`|Sprawdź duplikaty tokenów `mdMemberRef`, `mdTypeRef`, `mdSignature`, `mdTypeSpec`i `mdMethodSpec`.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorHdr. h  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Wyliczenia metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
