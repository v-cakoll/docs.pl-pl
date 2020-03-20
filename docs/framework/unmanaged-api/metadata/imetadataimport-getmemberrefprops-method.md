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
ms.openlocfilehash: a61254ba751e47b0089a3f7528aca337a32e2db3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175372"
---
# <a name="imetadataimportgetmemberrefprops-method"></a>IMetaDataImport::GetMemberRefProps — Metoda
Pobiera metadane skojarzone z elementem członkowskim, do którego odwołuje się określony token.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
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
  
## <a name="parameters"></a>Parametry  
 `mr`  
 [w] Token MemberRef do zwrócenia skojarzonych metadanych.  
  
 `ptk`  
 [na zewnątrz] A TypeDef lub TypeRef lub TypeSpec token, który reprezentuje klasę, która deklaruje element członkowski lub ModułRef token, który reprezentuje klasę modułu, który deklaruje element członkowski lub MethodDef, który reprezentuje element członkowski.  
  
 `szMember`  
 [na zewnątrz] Bufor ciągu dla nazwy członka.  
  
 `cchMember`  
 [w] Żądany rozmiar w szerokich znakach `szMember`.  
  
 `pchMember`  
 [na zewnątrz] Zwrócony rozmiar w `szMember`szerokich znakach .  
  
 `ppvSibBlob`  
 [na zewnątrz] Wskaźnik do podpisu binarnych metadanych dla członka.  
  
 `pbSig`  
 [na zewnątrz] Rozmiar w bajtach . `ppvSigBlob`  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Okręg wyborczy Cor.h  
  
 **Biblioteka:** Uwzględnione jako zasób w pliku MsCorEE.dll  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [IMetaDataImport — Interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
