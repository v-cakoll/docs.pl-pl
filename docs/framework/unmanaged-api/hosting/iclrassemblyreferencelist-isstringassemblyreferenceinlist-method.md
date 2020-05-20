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
ms.openlocfilehash: 91f174cab4986882df795eb531baedfc0dd43962
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615868"
---
# <a name="iclrassemblyreferencelistisstringassemblyreferenceinlist-method"></a><span data-ttu-id="7e04b-102">ICLRAssemblyReferenceList::IsStringAssemblyReferenceInList — Metoda</span><span class="sxs-lookup"><span data-stu-id="7e04b-102">ICLRAssemblyReferenceList::IsStringAssemblyReferenceInList Method</span></span>
<span data-ttu-id="7e04b-103">Pobiera wartość wskazującą, czy podana nazwa jest zgodna z nazwą zestawu znajdującego się na liście.</span><span class="sxs-lookup"><span data-stu-id="7e04b-103">Gets a value that indicates whether the supplied name matches the name of an assembly in the list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e04b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7e04b-104">Syntax</span></span>  
  
```cpp  
HRESULT IsStringAssemblyReferenceInList (  
    [in] LPCWSTR pwzAssemblyName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7e04b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7e04b-105">Parameters</span></span>  
 `pwzAssemblyName`  
 <span data-ttu-id="7e04b-106">podczas Nazwa zestawu, który ma zostać wyszukany.</span><span class="sxs-lookup"><span data-stu-id="7e04b-106">[in] The name of the assembly for which to search.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7e04b-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="7e04b-107">Return Value</span></span>  
  
|<span data-ttu-id="7e04b-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7e04b-108">HRESULT</span></span>|<span data-ttu-id="7e04b-109">Opis</span><span class="sxs-lookup"><span data-stu-id="7e04b-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7e04b-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="7e04b-110">S_OK</span></span>|<span data-ttu-id="7e04b-111">Ciąg zostanie wyświetlony na liście.</span><span class="sxs-lookup"><span data-stu-id="7e04b-111">The string appears in the list.</span></span>|  
|<span data-ttu-id="7e04b-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="7e04b-112">S_FALSE</span></span>|<span data-ttu-id="7e04b-113">Ciąg nie pojawia się na liście.</span><span class="sxs-lookup"><span data-stu-id="7e04b-113">The string does not appear in the list.</span></span>|  
|<span data-ttu-id="7e04b-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7e04b-114">E_FAIL</span></span>|<span data-ttu-id="7e04b-115">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="7e04b-115">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="7e04b-116">Po powrocie metody E_FAIL, środowisko uruchomieniowe języka wspólnego nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="7e04b-116">After a method returns E_FAIL, the common language runtime is no longer usable within the process.</span></span> <span data-ttu-id="7e04b-117">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="7e04b-117">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7e04b-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7e04b-118">Requirements</span></span>  
 <span data-ttu-id="7e04b-119">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7e04b-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7e04b-120">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="7e04b-120">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7e04b-121">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="7e04b-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7e04b-122">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7e04b-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e04b-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7e04b-123">See also</span></span>

- [<span data-ttu-id="7e04b-124">ICLRAssemblyIdentityManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="7e04b-124">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="7e04b-125">ICLRAssemblyReferenceList — Interfejs</span><span class="sxs-lookup"><span data-stu-id="7e04b-125">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="7e04b-126">IHostAssemblyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="7e04b-126">IHostAssemblyManager Interface</span></span>](ihostassemblymanager-interface.md)
- [<span data-ttu-id="7e04b-127">IHostAssemblyStore, interfejs</span><span class="sxs-lookup"><span data-stu-id="7e04b-127">IHostAssemblyStore Interface</span></span>](ihostassemblystore-interface.md)
