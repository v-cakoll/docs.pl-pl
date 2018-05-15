---
title: ICLRAssemblyIdentityManager::GetCLRAssemblyReferenceList — Metoda
ms.date: 03/30/2017
api_name:
- ICLRAssemblyIdentityManager.GetCLRAssemblyReferenceList
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyIdentityManager::GetCLRAssemblyReferenceList
helpviewer_keywords:
- GetClrAssemblyReferenceList method [.NET Framework hosting]
- ICLRAssemblyIdentityManager::GetCLRAssemblyReferenceList method [.NET Framework hosting]
ms.assetid: cb5ffae5-287b-4a87-9ca8-7ce3ae0601b7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 49962e632ced9aac376791ead672e6910117ee10
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="iclrassemblyidentitymanagergetclrassemblyreferencelist-method"></a><span data-ttu-id="7d3c7-102">ICLRAssemblyIdentityManager::GetCLRAssemblyReferenceList — Metoda</span><span class="sxs-lookup"><span data-stu-id="7d3c7-102">ICLRAssemblyIdentityManager::GetCLRAssemblyReferenceList Method</span></span>
<span data-ttu-id="7d3c7-103">Pobiera wskaźnika interfejsu do [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) wystąpienia z podanej listy tożsamości zestawu częściowej.</span><span class="sxs-lookup"><span data-stu-id="7d3c7-103">Gets an interface pointer to an [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) instance from the supplied list of partial assembly identities.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d3c7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7d3c7-104">Syntax</span></span>  
  
```  
HRESULT  GetCLRAssemblyReferenceList (  
    [in] LPCWSTR *ppwzAssemblyReferences,  
    [in] DWORD    dwNumOfReferences,  
    [out] ICLRAssemblyReferenceList **ppReferenceList  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7d3c7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7d3c7-105">Parameters</span></span>  
 `ppwzAssemblyReferences`  
 <span data-ttu-id="7d3c7-106">[in] Tablica ciągów zerem w formie "Nazwa właściwości = wartość..." określające listę tożsamości częściowego zestawu.</span><span class="sxs-lookup"><span data-stu-id="7d3c7-106">[in] An array of null-terminated strings in the form "name, property=value..." that specify a list of partial assembly identities.</span></span>  
  
 `dwNumOfReferences`  
 <span data-ttu-id="7d3c7-107">[in] Liczba elementów w `ppwzAssemblyReferences`.</span><span class="sxs-lookup"><span data-stu-id="7d3c7-107">[in] The number of items in `ppwzAssemblyReferences`.</span></span>  
  
 `ppReferenceList`  
 <span data-ttu-id="7d3c7-108">[out] Wskaźnik interfejsu do `ICLRAssemblyReferenceList` obiekt zawierający dane tożsamości zestawu do listy zestawów określone w `ppwzAssemblyReferences`.</span><span class="sxs-lookup"><span data-stu-id="7d3c7-108">[out] An interface pointer to an `ICLRAssemblyReferenceList` object that contains the assembly identity data for the list of assemblies specified in `ppwzAssemblyReferences`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7d3c7-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="7d3c7-109">Return Value</span></span>  
  
|<span data-ttu-id="7d3c7-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7d3c7-110">HRESULT</span></span>|<span data-ttu-id="7d3c7-111">Opis</span><span class="sxs-lookup"><span data-stu-id="7d3c7-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7d3c7-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="7d3c7-112">S_OK</span></span>|<span data-ttu-id="7d3c7-113">Metoda zwróciła pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="7d3c7-113">The method returned successfully.</span></span>|  
|<span data-ttu-id="7d3c7-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="7d3c7-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7d3c7-115">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="7d3c7-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="7d3c7-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="7d3c7-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="7d3c7-117">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="7d3c7-117">The call timed out.</span></span>|  
|<span data-ttu-id="7d3c7-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="7d3c7-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="7d3c7-119">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="7d3c7-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="7d3c7-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="7d3c7-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="7d3c7-121">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="7d3c7-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="7d3c7-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7d3c7-122">E_FAIL</span></span>|<span data-ttu-id="7d3c7-123">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="7d3c7-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="7d3c7-124">Jeśli metoda zwraca E_FAIL, CLR nie będzie już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="7d3c7-124">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="7d3c7-125">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="7d3c7-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7d3c7-126">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7d3c7-126">Requirements</span></span>  
 <span data-ttu-id="7d3c7-127">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7d3c7-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7d3c7-128">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7d3c7-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7d3c7-129">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7d3c7-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7d3c7-130">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7d3c7-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d3c7-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7d3c7-131">See Also</span></span>  
 [<span data-ttu-id="7d3c7-132">ICLRAssemblyIdentityManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="7d3c7-132">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [<span data-ttu-id="7d3c7-133">ICLRAssemblyReferenceList, interfejs</span><span class="sxs-lookup"><span data-stu-id="7d3c7-133">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
