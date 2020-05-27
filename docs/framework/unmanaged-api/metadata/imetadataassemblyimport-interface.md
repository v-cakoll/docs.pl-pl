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
ms.openlocfilehash: 2a67f50fa1042e8d3957a9a0394507f260a328c6
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009018"
---
# <a name="imetadataassemblyimport-interface"></a>IMetaDataAssemblyImport — Interfejs
Zapewnia metody umożliwiające dostęp i sprawdzanie zawartości manifestu zestawu.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[CloseEnum, metoda](imetadataassemblyimport-closeenum-method.md)|Zwalnia dojście do określonego modułu wyliczającego.|  
|[EnumAssemblyRefs — Metoda](imetadataassemblyimport-enumassemblyrefs-method.md)|Pobiera wskaźnik interfejsu do modułu wyliczającego, który zawiera `mdAssemblyRef` tokeny zestawów, do których odwołuje się zestaw w bieżącym zakresie metadanych.|  
|[EnumExportedTypes — Metoda](imetadataassemblyimport-enumexportedtypes-method.md)|Pobiera wskaźnik interfejsu do modułu wyliczającego, który zawiera `mdExportedType` tokeny typów com, do których odwołuje się zestaw w bieżącym zakresie metadanych.|  
|[EnumFiles — Metoda](imetadataassemblyimport-enumfiles-method.md)|Pobiera wskaźnik interfejsu do modułu wyliczającego, który zawiera `mdFile` tokeny plików, do których odwołuje się zestaw w bieżącym zakresie metadanych.|  
|[EnumManifestResources — Metoda](imetadataassemblyimport-enummanifestresources-method.md)|Pobiera wskaźnik interfejsu do modułu wyliczającego, który zawiera `mdManifestResource` tokeny zasobów, do których odwołuje się zestaw w bieżącym zakresie metadanych.|  
|[FindAssembliesByName — Metoda](imetadataassemblyimport-findassembliesbyname-method.md)|Pobiera tablicę `mdAssemblyRef` tokenów dla zestawów o określonej nazwie.|  
|[FindExportedTypeByName — Metoda](imetadataassemblyimport-findexportedtypebyname-method.md)|Pobiera `mdExportedType` token dla typu com o określonej nazwie.|  
|[FindManifestResourceByName — Metoda](imetadataassemblyimport-findmanifestresourcebyname-method.md)|Pobiera `mdManifestResource` token dla zasobu o określonej nazwie.|  
|[GetAssemblyFromScope — Metoda](imetadataassemblyimport-getassemblyfromscope-method.md)|Pobiera token dla zestawu w bieżącym zakresie metadanych.|  
|[GetAssemblyProps — Metoda](imetadataassemblyimport-getassemblyprops-method.md)|Pobiera ustawienia właściwości określonego zestawu.|  
|[GetAssemblyRefProps — Metoda](imetadataassemblyimport-getassemblyrefprops-method.md)|Pobiera ustawienia właściwości określonego `mdAssemblyRef` tokenu.|  
|[GetExportedTypeProps — Metoda](imetadataassemblyimport-getexportedtypeprops-method.md)|Pobiera ustawienia właściwości określonego typu COM.|  
|[GetFileProps — Metoda](imetadataassemblyimport-getfileprops-method.md)|Pobiera ustawienia właściwości określonego pliku.|  
|[GetManifestResourceProps — Metoda](imetadataassemblyimport-getmanifestresourceprops-method.md)|Pobiera ustawienia właściwości określonego zasobu manifestu.|  
  
## <a name="requirements"></a>Wymagania  
 **Platforma:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** Cor. h  
  
 **Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Interfejsy metadanych](metadata-interfaces.md)
- [IMetaDataAssemblyEmit — Interfejs](imetadataassemblyemit-interface.md)
