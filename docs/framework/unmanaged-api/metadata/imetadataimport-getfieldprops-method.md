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
ms.openlocfilehash: 04b6c04868efff31253b2d723c5783060382212b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33448976"
---
# <a name="imetadataimportgetfieldprops-method"></a>IMetaDataImport::GetFieldProps — Metoda
Pobiera metadane skojarzone z polem odwołuje się określony FieldDef token.  
  
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
  
#### <a name="parameters"></a>Parametry  
 `mb`  
 [in] Token FieldDef, który reprezentuje pole, aby pobrać skojarzone metadane.  
  
 `pClass`  
 [out] Wskaźnik do tokenu — TypeDef, który reprezentuje typ pola należącego do klasy.  
  
 `szField`  
 [out] Nazwa pola.  
  
 `cchField`  
 [in] Rozmiar w znaki dwubajtowe buforu dla *szField*.  
  
 `pchField`  
 [out] Rzeczywisty rozmiar buforu zwrócony.  
  
 `pdwAttr`  
 [out] Flagi skojarzone z metadanymi pola.  
  
 `ppvSigBlob`  
 [in] Wskaźnik do wartości binarne metadanych, opisujący pola.  
  
 `pcbSigBlob`  
 [out] Wyrażony w bajtach rozmiar `ppvSigBlob`.  
  
 `pdwCPlusTypeFlag`  
 [out] Flaga, która określa typ wartości pola.  
  
 `ppValue`  
 [out] Stała wartość dla pola.  
  
 `pcchValue`  
 [out] Rozmiar znaków z `ppValue`, lub zero, jeśli ciąg nie istnieje.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor.h  
  
 **Biblioteka:** uwzględnione jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [IMetaDataImport, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [IMetaDataImport2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
