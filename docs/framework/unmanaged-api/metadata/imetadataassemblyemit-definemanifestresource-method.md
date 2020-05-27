---
title: IMetaDataAssemblyEmit::DefineManifestResource — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.DefineManifestResource
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::DefineManifestResource
helpviewer_keywords:
- DefineManifestResource method [.NET Framework metadata]
- IMetaDataAssemblyEmit::DefineManifestResource method [.NET Framework metadata]
ms.assetid: 27f6d295-0fe9-4cda-b77e-6e7d5c53df09
topic_type:
- apiref
ms.openlocfilehash: 026f5efe195cdb34999b65c5f47de6f68d30e11a
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008134"
---
# <a name="imetadataassemblyemitdefinemanifestresource-method"></a>IMetaDataAssemblyEmit::DefineManifestResource — Metoda
Tworzy `ManifestResource` strukturę zawierającą metadane dla określonego zasobu manifestu i zwraca skojarzony token metadanych.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT DefineManifestResource (  
    [in] LPCWSTR                szName,
    [in] mdToken                tkImplementation,
    [in] DWORD                  dwOffset,
    [in] DWORD                  dwResourceFlags,  
    [out] mdManifestResource    *pmdmr  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `szName`  
 podczas Nazwa zasobu.  
  
 `tkImplementation`  
 podczas Token metadanych typu `mdtFile` lub `mdtAssemblyRef` mapowany do dostawcy zasobów. Wartość NULL wskazuje, że plik, w którym są osadzone metadane, jest dostawcą zasobów.  
  
 `dwOffset`  
 podczas Przesunięcie do początku zasobu w pliku. W przypadku zasobów w plikach autonomicznych zawsze będzie to zero. Jeśli zasób jest osadzony w pliku PE (przenośny plik wykonywalny), jest to przesunięcie obiektu BLOB zasobu, który jest uruchamiany w lokalizacji określonej w pliku nagłówkowym cor. h.  
  
 `dwResourceFlags`  
 podczas Bitowa kombinacja wartości flag, które określają ustawienia właściwości dla definicji zasobu.  
  
 `pmdmr`  
 określoną Wskaźnik do zwracanego tokenu metadanych.  
  
## <a name="remarks"></a>Uwagi  
 `ManifestResource`Dla każdego zasobu, który jest zaimplementowany w każdym z plików zestawu, musi być zdefiniowana jedna struktura metadanych.  
  
## <a name="requirements"></a>Wymagania  
 **Platforma:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** Cor. h  
  
 **Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [IMetaDataAssemblyEmit — Interfejs](imetadataassemblyemit-interface.md)
