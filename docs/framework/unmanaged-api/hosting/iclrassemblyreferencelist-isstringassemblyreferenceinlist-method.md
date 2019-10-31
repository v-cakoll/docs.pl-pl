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
ms.openlocfilehash: 4dc91723f009d46f9c57b1c99aa66ba7a1b127e4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126637"
---
# <a name="iclrassemblyreferencelistisstringassemblyreferenceinlist-method"></a><span data-ttu-id="fbfcd-102">ICLRAssemblyReferenceList::IsStringAssemblyReferenceInList — Metoda</span><span class="sxs-lookup"><span data-stu-id="fbfcd-102">ICLRAssemblyReferenceList::IsStringAssemblyReferenceInList Method</span></span>
<span data-ttu-id="fbfcd-103">Pobiera wartość wskazującą, czy podana nazwa jest zgodna z nazwą zestawu znajdującego się na liście.</span><span class="sxs-lookup"><span data-stu-id="fbfcd-103">Gets a value that indicates whether the supplied name matches the name of an assembly in the list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fbfcd-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fbfcd-104">Syntax</span></span>  
  
```cpp  
HRESULT IsStringAssemblyReferenceInList (  
    [in] LPCWSTR pwzAssemblyName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fbfcd-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fbfcd-105">Parameters</span></span>  
 `pwzAssemblyName`  
 <span data-ttu-id="fbfcd-106">podczas Nazwa zestawu, który ma zostać wyszukany.</span><span class="sxs-lookup"><span data-stu-id="fbfcd-106">[in] The name of the assembly for which to search.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fbfcd-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="fbfcd-107">Return Value</span></span>  
  
|<span data-ttu-id="fbfcd-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fbfcd-108">HRESULT</span></span>|<span data-ttu-id="fbfcd-109">Opis</span><span class="sxs-lookup"><span data-stu-id="fbfcd-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fbfcd-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="fbfcd-110">S_OK</span></span>|<span data-ttu-id="fbfcd-111">Ciąg zostanie wyświetlony na liście.</span><span class="sxs-lookup"><span data-stu-id="fbfcd-111">The string appears in the list.</span></span>|  
|<span data-ttu-id="fbfcd-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="fbfcd-112">S_FALSE</span></span>|<span data-ttu-id="fbfcd-113">Ciąg nie pojawia się na liście.</span><span class="sxs-lookup"><span data-stu-id="fbfcd-113">The string does not appear in the list.</span></span>|  
|<span data-ttu-id="fbfcd-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="fbfcd-114">E_FAIL</span></span>|<span data-ttu-id="fbfcd-115">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="fbfcd-115">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="fbfcd-116">Gdy metoda zwraca wartość E_FAIL, środowisko uruchomieniowe języka wspólnego nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="fbfcd-116">After a method returns E_FAIL, the common language runtime is no longer usable within the process.</span></span> <span data-ttu-id="fbfcd-117">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="fbfcd-117">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="fbfcd-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fbfcd-118">Requirements</span></span>  
 <span data-ttu-id="fbfcd-119">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fbfcd-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fbfcd-120">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="fbfcd-120">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fbfcd-121">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="fbfcd-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fbfcd-122">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fbfcd-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbfcd-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fbfcd-123">See also</span></span>

- [<span data-ttu-id="fbfcd-124">ICLRAssemblyIdentityManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="fbfcd-124">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="fbfcd-125">ICLRAssemblyReferenceList, interfejs</span><span class="sxs-lookup"><span data-stu-id="fbfcd-125">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="fbfcd-126">IHostAssemblyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="fbfcd-126">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
- [<span data-ttu-id="fbfcd-127">IHostAssemblyStore, interfejs</span><span class="sxs-lookup"><span data-stu-id="fbfcd-127">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
