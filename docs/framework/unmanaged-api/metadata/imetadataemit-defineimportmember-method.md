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
ms.openlocfilehash: 81acda4d395563fc8e0000e38036d1aaa0f14471
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59222695"
---
# <a name="imetadataemitdefineimportmember-method"></a>IMetaDataEmit::DefineImportMember — Metoda
Tworzy odwołanie do określonego elementu członkowskiego typu lub moduł, który jest zdefiniowane poza bieżącym zakresie i definiuje token dla tego odwołania.  
  
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
  
## <a name="parameters"></a>Parametry  
 `pAssemImport`  
 [in] [Imetadataassemblyimport —](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interfejs, który reprezentuje zestaw, z którego docelowy element członkowski jest importowany.  
  
 `pbHashValue`  
 [in] Tablica, która zawiera wartość skrótu dla zestawu określonego przez `pAssemImport`.  
  
 `cbHashValue`  
 [in] Liczba bajtów w `pbHashValue` tablicy.  
  
 `pImport`  
 [in] [Imetadataimport —](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interfejs, który reprezentuje zakres metadanych, z którego docelowy element członkowski jest importowany.  
  
 `mbMember`  
 [in] Token metadanych, który określa docelowy element członkowski. Token może być `mdMethodDef` (w przypadku elementu członkowskiego metody) `mdProperty` (w przypadku właściwości elementu członkowskiego), lub `mdFieldDef` (dla pola elementu członkowskiego) tokenu.  
  
 `pAssemEmit`  
 [in] [Imetadataassemblyemit —](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md) interfejs, który reprezentuje zestaw, do którego docelowy element członkowski jest importowany.  
  
 `tkParent`  
 [in] `mdTypeRef` Lub `mdModuleRef` tokenu dla typu lub modułu, odpowiednio, który jest właścicielem docelowy element członkowski.  
  
 `pmr`  
 [out] `mdMemberRef` Token, który jest zdefiniowany w bieżącym zakresie dla odwołania do elementu członkowskiego.  
  
## <a name="remarks"></a>Uwagi  
 `DefineImportMember` Metoda wyszukuje element określony przez `mbMember`, która jest zdefiniowana w innym zakresie określonym przez `pImport`i pobiera jego właściwości. Używa tych informacji w celu wywołania [IMetaDataEmit::DefineMemberRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md) metody w bieżącym zakresie można utworzyć odwołania do elementu członkowskiego.  
  
 Ogólnie rzecz biorąc, zanim użyjesz `DefineImportMember` metody, należy utworzyć, w bieżącym zakresie, odwołanie do typu lub odwołania do modułu docelowy element członkowski klasy nadrzędnej, interfejs lub moduł. Token metadanych dla tego odwołania jest następnie przekazywany w `tkParent` argumentu. Nie trzeba utworzyć odwołanie do elementu nadrzędnego elementu członkowskiego docelowy, jeśli będzie można rozwiązać w dalszej części, kompilator lub konsolidator. Podsumowując:  
  
-   Jeśli docelowy element członkowski jest ona polem ani metodą, użyj jednej [IMetaDataEmit::DefineTypeRefByName](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md) lub [IMetaDataEmit::DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md) metodę, aby utworzyć odwołanie do typu, w bieżącym zakresie dla klasy nadrzędnej lub interfejs nadrzędny tego elementu.  
  
-   Jeśli docelowy element członkowski, zmienna lub globalnego funkcją globalną (czyli nie jest członkiem klasy lub interfejsu), użyj [IMetaDataEmit::DefineModuleRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemoduleref-method.md) metodę w celu utworzenia odwołania do modułu w bieżącym zakresie i dla nadrzędnego elementu członkowskiego Moduł.  
  
-   Jeśli nadrzędny docelowy element członkowski zostanie rozwiązany później przez kompilator lub konsolidator, należy przekazać `mdTokenNil` w `tkParent`. Jest jedyny scenariusz, w którym ma to zastosowanie, gdy funkcja globalna lub zmienna globalna jest importowany z pliku .obj, który ostatecznie zostanie połączony do bieżącego modułu i metadane, scalone.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** COR.h  
  
 **Biblioteka:** Używany jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IMetaDataEmit — Interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 — Interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
