---
title: ICeeGen::GetSectionBlock — Metoda
ms.date: 03/30/2017
api_name:
- ICeeGen.GetSectionBlock
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetSectionBlock
helpviewer_keywords:
- GetSectionBlock method [.NET Framework metadata]
- ICeeGen::GetSectionBlock method [.NET Framework metadata]
ms.assetid: 05c78aaf-5bbd-497e-9ae2-55f4fae0c5fb
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e264a63dcea9c351289d1f63e1907f7c68779011
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57496758"
---
# <a name="iceegengetsectionblock-method"></a><span data-ttu-id="21cd1-102">ICeeGen::GetSectionBlock — Metoda</span><span class="sxs-lookup"><span data-stu-id="21cd1-102">ICeeGen::GetSectionBlock Method</span></span>
<span data-ttu-id="21cd1-103">Pobiera blok części bazy kodu.</span><span class="sxs-lookup"><span data-stu-id="21cd1-103">Gets a section block of the code base.</span></span>  
  
 <span data-ttu-id="21cd1-104">Ta metoda jest przestarzała i nie powinna być używana.</span><span class="sxs-lookup"><span data-stu-id="21cd1-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21cd1-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="21cd1-105">Syntax</span></span>  
  
```  
HRESULT GetSectionBlock (  
    [in]  HCEESECTION    section,     
    [in]  ULONG          len,  
    [in]  ULONG          align     = 1,  
    [out] void           **ppBytes = 0  
);   
```  
  
## <a name="parameters"></a><span data-ttu-id="21cd1-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="21cd1-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="21cd1-107">[in] Sekcja, z których mają być pobierane blok bazy kodu.</span><span class="sxs-lookup"><span data-stu-id="21cd1-107">[in] The section from which to retrieve a block of the code base.</span></span>  
  
 `len`  
 <span data-ttu-id="21cd1-108">[in] Długość bloku, które mają zostać pobrane.</span><span class="sxs-lookup"><span data-stu-id="21cd1-108">[in] The length of the block to be retrieved.</span></span>  
  
 `align`  
 <span data-ttu-id="21cd1-109">[in] Bajt względem początku sekcji, z którą ma zostać wyrównywanie pierwszego bajtu bloku.</span><span class="sxs-lookup"><span data-stu-id="21cd1-109">[in] The byte, relative to the beginning of the section, with which to align the first byte of the block.</span></span> <span data-ttu-id="21cd1-110">Jest to pozycja bloku, w ramach tej sekcji.</span><span class="sxs-lookup"><span data-stu-id="21cd1-110">This is the position of the block within the section.</span></span>  
  
 `ppBytes`  
 <span data-ttu-id="21cd1-111">[out] Wskaźnik do lokalizacji, która otrzymuje adres bloku pobrane.</span><span class="sxs-lookup"><span data-stu-id="21cd1-111">[out] A pointer to a location that receives the address of the retrieved block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="21cd1-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="21cd1-112">Remarks</span></span>  
 <span data-ttu-id="21cd1-113">Wywołaj `GetSectionBlock` tylko wtedy, gdy masz sekcją wymagań, które nie są obsługiwane przy użyciu innych metod.</span><span class="sxs-lookup"><span data-stu-id="21cd1-113">Call `GetSectionBlock` only if you have special section requirements that are not handled by other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="21cd1-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="21cd1-114">Requirements</span></span>  
 <span data-ttu-id="21cd1-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="21cd1-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="21cd1-116">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="21cd1-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="21cd1-117">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="21cd1-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="21cd1-118">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="21cd1-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21cd1-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="21cd1-119">See also</span></span>
- [<span data-ttu-id="21cd1-120">ICeeGen, interfejs</span><span class="sxs-lookup"><span data-stu-id="21cd1-120">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
