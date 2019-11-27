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
ms.openlocfilehash: 75711b3d87699ff5db21a04351ff0acaccabb5aa
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431856"
---
# <a name="imetadataemitdefineimportmember-method"></a>IMetaDataEmit::DefineImportMember — Metoda
Tworzy odwołanie do określonego elementu członkowskiego typu lub modułu, który jest zdefiniowany poza bieżącym zakresem, i definiuje token dla tego odwołania.  
  
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
 podczas Interfejs [IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) , który reprezentuje zestaw, z którego zostanie zaimportowany członek docelowy.  
  
 `pbHashValue`  
 podczas Tablica, która zawiera skrót dla zestawu określonego przez `pAssemImport`.  
  
 `cbHashValue`  
 podczas Liczba bajtów w tablicy `pbHashValue`.  
  
 `pImport`  
 podczas Interfejs [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) reprezentujący zakres metadanych, z którego zaimportowano element docelowy.  
  
 `mbMember`  
 podczas Token metadanych określający docelowy element członkowski. Token może być `mdMethodDef` (dla metody członkowskiej), `mdProperty` (dla właściwości elementu członkowskiego) lub `mdFieldDef` (dla pola elementu członkowskiego).  
  
 `pAssemEmit`  
 podczas Interfejs [IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md) , który reprezentuje zestaw, do którego zaimportowany jest docelowy element członkowski.  
  
 `tkParent`  
 podczas Token `mdTypeRef` lub `mdModuleRef` dla typu lub modułu, który jest właścicielem docelowego elementu członkowskiego.  
  
 `pmr`  
 określoną Token `mdMemberRef`, który jest zdefiniowany w bieżącym zakresie dla odwołania do elementu członkowskiego.  
  
## <a name="remarks"></a>Uwagi  
 Metoda `DefineImportMember` wyszukuje element członkowski, określony przez `mbMember`, który jest zdefiniowany w innym zakresie, określonym przez `pImport`i pobiera jego właściwości. Używa tych informacji do wywołania metody [IMetaDataEmit::D efinememberref](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md) w bieżącym zakresie w celu utworzenia odwołania do elementu członkowskiego.  
  
 Ogólnie rzecz biorąc, przed użyciem metody `DefineImportMember` należy utworzyć, w bieżącym zakresie, odwołanie do typu lub odwołanie do modułu dla klasy nadrzędnej, interfejsu lub modułu członkowskiego elementu docelowego. Token metadanych dla tego odwołania jest następnie przesyłany w `tkParent` argument. Nie trzeba tworzyć odwołania do elementu nadrzędnego elementu członkowskiego docelowej, jeśli zostanie on rozwiązany później przez kompilator lub konsolidator. Aby podsumować:  
  
- Jeśli docelowa składowa jest polem lub metodą, użyj metody [IMetaDataEmit::D efinetyperefbyname](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md) lub [IMetaDataEmit::D efineimporttype](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md) , aby utworzyć odwołanie do typu w bieżącym zakresie dla klasy nadrzędnej lub interfejsu nadrzędnego elementu członkowskiego.  
  
- Jeśli element członkowski docelowa to zmienna globalna lub funkcja globalna (to nie jest element członkowski klasy lub interfejsu), użyj metody [IMetaDataEmit::D efinemoduleref](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemoduleref-method.md) , aby utworzyć odwołanie do modułu w bieżącym zakresie dla modułu nadrzędnego elementu członkowskiego.  
  
- Jeśli element nadrzędny elementu członkowskiego docelowej zostanie rozwiązany później przez kompilator lub konsolidator, Przekaż `mdTokenNil` w `tkParent`. Jedyny scenariusz, w którym dotyczy to, gdy globalna funkcja lub zmienna globalna jest importowana z pliku. obj, który ostatecznie zostanie połączony z bieżącym modułem i scalone metadane.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor. h  
  
 **Biblioteka:** Używany jako zasób w bibliotece MSCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IMetaDataEmit, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
