---
title: IMetaDataAssemblyImport::FindExportedTypeByName — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.FindExportedTypeByName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::FindExportedTypeByName
helpviewer_keywords:
- FindExportedTypeByName method [.NET Framework metadata]
- IMetaDataAssemblyImport::FindExportedTypeByName method [.NET Framework metadata]
ms.assetid: 46264b2c-574d-4dde-aafc-77187a104fdd
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 048c7234fcb2592ea0dade135a32341a6e0f404f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33444922"
---
# <a name="imetadataassemblyimportfindexportedtypebyname-method"></a>IMetaDataAssemblyImport::FindExportedTypeByName — Metoda
Pobiera wskaźnik do wyeksportowanego typu podanej nazwy i typ otaczający.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT FindExportedTypeByName (  
    [in]  LPCWSTR           szName,   
    [in]  mdToken           mdtExportedType,   
    [out] mdExportedType    *ptkExportedType  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `szName`  
 [in] Nazwa wyeksportowanego typu.  
  
 `mdtExportedType`  
 [in] Token metadanych dla wyeksportowanego typu klasy otaczającej. Ta wartość jest `mdExportedTypeNil` Jeśli wyeksportowany żądany typ nie jest typem zagnieżdżonym.  
  
 `ptkExportedType`  
 [out] Wskaźnik do `mdExportedType` token reprezentujący wyeksportowanego typu.  
  
## <a name="remarks"></a>Uwagi  
 `FindExportedTypeByName` Metoda używa standardowych zasad stosowanych przez środowisko uruchomieniowe języka wspólnego do rozpoznawania odwołań.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor.h  
  
 **Biblioteka:** używany jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [IMetaDataAssemblyImport, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)  
 [Sposoby lokalizowania zestawów przez środowisko uruchomieniowe](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
