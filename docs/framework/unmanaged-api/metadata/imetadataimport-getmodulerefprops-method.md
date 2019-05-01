---
title: IMetaDataImport::GetModuleRefProps — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetModuleRefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetModuleRefProps
helpviewer_keywords:
- GetModuleRefProps method [.NET Framework metadata]
- IMetaDataImport::GetModuleRefProps method [.NET Framework metadata]
ms.assetid: b558e766-4c11-4628-ae47-b4e0a1800168
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e948644e4f2d91b2f1e3e3627f7adbe204dee9d4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61777679"
---
# <a name="imetadataimportgetmodulerefprops-method"></a>IMetaDataImport::GetModuleRefProps — Metoda
Pobiera nazwę modułu odwołuje się token określonych metadanych.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetModuleRefProps (  
   [in]  mdModuleRef         mur,  
   [out] LPWSTR              szName,   
   [in]  ULONG               cchName,   
   [out] ULONG               *pchName   
);  
```  
  
## <a name="parameters"></a>Parametry  
 `mur`  
 [in] Element ModuleRef metadanych tokenu który odwołuje się moduł, aby uzyskać informacje o metadanych.  
  
 `szName`  
 [out] Bufor do przechowywania nazwy modułu.  
  
 `cchName`  
 [in] Żądany rozmiar `szName` w znaki dwubajtowe.  
  
 `pchName`  
 [out] Rozmiar zwróconego `szName` w znaki dwubajtowe.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** COR.h  
  
 **Biblioteka:** Dołączony jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IMetaDataImport, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
