---
title: IMetaDataImport::GetMemberRefProps — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetMemberRefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetMemberRefProps
helpviewer_keywords:
- GetMemberRefProps method [.NET Framework metadata]
- IMetaDataImport::GetMemberRefProps method [.NET Framework metadata]
ms.assetid: 0ea73055-ece0-4151-a094-414c88ef8941
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0d62b9be1bef16014e2870c15a232bb46d4daf10
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33448754"
---
# <a name="imetadataimportgetmemberrefprops-method"></a>IMetaDataImport::GetMemberRefProps — Metoda
Pobiera metadane skojarzone z elementem członkowskim odwołuje się określony token.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetMemberRefProps (  
   [in]  mdMemberRef       mr,   
   [out] mdToken           *ptk,   
   [out] LPWSTR            szMember,   
   [in]  ULONG             cchMember,   
   [out] ULONG             *pchMember,   
   [out] PCCOR_SIGNATURE   *ppvSigBlob,   
   [out] ULONG             *pbSig   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `mr`  
 [in] Token elementu MemberRef do zwrócenia skojarzone metadane.  
  
 `ptk`  
 [out] Token TypeDef lub TypeRef lub elementu TypeSpec, który reprezentuje klasę, która deklaruje element członkowski lub element ModuleRef token, który reprezentuje klasę moduł, który deklaruje element członkowski lub MethodDef, który reprezentuje element członkowski.  
  
 `szMember`  
 [out] Buforu ciągu dla nazwy elementu członkowskiego.  
  
 `cchMember`  
 [in] Żądany rozmiar w znaki dwubajtowe `szMember`.  
  
 `pchMember`  
 [out] Rozmiar zwróconego w znaki dwubajtowe `szMember`.  
  
 `ppvSibBlob`  
 [out] Wskaźnik do podpisu metadanych binarnych dla elementu członkowskiego.  
  
 `pbSig`  
 [out] Wyrażony w bajtach rozmiar `ppvSigBlob`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor.h  
  
 **Biblioteka:** uwzględnione jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [IMetaDataImport, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [IMetaDataImport2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
