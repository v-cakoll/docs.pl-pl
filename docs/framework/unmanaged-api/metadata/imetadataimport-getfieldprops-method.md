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
ms.openlocfilehash: 8c3f98a124dbbcae3b0500932a2357ed1757951f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177247"
---
# <a name="imetadataimportgetfieldprops-method"></a>IMetaDataImport::GetFieldProps — Metoda
Pobiera metadane skojarzone z polem, do którego odwołuje się określony token FieldDef.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
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
 [w] A FieldDef token, który reprezentuje pole, aby uzyskać skojarzone metadane dla.  
  
 `pClass`  
 [na zewnątrz] Wskaźnik do Tokenu TypeDef, który reprezentuje typ klasy, do której należy pole.  
  
 `szField`  
 [na zewnątrz] Nazwa pola.  
  
 `cchField`  
 [w] Rozmiar w szerokich znaków buforu dla *szField*.  
  
 `pchField`  
 [na zewnątrz] Rzeczywisty rozmiar zwróconego buforu.  
  
 `pdwAttr`  
 [na zewnątrz] Flagi skojarzone z metadanymi pola.  
  
 `ppvSigBlob`  
 [w] Wskaźnik do wartości metadanych binarnych, który opisuje pole.  
  
 `pcbSigBlob`  
 [na zewnątrz] Rozmiar w bajtach . `ppvSigBlob`  
  
 `pdwCPlusTypeFlag`  
 [na zewnątrz] Flaga określająca typ wartości pola.  
  
 `ppValue`  
 [na zewnątrz] Stała wartość pola.  
  
 `pcchValue`  
 [na zewnątrz] Rozmiar w znakach `ppValue`, lub zero, jeśli nie istnieje ciąg.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Okręg wyborczy Cor.h  
  
 **Biblioteka:** Uwzględnione jako zasób w pliku MsCorEE.dll  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [IMetaDataImport — Interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
