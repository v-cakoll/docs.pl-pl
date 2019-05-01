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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61992631"
---
# <a name="iceegencomputepointer-method"></a><span data-ttu-id="bbdad-102">ICeeGen::ComputePointer — Metoda</span><span class="sxs-lookup"><span data-stu-id="bbdad-102">ICeeGen::ComputePointer Method</span></span>
<span data-ttu-id="bbdad-103">Określa bufor dla sekcji określonego kodu.</span><span class="sxs-lookup"><span data-stu-id="bbdad-103">Determines the buffer for the specified code section.</span></span>  
  
 <span data-ttu-id="bbdad-104">Ta metoda jest przestarzała i nie powinna być używana.</span><span class="sxs-lookup"><span data-stu-id="bbdad-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bbdad-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="bbdad-105">Syntax</span></span>  
  
```  
HRESULT ComputePointer (  
    [in]  HCEESECTION  section,  
    [in]  ULONG        RVA,   
    [out] UCHAR        **lpBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bbdad-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="bbdad-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="bbdad-107">[in] Sekcję kodu, dla której ma zostać zwrócone do buforu.</span><span class="sxs-lookup"><span data-stu-id="bbdad-107">[in] The code section for which to return a buffer.</span></span>  
  
 `RVA`  
 <span data-ttu-id="bbdad-108">[in] Wirtualny adres względny metody, do których chcesz uzyskać wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="bbdad-108">[in] The relative virtual address of the method for which to get a pointer.</span></span>  
  
 `lpBuffer`  
 <span data-ttu-id="bbdad-109">[out] Wskaźnik do buforu zwrócone.</span><span class="sxs-lookup"><span data-stu-id="bbdad-109">[out] A pointer to the returned buffer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bbdad-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bbdad-110">Requirements</span></span>  
 <span data-ttu-id="bbdad-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bbdad-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bbdad-112">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="bbdad-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bbdad-113">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="bbdad-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="bbdad-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bbdad-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbdad-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bbdad-115">See also</span></span>

- [<span data-ttu-id="bbdad-116">ICeeGen, interfejs</span><span class="sxs-lookup"><span data-stu-id="bbdad-116">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
