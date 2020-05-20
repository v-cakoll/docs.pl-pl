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
ms.openlocfilehash: 7f09cb2264b21fdfbc892069f2c2f0a963b131f8
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615972"
---
# <a name="iclrassemblyidentitymanagergetclrassemblyreferencelist-method"></a><span data-ttu-id="ef438-102">ICLRAssemblyIdentityManager::GetCLRAssemblyReferenceList — Metoda</span><span class="sxs-lookup"><span data-stu-id="ef438-102">ICLRAssemblyIdentityManager::GetCLRAssemblyReferenceList Method</span></span>
<span data-ttu-id="ef438-103">Pobiera wskaźnik interfejsu do wystąpienia [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) z podanej listy tożsamości zestawów częściowych.</span><span class="sxs-lookup"><span data-stu-id="ef438-103">Gets an interface pointer to an [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) instance from the supplied list of partial assembly identities.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef438-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ef438-104">Syntax</span></span>  
  
```cpp  
HRESULT  GetCLRAssemblyReferenceList (  
    [in] LPCWSTR *ppwzAssemblyReferences,  
    [in] DWORD    dwNumOfReferences,  
    [out] ICLRAssemblyReferenceList **ppReferenceList  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ef438-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ef438-105">Parameters</span></span>  
 `ppwzAssemblyReferences`  
 <span data-ttu-id="ef438-106">podczas Tablica ciągów zakończonych znakiem null w postaci "name, Property = Value..." określające listę tożsamości zestawów częściowych.</span><span class="sxs-lookup"><span data-stu-id="ef438-106">[in] An array of null-terminated strings in the form "name, property=value..." that specify a list of partial assembly identities.</span></span>  
  
 `dwNumOfReferences`  
 <span data-ttu-id="ef438-107">podczas Liczba elementów w `ppwzAssemblyReferences` .</span><span class="sxs-lookup"><span data-stu-id="ef438-107">[in] The number of items in `ppwzAssemblyReferences`.</span></span>  
  
 `ppReferenceList`  
 <span data-ttu-id="ef438-108">określoną Wskaźnik interfejsu do `ICLRAssemblyReferenceList` obiektu, który zawiera dane tożsamości zestawu dla listy zestawów określonych w `ppwzAssemblyReferences` .</span><span class="sxs-lookup"><span data-stu-id="ef438-108">[out] An interface pointer to an `ICLRAssemblyReferenceList` object that contains the assembly identity data for the list of assemblies specified in `ppwzAssemblyReferences`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ef438-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="ef438-109">Return Value</span></span>  
  
|<span data-ttu-id="ef438-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ef438-110">HRESULT</span></span>|<span data-ttu-id="ef438-111">Opis</span><span class="sxs-lookup"><span data-stu-id="ef438-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ef438-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="ef438-112">S_OK</span></span>|<span data-ttu-id="ef438-113">Metoda została pomyślnie zwrócona.</span><span class="sxs-lookup"><span data-stu-id="ef438-113">The method returned successfully.</span></span>|  
|<span data-ttu-id="ef438-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ef438-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ef438-115">Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="ef438-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ef438-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ef438-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ef438-117">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="ef438-117">The call timed out.</span></span>|  
|<span data-ttu-id="ef438-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ef438-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ef438-119">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="ef438-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ef438-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ef438-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ef438-121">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="ef438-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ef438-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ef438-122">E_FAIL</span></span>|<span data-ttu-id="ef438-123">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="ef438-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ef438-124">Jeśli metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="ef438-124">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ef438-125">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="ef438-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ef438-126">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ef438-126">Requirements</span></span>  
 <span data-ttu-id="ef438-127">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ef438-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ef438-128">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="ef438-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ef438-129">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="ef438-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ef438-130">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ef438-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef438-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ef438-131">See also</span></span>

- [<span data-ttu-id="ef438-132">ICLRAssemblyIdentityManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="ef438-132">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="ef438-133">ICLRAssemblyReferenceList — Interfejs</span><span class="sxs-lookup"><span data-stu-id="ef438-133">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
