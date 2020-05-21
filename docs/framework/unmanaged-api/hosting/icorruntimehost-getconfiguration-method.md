---
title: ICorRuntimeHost::GetConfiguration — Metoda
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.GetConfiguration
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::GetConfiguration
helpviewer_keywords:
- ICorRuntimeHost::GetConfiguration method [.NET Framework hosting]
- GetConfiguration method [.NET Framework hosting]
ms.assetid: c431617a-b055-44a0-8730-48b7a86d9610
topic_type:
- apiref
ms.openlocfilehash: 88abdbc62c8b27f48c5629afb99ab6e30ee67e00
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762269"
---
# <a name="icorruntimehostgetconfiguration-method"></a><span data-ttu-id="897db-102">ICorRuntimeHost::GetConfiguration — Metoda</span><span class="sxs-lookup"><span data-stu-id="897db-102">ICorRuntimeHost::GetConfiguration Method</span></span>
<span data-ttu-id="897db-103">Pobiera obiekt, który umożliwia hostowi określenie konfiguracji wywołania zwrotnego środowiska uruchomieniowego języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="897db-103">Gets an object that allows the host to specify the callback configuration of the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="897db-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="897db-104">Syntax</span></span>  
  
```cpp  
HRESULT GetConfiguration(  
    [out] ICorConfiguration** pConfiguration  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="897db-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="897db-105">Parameters</span></span>  
 `pConfiguration`  
 <span data-ttu-id="897db-106">określoną Wskaźnik do adresu obiektu [ICorConfiguration](icorconfiguration-interface.md) , który może służyć do konfigurowania środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="897db-106">[out] A pointer to the address of an [ICorConfiguration](icorconfiguration-interface.md) object that can be used to configure the CLR.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="897db-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="897db-107">Remarks</span></span>  
 <span data-ttu-id="897db-108">Środowisko CLR musi być skonfigurowane przed jego inicjalizacją; w przeciwnym razie `GetConfiguration` Metoda zwraca wynik HRESULT wskazujący błąd.</span><span class="sxs-lookup"><span data-stu-id="897db-108">The CLR must be configured prior to its initialization; otherwise, the `GetConfiguration` method returns an HRESULT indicating an error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="897db-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="897db-109">Requirements</span></span>  
 <span data-ttu-id="897db-110">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="897db-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="897db-111">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="897db-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="897db-112">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="897db-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="897db-113">**.NET Framework wersje:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="897db-113">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="897db-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="897db-114">See also</span></span>

- [<span data-ttu-id="897db-115">ICorRuntimeHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="897db-115">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
