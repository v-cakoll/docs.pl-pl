---
title: IMetaDataAssemblyEmit — Interfejs
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit
helpviewer_keywords:
- IMetaDataAssemblyEmit interface [.NET Framework metadata]
ms.assetid: 34fb03cc-2285-4a45-ac48-ad993b7a921a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3a66ef090a205019493e099919739867e3936873
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59081806"
---
# <a name="imetadataassemblyemit-interface"></a>IMetaDataAssemblyEmit — Interfejs
Udostępnia metody, które wspierają model własny opis używany przez środowisko uruchomieniowe języka wspólnego w rozwiązania i używanie zasobów.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[DefineAssembly, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassembly-method.md)|Tworzy zestaw danych struktury zawierającej metadanych dla określonego zestawu i zwraca token skojarzone metadane.|  
|[DefineAssemblyRef, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md)|Tworzy `AssemblyRef` struktury zawierający metadane dla zestawu, który odwołuje się ten zestaw i zwraca token skojarzone metadane.|  
|[DefineExportedType, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md)|Tworzy `ExportedType` struktury zawierającej metadanych dla określonego wyeksportować typu, a następnie zwraca token skojarzone metadane.|  
|[DefineFile, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md)|Tworzy `File` struktury metadanych zawierający metadane zestawu odwołuje się ten zestaw i zwraca token skojarzone metadane.|  
|[DefineManifestResource, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definemanifestresource-method.md)|Tworzy `ManifestResource` struktury zawierającymi metadane dla określonego zasobu manifestu, a następnie zwraca token skojarzone metadane.|  
|[SetAssemblyProps — Metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-setassemblyprops-method.md)|Modyfikuje określonego `Assembly` struktury metadanych.|  
|[SetAssemblyRefProps, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-setassemblyrefprops-method.md)|Modyfikuje określonego `AssemblyRef` struktury metadanych.|  
|[SetExportedTypeProps, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-setexportedtypeprops-method.md)|Modyfikuje określonego `ExportedType` struktury metadanych.|  
|[SetFileProps, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-setfileprops-method.md)|Modyfikuje określonego `File` struktury metadanych.|  
|[SetManifestResourceProps, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-setmanifestresourceprops-method.md)|Modyfikuje określonego `ManifestResource` struktury metadanych.|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** COR.h  
  
 **Biblioteka:** Używany jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Interfejsy metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [IMetaDataAssemblyImport — Interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
