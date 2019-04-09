---
title: IMetaDataTables2::GetMetaDataStorage — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataTables2.GetMetaDataStorage
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables2::GetMetaDataStorage
helpviewer_keywords:
- GetMetaDataStorage method [.NET Framework metadata]
- IMetaDataTables2::GetMetaDataStorage method [.NET Framework metadata]
ms.assetid: 667a6d1e-753d-4ea2-8fd8-a8337d1bb9cd
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f12243571262ad7511795c48721617932fc6b30b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59161411"
---
# <a name="imetadatatables2getmetadatastorage-method"></a>IMetaDataTables2::GetMetaDataStorage — Metoda
Pobiera rozmiar i zawartość z określonej sekcji metadanych.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetMetaDataStorage (  
   [in, out] const void   **ppvMd,  
   [out] ULONG   *pcbMd  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppvMd`  
 [out w] Wskaźnik do sekcji metadanych.  
  
 `pcbMd`  
 [out] Rozmiar strumienia metadanych.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** COR.h  
  
 **Biblioteka:** Używany jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IMetaDataTables2 — Interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
- [IMetaDataTables — Interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
