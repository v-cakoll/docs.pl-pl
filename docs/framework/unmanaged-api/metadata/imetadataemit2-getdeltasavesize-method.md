---
title: IMetaDataEmit2::GetDeltaSaveSize — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2.GetDeltaSaveSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::GetDeltaSaveSize
helpviewer_keywords:
- IMetaDataEmit2::GetDeltaSaveSize method [.NET Framework metadata]
- GetDeltaSaveSize method [.NET Framework metadata]
ms.assetid: 036db5e7-8211-4645-9a34-03d1a89be955
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ad6e565db634477e4f0382afdec12361ce7111a8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33446512"
---
# <a name="imetadataemit2getdeltasavesize-method"></a>IMetaDataEmit2::GetDeltaSaveSize — Metoda
Pobiera wartość wskazującą, wszelkie zmiany rozmiaru metadanych, będącą wynikiem bieżącej sesji edit-and-continue.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetDeltaSaveSize (  
    [in]  CorSaveSize  fSave,  
    [out] DWORD        *pdwSaveSize  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `fSave`  
 [in] Jeden z [CorSaveSize](../../../../docs/framework/unmanaged-api/metadata/corsavesize-enumeration.md) wartości i wskazujący poziom dokładności potrzebne. Ten parametr jest ignorowany dla programu .NET Framework w wersji 2.0.  
  
 `pdwSaveSize`  
 [out] Zmiana rozmiaru metadanych.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor.h  
  
 **Biblioteka:** używany jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [IMetaDataEmit2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)  
 [IMetaDataEmit, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
