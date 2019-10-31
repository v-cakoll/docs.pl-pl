---
title: ICorRuntimeHost::CloseEnum — Metoda
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.CloseEnum
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::CloseEnum
helpviewer_keywords:
- CloseEnum method, ICorRuntimeHost interface [.NET Framework hosting]
- ICorRuntimeHost::CloseEnum method [.NET Framework hosting]
ms.assetid: f7ce7e8c-0a3e-4587-a180-063e2b85940e
topic_type:
- apiref
ms.openlocfilehash: e2eddfab68e5c9e2ebffe2c96c9348f3cd799c7f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127750"
---
# <a name="icorruntimehostcloseenum-method"></a><span data-ttu-id="711b4-102">ICorRuntimeHost::CloseEnum — Metoda</span><span class="sxs-lookup"><span data-stu-id="711b4-102">ICorRuntimeHost::CloseEnum Method</span></span>
<span data-ttu-id="711b4-103">Resetuje moduł wyliczający domeny z powrotem do początku listy domen.</span><span class="sxs-lookup"><span data-stu-id="711b4-103">Resets a domain enumerator back to the beginning of the domain list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="711b4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="711b4-104">Syntax</span></span>  
  
```cpp  
HRESULT CloseEnum (  
    [in] HCORENUM hEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="711b4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="711b4-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="711b4-106">podczas Moduł wyliczający do zresetowania.</span><span class="sxs-lookup"><span data-stu-id="711b4-106">[in] The enumerator to reset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="711b4-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="711b4-107">Return Value</span></span>  
  
|<span data-ttu-id="711b4-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="711b4-108">HRESULT</span></span>|<span data-ttu-id="711b4-109">Opis</span><span class="sxs-lookup"><span data-stu-id="711b4-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="711b4-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="711b4-110">S_OK</span></span>|<span data-ttu-id="711b4-111">Operacja zakończyła się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="711b4-111">The operation was successful.</span></span>|  
|<span data-ttu-id="711b4-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="711b4-112">S_FALSE</span></span>|<span data-ttu-id="711b4-113">Nie można ukończyć operacji.</span><span class="sxs-lookup"><span data-stu-id="711b4-113">The operation failed to complete.</span></span>|  
|<span data-ttu-id="711b4-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="711b4-114">E_FAIL</span></span>|<span data-ttu-id="711b4-115">Wystąpił nieznany, Katastrofalny błąd.</span><span class="sxs-lookup"><span data-stu-id="711b4-115">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="711b4-116">Jeśli metoda zwraca wartość E_FAIL, środowisko uruchomieniowe języka wspólnego (CLR) nie jest już możliwe do użycia w procesie.</span><span class="sxs-lookup"><span data-stu-id="711b4-116">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="711b4-117">Kolejne wywołania interfejsów API hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="711b4-117">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="711b4-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="711b4-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="711b4-119">Środowisko CLR nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="711b4-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="711b4-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="711b4-120">Requirements</span></span>  
 <span data-ttu-id="711b4-121">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="711b4-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="711b4-122">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="711b4-122">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="711b4-123">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="711b4-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="711b4-124">**.NET Framework wersje:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="711b4-124">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="711b4-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="711b4-125">See also</span></span>

- [<span data-ttu-id="711b4-126">CorBindToRuntimeEx, funkcja</span><span class="sxs-lookup"><span data-stu-id="711b4-126">CorBindToRuntimeEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)
- [<span data-ttu-id="711b4-127">ICorRuntimeHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="711b4-127">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
