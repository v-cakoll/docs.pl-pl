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
ms.openlocfilehash: edce5cb93b770fb5730e5a06633ffffacf332f7a
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84004698"
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
 podczas Interfejs [IMetaDataAssemblyImport](imetadataassemblyimport-interface.md) , który reprezentuje zestaw, z którego zaimportowano typ docelowy.  
  
 `pbHashValue`  
 podczas Tablica, która zawiera skrót dla zestawu określonego przez `pAssemImport` .  
  
 `cbHashValue`  
 podczas Liczba bajtów w `pbHashValue` tablicy.  
  
 `pImport`  
 podczas Interfejs [IMetaDataImport](imetadataimport-interface.md) reprezentujący zakres metadanych, z którego jest importowany typ docelowy.  
  
 `tdImport`  
 podczas `mdTypeDef`Token określający typ docelowy.  
  
 `pAssemEmit`  
 podczas Interfejs [IMetaDataAssemblyEmit](imetadataassemblyemit-interface.md) , który reprezentuje zestaw, do którego zaimportowany jest typ docelowy.  
  
 `ptr`  
 określoną `mdTypeRef`Token, który jest zdefiniowany w bieżącym zakresie dla odwołania do typu.  
  
## <a name="remarks"></a>Uwagi  
 Przed wywołaniem metody [IMetaDataEmit::D efineimportmember](imetadataemit-defineimportmember-method.md) , można użyć `DefineImportType` metody, aby utworzyć odwołanie do typu w bieżącym zakresie dla klasy nadrzędnej lub interfejsu nadrzędnego elementu członkowskiego.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** Cor. h  
  
 **Biblioteka:** Używany jako zasób w bibliotece MSCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [IMetaDataEmit — Interfejs](imetadataemit-interface.md)
- [IMetaDataEmit2, interfejs](imetadataemit2-interface.md)
