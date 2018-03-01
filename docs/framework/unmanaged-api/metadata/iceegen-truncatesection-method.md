---
title: "ICeeGen::TruncateSection — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICeeGen.TruncateSection
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::TruncateSection
helpviewer_keywords:
- TruncateSection method [.NET Framework metadata]
- ICeeGen::TruncateSection method [.NET Framework metadata]
ms.assetid: 0451d752-1e5c-4c9a-8bad-6cd35b7ba3df
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 8e7deaaab58f1ee51bd3675faec892db5228c787
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="iceegentruncatesection-method"></a><span data-ttu-id="a579d-102">ICeeGen::TruncateSection — Metoda</span><span class="sxs-lookup"><span data-stu-id="a579d-102">ICeeGen::TruncateSection Method</span></span>
<span data-ttu-id="a579d-103">Obcina sekcji określonego kodu przez określony czas.</span><span class="sxs-lookup"><span data-stu-id="a579d-103">Truncates the specified code section by the specified length.</span></span>  
  
 <span data-ttu-id="a579d-104">Ta metoda jest przestarzała i nie powinna być używana.</span><span class="sxs-lookup"><span data-stu-id="a579d-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a579d-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="a579d-105">Syntax</span></span>  
  
```  
HRESULT TruncateSection (  
    [in]  HCEESECTION     section,  
    [in]  ULONG           len  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a579d-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="a579d-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="a579d-107">[in] Sekcja do obcięcia.</span><span class="sxs-lookup"><span data-stu-id="a579d-107">[in] The section to truncate.</span></span>  
  
 `len`  
 <span data-ttu-id="a579d-108">[in] Długość w bajtach, według którego ma zostać obcięta sekcji.</span><span class="sxs-lookup"><span data-stu-id="a579d-108">[in] The length, in bytes, by which to truncate the section.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a579d-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a579d-109">Remarks</span></span>  
 <span data-ttu-id="a579d-110">Wywołanie `TruncateSection` tylko wtedy, gdy sekcja specjalne wymagania, które nie są obsługiwane za pomocą innych metod.</span><span class="sxs-lookup"><span data-stu-id="a579d-110">Call `TruncateSection` only if you have special section requirements that are not handled by other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a579d-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a579d-111">Requirements</span></span>  
 <span data-ttu-id="a579d-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a579d-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a579d-113">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a579d-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a579d-114">**Biblioteka:** używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a579d-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a579d-115">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a579d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a579d-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a579d-116">See Also</span></span>  
 [<span data-ttu-id="a579d-117">ICeeGen, interfejs</span><span class="sxs-lookup"><span data-stu-id="a579d-117">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
