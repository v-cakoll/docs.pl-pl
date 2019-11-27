---
title: IMetaDataAssemblyImport — Interfejs
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport
helpviewer_keywords:
- IMetaDataAssemblyImport interface [.NET Framework metadata]
ms.assetid: 29c6fba5-4cea-417d-b484-7ed22ebff1c9
topic_type:
- apiref
ms.openlocfilehash: 289e26868ff2eb9e1d97cf084e9a888815062ea4
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436307"
---
# <a name="imetadataassemblyimport-interface"></a>IMetaDataAssemblyImport — Interfejs
Zapewnia metody umożliwiające dostęp i sprawdzanie zawartości manifestu zestawu.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[CloseEnum, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-closeenum-method.md)|Zwalnia dojście do określonego modułu wyliczającego.|  
|[EnumAssemblyRefs, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enumassemblyrefs-method.md)|Pobiera wskaźnik interfejsu do modułu wyliczającego, który zawiera `mdAssemblyRef` tokeny zestawów, do których odwołuje się zestaw w bieżącym zakresie metadanych.|  
|[EnumExportedTypes, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enumexportedtypes-method.md)|Pobiera wskaźnik interfejsu do modułu wyliczającego, który zawiera `mdExportedType` tokeny typów COM, do których odwołuje się zestaw w bieżącym zakresie metadanych.|  
|[EnumFiles, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enumfiles-method.md)|Pobiera wskaźnik interfejsu do modułu wyliczającego, który zawiera `mdFile` tokeny plików, do których odwołuje się zestaw w bieżącym zakresie metadanych.|  
|[EnumManifestResources, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enummanifestresources-method.md)|Pobiera wskaźnik interfejsu do modułu wyliczającego, który zawiera `mdManifestResource` tokeny zasobów, do których odwołuje się zestaw w bieżącym zakresie metadanych.|  
|[FindAssembliesByName, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-findassembliesbyname-method.md)|Pobiera tablicę `mdAssemblyRef` tokenów dla zestawów o określonej nazwie.|  
|[FindExportedTypeByName, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-findexportedtypebyname-method.md)|Pobiera token `mdExportedType` dla typu COM o określonej nazwie.|  
|[FindManifestResourceByName, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-findmanifestresourcebyname-method.md)|Pobiera token `mdManifestResource` dla zasobu o określonej nazwie.|  
|[GetAssemblyFromScope, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getassemblyfromscope-method.md)|Pobiera token dla zestawu w bieżącym zakresie metadanych.|  
|[GetAssemblyProps, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getassemblyprops-method.md)|Pobiera ustawienia właściwości określonego zestawu.|  
|[GetAssemblyRefProps, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getassemblyrefprops-method.md)|Pobiera ustawienia właściwości określonego tokenu `mdAssemblyRef`.|  
|[GetExportedTypeProps, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getexportedtypeprops-method.md)|Pobiera ustawienia właściwości określonego typu COM.|  
|[GetFileProps, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getfileprops-method.md)|Pobiera ustawienia właściwości określonego pliku.|  
|[GetManifestResourceProps, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getmanifestresourceprops-method.md)|Pobiera ustawienia właściwości określonego zasobu manifestu.|  
  
## <a name="requirements"></a>Wymagania  
 **Platforma:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor. h  
  
 **Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Interfejsy metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [IMetaDataAssemblyEmit, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
