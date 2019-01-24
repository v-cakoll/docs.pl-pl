---
title: IMetaDataTables2::GetMetaDataStreamInfo — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataTables2.GetMetaDataStreamInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables2::GetMetaDataStreamInfo
helpviewer_keywords:
- GetMetaDataStreamInfo method [.NET Framework metadata]
- IMetaDataTables2::GetMetaDataStreamInfo method [.NET Framework metadata]
ms.assetid: 8b280627-cc74-4789-95da-1fefc966de05
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f0301506d591a3738ea403393236c2574d48a7cb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54593969"
---
# <a name="imetadatatables2getmetadatastreaminfo-method"></a>IMetaDataTables2::GetMetaDataStreamInfo — Metoda
Pobiera nazwę, rozmiar i zawartość strumienia metadanych pod określonym indeksem.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetMetaDataStreamInfo (  
   [in]  ULONG        ix,  
   [out] const char   **ppchName,  
   [out] const void   **ppv,  
   [out] ULONG        *pcb  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ix`  
 [in] Indeks strumienia metadanych żądanej.  
  
 `ppchName`  
 [out] Wskaźnik na nazwę strumienia.  
  
 `ppv`  
 [out] Wskaźnik do strumienia metadanych.  
  
 `pcb`  
 [out] Rozmiar w bajtach z `ppv`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** COR.h  
  
 **Biblioteka:** Używany jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [IMetaDataTables2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
- [IMetaDataTables, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
