---
title: "ICeeGen::GetSectionBlock — Metoda"
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9e00d7ae1b110fc9f1e1d41d8c3ddb9427b3d44a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="iceegengetsectionblock-method"></a><span data-ttu-id="d4c4f-102">ICeeGen::GetSectionBlock — Metoda</span><span class="sxs-lookup"><span data-stu-id="d4c4f-102">ICeeGen::GetSectionBlock Method</span></span>
<span data-ttu-id="d4c4f-103">Pobiera blok sekcji ścieżki bazowej kodu.</span><span class="sxs-lookup"><span data-stu-id="d4c4f-103">Gets a section block of the code base.</span></span>  
  
 <span data-ttu-id="d4c4f-104">Ta metoda jest przestarzała i nie powinna być używana.</span><span class="sxs-lookup"><span data-stu-id="d4c4f-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4c4f-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="d4c4f-105">Syntax</span></span>  
  
```  
HRESULT GetSectionBlock (  
    [in]  HCEESECTION    section,     
    [in]  ULONG          len,  
    [in]  ULONG          align     = 1,  
    [out] void           **ppBytes = 0  
);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="d4c4f-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="d4c4f-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="d4c4f-107">[in] Sekcja, z którego można pobrać z bloku bazy kodu.</span><span class="sxs-lookup"><span data-stu-id="d4c4f-107">[in] The section from which to retrieve a block of the code base.</span></span>  
  
 `len`  
 <span data-ttu-id="d4c4f-108">[in] Długość bloku, które mają zostać pobrane.</span><span class="sxs-lookup"><span data-stu-id="d4c4f-108">[in] The length of the block to be retrieved.</span></span>  
  
 `align`  
 <span data-ttu-id="d4c4f-109">[in] Bajt względem początku sekcji, z którą ma zostać Wyrównaj do pierwszego bajtu bloku.</span><span class="sxs-lookup"><span data-stu-id="d4c4f-109">[in] The byte, relative to the beginning of the section, with which to align the first byte of the block.</span></span> <span data-ttu-id="d4c4f-110">Jest to pozycja blok w ramach sekcji.</span><span class="sxs-lookup"><span data-stu-id="d4c4f-110">This is the position of the block within the section.</span></span>  
  
 `ppBytes`  
 <span data-ttu-id="d4c4f-111">[out] Wskaźnik do lokalizacji, która odbiera adres pobrane bloku.</span><span class="sxs-lookup"><span data-stu-id="d4c4f-111">[out] A pointer to a location that receives the address of the retrieved block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d4c4f-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d4c4f-112">Remarks</span></span>  
 <span data-ttu-id="d4c4f-113">Wywołanie `GetSectionBlock` tylko wtedy, gdy sekcja specjalne wymagania, które nie są obsługiwane za pomocą innych metod.</span><span class="sxs-lookup"><span data-stu-id="d4c4f-113">Call `GetSectionBlock` only if you have special section requirements that are not handled by other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d4c4f-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d4c4f-114">Requirements</span></span>  
 <span data-ttu-id="d4c4f-115">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d4c4f-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d4c4f-116">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="d4c4f-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d4c4f-117">**Biblioteka:** używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d4c4f-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d4c4f-118">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d4c4f-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4c4f-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d4c4f-119">See Also</span></span>  
 [<span data-ttu-id="d4c4f-120">ICeeGen, interfejs</span><span class="sxs-lookup"><span data-stu-id="d4c4f-120">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
