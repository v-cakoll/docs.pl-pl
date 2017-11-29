---
title: "IMetaDataTables::GetBlob — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataTables.GetBlob
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataTables::GetBlob
helpviewer_keywords:
- GetBlob method [.NET Framework metadata]
- IMetaDataTables::GetBlob method [.NET Framework metadata]
ms.assetid: 94667c1c-6d58-4aa7-b74e-530b11e2a276
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c777396c5020e738c3aade0217bc400aa595dd30
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="imetadatatablesgetblob-method"></a>IMetaDataTables::GetBlob — Metoda
Pobiera wskaźnik do dużego obiektu binarnego (BLOB) pod indeksem określonej kolumny.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetBlob (  
    [in]  ULONG          ixBlob,  
    [out] ULONG          *pcbData,  
    [out] const void     **ppData  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ixBlob`  
 [in] Adres pamięci, z którego można pobrać `ppData`.  
  
 `pcbData`  
 [out] Wskaźnik do rozmiar w bajtach z `ppData`.  
  
 `ppData`  
 [out] Pobrać wskaźnik na wskaźnik do danych binarnych.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor.h  
  
 **Biblioteka:** używany jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [IMetaDataTables — interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [IMetaDataTables2 — interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
