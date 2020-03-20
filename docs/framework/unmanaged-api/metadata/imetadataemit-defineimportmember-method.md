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
ms.openlocfilehash: a7449ffc8a8ccf2db62ab3cff2f9cfaffd0c72a9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175866"
---
# <a name="imetadataemitdefineimportmember-method"></a>IMetaDataEmit::DefineImportMember — Metoda
Tworzy odwołanie do określonego elementu członkowskiego typu lub modułu, który jest zdefiniowany poza bieżącym zakresem i definiuje token dla tego odwołania.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
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
  
## <a name="parameters"></a>Parametry  
 `pAssemImport`  
 [w] [Interfejs IMetaDataAssemblyImport,](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) który reprezentuje zestaw, z którego jest importowany element członkowski obiektu docelowego.  
  
 `pbHashValue`  
 [w] Tablica zawierająca skrót dla zestawu `pAssemImport`określonego przez program .  
  
 `cbHashValue`  
 [w] Liczba bajtów w `pbHashValue` tablicy.  
  
 `pImport`  
 [w] Interfejs [IMetaDataImport reprezentujący](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) zakres metadanych, z którego jest importowany element członkowski obiektu docelowego.  
  
 `mbMember`  
 [w] Token metadanych, który określa docelowy element członkowski. Token może być `mdMethodDef` tokenem (dla `mdProperty` metody elementu członkowskiego) `mdFieldDef` (dla właściwości elementu członkowskiego) lub (dla pola członkowskiego).  
  
 `pAssemEmit`  
 [w] [Interfejs IMetaDataAssemblyEmit,](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md) który reprezentuje zestaw, do którego importowany jest element docelowy.  
  
 `tkParent`  
 [w] Lub `mdTypeRef` `mdModuleRef` token dla typu lub modułu, odpowiednio, który jest właścicielem elementu członkowskiego docelowego.  
  
 `pmr`  
 [na zewnątrz] Token, `mdMemberRef` który jest zdefiniowany w bieżącym zakresie odwołania elementu członkowskiego.  
  
## <a name="remarks"></a>Uwagi  
 Metoda `DefineImportMember` wyszukuje element `mbMember`członkowski, określony przez , `pImport`który jest zdefiniowany w innym zakresie, określonym przez program , i pobiera jego właściwości. Używa tych informacji do wywołania [IMetaDataEmit::DefineMemberRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md) metody w bieżącym zakresie, aby utworzyć odwołanie do elementu członkowskiego.  
  
 Ogólnie rzecz biorąc przed `DefineImportMember` użyciem metody, należy utworzyć w bieżącym zakresie odwołanie do typu lub odwołanie do modułu dla docelowego elementu nadrzędnego klasy, interfejsu lub modułu. Token metadanych dla tego odwołania `tkParent` jest następnie przekazywany w argumie. Nie trzeba tworzyć odwołanie do elementu nadrzędnego elementu docelowego, jeśli zostanie rozwiązany później przez kompilator lub konsolidator. Podsumowując:  
  
- Jeśli element członkowski obiektu docelowego jest polem lub metodą, należy użyć [metody IMetaDataEmit::DefineTypeRefByName](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md) lub [metody IMetaDataEmit::DefineImportType,](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md) aby utworzyć odwołanie do typu w bieżącym zakresie dla klasy nadrzędnej lub interfejsu nadrzędnego elementu członkowskiego.  
  
- Jeśli element członkowski obiektu docelowego jest zmienną globalną lub funkcją globalną (czyli nie jest członkiem klasy lub interfejsu), użyj metody [IMetaDataEmit::DefineModuleRef,](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemoduleref-method.md) aby utworzyć odwołanie do modułu w bieżącym zakresie dla modułu nadrzędnego elementu członkowskiego.  
  
- Jeśli element nadrzędny elementu docelowego zostanie później rozwiązany przez kompilator lub konsolidator, a następnie przekaż `mdTokenNil` . `tkParent` Jedynym scenariuszem, w którym ma to zastosowanie, jest, gdy funkcja globalna lub zmienna globalna jest importowana z pliku obj, który ostatecznie zostanie połączony z bieżącym modułem i scalonymi metadanymi.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Okręg wyborczy Cor.h  
  
 **Biblioteka:** Używany jako zasób w pliku MSCorEE.dll  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [IMetaDataEmit — Interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
