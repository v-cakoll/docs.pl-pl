---
title: IGCHost::SetVirtualMemLimit — Metoda
ms.date: 03/30/2017
api_name:
- IGCHost.SetVirtualMemLimit
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- SetVirtualMemLimit
helpviewer_keywords:
- IGCHost::SetVirtualMemLimit method [.NET Framework hosting]
- SetVirtualMemLimit method [.NET Framework hosting]
ms.assetid: c7e7c2d0-e58c-4650-b40c-47b2be2cda45
topic_type:
- apiref
ms.openlocfilehash: c060e4883335a8318970b5fbd74bf72c9e13f5bf
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134862"
---
# <a name="igchostsetvirtualmemlimit-method"></a>IGCHost::SetVirtualMemLimit — Metoda
Ustawia maksymalny rozmiar pamięci wirtualnej środowiska uruchomieniowego.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT SetVirtualMemLimit (  
    [in] SIZE_T sztMaxVirtualMemMB  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `sztMaxVirtualMemMB`  
 podczas Maksymalny rozmiar pamięci wirtualnej środowiska uruchomieniowego (w megabajtach).  
  
## <a name="remarks"></a>Uwagi  
 Maksymalny rozmiar pamięci wirtualnej środowiska uruchomieniowego można zmienić dynamicznie.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** GCHost. idl, GCHost. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IGCHost, interfejs](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)
