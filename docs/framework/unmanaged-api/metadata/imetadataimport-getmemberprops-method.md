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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 98d7be5adc81cff09b121265e7d5b5f712122607
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54611413"
---
# <a name="imetadataimportgetmemberprops-method"></a>IMetaDataImport::GetMemberProps — Metoda
Pobiera informacje o metadanych, w tym m.in. nazwy, podpis binarny i względny adres wirtualny, <xref:System.Type> odwołuje się token metadanych określonego elementu członkowskiego.  
  
## <a name="syntax"></a>Składnia  
  
```  
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
  
#### <a name="parameters"></a>Parametry  
 `mb`  
 [in] Token, który odwołuje się do elementu członkowskiego, który można pobrać skojarzone metadane.  
  
 `pClass`  
 [out] Wskaźnik do tokenu metadanych, który reprezentuje klasę elementu członkowskiego.  
  
 `szMember`  
 [out] Nazwa elementu członkowskiego.  
  
 `cchMember`  
 [in] Rozmiar w znaków `szMember` buforu.  
  
 `pchMember`  
 [out] Rozmiar w znaki dwubajtowe zwrócone nazwy.  
  
 `pdwAttr`  
 [out] Wartości flagi zastosowane do elementu członkowskiego.  
  
 `ppvSigBlob`  
 [out] Wskaźnik do podpisu binarne metadanych elementu członkowskiego.  
  
 `pcbSigBlob`  
 [out] Rozmiar w bajtach `ppvSigBlob`.  
  
 `pulCodeRVA`  
 [out] Wskaźnik do wirtualnej adres względny elementu członkowskiego.  
  
 `pdwImplFlags`  
 [out] Wszystkie skojarzone z elementem flagi implementacji metody.  
  
 `pdwCPlusTypeFlag`  
 [out] Flaga, która oznacza <xref:System.ValueType>.  
  
 `ppValue`  
 [out] Wartość stała ciągu zwracane przez ten element członkowski.  
  
 `pcchValue`  
 [out] Rozmiar w znakach `ppValue`, lub zero, jeśli `ppValue` nie zawiera ciągu.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** COR.h  
  
 **Biblioteka:** Dołączony jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [IMetaDataImport, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
