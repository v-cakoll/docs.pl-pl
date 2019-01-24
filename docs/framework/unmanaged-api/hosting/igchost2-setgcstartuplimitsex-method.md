---
title: IGCHost2::SetGCStartupLimitsEx — Metoda
ms.date: 03/30/2017
api_name:
- IGCHost2.SetGCStartupLimitsEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IGCHost2::SetGCStartupLimitsEx
helpviewer_keywords:
- IGCHost2::SetGCStartupLimitsEx method [.NET Framework hosting]
- SetGCStartupLimitsEx method, IGCHost2 interface [.NET Framework hosting]
ms.assetid: bba941c2-1c57-46d3-bbf5-5fb92700c490
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f61f6ed5712f3c98f06f5fa76657f3fa7b70fe84
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54666335"
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
 [in] Rozmiar segmentu używaną przez system kolekcji wyrzucania elementów.  
  
 `MaxGen0Size`  
 [in] Maksymalny rozmiar generacji 0.  
  
## <a name="remarks"></a>Uwagi  
 Wartości, `SetGCStartupLimitsEx` zestawy można określić tylko, aby uruchomić hosta. Te wartości nie można zmienić później.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** GCHost.idl, GCHost.h  
  
 **Biblioteka:** Dołączony jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [IGCHost2, interfejs](../../../../docs/framework/unmanaged-api/hosting/igchost2-interface.md)
