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
ms.openlocfilehash: 01be6c30e16e4abdd6002fc8207b33a9c76a2eef
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448745"
---
# <a name="iceegencomputepointer-method"></a><span data-ttu-id="b8b6d-102">ICeeGen::ComputePointer — Metoda</span><span class="sxs-lookup"><span data-stu-id="b8b6d-102">ICeeGen::ComputePointer Method</span></span>
<span data-ttu-id="b8b6d-103">Determines the buffer for the specified code section.</span><span class="sxs-lookup"><span data-stu-id="b8b6d-103">Determines the buffer for the specified code section.</span></span>  
  
 <span data-ttu-id="b8b6d-104">This method is obsolete and should not be used.</span><span class="sxs-lookup"><span data-stu-id="b8b6d-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8b6d-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="b8b6d-105">Syntax</span></span>  
  
```cpp  
HRESULT ComputePointer (  
    [in]  HCEESECTION  section,  
    [in]  ULONG        RVA,   
    [out] UCHAR        **lpBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b8b6d-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="b8b6d-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="b8b6d-107">[in] The code section for which to return a buffer.</span><span class="sxs-lookup"><span data-stu-id="b8b6d-107">[in] The code section for which to return a buffer.</span></span>  
  
 `RVA`  
 <span data-ttu-id="b8b6d-108">[in] The relative virtual address of the method for which to get a pointer.</span><span class="sxs-lookup"><span data-stu-id="b8b6d-108">[in] The relative virtual address of the method for which to get a pointer.</span></span>  
  
 `lpBuffer`  
 <span data-ttu-id="b8b6d-109">[out] A pointer to the returned buffer.</span><span class="sxs-lookup"><span data-stu-id="b8b6d-109">[out] A pointer to the returned buffer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b8b6d-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b8b6d-110">Requirements</span></span>  
 <span data-ttu-id="b8b6d-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b8b6d-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b8b6d-112">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b8b6d-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b8b6d-113">**Library:** Used as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b8b6d-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b8b6d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b8b6d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8b6d-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b8b6d-115">See also</span></span>

- [<span data-ttu-id="b8b6d-116">ICeeGen, interfejs</span><span class="sxs-lookup"><span data-stu-id="b8b6d-116">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
