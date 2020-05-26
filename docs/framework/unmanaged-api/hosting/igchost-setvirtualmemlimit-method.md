---
title: IGCHost::SetVirtualMemLimit — Metoda
ms.date: 03/30/2017
api_name:
- IGCHost.SetVirtualMemLimit
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- SetVirtualMemLimit
helpviewer_keywords:
- IGCHost::SetVirtualMemLimit method [.NET Framework hosting]
- SetVirtualMemLimit method [.NET Framework hosting]
ms.assetid: c7e7c2d0-e58c-4650-b40c-47b2be2cda45
topic_type:
- apiref
ms.openlocfilehash: 93ed63b4abacce1d8943434965aacf67190631b6
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2020
ms.locfileid: "83805189"
---
# <a name="igchostsetvirtualmemlimit-method"></a><span data-ttu-id="79835-102">IGCHost::SetVirtualMemLimit — Metoda</span><span class="sxs-lookup"><span data-stu-id="79835-102">IGCHost::SetVirtualMemLimit Method</span></span>
<span data-ttu-id="79835-103">Ustawia maksymalny rozmiar pamięci wirtualnej środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="79835-103">Sets the maximum size of the runtime's virtual memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79835-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="79835-104">Syntax</span></span>  
  
```cpp  
HRESULT SetVirtualMemLimit (  
    [in] SIZE_T sztMaxVirtualMemMB  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="79835-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="79835-105">Parameters</span></span>  
 `sztMaxVirtualMemMB`  
 <span data-ttu-id="79835-106">podczas Maksymalny rozmiar pamięci wirtualnej środowiska uruchomieniowego (w megabajtach).</span><span class="sxs-lookup"><span data-stu-id="79835-106">[in] The maximum size, in megabytes, of the runtime's virtual memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="79835-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="79835-107">Remarks</span></span>  
 <span data-ttu-id="79835-108">Maksymalny rozmiar pamięci wirtualnej środowiska uruchomieniowego można zmienić dynamicznie.</span><span class="sxs-lookup"><span data-stu-id="79835-108">The maximum size of the runtime's virtual memory can be changed dynamically.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="79835-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="79835-109">Requirements</span></span>  
 <span data-ttu-id="79835-110">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="79835-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="79835-111">**Nagłówek:** GCHost. idl, GCHost. h</span><span class="sxs-lookup"><span data-stu-id="79835-111">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="79835-112">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="79835-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="79835-113">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="79835-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79835-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="79835-114">See also</span></span>

- [<span data-ttu-id="79835-115">IGCHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="79835-115">IGCHost Interface</span></span>](igchost-interface.md)
