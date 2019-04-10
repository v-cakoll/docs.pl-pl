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
ms.openlocfilehash: de17a91b5093372579a4d9435532a95406addd0a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59216902"
---
# <a name="iclrassemblyreferencelistisstringassemblyreferenceinlist-method"></a><span data-ttu-id="267e4-102">ICLRAssemblyReferenceList::IsStringAssemblyReferenceInList — Metoda</span><span class="sxs-lookup"><span data-stu-id="267e4-102">ICLRAssemblyReferenceList::IsStringAssemblyReferenceInList Method</span></span>
<span data-ttu-id="267e4-103">Pobiera wartość wskazującą, czy podana nazwa jest zgodna z nazwą zestawu na liście.</span><span class="sxs-lookup"><span data-stu-id="267e4-103">Gets a value that indicates whether the supplied name matches the name of an assembly in the list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="267e4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="267e4-104">Syntax</span></span>  
  
```  
HRESULT IsStringAssemblyReferenceInList (  
    [in] LPCWSTR pwzAssemblyName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="267e4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="267e4-105">Parameters</span></span>  
 `pwzAssemblyName`  
 <span data-ttu-id="267e4-106">[in] Nazwa zestawu, który chcesz wyszukać.</span><span class="sxs-lookup"><span data-stu-id="267e4-106">[in] The name of the assembly for which to search.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="267e4-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="267e4-107">Return Value</span></span>  
  
|<span data-ttu-id="267e4-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="267e4-108">HRESULT</span></span>|<span data-ttu-id="267e4-109">Opis</span><span class="sxs-lookup"><span data-stu-id="267e4-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="267e4-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="267e4-110">S_OK</span></span>|<span data-ttu-id="267e4-111">Ten ciąg pojawi się na liście.</span><span class="sxs-lookup"><span data-stu-id="267e4-111">The string appears in the list.</span></span>|  
|<span data-ttu-id="267e4-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="267e4-112">S_FALSE</span></span>|<span data-ttu-id="267e4-113">Ciąg nie ma na liście.</span><span class="sxs-lookup"><span data-stu-id="267e4-113">The string does not appear in the list.</span></span>|  
|<span data-ttu-id="267e4-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="267e4-114">E_FAIL</span></span>|<span data-ttu-id="267e4-115">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="267e4-115">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="267e4-116">Po powrocie z metody E_FAIL środowiska uruchomieniowego języka wspólnego nie będzie już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="267e4-116">After a method returns E_FAIL, the common language runtime is no longer usable within the process.</span></span> <span data-ttu-id="267e4-117">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="267e4-117">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="267e4-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="267e4-118">Requirements</span></span>  
 <span data-ttu-id="267e4-119">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="267e4-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="267e4-120">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="267e4-120">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="267e4-121">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="267e4-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="267e4-122">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="267e4-122">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="267e4-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="267e4-123">See also</span></span>

- [<span data-ttu-id="267e4-124">ICLRAssemblyIdentityManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="267e4-124">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="267e4-125">ICLRAssemblyReferenceList — Interfejs</span><span class="sxs-lookup"><span data-stu-id="267e4-125">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="267e4-126">IHostAssemblyManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="267e4-126">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
- [<span data-ttu-id="267e4-127">IHostAssemblyStore — Interfejs</span><span class="sxs-lookup"><span data-stu-id="267e4-127">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
