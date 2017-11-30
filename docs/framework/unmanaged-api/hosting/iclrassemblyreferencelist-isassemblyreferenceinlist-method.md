---
title: "ICLRAssemblyReferenceList::IsAssemblyReferenceInList — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRAssemblyReferenceList.IsAssemblyReferenceInList
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRAssemblyReferenceList::IsAssemblyReferenceInList
helpviewer_keywords:
- ICLRAssemblyReferenceList::IsAssemblyReferenceInList method [.NET Framework hosting]
- IsAssemblyReferenceInList method [.NET Framework hosting]
ms.assetid: 8a570813-21be-407e-92a6-7ae8de3bc728
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 923f7f4178d3c310b51ebb7e7df06040ba69f9c7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="iclrassemblyreferencelistisassemblyreferenceinlist-method"></a><span data-ttu-id="4b6f2-102">ICLRAssemblyReferenceList::IsAssemblyReferenceInList — Metoda</span><span class="sxs-lookup"><span data-stu-id="4b6f2-102">ICLRAssemblyReferenceList::IsAssemblyReferenceInList Method</span></span>
<span data-ttu-id="4b6f2-103">Pobiera wartość wskazującą, czy podany wskaźnik odwołuje się do zestawu na liście.</span><span class="sxs-lookup"><span data-stu-id="4b6f2-103">Gets a value that indicates whether the supplied pointer refers to an assembly in the list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b6f2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4b6f2-104">Syntax</span></span>  
  
```  
HRESULT IsAssemblyReferenceInList (  
    [in] IUnknown *pName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4b6f2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4b6f2-105">Parameters</span></span>  
 `pName`  
 <span data-ttu-id="4b6f2-106">[in] Wskaźnik interfejsu do zestawu do wyszukania.</span><span class="sxs-lookup"><span data-stu-id="4b6f2-106">[in] An interface pointer to the assembly for which to search.</span></span> <span data-ttu-id="4b6f2-107">Prawidłowe wartości to typu `IAssemblyName` lub `IReferenceIdentity`.</span><span class="sxs-lookup"><span data-stu-id="4b6f2-107">Valid values are of type `IAssemblyName` or `IReferenceIdentity`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4b6f2-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="4b6f2-108">Return Value</span></span>  
  
|<span data-ttu-id="4b6f2-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4b6f2-109">HRESULT</span></span>|<span data-ttu-id="4b6f2-110">Opis</span><span class="sxs-lookup"><span data-stu-id="4b6f2-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4b6f2-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="4b6f2-111">S_OK</span></span>|<span data-ttu-id="4b6f2-112">Ten ciąg jest wyświetlana na liście.</span><span class="sxs-lookup"><span data-stu-id="4b6f2-112">The string appears in the list.</span></span>|  
|<span data-ttu-id="4b6f2-113">WARTOŚCI S_FALSE</span><span class="sxs-lookup"><span data-stu-id="4b6f2-113">S_FALSE</span></span>|<span data-ttu-id="4b6f2-114">Ciąg nie ma na liście.</span><span class="sxs-lookup"><span data-stu-id="4b6f2-114">The string does not appear in the list.</span></span>|  
|<span data-ttu-id="4b6f2-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="4b6f2-115">E_FAIL</span></span>|<span data-ttu-id="4b6f2-116">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="4b6f2-116">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="4b6f2-117">Po powrocie E_FAIL metody środowisko uruchomieniowe języka wspólnego nie będzie już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="4b6f2-117">After a method returns E_FAIL, the common language runtime is no longer usable within the process.</span></span> <span data-ttu-id="4b6f2-118">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="4b6f2-118">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4b6f2-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4b6f2-119">Requirements</span></span>  
 <span data-ttu-id="4b6f2-120">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4b6f2-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4b6f2-121">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="4b6f2-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4b6f2-122">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4b6f2-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4b6f2-123">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4b6f2-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b6f2-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4b6f2-124">See Also</span></span>  
 [<span data-ttu-id="4b6f2-125">ICLRAssemblyIdentityManager — interfejs</span><span class="sxs-lookup"><span data-stu-id="4b6f2-125">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [<span data-ttu-id="4b6f2-126">ICLRAssemblyReferenceList — interfejs</span><span class="sxs-lookup"><span data-stu-id="4b6f2-126">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="4b6f2-127">IHostAssemblyManager — interfejs</span><span class="sxs-lookup"><span data-stu-id="4b6f2-127">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
 [<span data-ttu-id="4b6f2-128">IHostAssemblyStore — interfejs</span><span class="sxs-lookup"><span data-stu-id="4b6f2-128">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
