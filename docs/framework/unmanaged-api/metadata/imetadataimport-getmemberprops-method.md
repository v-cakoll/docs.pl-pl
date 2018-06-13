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
ms.openlocfilehash: d93763da2afbbdb1e738c802ba172e9f16e5f7af
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33448461"
---
# <a name="imetadataimportgetmemberprops-method"></a>IMetaDataImport::GetMemberProps — Metoda
Pobiera informacje o metadanych, łącznie z nazwą, podpis binarny i wirtualny adres względny elementu <xref:System.Type> odwołuje się token metadanych określonego elementu członkowskiego.  
  
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
 [in] Token, który odwołuje się do elementu członkowskiego do pobrania skojarzone metadane.  
  
 `pClass`  
 [out] Wskaźnik do tokenu metadanych, który reprezentuje klasę elementu członkowskiego.  
  
 `szMember`  
 [out] Nazwa elementu członkowskiego.  
  
 `cchMember`  
 [in] Rozmiar w znaki dwubajtowe `szMember` buforu.  
  
 `pchMember`  
 [out] Rozmiar w znaki dwubajtowe zwrócony nazwy.  
  
 `pdwAttr`  
 [out] Wartości flagi zastosowany do elementu członkowskiego.  
  
 `ppvSigBlob`  
 [out] Wskaźnik do sygnatury binarne metadanych elementu członkowskiego.  
  
 `pcbSigBlob`  
 [out] Wyrażony w bajtach rozmiar `ppvSigBlob`.  
  
 `pulCodeRVA`  
 [out] Wskaźnik do wirtualnego adres względny elementu członkowskiego.  
  
 `pdwImplFlags`  
 [out] Wszystkie skojarzone z danym elementem flagi implementacji metod.  
  
 `pdwCPlusTypeFlag`  
 [out] Flaga, która oznacza <xref:System.ValueType>.  
  
 `ppValue`  
 [out] Wartość stałej ciągu zwróconych przez ten element członkowski.  
  
 `pcchValue`  
 [out] Rozmiar w znakach `ppValue`, lub zero, jeśli `ppValue` nie zawiera ciąg.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor.h  
  
 **Biblioteka:** uwzględnione jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [IMetaDataImport, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [IMetaDataImport2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
