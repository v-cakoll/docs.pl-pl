---
title: ICeeGen::ComputePointer — Metoda
ms.date: 03/30/2017
api_name:
- ICeeGen.ComputePointer
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::ComputePointer
helpviewer_keywords:
- ICeeGen::ComputePointer method [.NET Framework metadata]
- ComputePointer method [.NET Framework metadata]
ms.assetid: b6b95c04-0f2c-4fcc-a8bc-3b1dcbdba731
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 79ef272e0c8afa0cd1942416c3a5eb9b825c2e6f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59145148"
---
# <a name="iceegencomputepointer-method"></a><span data-ttu-id="97417-102">ICeeGen::ComputePointer — Metoda</span><span class="sxs-lookup"><span data-stu-id="97417-102">ICeeGen::ComputePointer Method</span></span>
<span data-ttu-id="97417-103">Określa bufor dla sekcji określonego kodu.</span><span class="sxs-lookup"><span data-stu-id="97417-103">Determines the buffer for the specified code section.</span></span>  
  
 <span data-ttu-id="97417-104">Ta metoda jest przestarzała i nie powinna być używana.</span><span class="sxs-lookup"><span data-stu-id="97417-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97417-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="97417-105">Syntax</span></span>  
  
```  
HRESULT ComputePointer (  
    [in]  HCEESECTION  section,  
    [in]  ULONG        RVA,   
    [out] UCHAR        **lpBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="97417-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="97417-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="97417-107">[in] Sekcję kodu, dla której ma zostać zwrócone do buforu.</span><span class="sxs-lookup"><span data-stu-id="97417-107">[in] The code section for which to return a buffer.</span></span>  
  
 `RVA`  
 <span data-ttu-id="97417-108">[in] Wirtualny adres względny metody, do których chcesz uzyskać wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="97417-108">[in] The relative virtual address of the method for which to get a pointer.</span></span>  
  
 `lpBuffer`  
 <span data-ttu-id="97417-109">[out] Wskaźnik do buforu zwrócone.</span><span class="sxs-lookup"><span data-stu-id="97417-109">[out] A pointer to the returned buffer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="97417-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="97417-110">Requirements</span></span>  
 <span data-ttu-id="97417-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="97417-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="97417-112">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="97417-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="97417-113">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="97417-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="97417-114">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="97417-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="97417-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="97417-115">See also</span></span>

- [<span data-ttu-id="97417-116">ICeeGen — Interfejs</span><span class="sxs-lookup"><span data-stu-id="97417-116">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
