---
title: ICLRErrorReportingManager::GetBucketParametersForCurrentException — Metoda
ms.date: 03/30/2017
api_name:
- ICLRErrorReportingManager.GetBucketParametersForCurrentException
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRErrorReportingManager::GetBucketParametersForCurrentException
helpviewer_keywords:
- ICLRErrorReportingManager::GetBucketParametersForCurrentException method [.NET Framework hosting]
- GetBucketParametersForCurrentException method [.NET Framework hosting]
ms.assetid: a13ec8a6-8e18-4acb-8054-77f5b1a0e0b9
topic_type:
- apiref
ms.openlocfilehash: b24f8ed4f5e2c6e0022f5599f2ab8c44a30a561a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129278"
---
# <a name="iclrerrorreportingmanagergetbucketparametersforcurrentexception-method"></a>ICLRErrorReportingManager::GetBucketParametersForCurrentException — Metoda
Pobiera pakiet programu Watson dla bieżącego wyjątku w wątku wywołującym.  
  
 *Zasobnik* to kolekcja danych błędów, która jest powiązana z tą samą wadą kodu. Program *Watson* odwołuje się do zestawu technologii służących do zbierania i analizowania danych, które są skojarzone z wyjątkiem.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetBucketParametersForCurrentException(  
    [out] BucketParameters *pParams  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pParams`  
 określoną Wskaźnik do struktury [BucketParameters —](../../../../docs/framework/unmanaged-api/hosting/bucketparameters-structure.md) , która zawiera dane błędów dla wyjątku.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICLRErrorReportingManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)
