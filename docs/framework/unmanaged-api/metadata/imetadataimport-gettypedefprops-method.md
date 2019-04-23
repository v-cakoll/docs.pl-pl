---
title: IMetaDataImport::GetTypeDefProps — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetTypeDefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetTypeDefProps
helpviewer_keywords:
- GetTypeDefProps method [.NET Framework metadata]
- IMetaDataImport::GetTypeDefProps method [.NET Framework metadata]
ms.assetid: 00061a25-ba05-47a7-b984-fd916b06b149
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a482c7a06efe888408206f2de569e0a8739b85b8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59121514"
---
# <a name="imetadataimportgettypedefprops-method"></a>IMetaDataImport::GetTypeDefProps — Metoda
Zwraca informacje o metadanych <xref:System.Type> reprezentowany przez określony token TypeDef.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetTypeDefProps (  
   [in]  mdTypeDef   td,  
   [out] LPWSTR      szTypeDef,  
   [in]  ULONG       cchTypeDef,  
   [out] ULONG       *pchTypeDef,  
   [out] DWORD       *pdwTypeDefFlags,  
   [out] mdToken     *ptkExtends  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `td`  
 [in] TypeDef token, który reprezentuje typ, można zwrócić metadanych dla.  
  
 `szTypeDef`  
 [out] Bufor zawierający nazwę typu.  
  
 `cchTypeDef`  
 [in] Rozmiar w znaków `szTypeDef`.  
  
 `pchTypeDef`  
 [out] Liczba znaków dwubajtowych zwracane w `szTypeDef`.  
  
 `pdwTypeDefFlags`  
 [out] Wskaźnik do flag, które modyfikują definicji typu. Ta wartość jest z [cortypeattr —](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) wyliczenia.  
  
 `ptkExtends`  
 [out] Element TypeDef lub TypeRef metadanych token, który reprezentuje typ podstawowy elementu żądanego typu.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** COR.h  
  
 **Biblioteka:** Dołączony jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IMetaDataImport, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
