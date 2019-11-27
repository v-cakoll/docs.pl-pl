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
ms.openlocfilehash: 462512fd2c2b33905b45bb67599b23b301fc71f7
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437996"
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
 podczas Token FieldDef reprezentujący pole, dla którego mają zostać pobrane powiązane metadane.  
  
 `pClass`  
 określoną Wskaźnik do tokenu TypeDef, który reprezentuje typ klasy, do której należy pole.  
  
 `szField`  
 określoną Nazwa pola.  
  
 `cchField`  
 podczas Rozmiar w postaci znaków dwubajtowych buforu dla *szField*.  
  
 `pchField`  
 określoną Rzeczywisty rozmiar zwróconego buforu.  
  
 `pdwAttr`  
 określoną Flagi skojarzone z metadanymi pola.  
  
 `ppvSigBlob`  
 podczas Wskaźnik do wartości metadanych Binary opisującej pole.  
  
 `pcbSigBlob`  
 określoną Rozmiar w bajtach `ppvSigBlob`.  
  
 `pdwCPlusTypeFlag`  
 określoną Flaga określająca typ wartości pola.  
  
 `ppValue`  
 określoną Stała wartość pola.  
  
 `pcchValue`  
 określoną Rozmiar w znakach `ppValue`lub zero, jeśli nie istnieje żaden ciąg.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IMetaDataImport, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
