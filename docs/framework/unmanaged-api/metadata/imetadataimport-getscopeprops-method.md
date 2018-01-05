---
title: "IMetaDataImport::GetScopeProps — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetScopeProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetScopeProps
helpviewer_keywords:
- IMetaDataImport::GetScopeProps method [.NET Framework metadata]
- GetScopeProps method [.NET Framework metadata]
ms.assetid: c8ba42d2-d9fa-43cb-bbc0-f33e1e592cb6
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 53e77a7bf0bd0aafc205469c4e101f8bfdcbe80b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportgetscopeprops-method"></a>IMetaDataImport::GetScopeProps — Metoda
Pobiera nazwę i opcjonalnie identyfikator wersji zestawu lub modułu w bieżącym zakresie metadanych.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetScopeProps (  
   [out] LPWSTR           szName,  
   [in]  ULONG            cchName,  
   [out] ULONG            *pchName,  
   [out, optional] GUID   *pmvid  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `szName`  
 [out] Bufor dla nazwy zestawu lub modułu.  
  
 `cchName`  
 [in] Rozmiar w znaki dwubajtowe `szName`.  
  
 `pchName`  
 [out] Liczba zwracanych w znaki dwubajtowe `szName`.  
  
 `pmvid`  
 [out, opcjonalnie] Wskaźnik do identyfikatora GUID, który unikatowo identyfikuje wersję zestawu lub modułu.  
  
## <a name="remarks"></a>Uwagi  
 [IMetaDataEmit::SetModuleProps](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmoduleprops-method.md) metoda służy do ustawiania tych właściwości.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor.h  
  
 **Biblioteka:** uwzględnione jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [IMetaDataImport, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [IMetaDataImport2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
