---
title: "IGCHost2::SetGCStartupLimitsEx — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IGCHost2.SetGCStartupLimitsEx
api_location: mscoree.dll
api_type: COM
f1_keywords: IGCHost2::SetGCStartupLimitsEx
helpviewer_keywords:
- IGCHost2::SetGCStartupLimitsEx method [.NET Framework hosting]
- SetGCStartupLimitsEx method, IGCHost2 interface [.NET Framework hosting]
ms.assetid: bba941c2-1c57-46d3-bbf5-5fb92700c490
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ae924447e38dfec8d365fe6cdc85e5dccb028714
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="igchost2setgcstartuplimitsex-method"></a>IGCHost2::SetGCStartupLimitsEx — Metoda
Ustawia rozmiar segmentu i maksymalny rozmiar generacji 0.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT SetGCStartupLimitsEx (  
    [in] SIZE_T SegmentSize,  
    [in] SIZE_T MaxGen0Size  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `SegmentSize`  
 [in] Rozmiar segmentu używaną przez system kolekcji pamięci.  
  
 `MaxGen0Size`  
 [in] Maksymalny rozmiar generacji 0.  
  
## <a name="remarks"></a>Uwagi  
 Wartości który `SetGCStartupLimitsEx` zestawy można określić jedynie, aby uruchomić hosta. Nie można później zmienić tych wartości.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** GCHost.idl, GCHost.h  
  
 **Biblioteka:** uwzględnione jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [IGCHost2 — interfejs](../../../../docs/framework/unmanaged-api/hosting/igchost2-interface.md)
