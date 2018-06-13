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
ms.openlocfilehash: 46fa6ab3ea4a63583b01ffe25d22840301613100
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33444799"
---
# <a name="imetadataassemblyemitdefinefile-method"></a>IMetaDataAssemblyEmit::DefineFile — Metoda
Tworzy `File` struktury metadane zawierające metadanych dla zestawu odwołuje się ten zestaw i zwraca token skojarzone metadane.  
  
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
  
#### <a name="parameters"></a>Parametry  
 `szName`  
 [in] Nazwa pliku, który ma być używane.  
  
 `pbHashValue`  
 [in] Wskaźnik do wyznaczania wartości skrótu skojarzonych z zestawu danych.  
  
 `cbHashValue`  
 [in] Wyrażony w bajtach rozmiar `pbHashValue`.  
  
 `dwFileFlags`  
 [in] Bitowe połączenie `FileFlags` wartości, które określają ustawienia właściwości.  
  
 `pmdf`  
 [out] Wskaźnik do zwróconego `File` tokenu.  
  
## <a name="remarks"></a>Uwagi  
 Jeden `File` struktura metadanych musi być zdefiniowana dla każdego pliku, który jest częścią tego zestawu w czasie ten zestaw został utworzony, wyłączając plik zawierający metadane.  
  
## <a name="requirements"></a>Wymagania  
 **Platforma:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor.h  
  
 **Biblioteka:** używany jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [IMetaDataAssemblyEmit, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
