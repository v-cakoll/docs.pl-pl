---
title: "IMetaDataImport::GetMemberProps — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 543929390977fc593e86947feece06f43bc0cad6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
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
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [IMetaDataImport, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [IMetaDataImport2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
