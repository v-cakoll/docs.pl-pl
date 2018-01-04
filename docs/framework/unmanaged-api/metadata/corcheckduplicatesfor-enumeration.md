---
title: "CorCheckDuplicatesFor — Wyliczenie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorCheckDuplicatesFor
api_location: mscoree.dll
api_type: COM
f1_keywords: CorCheckDuplicatesFor
helpviewer_keywords: CorCheckDuplicatesFor enumeration [.NET Framework metadata]
ms.assetid: d8ec8d3c-70f7-4cc6-9957-68068fd8f49c
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0c5a9376f6d56e2a21ee474e2724ce5eff8f6f63
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="corcheckduplicatesfor-enumeration"></a>CorCheckDuplicatesFor — Wyliczenie
Określa tokenów metadanych, które zostaną sprawdzone duplikatów.  
  
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
|`MDDupAll`|Sprawdź wszystkie tokeny metadanych duplikatów.|  
|`MDDupENC`|Nie używany.|  
|`MDNoDupChecks`|Nie sprawdzaj tokenów metadanych duplikatów.|  
|`MDDupTypeDef`|Sprawdź, czy duplikaty `mdTypeDef` tokenów.|  
|`MDDupInterfaceImpl`|Sprawdź, czy duplikaty `mdInterfaceImpl` tokenów.|  
|`MDDupMethodDef`|Sprawdź, czy duplikaty `mdMethodDef` tokenów.|  
|`MDDupTypeRef`|Sprawdź, czy duplikaty `mdTypeRef` tokenów.|  
|`MDDupMemberRef`|Sprawdź, czy duplikaty `mdMemberRef` tokenów.|  
|`MDDupCustomAttribute`|Sprawdź, czy duplikaty `mdCustomAttribute` tokenów.|  
|`MDDupParamDef`|Sprawdź, czy duplikaty `mdParamDef` tokenów.|  
|`MDDupPermission`|Sprawdź, czy duplikaty `mdPermission` tokenów.|  
|`MDDupProperty`|Sprawdź, czy duplikaty `mdProperty` tokenów.|  
|`MDDupEvent`|Sprawdź, czy duplikaty `mdEvent` tokenów.|  
|`MDDupFieldDef`|Sprawdź, czy duplikaty `mdFieldDef` tokenów.|  
|`MDDupSignature`|Sprawdź, czy duplikaty `mdSignature` tokenów.|  
|`MDDupModuleRef`|Sprawdź, czy duplikaty `mdModuleRef` tokenów.|  
|`MDDupTypeSpec`|Sprawdź, czy duplikaty `mdTypeSpec` tokenów.|  
|`MDDupImplMap`|Sprawdź, czy duplikaty `mdImplMap` tokenów.|  
|`MDDupAssemblyRef`|Sprawdź, czy duplikaty `mdAssemblyRef` tokenów.|  
|`MDDupFile`|Sprawdź, czy duplikaty `mdFile` tokenów.|  
|`MDDupExportedType`|Sprawdź, czy duplikaty `mdExportedType` tokenów.|  
|`MDDupManifestResource`|Sprawdź, czy duplikaty `mdManifestResource` tokenów.|  
|`MDDupGenericParam`|Sprawdź, czy duplikaty `mdGenericParam` tokenów.|  
|`MDDupMethodSpec`|Sprawdź, czy duplikaty `mdMethodSpec` tokenów.|  
|`MDDupGenericParamConstraint`|Sprawdź, czy duplikaty `mdGenericParamConstraint` tokenów.|  
|`MDDupAssembly`|Sprawdź, czy duplikaty `mdAssembly` tokenów.|  
|`MDDupDefault`|Sprawdź, czy duplikaty `mdMemberRef`, `mdTypeRef`, `mdSignature`, `mdTypeSpec`, i `mdMethodSpec` tokenów.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorHdr.h  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
