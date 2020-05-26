---
title: IGCHost::SetGCStartupLimits — Metoda
ms.date: 03/30/2017
api_name:
- IGCHost.SetGCStartupLimits
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- SetGCStartupLimits
helpviewer_keywords:
- SetGCStartupLimits method, IGCHost interface [.NET Framework hosting]
- IGCHost::SetGCStartupLimits method [.NET Framework hosting]
ms.assetid: cae53926-82ac-4d1d-b297-0bde0bd1bebb
topic_type:
- apiref
ms.openlocfilehash: 3b0c11ac9d827bd252018172e2337df653054a7b
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2020
ms.locfileid: "83805201"
---
# <a name="igchostsetgcstartuplimits-method"></a>IGCHost::SetGCStartupLimits — Metoda
Ustawia rozmiar segmentu i maksymalny rozmiar generacji 0.  
  
> [!IMPORTANT]
> Począwszy od .NET Framework 4,5, można ustawić rozmiar segmentu i rozmiar maksymalnej generacji 0 na wartości większe niż przy `DWORD` użyciu metody [IGCHost2:: SetGCStartupLimitsEx —](igchost2-setgcstartuplimitsex-method.md) .  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT SetGCStartupLimits (  
    [in] DWORD SegmentSize,  
    [in] DWORD MaxGen0Size  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `SegmentSize`  
 podczas Rozmiar segmentu używany przez system odzyskiwania pamięci.  
  
 `MaxGen0Size`  
 podczas Maksymalny rozmiar generacji 0.  
  
## <a name="remarks"></a>Uwagi  
 `SetGCStartupLimits`Metoda może być wywoływana tylko raz. Tych wartości nie można później zmienić.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** GCHost. idl, GCHost. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [IGCHost, interfejs](igchost-interface.md)
