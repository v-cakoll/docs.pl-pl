---
title: "ICLRAssemblyReferenceList::IsStringAssemblyReferenceInList — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRAssemblyReferenceList.IsStringAssemblyReferenceInList
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRAssemblyReferenceList::IsStringAssemblyReferenceInList
helpviewer_keywords:
- ICLRAssemblyReferenceList::IsStringAssemblyReferenceInList method [.NET Framework hosting]
- IsStringAssemblyReferenceInList method [.NET Framework hosting]
ms.assetid: e6121cc3-2f11-42c7-bdae-47808581ff71
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 27d81e8b5171ded3301eaafea19d4a09b461078e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="iclrassemblyreferencelistisstringassemblyreferenceinlist-method"></a><span data-ttu-id="2bf2a-102">ICLRAssemblyReferenceList::IsStringAssemblyReferenceInList — Metoda</span><span class="sxs-lookup"><span data-stu-id="2bf2a-102">ICLRAssemblyReferenceList::IsStringAssemblyReferenceInList Method</span></span>
<span data-ttu-id="2bf2a-103">Pobiera wartość wskazującą, czy podana nazwa odpowiada nazwie zestawu na liście.</span><span class="sxs-lookup"><span data-stu-id="2bf2a-103">Gets a value that indicates whether the supplied name matches the name of an assembly in the list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2bf2a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2bf2a-104">Syntax</span></span>  
  
```  
HRESULT IsStringAssemblyReferenceInList (  
    [in] LPCWSTR pwzAssemblyName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2bf2a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2bf2a-105">Parameters</span></span>  
 `pwzAssemblyName`  
 <span data-ttu-id="2bf2a-106">[in] Nazwa zestawu, który chcesz wyszukać.</span><span class="sxs-lookup"><span data-stu-id="2bf2a-106">[in] The name of the assembly for which to search.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2bf2a-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="2bf2a-107">Return Value</span></span>  
  
|<span data-ttu-id="2bf2a-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2bf2a-108">HRESULT</span></span>|<span data-ttu-id="2bf2a-109">Opis</span><span class="sxs-lookup"><span data-stu-id="2bf2a-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2bf2a-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="2bf2a-110">S_OK</span></span>|<span data-ttu-id="2bf2a-111">Ten ciąg jest wyświetlana na liście.</span><span class="sxs-lookup"><span data-stu-id="2bf2a-111">The string appears in the list.</span></span>|  
|<span data-ttu-id="2bf2a-112">WARTOŚCI S_FALSE</span><span class="sxs-lookup"><span data-stu-id="2bf2a-112">S_FALSE</span></span>|<span data-ttu-id="2bf2a-113">Ciąg nie ma na liście.</span><span class="sxs-lookup"><span data-stu-id="2bf2a-113">The string does not appear in the list.</span></span>|  
|<span data-ttu-id="2bf2a-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2bf2a-114">E_FAIL</span></span>|<span data-ttu-id="2bf2a-115">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="2bf2a-115">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="2bf2a-116">Po powrocie E_FAIL metody środowisko uruchomieniowe języka wspólnego nie będzie już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="2bf2a-116">After a method returns E_FAIL, the common language runtime is no longer usable within the process.</span></span> <span data-ttu-id="2bf2a-117">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="2bf2a-117">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2bf2a-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2bf2a-118">Requirements</span></span>  
 <span data-ttu-id="2bf2a-119">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2bf2a-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2bf2a-120">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="2bf2a-120">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2bf2a-121">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2bf2a-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2bf2a-122">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2bf2a-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2bf2a-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2bf2a-123">See Also</span></span>  
 [<span data-ttu-id="2bf2a-124">ICLRAssemblyIdentityManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="2bf2a-124">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [<span data-ttu-id="2bf2a-125">ICLRAssemblyReferenceList, interfejs</span><span class="sxs-lookup"><span data-stu-id="2bf2a-125">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="2bf2a-126">IHostAssemblyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="2bf2a-126">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
 [<span data-ttu-id="2bf2a-127">IHostAssemblyStore, interfejs</span><span class="sxs-lookup"><span data-stu-id="2bf2a-127">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
