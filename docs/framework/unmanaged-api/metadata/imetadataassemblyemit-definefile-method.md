---
title: IMetaDataAssemblyEmit::DefineFile — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.DefineFile
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::DefineFile
helpviewer_keywords:
- IMetaDataAssemblyEmit::DefineFile method [.NET Framework metadata]
- DefineFile method [.NET Framework metadata]
ms.assetid: c065aadf-c1ca-4981-bde6-597042cb29c4
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5693da3b5e6d883efd9ad8a5a409a5dba8dd8b6e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59203434"
---
# <a name="imetadataassemblyemitdefinefile-method"></a>IMetaDataAssemblyEmit::DefineFile — Metoda
Tworzy `File` struktury metadanych zawierający metadane zestawu odwołuje się ten zestaw i zwraca token skojarzone metadane.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT DefineFile (  
    [in]  LPCWSTR        szName,   
    [in]  const void     *pbHashValue,   
    [in]  ULONG          cbHashValue,  
    [in]  DWORD          dwFileFlags,  
    [out] mdFile         *pmdf  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `szName`  
 [in] Nazwa pliku do użycia.  
  
 `pbHashValue`  
 [in] Wskaźnik do danych wyznaczania wartości skrótu, skojarzone z zestawem.  
  
 `cbHashValue`  
 [in] Rozmiar w bajtach `pbHashValue`.  
  
 `dwFileFlags`  
 [in] Bitowa kombinacja `FileFlags` wartości, które określają ustawienia właściwości.  
  
 `pmdf`  
 [out] Wskaźnik do zwracanego `File` tokenu.  
  
## <a name="remarks"></a>Uwagi  
 Jeden `File` struktury metadanych musi być zdefiniowana dla każdego pliku, które było częścią tego zestawu w czasie, który został zbudowany tego zestawu, z wyjątkiem pliku który zawiera metadane.  
  
## <a name="requirements"></a>Wymagania  
 **Platforma:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** COR.h  
  
 **Biblioteka:** Używany jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IMetaDataAssemblyEmit — Interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
