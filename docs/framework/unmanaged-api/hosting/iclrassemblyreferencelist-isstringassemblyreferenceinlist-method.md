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
ms.openlocfilehash: ff0e51327e0e66c2a282ebf46e6036f81d3d568b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="iclrassemblyreferencelistisstringassemblyreferenceinlist-method"></a><span data-ttu-id="f5353-102">ICLRAssemblyReferenceList::IsStringAssemblyReferenceInList — Metoda</span><span class="sxs-lookup"><span data-stu-id="f5353-102">ICLRAssemblyReferenceList::IsStringAssemblyReferenceInList Method</span></span>
<span data-ttu-id="f5353-103">Pobiera wartość wskazującą, czy podana nazwa odpowiada nazwie zestawu na liście.</span><span class="sxs-lookup"><span data-stu-id="f5353-103">Gets a value that indicates whether the supplied name matches the name of an assembly in the list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5353-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f5353-104">Syntax</span></span>  
  
```  
HRESULT IsStringAssemblyReferenceInList (  
    [in] LPCWSTR pwzAssemblyName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f5353-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f5353-105">Parameters</span></span>  
 `pwzAssemblyName`  
 <span data-ttu-id="f5353-106">[in] Nazwa zestawu, który chcesz wyszukać.</span><span class="sxs-lookup"><span data-stu-id="f5353-106">[in] The name of the assembly for which to search.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f5353-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="f5353-107">Return Value</span></span>  
  
|<span data-ttu-id="f5353-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f5353-108">HRESULT</span></span>|<span data-ttu-id="f5353-109">Opis</span><span class="sxs-lookup"><span data-stu-id="f5353-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f5353-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="f5353-110">S_OK</span></span>|<span data-ttu-id="f5353-111">Ten ciąg jest wyświetlana na liście.</span><span class="sxs-lookup"><span data-stu-id="f5353-111">The string appears in the list.</span></span>|  
|<span data-ttu-id="f5353-112">WARTOŚCI S_FALSE</span><span class="sxs-lookup"><span data-stu-id="f5353-112">S_FALSE</span></span>|<span data-ttu-id="f5353-113">Ciąg nie ma na liście.</span><span class="sxs-lookup"><span data-stu-id="f5353-113">The string does not appear in the list.</span></span>|  
|<span data-ttu-id="f5353-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f5353-114">E_FAIL</span></span>|<span data-ttu-id="f5353-115">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="f5353-115">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f5353-116">Po powrocie E_FAIL metody środowisko uruchomieniowe języka wspólnego nie będzie już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="f5353-116">After a method returns E_FAIL, the common language runtime is no longer usable within the process.</span></span> <span data-ttu-id="f5353-117">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="f5353-117">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f5353-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f5353-118">Requirements</span></span>  
 <span data-ttu-id="f5353-119">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f5353-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5353-120">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f5353-120">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f5353-121">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f5353-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f5353-122">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5353-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5353-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f5353-123">See Also</span></span>  
 [<span data-ttu-id="f5353-124">ICLRAssemblyIdentityManager — interfejs</span><span class="sxs-lookup"><span data-stu-id="f5353-124">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [<span data-ttu-id="f5353-125">ICLRAssemblyReferenceList — interfejs</span><span class="sxs-lookup"><span data-stu-id="f5353-125">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="f5353-126">IHostAssemblyManager — interfejs</span><span class="sxs-lookup"><span data-stu-id="f5353-126">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
 [<span data-ttu-id="f5353-127">IHostAssemblyStore — interfejs</span><span class="sxs-lookup"><span data-stu-id="f5353-127">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
