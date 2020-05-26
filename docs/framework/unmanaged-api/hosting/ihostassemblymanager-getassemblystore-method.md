---
title: IHostAssemblyManager::GetAssemblyStore — Metoda
ms.date: 03/30/2017
api_name:
- IHostAssemblyManager.GetAssemblyStore
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAssemblyManager::GetAssemblyStore
helpviewer_keywords:
- IHostAssemblyManager::GetAssemblyStore method [.NET Framework hosting]
- GetAssemblyStore method [.NET Framework hosting]
ms.assetid: d0f74593-9bb1-4a11-8096-e29734b20698
topic_type:
- apiref
ms.openlocfilehash: 587861529c340fad9fd817b904e4d3651b236e8d
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2020
ms.locfileid: "83805071"
---
# <a name="ihostassemblymanagergetassemblystore-method"></a><span data-ttu-id="9e587-102">IHostAssemblyManager::GetAssemblyStore — Metoda</span><span class="sxs-lookup"><span data-stu-id="9e587-102">IHostAssemblyManager::GetAssemblyStore Method</span></span>
<span data-ttu-id="9e587-103">Pobiera wskaźnik interfejsu do [IHostAssemblyStore](ihostassemblystore-interface.md) , który reprezentuje listę zestawów załadowanych przez hosta.</span><span class="sxs-lookup"><span data-stu-id="9e587-103">Gets an interface pointer to an [IHostAssemblyStore](ihostassemblystore-interface.md) that represents the list of assemblies loaded by the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e587-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9e587-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyStore (  
    [out] IHostAssemblyStore **ppAssemblyStore  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9e587-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9e587-105">Parameters</span></span>  
 `ppAssemblyStore`  
 <span data-ttu-id="9e587-106">określoną Wskaźnik funkcji do `IHostAssemblyStore` wystąpienia lub wartość null, Jeśli host nie implementuje `IHostAssemblyStore` .</span><span class="sxs-lookup"><span data-stu-id="9e587-106">[out] A function pointer to an `IHostAssemblyStore` instance, or null, if the host does not implement `IHostAssemblyStore`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9e587-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="9e587-107">Return Value</span></span>  
  
|<span data-ttu-id="9e587-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9e587-108">HRESULT</span></span>|<span data-ttu-id="9e587-109">Opis</span><span class="sxs-lookup"><span data-stu-id="9e587-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9e587-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="9e587-110">S_OK</span></span>|<span data-ttu-id="9e587-111">`GetAssemblyStore`pomyślnie zwrócono.</span><span class="sxs-lookup"><span data-stu-id="9e587-111">`GetAssemblyStore` returned successfully.</span></span>|  
|<span data-ttu-id="9e587-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9e587-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9e587-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="9e587-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="9e587-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="9e587-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="9e587-115">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="9e587-115">The call timed out.</span></span>|  
|<span data-ttu-id="9e587-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="9e587-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="9e587-117">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="9e587-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="9e587-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="9e587-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="9e587-119">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="9e587-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="9e587-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9e587-120">E_FAIL</span></span>|<span data-ttu-id="9e587-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="9e587-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="9e587-122">Gdy metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="9e587-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="9e587-123">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="9e587-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="9e587-124">E_NOINTERFACE</span><span class="sxs-lookup"><span data-stu-id="9e587-124">E_NOINTERFACE</span></span>|<span data-ttu-id="9e587-125">Host nie oferuje implementacji programu `IHostAssemblyStore` .</span><span class="sxs-lookup"><span data-stu-id="9e587-125">The host does not provide an implementation of `IHostAssemblyStore`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9e587-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9e587-126">Remarks</span></span>  
 <span data-ttu-id="9e587-127">`IHostAssemblyStore`dostarcza metody, które umożliwiają hostowi powiązanie z zestawami i modułami niezależnie od środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="9e587-127">`IHostAssemblyStore` provides methods that allow a host to bind to assemblies and modules independently of the CLR.</span></span> <span data-ttu-id="9e587-128">Hosty zwykle zapewniają magazyny zestawów pozwalające ładować zestawy z formatów innych niż system plików.</span><span class="sxs-lookup"><span data-stu-id="9e587-128">Hosts typically provide assembly stores to allow assemblies to be loaded from formats other than the file system.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9e587-129">Jeśli host nie jest zaimplementowany `IHostAssemblyStore` , `GetAssemblyStore` powinien zwrócić wartość HRESULT o wartości E_NOINTERFACE i powinien mieć ustawioną wartość `ppAssemblyStore` null.</span><span class="sxs-lookup"><span data-stu-id="9e587-129">If the host does not implement `IHostAssemblyStore`, `GetAssemblyStore` should return an HRESULT value of E_NOINTERFACE, and should set `ppAssemblyStore` to null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9e587-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9e587-130">Requirements</span></span>  
 <span data-ttu-id="9e587-131">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9e587-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9e587-132">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="9e587-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9e587-133">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="9e587-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9e587-134">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9e587-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e587-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9e587-135">See also</span></span>

- [<span data-ttu-id="9e587-136">IHostAssemblyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="9e587-136">IHostAssemblyManager Interface</span></span>](ihostassemblymanager-interface.md)
- [<span data-ttu-id="9e587-137">IHostAssemblyStore, interfejs</span><span class="sxs-lookup"><span data-stu-id="9e587-137">IHostAssemblyStore Interface</span></span>](ihostassemblystore-interface.md)
