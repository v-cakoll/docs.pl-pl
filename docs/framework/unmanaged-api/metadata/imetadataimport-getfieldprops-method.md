---
title: IMetaDataImport::GetFieldProps — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetFieldProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetFieldProps
helpviewer_keywords:
- IMetaDataImport::GetFieldProps method [.NET Framework metadata]
- GetFieldProps method [.NET Framework metadata]
ms.assetid: 7b0e9b10-8cef-4ba6-8432-40bf63e65ab1
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d7f8cccf8d583645982eb37f6afcb553914679ad
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59075678"
---
# <a name="imetadataimportgetfieldprops-method"></a>IMetaDataImport::GetFieldProps — Metoda
Pobiera metadane skojarzone z polem odwołuje się określona FieldDef token.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetFieldProps (  
   [in]  mdFieldDef        mb,   
   [out] mdTypeDef         *pClass,  
   [out] LPWSTR            szField,  
   [in]  ULONG             cchField,   
   [out] ULONG             *pchField,  
   [out] DWORD             *pdwAttr,  
   [in]  PCCOR_SIGNATURE   *ppvSigBlob,   
   [out] ULONG             *pcbSigBlob,   
   [out] DWORD             *pdwCPlusTypeFlag,   
   [out] UVCP_CONSTANT     *ppValue,  
   [out] ULONG             *pcchValue  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `mb`  
 [in] Token FieldDef, który reprezentuje pole, które można pobrać skojarzone metadane.  
  
 `pClass`  
 [out] Wskaźnik do TypeDef token, który reprezentuje typ klasy, które pole należy do.  
  
 `szField`  
 [out] Nazwa pola.  
  
 `cchField`  
 [in] Rozmiar w znaki dwubajtowe buforu dla *szField*.  
  
 `pchField`  
 [out] Rzeczywisty rozmiar buforu zwrócony.  
  
 `pdwAttr`  
 [out] Flagi skojarzone ze pola metadanych.  
  
 `ppvSigBlob`  
 [in] Wskaźnik do wartości binarne metadanych, opisujący pola.  
  
 `pcbSigBlob`  
 [out] Rozmiar w bajtach `ppvSigBlob`.  
  
 `pdwCPlusTypeFlag`  
 [out] Flaga, która określa typ wartości pola.  
  
 `ppValue`  
 [out] Stała wartość dla pola.  
  
 `pcchValue`  
 [out] Rozmiar w znaki z `ppValue`, lub zero, jeśli ciąg nie istnieje.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** COR.h  
  
 **Biblioteka:** Dołączony jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IMetaDataImport, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
