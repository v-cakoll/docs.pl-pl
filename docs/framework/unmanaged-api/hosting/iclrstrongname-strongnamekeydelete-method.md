---
title: ICLRStrongName::StrongNameKeyDelete — Metoda
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameKeyDelete
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameKeyDelete
helpviewer_keywords:
- StrongNameKeyDelete method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameKeyDelete method [.NET Framework hosting]
ms.assetid: 0163412f-f617-4428-89e0-03992fec31e8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 412aa8fd30294ac9681a5edd02bb4bdfe25b3fab
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59143991"
---
# <a name="iclrstrongnamestrongnamekeydelete-method"></a>ICLRStrongName::StrongNameKeyDelete — Metoda
Usuwa określony kontener kluczy.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT StrongNameKeyDelete (  
    [in]  LPCWSTR   wszKeyContainer  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `wszKeyContainer`  
 [in] Nazwa kontenera kluczy do usunięcia.  
  
## <a name="return-value"></a>Wartość zwracana  
 `S_OK` Jeśli metoda została ukończona pomyślnie; w przeciwnym razie wartość HRESULT, która wskazuje błąd (zobacz [typowe wartości HRESULT](https://go.microsoft.com/fwlink/?LinkId=213878) dla listy).  
  
## <a name="remarks"></a>Uwagi  
 Użyj [iclrstrongname::strongnamekeyinstall —](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md) metodę, aby zaimportować pary kluczy publiczny/prywatny w kontenerze.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MetaHost.h  
  
 **Biblioteka:** Dołączony jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [StrongNameKeyInstall, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md)
- [ICLRStrongName — Interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
