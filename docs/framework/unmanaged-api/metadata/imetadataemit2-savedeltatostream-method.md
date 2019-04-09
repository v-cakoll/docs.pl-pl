---
title: IMetaDataEmit2::SaveDeltaToStream — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2.SaveDeltaToStream
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::SaveDeltaToStream
helpviewer_keywords:
- IMetaDataEmit2::SaveDeltaToStream method [.NET Framework metadata]
- SaveDeltaToStream method [.NET Framework metadata]
ms.assetid: ecd786e8-f9a4-4190-a6ef-af18e8c6d654
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 31bed2019eef5a37e1086624afdae3e8f2c58632
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59119213"
---
# <a name="imetadataemit2savedeltatostream-method"></a>IMetaDataEmit2::SaveDeltaToStream — Metoda
Zapisuje zmiany z bieżącej sesji Edytuj i Kontynuuj do określonego strumienia.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT SaveDeltaToStream (  
    [in] IStream     *pIStream,   
    [in] DWORD       dwSaveFlags  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pIStream`  
 [in] Wskaźnik interfejsu do zapisywalnego strumień, do której chcesz zapisać zmiany.  
  
 `dwSaveFlags`  
 [in] Zastrzeżone. Ta wartość musi mieć wartość zero.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** COR.h  
  
 **Biblioteka:** Używany jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IMetaDataEmit2 — Interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [IMetaDataEmit — Interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
