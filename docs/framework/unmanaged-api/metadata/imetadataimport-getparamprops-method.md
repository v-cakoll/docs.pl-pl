---
title: IMetaDataImport::GetParamProps — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetParamProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetParamProps
helpviewer_keywords:
- IMetaDataImport::GetParamProps method [.NET Framework metadata]
- GetParamProps method [.NET Framework metadata]
ms.assetid: 4d5e5f00-bcab-4f41-b191-176511a186a7
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 95850448504fd863f2726a7fb7574436476a6dc5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="imetadataimportgetparamprops-method"></a>IMetaDataImport::GetParamProps — Metoda
Pobiera wartości metadanych dla parametru odwołuje się określony ParamDef token.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetParamProps (  
   [in]  mdParamDef      tk,  
   [out] mdMethodDef     *pmd,  
   [out] ULONG           *pulSequence,  
   [out] LPWSTR          szName,  
   [in]  ULONG           cchName,  
   [out] ULONG           *pchName,  
   [out] DWORD           *pdwAttr,  
   [out] DWORD           *pdwCPlusTypeFlag,  
   [out] UVCP_CONSTANT   *ppValue,  
   [out] ULONG           *pcchValue  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `tk`  
 [in] Token ParamDef, który reprezentuje parametr do zwracania metadanych.  
  
 `pmd`  
 [out] Wskaźnik do tokenu MethodDef reprezentujący metodę, która przyjmuje parametr.  
  
 `pulSequence`  
 [out] {Numer porządkowy pozycja parametru na liście argumentów metody.  
  
 `szName`  
 [out] Bufor aby pomieścić nazwę parametru.  
  
 `cchName`  
 [in] Żądany rozmiar w znaki dwubajtowe `szName`.  
  
 `pchName`  
 [out] Rozmiar zwróconego w znaki dwubajtowe `szName`.  
  
 `pdwAttr`  
 [out] Wskaźnik do żadnych flag atrybutów skojarzonych z parametrem.  
  
 `pdwCPlusTypeFlag`  
 [out] Wskaźnik do określania flagi, że parametr jest <xref:System.ValueType>.  
  
 `ppValue`  
 [out] Wskaźnik ze stałym ciągiem zwrócona przez parametr.  
  
 `pcchValue`  
 [out] Rozmiar `ppValue` w znaki dwubajtowe lub zero, jeśli `ppValue` nie zawiera ciąg.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor.h  
  
 **Biblioteka:** uwzględnione jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [IMetaDataImport, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [IMetaDataImport2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
