---
title: ICLRAssemblyReferenceList::IsStringAssemblyReferenceInList — Metoda
ms.date: 03/30/2017
api_name:
- ICLRAssemblyReferenceList.IsStringAssemblyReferenceInList
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyReferenceList::IsStringAssemblyReferenceInList
helpviewer_keywords:
- ICLRAssemblyReferenceList::IsStringAssemblyReferenceInList method [.NET Framework hosting]
- IsStringAssemblyReferenceInList method [.NET Framework hosting]
ms.assetid: e6121cc3-2f11-42c7-bdae-47808581ff71
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4b2860e811a16406a71d7ab8df123f2b32aaf13e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67773299"
---
# <a name="iclrassemblyreferencelistisstringassemblyreferenceinlist-method"></a><span data-ttu-id="a1b1c-102">ICLRAssemblyReferenceList::IsStringAssemblyReferenceInList — Metoda</span><span class="sxs-lookup"><span data-stu-id="a1b1c-102">ICLRAssemblyReferenceList::IsStringAssemblyReferenceInList Method</span></span>
<span data-ttu-id="a1b1c-103">Pobiera wartość wskazującą, czy podana nazwa jest zgodna z nazwą zestawu na liście.</span><span class="sxs-lookup"><span data-stu-id="a1b1c-103">Gets a value that indicates whether the supplied name matches the name of an assembly in the list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1b1c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a1b1c-104">Syntax</span></span>  
  
```cpp  
HRESULT IsStringAssemblyReferenceInList (  
    [in] LPCWSTR pwzAssemblyName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a1b1c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a1b1c-105">Parameters</span></span>  
 `pwzAssemblyName`  
 <span data-ttu-id="a1b1c-106">[in] Nazwa zestawu, który chcesz wyszukać.</span><span class="sxs-lookup"><span data-stu-id="a1b1c-106">[in] The name of the assembly for which to search.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a1b1c-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="a1b1c-107">Return Value</span></span>  
  
|<span data-ttu-id="a1b1c-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a1b1c-108">HRESULT</span></span>|<span data-ttu-id="a1b1c-109">Opis</span><span class="sxs-lookup"><span data-stu-id="a1b1c-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a1b1c-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="a1b1c-110">S_OK</span></span>|<span data-ttu-id="a1b1c-111">Ten ciąg pojawi się na liście.</span><span class="sxs-lookup"><span data-stu-id="a1b1c-111">The string appears in the list.</span></span>|  
|<span data-ttu-id="a1b1c-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="a1b1c-112">S_FALSE</span></span>|<span data-ttu-id="a1b1c-113">Ciąg nie ma na liście.</span><span class="sxs-lookup"><span data-stu-id="a1b1c-113">The string does not appear in the list.</span></span>|  
|<span data-ttu-id="a1b1c-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a1b1c-114">E_FAIL</span></span>|<span data-ttu-id="a1b1c-115">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="a1b1c-115">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a1b1c-116">Po powrocie z metody E_FAIL środowiska uruchomieniowego języka wspólnego nie będzie już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="a1b1c-116">After a method returns E_FAIL, the common language runtime is no longer usable within the process.</span></span> <span data-ttu-id="a1b1c-117">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="a1b1c-117">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a1b1c-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a1b1c-118">Requirements</span></span>  
 <span data-ttu-id="a1b1c-119">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a1b1c-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a1b1c-120">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a1b1c-120">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a1b1c-121">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a1b1c-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a1b1c-122">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a1b1c-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1b1c-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a1b1c-123">See also</span></span>

- [<span data-ttu-id="a1b1c-124">ICLRAssemblyIdentityManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="a1b1c-124">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="a1b1c-125">ICLRAssemblyReferenceList, interfejs</span><span class="sxs-lookup"><span data-stu-id="a1b1c-125">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="a1b1c-126">IHostAssemblyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="a1b1c-126">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
- [<span data-ttu-id="a1b1c-127">IHostAssemblyStore, interfejs</span><span class="sxs-lookup"><span data-stu-id="a1b1c-127">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
