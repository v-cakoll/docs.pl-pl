---
title: "IHostMemoryManager::NeedsVirtualAddressSpace — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostMemoryManager.NeedsVirtualAddressSpace
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostMemoryManager::NeedsVirtualAddressSpace
helpviewer_keywords:
- IHostMemoryManager::NeedsVirtualAddressSpace method [.NET Framework hosting]
- NeedsVirtualAddressSpace method [.NET Framework hosting]
ms.assetid: 71f0eab5-0170-46f8-9f88-1df5abdeb34a
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 62ceb9e5b4d5843b8e2adad344b3ffb662ab3aff
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="ihostmemorymanagerneedsvirtualaddressspace-method"></a>IHostMemoryManager::NeedsVirtualAddressSpace — Metoda
Powiadamia hosta, że środowisko uruchomieniowe języka wspólnego (CLR) ma próbować używać pamięci określony.  
  
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
 `NeedsVirtualAddressSpace` Metoda to metoda wywołania zwrotnego i musi być implementowana przez Edytor hostingu aplikacji. Jest ona wywoływana przez środowisko CLR.  
  
 Jeśli host nie chce CLR do użycia pamięci określony, zwracać E_OUTOFMEMORY HRESULT.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** uwzględnione jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [IHostMemoryManager — interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
