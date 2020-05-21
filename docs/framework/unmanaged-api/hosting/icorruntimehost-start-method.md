---
title: ICorRuntimeHost::Start — Metoda
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.Start
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::Start
helpviewer_keywords:
- Start method, ICorRuntimeHost interface [.NET Framework hosting]
- ICorRuntimeHost::Start method [.NET Framework hosting]
ms.assetid: c66f3ac5-6489-484a-9bed-c31b711cee01
topic_type:
- apiref
ms.openlocfilehash: ccad76e1c8a49222d4f527f8b7b18d4e40ff8cae
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/21/2020
ms.locfileid: "83760410"
---
# <a name="icorruntimehoststart-method"></a><span data-ttu-id="385e0-102">ICorRuntimeHost::Start — Metoda</span><span class="sxs-lookup"><span data-stu-id="385e0-102">ICorRuntimeHost::Start Method</span></span>
<span data-ttu-id="385e0-103">Uruchamia środowisko uruchomieniowe języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="385e0-103">Starts the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="385e0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="385e0-104">Syntax</span></span>  
  
```cpp  
HRESULT Start ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="385e0-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="385e0-105">Return Value</span></span>  
  
|<span data-ttu-id="385e0-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="385e0-106">HRESULT</span></span>|<span data-ttu-id="385e0-107">Opis</span><span class="sxs-lookup"><span data-stu-id="385e0-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="385e0-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="385e0-108">S_OK</span></span>|<span data-ttu-id="385e0-109">Operacja zakończyła się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="385e0-109">The operation was successful.</span></span>|  
|<span data-ttu-id="385e0-110">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="385e0-110">S_FALSE</span></span>|<span data-ttu-id="385e0-111">Nie można ukończyć operacji.</span><span class="sxs-lookup"><span data-stu-id="385e0-111">The operation failed to complete.</span></span>|  
|<span data-ttu-id="385e0-112">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="385e0-112">E_FAIL</span></span>|<span data-ttu-id="385e0-113">Wystąpił nieznany, Katastrofalny błąd.</span><span class="sxs-lookup"><span data-stu-id="385e0-113">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="385e0-114">Jeśli metoda zwraca E_FAIL, środowisko CLR nie będzie już możliwe do użycia w procesie.</span><span class="sxs-lookup"><span data-stu-id="385e0-114">If a method returns E_FAIL, the CLR is no longer usable in the process.</span></span> <span data-ttu-id="385e0-115">Kolejne wywołania interfejsów API hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="385e0-115">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="385e0-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="385e0-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="385e0-117">Środowisko CLR nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="385e0-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="385e0-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="385e0-118">Remarks</span></span>  
 <span data-ttu-id="385e0-119">Zazwyczaj nie jest konieczne wywoływanie `Start` metody, ponieważ środowisko CLR jest uruchamiane automatycznie przy pierwszym żądaniu uruchomienia kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="385e0-119">It is typically not necessary to call the `Start` method, because the CLR starts automatically upon the first request to run managed code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="385e0-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="385e0-120">Requirements</span></span>  
 <span data-ttu-id="385e0-121">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="385e0-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="385e0-122">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="385e0-122">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="385e0-123">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="385e0-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="385e0-124">**.NET Framework wersje:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="385e0-124">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="385e0-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="385e0-125">See also</span></span>

- [<span data-ttu-id="385e0-126">ICorRuntimeHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="385e0-126">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
