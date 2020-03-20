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
ms.openlocfilehash: 6825a5198976cc7ab2c04ebd6e782418dcf4a8f7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177679"
---
# <a name="imetadataemitdefineimporttype-method"></a>IMetaDataEmit::DefineImportType — Metoda
Tworzy odwołanie do określonego typu, który jest zdefiniowany poza bieżącym zakresem i definiuje token dla tego odwołania.  
  
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
 [w] [Interfejs IMetaDataAssemblyImport,](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) który reprezentuje zestaw, z którego jest importowany typ docelowy.  
  
 `pbHashValue`  
 [w] Tablica zawierająca skrót dla zestawu `pAssemImport`określonego przez program .  
  
 `cbHashValue`  
 [w] Liczba bajtów w `pbHashValue` tablicy.  
  
 `pImport`  
 [w] Interfejs [IMetaDataImport reprezentujący](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) zakres metadanych, z którego jest importowany typ docelowy.  
  
 `tdImport`  
 [w] Token, `mdTypeDef` który określa typ docelowy.  
  
 `pAssemEmit`  
 [w] [Interfejs IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md) reprezentujący zestaw, do którego importowany jest typ docelowy.  
  
 `ptr`  
 [na zewnątrz] Token, `mdTypeRef` który jest zdefiniowany w bieżącym zakresie odwołania do typu.  
  
## <a name="remarks"></a>Uwagi  
 Przed [wywołaniem metody IMetaDataEmit::DefineImportMember](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimportmember-method.md) można użyć `DefineImportType` tej metody, aby utworzyć odwołanie do typu w bieżącym zakresie dla klasy nadrzędnej elementu członkowskiego lub interfejsu nadrzędnego.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Okręg wyborczy Cor.h  
  
 **Biblioteka:** Używany jako zasób w pliku MSCorEE.dll  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [IMetaDataEmit — Interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
