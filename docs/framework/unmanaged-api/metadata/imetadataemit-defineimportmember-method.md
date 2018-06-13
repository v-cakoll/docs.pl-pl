---
title: IMetaDataEmit::DefineImportMember — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineImportMember
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineImportMember
helpviewer_keywords:
- DefineImportMember method [.NET Framework metadata]
- IMetaDataEmit::DefineImportMember method [.NET Framework metadata]
ms.assetid: c7dd94c6-335b-46ff-9dfe-505056db5673
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f9995fda70d1d5a3c19c30496de6c32f20015d47
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33449393"
---
# <a name="imetadataemitdefineimportmember-method"></a>IMetaDataEmit::DefineImportMember — Metoda
Tworzy odwołanie do określonego elementu członkowskiego o typie lub module, który jest zdefiniowany poza bieżącym zakresem i definiuje token dla tego odwołania.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT DefineImportMember (   
    [in]  IMetaDataAssemblyImport  *pAssemImport,   
    [in]  const void               *pbHashValue,   
    [in]  ULONG                    cbHashValue,  
    [in]  IMetaDataImport          *pImport,   
    [in]  mdToken                  mbMember,   
    [in]  IMetaDataAssemblyEmit    *pAssemEmit,   
    [in]  mdToken                  tkParent,   
    [out] mdMemberRef              *pmr   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pAssemImport`  
 [in] [IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interfejs, który reprezentuje zestaw, z którego jest importowany członek docelowego.  
  
 `pbHashValue`  
 [in] Tablica zawierająca wartość skrótu dla zestawu określony przez `pAssemImport`.  
  
 `cbHashValue`  
 [in] Liczba bajtów w `pbHashValue` tablicy.  
  
 `pImport`  
 [in] [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interfejs, który reprezentuje zakres metadanych, z którego jest importowany członek docelowego.  
  
 `mbMember`  
 [in] Token metadanych, który określa docelowy element członkowski. Token może być `mdMethodDef` (w przypadku elementu członkowskiego metody) `mdProperty` (dla właściwości elementu członkowskiego), lub `mdFieldDef` (dla pola elementu członkowskiego) tokenu.  
  
 `pAssemEmit`  
 [in] [IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md) interfejs, który reprezentuje zestaw, do którego jest importowany członek docelowego.  
  
 `tkParent`  
 [in] `mdTypeRef` Lub `mdModuleRef` tokenu typu lub moduł, odpowiednio, który jest właścicielem docelowy element członkowski.  
  
 `pmr`  
 [out] `mdMemberRef` Token, który jest zdefiniowany w bieżącym zakresie dla odwołania do elementu członkowskiego.  
  
## <a name="remarks"></a>Uwagi  
 `DefineImportMember` Metody wyszukuje element określony przez `mbMember`, która jest zdefiniowana w innym zakresie określonym przez `pImport`i pobiera jego właściwości. Używa tych informacji do wywołania [IMetaDataEmit::DefineMemberRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md) metody w bieżącym zakresie, aby utworzyć odwołanie do elementu członkowskiego.  
  
 Ogólnie rzecz biorąc, zanim użyjesz `DefineImportMember` metody, należy utworzyć, w bieżącym zakresie, odwołanie do typu lub odwołania do modułu do docelowego elementu członkowskiego klasy nadrzędnej, interfejsem lub modułu. Token metadanych dla tego odwołania są następnie przekazywane w `tkParent` argumentu. Nie trzeba utworzyć odwołanie do nadrzędnego elementu członkowskiego docelowego, jeśli jego zostanie rozwiązany później kompilatora lub konsolidatora. Podsumowując:  
  
-   Jeśli element docelowy jest pole lub metoda, użyj jednej [IMetaDataEmit::DefineTypeRefByName](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md) lub [IMetaDataEmit::DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md) metodę, aby utworzyć odwołanie do typu, w bieżącym zakresie dla klasy nadrzędnej lub interfejsu nadrzędnego elementu członkowskiego.  
  
-   Jeśli element docelowy jest zmienna lub globalnego funkcją globalną (to znaczy, że nie jesteś członkiem klasy lub interfejsu), użyj [IMetaDataEmit::DefineModuleRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemoduleref-method.md) metodę w celu utworzenia odwołania do modułu w bieżącym zakresie dla nadrzędnego elementu członkowskiego Moduł.  
  
-   Jeśli nadrzędny docelowy element członkowski zostanie rozwiązany później kompilatora lub konsolidatora, następnie przekazać `mdTokenNil` w `tkParent`. Jest jedyny scenariusz, w którym ma to zastosowanie, gdy funkcja globalna lub zmiennej globalnej jest importowany z pliku obj, który ostatecznie zostanie połączony do bieżącego modułu i scalić metadanych.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor.h  
  
 **Biblioteka:** używany jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [IMetaDataEmit, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [IMetaDataEmit2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
