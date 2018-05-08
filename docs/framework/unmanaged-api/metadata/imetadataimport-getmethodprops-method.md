---
title: IMetaDataImport::GetMethodProps — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetMethodProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetMethodProps
helpviewer_keywords:
- GetMethodProps method [.NET Framework metadata]
- IMetaDataImport::GetMethodProps method [.NET Framework metadata]
ms.assetid: e0667ef7-1d31-4c89-a2d3-d426f023f8d2
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4037ca42c5a66f075e949cd2035c1e7db510bb8e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="imetadataimportgetmethodprops-method"></a>IMetaDataImport::GetMethodProps — Metoda
Pobiera metadane skojarzone z metody odwołuje się określony MethodDef token.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetMethodProps (  
    [in]  mdMethodDef         mb,  
    [out] mdTypeDef           *pClass,  
    [out] LPWSTR              szMethod,  
    [in]  ULONG               cchMethod,  
    [out] ULONG               *pchMethod,  
    [out] DWORD               *pdwAttr,  
    [out] PCCOR_SIGNATURE     *ppvSigBlob,  
    [out] ULONG               *pcbSigBlob,  
    [out] ULONG               *pulCodeRVA,  
    [out] DWORD               *pdwImplFlags  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `mb`  
 [in] Token MethodDef, który reprezentuje metodę do zwracania metadanych.  
  
 `pClass`  
 [out] Wskaźnik do token TypeDef, który reprezentuje typ, który implementuje metody.  
  
 `szMethod`  
 [out] Wskaźnik do buforu, który ma nazwę metody.  
  
 `cchMethod`  
 [in] Żądany rozmiar `szMethod`.  
  
 `pchMethod`  
 [out] Wskaźnik do rozmiaru znaki dwubajtowe `szMethod`, lub w przypadku obcięcia, rzeczywista liczba znaki dwubajtowe w nazwie metody.  
  
 `pdwAttr`  
 [out] Wskaźnik do żadnych flag skojarzonego z metodą.  
  
 `ppvSigBlob`  
 [out] Wskaźnik do metadanych binarne sygnatury metody.  
  
 `pcbSigBlob`  
 [out] Wskaźnik do wyrażony w bajtach rozmiar `ppvSigBlob`.  
  
 `pulCodeRVA`  
 [out] Wskaźnik do wirtualnego adres względny metody.  
  
 `pdwImplFlags`  
 [out] Wskaźnik do dowolnego flagi implementacji metody.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor.h  
  
 **Biblioteka:** uwzględnione jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [IMetaDataImport, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [IMetaDataImport2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
