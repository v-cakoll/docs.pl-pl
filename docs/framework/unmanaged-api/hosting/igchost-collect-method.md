---
title: IGCHost::Collect — Metoda
ms.date: 03/30/2017
api_name:
- IGCHost.Collect
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- Collect
helpviewer_keywords:
- Collect method, IGCHost interface [.NET Framework hosting]
- IGCHost::Collect method [.NET Framework hosting]
ms.assetid: fc7d9448-3186-494d-9f0d-ea39717e9a82
topic_type:
- apiref
ms.openlocfilehash: ac73c462aa210927f0665cae161fd7f3e17a0cdb
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2020
ms.locfileid: "83805310"
---
# <a name="igchostcollect-method"></a><span data-ttu-id="7749a-102">IGCHost::Collect — Metoda</span><span class="sxs-lookup"><span data-stu-id="7749a-102">IGCHost::Collect Method</span></span>
<span data-ttu-id="7749a-103">Wymusza, aby kolekcja była wykonywana dla danej generacji, niezależnie od stanu bieżącej wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="7749a-103">Forces a collection to occur for the given generation, regardless of the state of the current garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7749a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7749a-104">Syntax</span></span>  
  
```cpp  
HRESULT Collect (  
    [in] LONG Generation  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7749a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7749a-105">Parameters</span></span>  
 `Generation`  
 <span data-ttu-id="7749a-106">podczas Generacja, na której ma zostać wykonane odzyskiwanie pamięci.</span><span class="sxs-lookup"><span data-stu-id="7749a-106">[in] The generation on which to perform the garbage collection.</span></span> <span data-ttu-id="7749a-107">Wartość-1 oznacza, że wszystkie generacji zostaną poddane wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="7749a-107">A value of -1 indicates that all generations will undergo a garbage collection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7749a-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7749a-108">Requirements</span></span>  
 <span data-ttu-id="7749a-109">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7749a-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7749a-110">**Nagłówek:** GCHost. idl, GCHost. h</span><span class="sxs-lookup"><span data-stu-id="7749a-110">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="7749a-111">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="7749a-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7749a-112">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7749a-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7749a-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7749a-113">See also</span></span>

- [<span data-ttu-id="7749a-114">IGCHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="7749a-114">IGCHost Interface</span></span>](igchost-interface.md)
