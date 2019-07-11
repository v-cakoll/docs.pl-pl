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
ms.openlocfilehash: 276a69deecccc91b3c511403c2bd0d5c0baabd9d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67772798"
---
# <a name="iclrerrorreportingmanagergetbucketparametersforcurrentexception-method"></a><span data-ttu-id="33116-102">ICLRErrorReportingManager::GetBucketParametersForCurrentException — Metoda</span><span class="sxs-lookup"><span data-stu-id="33116-102">ICLRErrorReportingManager::GetBucketParametersForCurrentException Method</span></span>
<span data-ttu-id="33116-103">Pobiera pakiet programu Watson bieżący wyjątek w wątku wywołującego.</span><span class="sxs-lookup"><span data-stu-id="33116-103">Gets the Watson bucket for the current exception on the calling thread.</span></span>  
  
 <span data-ttu-id="33116-104">A *zasobnika* to kolekcja danych błędu, który jest powiązany z samą wadę kodu.</span><span class="sxs-lookup"><span data-stu-id="33116-104">A *bucket* is a collection of error data that is related to the same code defect.</span></span> <span data-ttu-id="33116-105">*Watson* odwołuje się do zestawu technologii do zbierania i analizowania danych, który jest skojarzony z powodu wyjątku.</span><span class="sxs-lookup"><span data-stu-id="33116-105">*Watson* refers to a set of technologies for collecting and analyzing data that is associated with an exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33116-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="33116-106">Syntax</span></span>  
  
```cpp  
HRESULT GetBucketParametersForCurrentException(  
    [out] BucketParameters *pParams  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="33116-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="33116-107">Parameters</span></span>  
 `pParams`  
 <span data-ttu-id="33116-108">[out] Wskaźnik do [bucketparameters —](../../../../docs/framework/unmanaged-api/hosting/bucketparameters-structure.md) strukturę, która zawiera dane o błędach dla wyjątku.</span><span class="sxs-lookup"><span data-stu-id="33116-108">[out] A pointer to a [BucketParameters](../../../../docs/framework/unmanaged-api/hosting/bucketparameters-structure.md) structure that contains error data for the exception.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="33116-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="33116-109">Requirements</span></span>  
 <span data-ttu-id="33116-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="33116-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="33116-111">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="33116-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="33116-112">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="33116-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="33116-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="33116-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33116-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="33116-114">See also</span></span>

- [<span data-ttu-id="33116-115">ICLRErrorReportingManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="33116-115">ICLRErrorReportingManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)
