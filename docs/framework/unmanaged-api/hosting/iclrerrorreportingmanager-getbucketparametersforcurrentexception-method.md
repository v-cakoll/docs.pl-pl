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
# <a name="iclrerrorreportingmanagergetbucketparametersforcurrentexception-method"></a><span data-ttu-id="ec89b-102">ICLRErrorReportingManager::GetBucketParametersForCurrentException — Metoda</span><span class="sxs-lookup"><span data-stu-id="ec89b-102">ICLRErrorReportingManager::GetBucketParametersForCurrentException Method</span></span>
<span data-ttu-id="ec89b-103">Pobiera pakiet programu Watson dla bieżącego wyjątku w wątku wywołującym.</span><span class="sxs-lookup"><span data-stu-id="ec89b-103">Gets the Watson bucket for the current exception on the calling thread.</span></span>  
  
 <span data-ttu-id="ec89b-104">*Zasobnik* to kolekcja danych błędów, która jest powiązana z tą samą wadą kodu.</span><span class="sxs-lookup"><span data-stu-id="ec89b-104">A *bucket* is a collection of error data that is related to the same code defect.</span></span> <span data-ttu-id="ec89b-105">Program *Watson* odwołuje się do zestawu technologii służących do zbierania i analizowania danych, które są skojarzone z wyjątkiem.</span><span class="sxs-lookup"><span data-stu-id="ec89b-105">*Watson* refers to a set of technologies for collecting and analyzing data that is associated with an exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec89b-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="ec89b-106">Syntax</span></span>  
  
```cpp  
HRESULT GetBucketParametersForCurrentException(  
    [out] BucketParameters *pParams  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ec89b-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="ec89b-107">Parameters</span></span>  
 `pParams`  
 <span data-ttu-id="ec89b-108">określoną Wskaźnik do struktury [BucketParameters —](../../../../docs/framework/unmanaged-api/hosting/bucketparameters-structure.md) , która zawiera dane błędów dla wyjątku.</span><span class="sxs-lookup"><span data-stu-id="ec89b-108">[out] A pointer to a [BucketParameters](../../../../docs/framework/unmanaged-api/hosting/bucketparameters-structure.md) structure that contains error data for the exception.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ec89b-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ec89b-109">Requirements</span></span>  
 <span data-ttu-id="ec89b-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ec89b-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ec89b-111">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="ec89b-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ec89b-112">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="ec89b-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ec89b-113">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ec89b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec89b-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ec89b-114">See also</span></span>

- [<span data-ttu-id="ec89b-115">ICLRErrorReportingManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="ec89b-115">ICLRErrorReportingManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)
