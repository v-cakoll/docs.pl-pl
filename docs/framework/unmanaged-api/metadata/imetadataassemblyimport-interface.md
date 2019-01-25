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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9f213bcb9f87c34d23b53c2016bd841aae7c7194
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54540285"
---
# <a name="imetadataassemblyimport-interface"></a>IMetaDataAssemblyImport — Interfejs
Udostępnia metody dostępu i sprawdź zawartość w manifeście zestawu.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[CloseEnum, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-closeenum-method.md)|Zwalnia dojścia do określonego modułu wyliczającego.|  
|[EnumAssemblyRefs, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enumassemblyrefs-method.md)|Pobiera moduł wyliczający, który zawiera wskaźnik interfejsu `mdAssemblyRef` tokenów zestawów odwołuje się zestaw w bieżącym zakresie metadanych.|  
|[EnumExportedTypes, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enumexportedtypes-method.md)|Pobiera moduł wyliczający, który zawiera wskaźnik interfejsu `mdExportedType` tokenów typów modelu COM, który odwołuje się zestaw w bieżącym zakresie metadanych.|  
|[EnumFiles, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enumfiles-method.md)|Pobiera moduł wyliczający, który zawiera wskaźnik interfejsu `mdFile` tokeny plików odwołuje się zestaw w bieżącym zakresie metadanych.|  
|[EnumManifestResources, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enummanifestresources-method.md)|Pobiera moduł wyliczający, który zawiera wskaźnik interfejsu `mdManifestResource` tokenów zasobów odwołuje się zestaw w bieżącym zakresie metadanych.|  
|[FindAssembliesByName, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-findassembliesbyname-method.md)|Pobiera tablicę elementów `mdAssemblyRef` tokenów dla zespołów o określonej nazwie.|  
|[FindExportedTypeByName, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-findexportedtypebyname-method.md)|Pobiera `mdExportedType` tokenu dla typu COM o określonej nazwie.|  
|[FindManifestResourceByName, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-findmanifestresourcebyname-method.md)|Pobiera `mdManifestResource` tokenu dla zasobu o określonej nazwie.|  
|[GetAssemblyFromScope, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getassemblyfromscope-method.md)|Pobiera token dla zestawu w bieżącym zakresie metadanych.|  
|[GetAssemblyProps, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getassemblyprops-method.md)|Pobiera ustawienia właściwości określonego zestawu.|  
|[GetAssemblyRefProps, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getassemblyrefprops-method.md)|Pobiera ustawienia właściwości określonego `mdAssemblyRef` tokenu.|  
|[GetExportedTypeProps, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getexportedtypeprops-method.md)|Pobiera ustawienia właściwości określonego typu modelu COM.|  
|[GetFileProps, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getfileprops-method.md)|Pobiera ustawienia właściwości określonego pliku.|  
|[GetManifestResourceProps, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getmanifestresourceprops-method.md)|Pobiera ustawienia właściwości określonego zasobu manifestu.|  
  
## <a name="requirements"></a>Wymagania  
 **Platforma:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** COR.h  
  
 **Biblioteka:** Używany jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [Interfejsy metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [IMetaDataAssemblyEmit, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
