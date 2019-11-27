---
title: IMetaDataEmit::DefineImportType — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineImportType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineImportType
helpviewer_keywords:
- DefineImportType method [.NET Framework metadata]
- IMetaDataEmit::DefineImportType method [.NET Framework metadata]
ms.assetid: 37fd27af-8062-4904-ace4-51bb78ec600a
topic_type:
- apiref
ms.openlocfilehash: 5b4b0682b2bddff96cb3d720900ed3aa39f06f9d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431853"
---
# <a name="imetadataemitdefineimporttype-method"></a>IMetaDataEmit::DefineImportType — Metoda
Tworzy odwołanie do określonego typu, który jest zdefiniowany poza bieżącym zakresem, i definiuje token dla tego odwołania.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT DefineImportType (   
    [in]  IMetaDataAssemblyImport  *pAssemImport,   
    [in]  const void               *pbHashValue,   
    [in]  ULONG                    cbHashValue,    
    [in]  IMetaDataImport          *pImport,   
    [in]  mdTypeDef                tdImport,   
    [in]  IMetaDataAssemblyEmit    *pAssemEmit,   
    [out] mdTypeRef                *ptr  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pAssemImport`  
 podczas Interfejs [IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) , który reprezentuje zestaw, z którego zaimportowano typ docelowy.  
  
 `pbHashValue`  
 podczas Tablica, która zawiera skrót dla zestawu określonego przez `pAssemImport`.  
  
 `cbHashValue`  
 podczas Liczba bajtów w tablicy `pbHashValue`.  
  
 `pImport`  
 podczas Interfejs [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) reprezentujący zakres metadanych, z którego jest importowany typ docelowy.  
  
 `tdImport`  
 podczas Token `mdTypeDef`, który określa typ docelowy.  
  
 `pAssemEmit`  
 podczas Interfejs [IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md) , który reprezentuje zestaw, do którego zaimportowany jest typ docelowy.  
  
 `ptr`  
 określoną Token `mdTypeRef`, który jest zdefiniowany w bieżącym zakresie dla odwołania do typu.  
  
## <a name="remarks"></a>Uwagi  
 Przed wywołaniem metody [IMetaDataEmit::D efineimportmember](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimportmember-method.md) , można użyć metody `DefineImportType`, aby utworzyć odwołanie do typu w bieżącym zakresie dla klasy nadrzędnej lub interfejsu nadrzędnego elementu członkowskiego.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor. h  
  
 **Biblioteka:** Używany jako zasób w bibliotece MSCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IMetaDataEmit, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
