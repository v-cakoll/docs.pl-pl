---
title: ICorRuntimeHost::UnloadDomain — Metoda
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.UnloadDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::UnloadDomain
helpviewer_keywords:
- ICorRuntimeHost::UnloadDomain method [.NET Framework hosting]
- UnloadDomain method [.NET Framework hosting]
ms.assetid: dd9e9204-a80d-44f3-8192-779224b35056
topic_type:
- apiref
ms.openlocfilehash: 558b6e4c6ac369e33be3d45b7241e8b11db8bfae
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/21/2020
ms.locfileid: "83760397"
---
# <a name="icorruntimehostunloaddomain-method"></a><span data-ttu-id="e97d4-102">ICorRuntimeHost::UnloadDomain — Metoda</span><span class="sxs-lookup"><span data-stu-id="e97d4-102">ICorRuntimeHost::UnloadDomain Method</span></span>
<span data-ttu-id="e97d4-103">Zwalnia określoną domenę aplikacji z bieżącego procesu.</span><span class="sxs-lookup"><span data-stu-id="e97d4-103">Unloads the specified application domain from the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e97d4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e97d4-104">Syntax</span></span>  
  
```cpp  
HRESULT UnloadDomain (  
    [in] IUnknown* pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e97d4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e97d4-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="e97d4-106">podczas Wskaźnik typu <xref:System._AppDomain?displayProperty=nameWithType> reprezentujący domenę, która ma zostać zwolniona.</span><span class="sxs-lookup"><span data-stu-id="e97d4-106">[in] A pointer of type <xref:System._AppDomain?displayProperty=nameWithType> that represents the domain to be unloaded.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e97d4-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="e97d4-107">Return Value</span></span>  
  
|<span data-ttu-id="e97d4-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e97d4-108">HRESULT</span></span>|<span data-ttu-id="e97d4-109">Opis</span><span class="sxs-lookup"><span data-stu-id="e97d4-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e97d4-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="e97d4-110">S_OK</span></span>|<span data-ttu-id="e97d4-111">Operacja zakończyła się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="e97d4-111">The operation was successful.</span></span>|  
|<span data-ttu-id="e97d4-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="e97d4-112">S_FALSE</span></span>|<span data-ttu-id="e97d4-113">Nie można ukończyć operacji.</span><span class="sxs-lookup"><span data-stu-id="e97d4-113">The operation failed to complete.</span></span>|  
|<span data-ttu-id="e97d4-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e97d4-114">E_FAIL</span></span>|<span data-ttu-id="e97d4-115">Wystąpił nieznany, Katastrofalny błąd.</span><span class="sxs-lookup"><span data-stu-id="e97d4-115">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="e97d4-116">Jeśli metoda zwraca E_FAIL, środowisko uruchomieniowe języka wspólnego (CLR) nie jest już możliwe do użycia w procesie.</span><span class="sxs-lookup"><span data-stu-id="e97d4-116">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="e97d4-117">Kolejne wywołania interfejsów API hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="e97d4-117">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="e97d4-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e97d4-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e97d4-119">Środowisko CLR nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="e97d4-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e97d4-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e97d4-120">Requirements</span></span>  
 <span data-ttu-id="e97d4-121">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e97d4-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e97d4-122">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="e97d4-122">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e97d4-123">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="e97d4-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e97d4-124">**Wersja .NET Framework:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="e97d4-124">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e97d4-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e97d4-125">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [<span data-ttu-id="e97d4-126">ICorRuntimeHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="e97d4-126">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
