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
ms.openlocfilehash: 2bd05b49c3d51ac13865997910c99cc0cd5ca2d9
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84491250"
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
 określoną Rozmiar w bajtach `ppvSigBlob` .  
  
 `pdwCPlusTypeFlag`  
 określoną Flaga określająca typ wartości pola.  
  
 `ppValue`  
 określoną Stała wartość pola.  
  
 `pcchValue`  
 określoną Rozmiar w znakach `ppValue` lub zero, jeśli nie istnieje ciąg.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** Cor. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IMetaDataImport — Interfejs](imetadataimport-interface.md)
- [IMetaDataImport2, interfejs](imetadataimport2-interface.md)
