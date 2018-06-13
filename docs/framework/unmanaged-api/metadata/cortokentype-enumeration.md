---
title: CorTokenType — Wyliczenie
ms.date: 03/30/2017
api_name:
- CorTokenType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorTokenType
helpviewer_keywords:
- CorTokenType enumeration [.NET Framework metadata]
ms.assetid: 93c9a369-225f-4eff-9b78-3fbee4902cf1
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 769802eae048427325af9807d788b1fbc5a15665
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33448435"
---
# <a name="cortokentype-enumeration"></a>CorTokenType — Wyliczenie
Wskazuje typ tokenu metadanych.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef enum CorTokenType {  
  
    mdtModule                       = 0x00000000,  
    mdtTypeRef                      = 0x01000000,  
    mdtTypeDef                      = 0x02000000,  
    mdtFieldDef                     = 0x04000000,  
    mdtMethodDef                    = 0x06000000,  
    mdtParamDef                     = 0x08000000,  
    mdtInterfaceImpl                = 0x09000000,  
    mdtMemberRef                    = 0x0a000000,  
    mdtCustomAttribute              = 0x0c000000,  
    mdtPermission                   = 0x0e000000,  
    mdtSignature                    = 0x11000000,  
    mdtEvent                        = 0x14000000,  
    mdtProperty                     = 0x17000000,  
    mdtModuleRef                    = 0x1a000000,  
    mdtTypeSpec                     = 0x1b000000,  
    mdtAssembly                     = 0x20000000,  
    mdtAssemblyRef                  = 0x23000000,  
    mdtFile                         = 0x26000000,  
    mdtExportedType                 = 0x27000000,  
    mdtManifestResource             = 0x28000000,  
    mdtGenericParam                 = 0x2a000000,  
    mdtMethodSpec                   = 0x2b000000,  
    mdtGenericParamConstraint       = 0x2c000000,  
    mdtString                       = 0x70000000,  
    mdtName                         = 0x71000000,  
    mdtBaseType                     = 0x72000000  
  
} CorTokenType;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`mdtModule`|`mdModule` Tokenu.|  
|`mdtTypeRef`|`mdTypeRef` Tokenu.|  
|`mdtTypeDef`|`mdTypeDef` Tokenu.|  
|`mdtFieldDef`|`mdFieldDef` Tokenu.|  
|`mdtMethodDef`|`mdMethodDef` Tokenu.|  
|`mdtParamDef`|`mdParamDef` Tokenu.|  
|`mdtInterfaceImpl`|`mdInterfaceImpl` Tokenu.|  
|`mdtMemberRef`|`mdMemberRef` Tokenu.|  
|`mdtCustomAttribute`|`mdCustomAttribute` Tokenu.|  
|`mdtPermission`|`mdPermission` Tokenu.|  
|`mdtSignature`|`mdSignature` Tokenu.|  
|`mdtEvent`|`mdEvent` Tokenu.|  
|`mdtProperty`|`mdProperty` Tokenu.|  
|`mdtModuleRef`|`mdModuleRef` Tokenu.|  
|`mdtTypeSpec`|`mdTypeSpec` Tokenu.|  
|`mdtAssembly`|`mdAssembly` Tokenu.|  
|`mdtAssemblyRef`|`mdAssemblyRef` Tokenu.|  
|`mdtFile`|`mdFile` Tokenu.|  
|`mdtExportedType`|`mdExportedType` Tokenu.|  
|`mdtManifestResource`|`mdManifestResource` Tokenu.|  
|`mdtGenericParam`|`mdGenericParam` Tokenu.|  
|`mdtMethodSpec`|`mdMethodSpec` Tokenu.|  
|`mdtGenericParamConstraint`|`mdGenericParamConstraint` Tokenu.|  
|`mdtString`|`mdString` Tokenu.|  
|`mdtName`|`mdName` Tokenu.|  
|`mdtBaseType`|Nie używany.|  
  
## <a name="remarks"></a>Uwagi  
 Każda wartość jest równa wartości bajtu najwyższego odpowiedniego token metadanych.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorHdr.h  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
