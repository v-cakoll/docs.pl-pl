---
title: "ICeeGen::GetSectionBlock — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICeeGen.GetSectionBlock
api_location: mscoree.dll
api_type: COM
f1_keywords: ICeeGen::GetSectionBlock
helpviewer_keywords:
- GetSectionBlock method [.NET Framework metadata]
- ICeeGen::GetSectionBlock method [.NET Framework metadata]
ms.assetid: 05c78aaf-5bbd-497e-9ae2-55f4fae0c5fb
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 4732eef9a47f9ea1e919bd9d855afbec18974454
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="iceegengetsectionblock-method"></a><span data-ttu-id="10b7b-102">ICeeGen::GetSectionBlock — Metoda</span><span class="sxs-lookup"><span data-stu-id="10b7b-102">ICeeGen::GetSectionBlock Method</span></span>
<span data-ttu-id="10b7b-103">Pobiera blok sekcji ścieżki bazowej kodu.</span><span class="sxs-lookup"><span data-stu-id="10b7b-103">Gets a section block of the code base.</span></span>  
  
 <span data-ttu-id="10b7b-104">Ta metoda jest przestarzała i nie powinna być używana.</span><span class="sxs-lookup"><span data-stu-id="10b7b-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10b7b-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="10b7b-105">Syntax</span></span>  
  
```  
HRESULT GetSectionBlock (  
    [in]  HCEESECTION    section,     
    [in]  ULONG          len,  
    [in]  ULONG          align     = 1,  
    [out] void           **ppBytes = 0  
);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="10b7b-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="10b7b-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="10b7b-107">[in] Sekcja, z którego można pobrać z bloku bazy kodu.</span><span class="sxs-lookup"><span data-stu-id="10b7b-107">[in] The section from which to retrieve a block of the code base.</span></span>  
  
 `len`  
 <span data-ttu-id="10b7b-108">[in] Długość bloku, które mają zostać pobrane.</span><span class="sxs-lookup"><span data-stu-id="10b7b-108">[in] The length of the block to be retrieved.</span></span>  
  
 `align`  
 <span data-ttu-id="10b7b-109">[in] Bajt względem początku sekcji, z którą ma zostać Wyrównaj do pierwszego bajtu bloku.</span><span class="sxs-lookup"><span data-stu-id="10b7b-109">[in] The byte, relative to the beginning of the section, with which to align the first byte of the block.</span></span> <span data-ttu-id="10b7b-110">Jest to pozycja blok w ramach sekcji.</span><span class="sxs-lookup"><span data-stu-id="10b7b-110">This is the position of the block within the section.</span></span>  
  
 `ppBytes`  
 <span data-ttu-id="10b7b-111">[out] Wskaźnik do lokalizacji, która odbiera adres pobrane bloku.</span><span class="sxs-lookup"><span data-stu-id="10b7b-111">[out] A pointer to a location that receives the address of the retrieved block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="10b7b-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="10b7b-112">Remarks</span></span>  
 <span data-ttu-id="10b7b-113">Wywołanie `GetSectionBlock` tylko wtedy, gdy sekcja specjalne wymagania, które nie są obsługiwane za pomocą innych metod.</span><span class="sxs-lookup"><span data-stu-id="10b7b-113">Call `GetSectionBlock` only if you have special section requirements that are not handled by other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="10b7b-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="10b7b-114">Requirements</span></span>  
 <span data-ttu-id="10b7b-115">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="10b7b-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="10b7b-116">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="10b7b-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="10b7b-117">**Biblioteka:** używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="10b7b-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="10b7b-118">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="10b7b-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10b7b-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="10b7b-119">See Also</span></span>  
 [<span data-ttu-id="10b7b-120">ICeeGen — interfejs</span><span class="sxs-lookup"><span data-stu-id="10b7b-120">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
