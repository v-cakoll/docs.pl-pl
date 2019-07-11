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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6aeda4901551b7e79becff132e44382ed11b0d31
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67773353"
---
# <a name="iclrassemblyreferencelistisassemblyreferenceinlist-method"></a><span data-ttu-id="44b1e-102">ICLRAssemblyReferenceList::IsAssemblyReferenceInList — Metoda</span><span class="sxs-lookup"><span data-stu-id="44b1e-102">ICLRAssemblyReferenceList::IsAssemblyReferenceInList Method</span></span>
<span data-ttu-id="44b1e-103">Pobiera wartość wskazującą, czy podany wskaźnik odwołuje się do zestawu, na liście.</span><span class="sxs-lookup"><span data-stu-id="44b1e-103">Gets a value that indicates whether the supplied pointer refers to an assembly in the list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44b1e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="44b1e-104">Syntax</span></span>  
  
```cpp  
HRESULT IsAssemblyReferenceInList (  
    [in] IUnknown *pName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="44b1e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="44b1e-105">Parameters</span></span>  
 `pName`  
 <span data-ttu-id="44b1e-106">[in] Wskaźnik interfejsu do zestawu, który chcesz wyszukać.</span><span class="sxs-lookup"><span data-stu-id="44b1e-106">[in] An interface pointer to the assembly for which to search.</span></span> <span data-ttu-id="44b1e-107">Prawidłowe wartości są typu `IAssemblyName` lub `IReferenceIdentity`.</span><span class="sxs-lookup"><span data-stu-id="44b1e-107">Valid values are of type `IAssemblyName` or `IReferenceIdentity`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="44b1e-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="44b1e-108">Return Value</span></span>  
  
|<span data-ttu-id="44b1e-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="44b1e-109">HRESULT</span></span>|<span data-ttu-id="44b1e-110">Opis</span><span class="sxs-lookup"><span data-stu-id="44b1e-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="44b1e-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="44b1e-111">S_OK</span></span>|<span data-ttu-id="44b1e-112">Ten ciąg pojawi się na liście.</span><span class="sxs-lookup"><span data-stu-id="44b1e-112">The string appears in the list.</span></span>|  
|<span data-ttu-id="44b1e-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="44b1e-113">S_FALSE</span></span>|<span data-ttu-id="44b1e-114">Ciąg nie ma na liście.</span><span class="sxs-lookup"><span data-stu-id="44b1e-114">The string does not appear in the list.</span></span>|  
|<span data-ttu-id="44b1e-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="44b1e-115">E_FAIL</span></span>|<span data-ttu-id="44b1e-116">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="44b1e-116">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="44b1e-117">Po powrocie z metody E_FAIL środowiska uruchomieniowego języka wspólnego nie będzie już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="44b1e-117">After a method returns E_FAIL, the common language runtime is no longer usable within the process.</span></span> <span data-ttu-id="44b1e-118">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="44b1e-118">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="44b1e-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="44b1e-119">Requirements</span></span>  
 <span data-ttu-id="44b1e-120">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="44b1e-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="44b1e-121">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="44b1e-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="44b1e-122">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="44b1e-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="44b1e-123">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="44b1e-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44b1e-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="44b1e-124">See also</span></span>

- [<span data-ttu-id="44b1e-125">ICLRAssemblyIdentityManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="44b1e-125">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="44b1e-126">ICLRAssemblyReferenceList, interfejs</span><span class="sxs-lookup"><span data-stu-id="44b1e-126">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="44b1e-127">IHostAssemblyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="44b1e-127">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
- [<span data-ttu-id="44b1e-128">IHostAssemblyStore, interfejs</span><span class="sxs-lookup"><span data-stu-id="44b1e-128">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
