---
title: IManagedObject::GetObjectIdentity — Metoda
ms.date: 03/30/2017
api_name:
- IManagedObject.GetObjectIdentity
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetObjectIdentity
helpviewer_keywords:
- GetObjectIdentity method [.NET Framework hosting]
- IManagedObject::GetObjectIdentity method [.NET Framework hosting]
ms.assetid: b862ff3e-e480-4cdf-84e2-e1013334a467
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4d825a0c67f88e1f37023feb96a217b115653056
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57496940"
---
# <a name="imanagedobjectgetobjectidentity-method"></a><span data-ttu-id="a7103-102">IManagedObject::GetObjectIdentity — Metoda</span><span class="sxs-lookup"><span data-stu-id="a7103-102">IManagedObject::GetObjectIdentity Method</span></span>
<span data-ttu-id="a7103-103">Pobiera tożsamość tego zarządzanego obiektu.</span><span class="sxs-lookup"><span data-stu-id="a7103-103">Gets the identity of this managed object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7103-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a7103-104">Syntax</span></span>  
  
```  
HRESULT GetObjectIdentity (  
    [out] BSTR*   pBSTRGUID,  
    [out] int*    AppDomainID,  
    [out] CCW_PTR pCCW  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a7103-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a7103-105">Parameters</span></span>  
 `pBSTRGUID`  
 <span data-ttu-id="a7103-106">[out] Wskaźnik na identyfikator GUID procesu, w której znajduje się obiekt.</span><span class="sxs-lookup"><span data-stu-id="a7103-106">[out] A pointer to the GUID of the process in which the object resides.</span></span>  
  
 `AppDomainID`  
 <span data-ttu-id="a7103-107">[out] Wskaźnik do Identyfikatora domeny aplikacji obiektu.</span><span class="sxs-lookup"><span data-stu-id="a7103-107">[out] A pointer to the ID of the object's application domain.</span></span>  
  
 `pCCW`  
 <span data-ttu-id="a7103-108">[out] Wskaźnik do obiektu indeksu w klasycznym modelu COM v-table.</span><span class="sxs-lookup"><span data-stu-id="a7103-108">[out] A pointer to object's index in the COM classic v-table.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a7103-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a7103-109">Remarks</span></span>  
 <span data-ttu-id="a7103-110">Tożsamość obiektu zarządzanego zawiera identyfikator GUID procesu, identyfikator domeny aplikacji i indeks obiektu w klasycznym modelu COM v-table.</span><span class="sxs-lookup"><span data-stu-id="a7103-110">The identity of a managed object includes process GUID, application domain ID, and the object's index in the COM classic v-table.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a7103-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a7103-111">Requirements</span></span>  
 <span data-ttu-id="a7103-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a7103-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a7103-113">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a7103-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a7103-114">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a7103-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a7103-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a7103-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7103-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a7103-116">See also</span></span>
- [<span data-ttu-id="a7103-117">IManagedObject, interfejs</span><span class="sxs-lookup"><span data-stu-id="a7103-117">IManagedObject Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md)
