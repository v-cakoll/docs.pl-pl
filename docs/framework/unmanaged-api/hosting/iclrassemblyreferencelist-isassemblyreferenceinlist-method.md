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
ms.openlocfilehash: 0632a7f5feee87c386d9488a6c989413af68a47f
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615894"
---
# <a name="iclrassemblyreferencelistisassemblyreferenceinlist-method"></a><span data-ttu-id="cd237-102">ICLRAssemblyReferenceList::IsAssemblyReferenceInList — Metoda</span><span class="sxs-lookup"><span data-stu-id="cd237-102">ICLRAssemblyReferenceList::IsAssemblyReferenceInList Method</span></span>
<span data-ttu-id="cd237-103">Pobiera wartość wskazującą, czy dostarczony wskaźnik odwołuje się do zestawu na liście.</span><span class="sxs-lookup"><span data-stu-id="cd237-103">Gets a value that indicates whether the supplied pointer refers to an assembly in the list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd237-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="cd237-104">Syntax</span></span>  
  
```cpp  
HRESULT IsAssemblyReferenceInList (  
    [in] IUnknown *pName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cd237-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cd237-105">Parameters</span></span>  
 `pName`  
 <span data-ttu-id="cd237-106">podczas Wskaźnik interfejsu do zestawu, który ma zostać wyszukany.</span><span class="sxs-lookup"><span data-stu-id="cd237-106">[in] An interface pointer to the assembly for which to search.</span></span> <span data-ttu-id="cd237-107">Prawidłowe wartości to typu `IAssemblyName` lub `IReferenceIdentity` .</span><span class="sxs-lookup"><span data-stu-id="cd237-107">Valid values are of type `IAssemblyName` or `IReferenceIdentity`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cd237-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="cd237-108">Return Value</span></span>  
  
|<span data-ttu-id="cd237-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="cd237-109">HRESULT</span></span>|<span data-ttu-id="cd237-110">Opis</span><span class="sxs-lookup"><span data-stu-id="cd237-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="cd237-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="cd237-111">S_OK</span></span>|<span data-ttu-id="cd237-112">Ciąg zostanie wyświetlony na liście.</span><span class="sxs-lookup"><span data-stu-id="cd237-112">The string appears in the list.</span></span>|  
|<span data-ttu-id="cd237-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="cd237-113">S_FALSE</span></span>|<span data-ttu-id="cd237-114">Ciąg nie pojawia się na liście.</span><span class="sxs-lookup"><span data-stu-id="cd237-114">The string does not appear in the list.</span></span>|  
|<span data-ttu-id="cd237-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="cd237-115">E_FAIL</span></span>|<span data-ttu-id="cd237-116">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="cd237-116">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="cd237-117">Po powrocie metody E_FAIL, środowisko uruchomieniowe języka wspólnego nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="cd237-117">After a method returns E_FAIL, the common language runtime is no longer usable within the process.</span></span> <span data-ttu-id="cd237-118">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="cd237-118">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cd237-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cd237-119">Requirements</span></span>  
 <span data-ttu-id="cd237-120">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cd237-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cd237-121">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="cd237-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cd237-122">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="cd237-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cd237-123">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cd237-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd237-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cd237-124">See also</span></span>

- [<span data-ttu-id="cd237-125">ICLRAssemblyIdentityManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="cd237-125">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="cd237-126">ICLRAssemblyReferenceList — Interfejs</span><span class="sxs-lookup"><span data-stu-id="cd237-126">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="cd237-127">IHostAssemblyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="cd237-127">IHostAssemblyManager Interface</span></span>](ihostassemblymanager-interface.md)
- [<span data-ttu-id="cd237-128">IHostAssemblyStore, interfejs</span><span class="sxs-lookup"><span data-stu-id="cd237-128">IHostAssemblyStore Interface</span></span>](ihostassemblystore-interface.md)
