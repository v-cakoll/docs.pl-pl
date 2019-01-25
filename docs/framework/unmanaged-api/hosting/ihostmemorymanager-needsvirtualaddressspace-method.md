---
title: IHostMemoryManager::NeedsVirtualAddressSpace — Metoda
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.NeedsVirtualAddressSpace
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::NeedsVirtualAddressSpace
helpviewer_keywords:
- IHostMemoryManager::NeedsVirtualAddressSpace method [.NET Framework hosting]
- NeedsVirtualAddressSpace method [.NET Framework hosting]
ms.assetid: 71f0eab5-0170-46f8-9f88-1df5abdeb34a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c4a67e1eb5a257cc6d4e4c9bc8798b61c97fba38
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54661753"
---
# <a name="ihostmemorymanagerneedsvirtualaddressspace-method"></a>IHostMemoryManager::NeedsVirtualAddressSpace — Metoda
Powiadamia hosta, że środowisko uruchomieniowe języka wspólnego (CLR) ma podejmują próbę użycia określonego pamięci.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT NeedsVirtualAddressSpace (  
    [in] LPVOID  startAddress,  
    [in] SIZE_T  size  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `startAddress`  
 [in] Początkowy adres pamięci.  
  
 `size`  
 [in] Rozmiar w bajtach pamięci.  
  
## <a name="remarks"></a>Uwagi  
 `NeedsVirtualAddressSpace` Metoda jest metodą wywołania zwrotnego i musi być implementowana przez moduł zapisujący aplikacji macierzystej. Jest ona wywoływana przez środowisko CLR.  
  
 Jeśli host nie chce CLR, aby użyć określonego pamięci, może on zwrócić wartość HRESULT E_OUTOFMEMORY.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** Dołączony jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [IHostMemoryManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
