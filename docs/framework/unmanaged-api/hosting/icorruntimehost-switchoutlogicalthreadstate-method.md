---
title: ICorRuntimeHost::SwitchOutLogicalThreadState — Metoda
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.SwitchOutLogicalThreadState
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::SwitchOutLogicalThreadState
helpviewer_keywords:
- ICorRuntimeHost::SwitchOutLogicalThreadState method [.NET Framework hosting]
- SwitchOutLogicalThreadState method [.NET Framework hosting]
ms.assetid: e1968f0b-2675-4dc2-8507-46164e1df154
topic_type:
- apiref
ms.openlocfilehash: f32381dc40a744157e46780e59b83efd63e58dcb
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762646"
---
# <a name="icorruntimehostswitchoutlogicalthreadstate-method"></a><span data-ttu-id="fb583-102">ICorRuntimeHost::SwitchOutLogicalThreadState — Metoda</span><span class="sxs-lookup"><span data-stu-id="fb583-102">ICorRuntimeHost::SwitchOutLogicalThreadState Method</span></span>
<span data-ttu-id="fb583-103">Ta metoda obsługuje infrastrukturę .NET Framework i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="fb583-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb583-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fb583-104">Syntax</span></span>  
  
```cpp  
HRESULT SwitchOutLogicalThreadState(  
    [out] DWORD **pFiberCookie  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fb583-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fb583-105">Parameters</span></span>  
 `pFiberCookie`  
 <span data-ttu-id="fb583-106">określoną Plik cookie wskazujący, że włókna są przełączane.</span><span class="sxs-lookup"><span data-stu-id="fb583-106">[out] Cookie that indicates the fiber being switched out.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fb583-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fb583-107">Requirements</span></span>  
 <span data-ttu-id="fb583-108">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fb583-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fb583-109">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="fb583-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fb583-110">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="fb583-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fb583-111">**Wersja .NET Framework:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="fb583-111">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb583-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fb583-112">See also</span></span>

- [<span data-ttu-id="fb583-113">ICorRuntimeHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="fb583-113">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
