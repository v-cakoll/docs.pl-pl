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
ms.openlocfilehash: 1b40ed8e107d30c22b4ade25d29376b1b74583d1
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/26/2020
ms.locfileid: "83842416"
---
# <a name="imanagedobjectgetobjectidentity-method"></a><span data-ttu-id="8b2ff-102">IManagedObject::GetObjectIdentity — Metoda</span><span class="sxs-lookup"><span data-stu-id="8b2ff-102">IManagedObject::GetObjectIdentity Method</span></span>
<span data-ttu-id="8b2ff-103">Pobiera tożsamość tego obiektu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="8b2ff-103">Gets the identity of this managed object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b2ff-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8b2ff-104">Syntax</span></span>  
  
```cpp  
HRESULT GetObjectIdentity (  
    [out] BSTR*   pBSTRGUID,  
    [out] int*    AppDomainID,  
    [out] CCW_PTR pCCW  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8b2ff-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8b2ff-105">Parameters</span></span>  
 `pBSTRGUID`  
 <span data-ttu-id="8b2ff-106">określoną Wskaźnik do identyfikatora GUID procesu, w którym znajduje się obiekt.</span><span class="sxs-lookup"><span data-stu-id="8b2ff-106">[out] A pointer to the GUID of the process in which the object resides.</span></span>  
  
 `AppDomainID`  
 <span data-ttu-id="8b2ff-107">określoną Wskaźnik do identyfikatora domeny aplikacji obiektu.</span><span class="sxs-lookup"><span data-stu-id="8b2ff-107">[out] A pointer to the ID of the object's application domain.</span></span>  
  
 `pCCW`  
 <span data-ttu-id="8b2ff-108">określoną Wskaźnik do indeksu obiektu w klasycznej tabeli COM.</span><span class="sxs-lookup"><span data-stu-id="8b2ff-108">[out] A pointer to object's index in the COM classic v-table.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8b2ff-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8b2ff-109">Remarks</span></span>  
 <span data-ttu-id="8b2ff-110">Tożsamość obiektu zarządzanego obejmuje identyfikator GUID procesu, identyfikator domeny aplikacji i indeks obiektu w klasycznej tabeli COM.</span><span class="sxs-lookup"><span data-stu-id="8b2ff-110">The identity of a managed object includes process GUID, application domain ID, and the object's index in the COM classic v-table.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8b2ff-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8b2ff-111">Requirements</span></span>  
 <span data-ttu-id="8b2ff-112">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8b2ff-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8b2ff-113">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="8b2ff-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8b2ff-114">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="8b2ff-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8b2ff-115">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8b2ff-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b2ff-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8b2ff-116">See also</span></span>

- [<span data-ttu-id="8b2ff-117">IManagedObject, interfejs</span><span class="sxs-lookup"><span data-stu-id="8b2ff-117">IManagedObject Interface</span></span>](imanagedobject-interface.md)
