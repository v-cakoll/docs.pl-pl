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
ms.openlocfilehash: 72e14ea0414ebdeb8f54a4bdef8ce5208fc8ef72
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177227"
---
# <a name="imetadataimportgetmemberprops-method"></a>IMetaDataImport::GetMemberProps — Metoda
Pobiera informacje przechowywane w metadanych dla definicji określonego elementu członkowskiego, w tym <xref:System.Type> nazwę, podpis binarny i względny adres wirtualny elementu członkowskiego, do którego odwołuje się określony token metadanych. Jest to prosta metoda pomocnika: jeśli *mb* jest MethodDef, a następnie **GetMethodProps** jest wywoływana; jeśli *mb* jest FieldDef, a następnie **GetFieldProps** jest wywoływana. Zobacz te inne metody, aby uzyskać szczegółowe informacje.
  
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
 [w] Token, który odwołuje się do elementu członkowskiego, aby uzyskać skojarzone metadane.  
  
 `pClass`  
 [na zewnątrz] Wskaźnik do tokenu metadanych, który reprezentuje klasę członka.  
  
 `szMember`  
 [na zewnątrz] Nazwa elementu członkowskiego.  
  
 `cchMember`  
 [w] Rozmiar w szerokich `szMember` znakach buforu.  
  
 `pchMember`  
 [na zewnątrz] Rozmiar w szerokich znakach zwracanej nazwy.  
  
 `pdwAttr`  
 [na zewnątrz] Wszystkie wartości flag zastosowanych do elementu członkowskiego.  
  
 `ppvSigBlob`  
 [na zewnątrz] Wskaźnik do podpisu binarnych metadanych członka.  
  
 `pcbSigBlob`  
 [na zewnątrz] Rozmiar w bajtach . `ppvSigBlob`  
  
 `pulCodeRVA`  
 [na zewnątrz] Wskaźnik do względnego adresu wirtualnego elementu członkowskiego.  
  
 `pdwImplFlags`  
 [na zewnątrz] Flagi implementacji dowolnej metody skojarzone z elementem członkowskim.  
  
 `pdwCPlusTypeFlag`  
 [na zewnątrz] Flaga oznaczająca <xref:System.ValueType>. Jest to jedna `ELEMENT_TYPE_*` z wartości.
  
 `ppValue`  
 [na zewnątrz] Stała wartość ciągu zwrócona przez ten element członkowski.  
  
 `pcchValue`  
 [na zewnątrz] Rozmiar znaków `ppValue`, lub zero, jeśli `ppValue` nie posiada ciągu.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Okręg wyborczy Cor.h  
  
 **Biblioteka:** Uwzględnione jako zasób w pliku MsCorEE.dll  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [IMetaDataImport — Interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
