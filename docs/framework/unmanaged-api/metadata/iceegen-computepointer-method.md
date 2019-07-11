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
ms.openlocfilehash: 5741ba1b4564a703ff57b45c728bb9efac0bb35a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782011"
---
# <a name="iceegencomputepointer-method"></a><span data-ttu-id="6c297-102">ICeeGen::ComputePointer — Metoda</span><span class="sxs-lookup"><span data-stu-id="6c297-102">ICeeGen::ComputePointer Method</span></span>
<span data-ttu-id="6c297-103">Określa bufor dla sekcji określonego kodu.</span><span class="sxs-lookup"><span data-stu-id="6c297-103">Determines the buffer for the specified code section.</span></span>  
  
 <span data-ttu-id="6c297-104">Ta metoda jest przestarzała i nie powinna być używana.</span><span class="sxs-lookup"><span data-stu-id="6c297-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c297-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="6c297-105">Syntax</span></span>  
  
```cpp  
HRESULT ComputePointer (  
    [in]  HCEESECTION  section,  
    [in]  ULONG        RVA,   
    [out] UCHAR        **lpBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6c297-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="6c297-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="6c297-107">[in] Sekcję kodu, dla której ma zostać zwrócone do buforu.</span><span class="sxs-lookup"><span data-stu-id="6c297-107">[in] The code section for which to return a buffer.</span></span>  
  
 `RVA`  
 <span data-ttu-id="6c297-108">[in] Wirtualny adres względny metody, do których chcesz uzyskać wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="6c297-108">[in] The relative virtual address of the method for which to get a pointer.</span></span>  
  
 `lpBuffer`  
 <span data-ttu-id="6c297-109">[out] Wskaźnik do buforu zwrócone.</span><span class="sxs-lookup"><span data-stu-id="6c297-109">[out] A pointer to the returned buffer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c297-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6c297-110">Requirements</span></span>  
 <span data-ttu-id="6c297-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6c297-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6c297-112">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="6c297-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6c297-113">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6c297-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6c297-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6c297-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c297-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6c297-115">See also</span></span>

- [<span data-ttu-id="6c297-116">ICeeGen, interfejs</span><span class="sxs-lookup"><span data-stu-id="6c297-116">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
