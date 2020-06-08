---
title: IMetaDataImport::GetMemberProps — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetMemberProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetMemberProps
helpviewer_keywords:
- IMetaDataImport::GetMemberProps method [.NET Framework metadata]
- GetMemberProps method [.NET Framework metadata]
ms.assetid: 42790918-4142-4938-b8f4-a56979a55846
topic_type:
- apiref
ms.openlocfilehash: 0357444aa8fa38bce5a7175cf6aacfe1a2b2b16e
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503643"
---
# <a name="imetadataimportgetmemberprops-method"></a>IMetaDataImport::GetMemberProps — Metoda
Pobiera informacje przechowywane w metadanych dla określonej definicji elementu członkowskiego, w tym nazwę, podpis binarny i względny adres wirtualny, do <xref:System.Type> elementu członkowskiego, do którego odwołuje się określony token metadanych. Jest to prosta metoda pomocnicza: Jeśli *MB* jest elementem MethodDef, **GetMethodProps —** jest wywoływana; Jeśli liczba *MB* to FieldDef, **GetFieldProps —** jest wywoływana. Zobacz te inne metody, aby uzyskać szczegółowe informacje.
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetMemberProps (  
   [in]  mdToken           mb,
   [out] mdTypeDef         *pClass,  
   [out] LPWSTR            szMember,
   [in]  ULONG             cchMember,
   [out] ULONG             *pchMember,
   [out] DWORD             *pdwAttr,  
   [out] PCCOR_SIGNATURE   *ppvSigBlob,
   [out] ULONG             *pcbSigBlob,
   [out] ULONG             *pulCodeRVA,
   [out] DWORD             *pdwImplFlags,
   [out] DWORD             *pdwCPlusTypeFlag,
   [out] UVCP_CONSTANT     *ppValue,  
   [out] ULONG             *pcchValue  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `mb`  
 podczas Token, który odwołuje się do elementu członkowskiego, aby uzyskać skojarzone metadane.  
  
 `pClass`  
 określoną Wskaźnik do tokenu metadanych, który reprezentuje klasę elementu członkowskiego.  
  
 `szMember`  
 określoną Nazwa elementu członkowskiego.  
  
 `cchMember`  
 podczas Rozmiar w postaci znaków dwubajtowych w `szMember` buforze.  
  
 `pchMember`  
 określoną Rozmiar w postaci znaków dwubajtowych zwracanej nazwy.  
  
 `pdwAttr`  
 określoną Wszystkie wartości flag zastosowane do elementu członkowskiego.  
  
 `ppvSigBlob`  
 określoną Wskaźnik do binarnego podpisu metadanych elementu członkowskiego.  
  
 `pcbSigBlob`  
 określoną Rozmiar w bajtach `ppvSigBlob` .  
  
 `pulCodeRVA`  
 określoną Wskaźnik do względnego adresu wirtualnego elementu członkowskiego.  
  
 `pdwImplFlags`  
 określoną Wszystkie flagi implementacji metody skojarzone z elementem członkowskim.  
  
 `pdwCPlusTypeFlag`  
 określoną Flaga oznaczająca element <xref:System.ValueType> . Jest to jedna z `ELEMENT_TYPE_*` wartości.
  
 `ppValue`  
 określoną Wartość stałej ciągu zwrócona przez ten element członkowski.  
  
 `pcchValue`  
 określoną Rozmiar w znakach `ppValue` lub zero, jeśli nie zawiera `ppValue` ciągu.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** Cor. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IMetaDataImport — Interfejs](imetadataimport-interface.md)
- [IMetaDataImport2, interfejs](imetadataimport2-interface.md)
