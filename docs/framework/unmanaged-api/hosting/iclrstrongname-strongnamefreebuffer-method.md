---
title: ICLRStrongName::StrongNameFreeBuffer — Metoda
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameFreeBuffer
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameFreeBuffer
helpviewer_keywords:
- StrongNameFreeBuffer method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameFreeBuffer method [.NET Framework hosting]
ms.assetid: 6148c508-bd1d-4a37-85c3-06ecb09cc857
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8e42f13d3d3ac0154cd1f8bbe9785e1e4ae16379
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59127572"
---
# <a name="iclrstrongnamestrongnamefreebuffer-method"></a>ICLRStrongName::StrongNameFreeBuffer — Metoda
Zwalnia pamięć, która została przydzielona z poprzedniego wywołania do metody silnej nazwy, takie jak [iclrstrongname::strongnamegetpublickey —](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md), [iclrstrongname::strongnametokenfrompublickey —](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md), lub [ Iclrstrongname::strongnamesignaturegeneration —](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegeneration-method.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT StrongNameFreeBuffer (   
   [in] BYTE   *pbMemory  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pbMemory`  
 [in] Wskaźnik do pamięci, aby zwolnić.  
  
## <a name="return-value"></a>Wartość zwracana  
 `S_OK` Jeśli metoda została ukończona pomyślnie; w przeciwnym razie wartość HRESULT, która wskazuje błąd (zobacz [typowe wartości HRESULT](https://go.microsoft.com/fwlink/?LinkId=213878) dla listy).  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MetaHost.h  
  
 **Biblioteka:** Dołączony jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICLRStrongName, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
