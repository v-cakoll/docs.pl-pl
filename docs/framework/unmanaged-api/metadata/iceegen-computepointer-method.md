---
title: "ICeeGen::ComputePointer — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICeeGen.ComputePointer
api_location: mscoree.dll
api_type: COM
f1_keywords: ICeeGen::ComputePointer
helpviewer_keywords:
- ICeeGen::ComputePointer method [.NET Framework metadata]
- ComputePointer method [.NET Framework metadata]
ms.assetid: b6b95c04-0f2c-4fcc-a8bc-3b1dcbdba731
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0b027615f7697b9ea103d44bea0ec44834fe3f04
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="iceegencomputepointer-method"></a><span data-ttu-id="113da-102">ICeeGen::ComputePointer — Metoda</span><span class="sxs-lookup"><span data-stu-id="113da-102">ICeeGen::ComputePointer Method</span></span>
<span data-ttu-id="113da-103">Określa bufor dla określonego kodu sekcji.</span><span class="sxs-lookup"><span data-stu-id="113da-103">Determines the buffer for the specified code section.</span></span>  
  
 <span data-ttu-id="113da-104">Ta metoda jest przestarzała i nie powinna być używana.</span><span class="sxs-lookup"><span data-stu-id="113da-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="113da-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="113da-105">Syntax</span></span>  
  
```  
HRESULT ComputePointer (  
    [in]  HCEESECTION  section,  
    [in]  ULONG        RVA,   
    [out] UCHAR        **lpBuffer  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="113da-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="113da-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="113da-107">[in] Sekcji kodu, dla którego ma zostać zwrócona w buforze.</span><span class="sxs-lookup"><span data-stu-id="113da-107">[in] The code section for which to return a buffer.</span></span>  
  
 `RVA`  
 <span data-ttu-id="113da-108">[in] Wirtualny adres względny metody, do których chcesz otrzymywać wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="113da-108">[in] The relative virtual address of the method for which to get a pointer.</span></span>  
  
 `lpBuffer`  
 <span data-ttu-id="113da-109">[out] Wskaźnik do buforu zwrócony.</span><span class="sxs-lookup"><span data-stu-id="113da-109">[out] A pointer to the returned buffer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="113da-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="113da-110">Requirements</span></span>  
 <span data-ttu-id="113da-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="113da-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="113da-112">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="113da-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="113da-113">**Biblioteka:** używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="113da-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="113da-114">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="113da-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="113da-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="113da-115">See Also</span></span>  
 [<span data-ttu-id="113da-116">ICeeGen, interfejs</span><span class="sxs-lookup"><span data-stu-id="113da-116">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
