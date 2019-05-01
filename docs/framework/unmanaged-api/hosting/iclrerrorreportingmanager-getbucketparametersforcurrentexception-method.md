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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3cb2a8d2a4e089d16b6c2129c165a9d8b6828f3f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61969836"
---
# <a name="iclrerrorreportingmanagergetbucketparametersforcurrentexception-method"></a>ICLRErrorReportingManager::GetBucketParametersForCurrentException — Metoda
Pobiera pakiet programu Watson bieżący wyjątek w wątku wywołującego.  
  
 A *zasobnika* to kolekcja danych błędu, który jest powiązany z samą wadę kodu. *Watson* odwołuje się do zestawu technologii do zbierania i analizowania danych, który jest skojarzony z powodu wyjątku.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetBucketParametersForCurrentException(  
    [out] BucketParameters *pParams  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pParams`  
 [out] Wskaźnik do [bucketparameters —](../../../../docs/framework/unmanaged-api/hosting/bucketparameters-structure.md) strukturę, która zawiera dane o błędach dla wyjątku.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** Dołączony jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICLRErrorReportingManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)
