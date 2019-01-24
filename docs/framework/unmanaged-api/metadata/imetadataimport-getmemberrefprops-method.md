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
ms.openlocfilehash: 5ac0d77b1d8d35a7753d3a501f147bd5ac53750c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54583733"
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
 [in] Token MemberRef do zwrócenia skojarzone metadane.  
  
 `ptk`  
 [out] Token TypeDef TypeRef i/lub elementu TypeSpec, który reprezentuje klasę, która deklaruje element członkowski lub token element ModuleRef, który reprezentuje klasę modułu, która deklaruje element członkowski lub MethodDef, który reprezentuje element członkowski.  
  
 `szMember`  
 [out] Buforu ciągu dla nazwy elementu członkowskiego.  
  
 `cchMember`  
 [in] Żądany rozmiar w znaków `szMember`.  
  
 `pchMember`  
 [out] Rozmiar zwrócony w znaków `szMember`.  
  
 `ppvSibBlob`  
 [out] Wskaźnik do podpisu metadanych binarnych dla elementu członkowskiego.  
  
 `pbSig`  
 [out] Rozmiar w bajtach `ppvSigBlob`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** COR.h  
  
 **Biblioteka:** Dołączony jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [IMetaDataImport, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
