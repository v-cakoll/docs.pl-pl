---
title: ICLRAssemblyReferenceList::IsAssemblyReferenceInList — Metoda
ms.date: 03/30/2017
api_name:
- ICLRAssemblyReferenceList.IsAssemblyReferenceInList
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyReferenceList::IsAssemblyReferenceInList
helpviewer_keywords:
- ICLRAssemblyReferenceList::IsAssemblyReferenceInList method [.NET Framework hosting]
- IsAssemblyReferenceInList method [.NET Framework hosting]
ms.assetid: 8a570813-21be-407e-92a6-7ae8de3bc728
topic_type:
- apiref
ms.openlocfilehash: 4e75b8553ff33946654a6a3b6184f98049c6a6cb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126678"
---
# <a name="iclrassemblyreferencelistisassemblyreferenceinlist-method"></a><span data-ttu-id="9c282-102">ICLRAssemblyReferenceList::IsAssemblyReferenceInList — Metoda</span><span class="sxs-lookup"><span data-stu-id="9c282-102">ICLRAssemblyReferenceList::IsAssemblyReferenceInList Method</span></span>
<span data-ttu-id="9c282-103">Pobiera wartość wskazującą, czy dostarczony wskaźnik odwołuje się do zestawu na liście.</span><span class="sxs-lookup"><span data-stu-id="9c282-103">Gets a value that indicates whether the supplied pointer refers to an assembly in the list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c282-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9c282-104">Syntax</span></span>  
  
```cpp  
HRESULT IsAssemblyReferenceInList (  
    [in] IUnknown *pName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9c282-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9c282-105">Parameters</span></span>  
 `pName`  
 <span data-ttu-id="9c282-106">podczas Wskaźnik interfejsu do zestawu, który ma zostać wyszukany.</span><span class="sxs-lookup"><span data-stu-id="9c282-106">[in] An interface pointer to the assembly for which to search.</span></span> <span data-ttu-id="9c282-107">Prawidłowe wartości są typu `IAssemblyName` lub `IReferenceIdentity`.</span><span class="sxs-lookup"><span data-stu-id="9c282-107">Valid values are of type `IAssemblyName` or `IReferenceIdentity`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9c282-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="9c282-108">Return Value</span></span>  
  
|<span data-ttu-id="9c282-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9c282-109">HRESULT</span></span>|<span data-ttu-id="9c282-110">Opis</span><span class="sxs-lookup"><span data-stu-id="9c282-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9c282-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="9c282-111">S_OK</span></span>|<span data-ttu-id="9c282-112">Ciąg zostanie wyświetlony na liście.</span><span class="sxs-lookup"><span data-stu-id="9c282-112">The string appears in the list.</span></span>|  
|<span data-ttu-id="9c282-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="9c282-113">S_FALSE</span></span>|<span data-ttu-id="9c282-114">Ciąg nie pojawia się na liście.</span><span class="sxs-lookup"><span data-stu-id="9c282-114">The string does not appear in the list.</span></span>|  
|<span data-ttu-id="9c282-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9c282-115">E_FAIL</span></span>|<span data-ttu-id="9c282-116">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="9c282-116">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="9c282-117">Gdy metoda zwraca wartość E_FAIL, środowisko uruchomieniowe języka wspólnego nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="9c282-117">After a method returns E_FAIL, the common language runtime is no longer usable within the process.</span></span> <span data-ttu-id="9c282-118">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="9c282-118">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9c282-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9c282-119">Requirements</span></span>  
 <span data-ttu-id="9c282-120">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9c282-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9c282-121">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="9c282-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9c282-122">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="9c282-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9c282-123">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9c282-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c282-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9c282-124">See also</span></span>

- [<span data-ttu-id="9c282-125">ICLRAssemblyIdentityManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="9c282-125">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="9c282-126">ICLRAssemblyReferenceList, interfejs</span><span class="sxs-lookup"><span data-stu-id="9c282-126">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="9c282-127">IHostAssemblyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="9c282-127">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
- [<span data-ttu-id="9c282-128">IHostAssemblyStore, interfejs</span><span class="sxs-lookup"><span data-stu-id="9c282-128">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
