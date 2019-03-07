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
ms.openlocfilehash: 5fb63d4fe1e736ca1ff0c729d8d83cfe092eaaf5
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57465533"
---
# <a name="iceegencomputepointer-method"></a><span data-ttu-id="c2244-102">ICeeGen::ComputePointer — Metoda</span><span class="sxs-lookup"><span data-stu-id="c2244-102">ICeeGen::ComputePointer Method</span></span>
<span data-ttu-id="c2244-103">Określa bufor dla sekcji określonego kodu.</span><span class="sxs-lookup"><span data-stu-id="c2244-103">Determines the buffer for the specified code section.</span></span>  
  
 <span data-ttu-id="c2244-104">Ta metoda jest przestarzała i nie powinna być używana.</span><span class="sxs-lookup"><span data-stu-id="c2244-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2244-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="c2244-105">Syntax</span></span>  
  
```  
HRESULT ComputePointer (  
    [in]  HCEESECTION  section,  
    [in]  ULONG        RVA,   
    [out] UCHAR        **lpBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c2244-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="c2244-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="c2244-107">[in] Sekcję kodu, dla której ma zostać zwrócone do buforu.</span><span class="sxs-lookup"><span data-stu-id="c2244-107">[in] The code section for which to return a buffer.</span></span>  
  
 `RVA`  
 <span data-ttu-id="c2244-108">[in] Wirtualny adres względny metody, do których chcesz uzyskać wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="c2244-108">[in] The relative virtual address of the method for which to get a pointer.</span></span>  
  
 `lpBuffer`  
 <span data-ttu-id="c2244-109">[out] Wskaźnik do buforu zwrócone.</span><span class="sxs-lookup"><span data-stu-id="c2244-109">[out] A pointer to the returned buffer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c2244-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c2244-110">Requirements</span></span>  
 <span data-ttu-id="c2244-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c2244-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c2244-112">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="c2244-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c2244-113">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c2244-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c2244-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c2244-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2244-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c2244-115">See also</span></span>
- [<span data-ttu-id="c2244-116">ICeeGen, interfejs</span><span class="sxs-lookup"><span data-stu-id="c2244-116">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
