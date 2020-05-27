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
ms.openlocfilehash: ed534890fc90d3b8543a1166c85903f10163f0a8
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008333"
---
# <a name="iceegengetsectionblock-method"></a><span data-ttu-id="63c52-102">ICeeGen::GetSectionBlock — Metoda</span><span class="sxs-lookup"><span data-stu-id="63c52-102">ICeeGen::GetSectionBlock Method</span></span>
<span data-ttu-id="63c52-103">Pobiera blok sekcji bazy kodu.</span><span class="sxs-lookup"><span data-stu-id="63c52-103">Gets a section block of the code base.</span></span>  
  
 <span data-ttu-id="63c52-104">Ta metoda jest przestarzała i nie powinna być używana.</span><span class="sxs-lookup"><span data-stu-id="63c52-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63c52-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="63c52-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSectionBlock (  
    [in]  HCEESECTION    section,
    [in]  ULONG          len,  
    [in]  ULONG          align     = 1,  
    [out] void           **ppBytes = 0  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="63c52-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="63c52-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="63c52-107">podczas Sekcja, z której ma zostać pobrany blok bazy kodu.</span><span class="sxs-lookup"><span data-stu-id="63c52-107">[in] The section from which to retrieve a block of the code base.</span></span>  
  
 `len`  
 <span data-ttu-id="63c52-108">podczas Długość bloku do pobrania.</span><span class="sxs-lookup"><span data-stu-id="63c52-108">[in] The length of the block to be retrieved.</span></span>  
  
 `align`  
 <span data-ttu-id="63c52-109">podczas Bajt względem początku sekcji, za pomocą którego ma zostać wyrównany pierwszy bajt bloku.</span><span class="sxs-lookup"><span data-stu-id="63c52-109">[in] The byte, relative to the beginning of the section, with which to align the first byte of the block.</span></span> <span data-ttu-id="63c52-110">To jest pozycja bloku w sekcji.</span><span class="sxs-lookup"><span data-stu-id="63c52-110">This is the position of the block within the section.</span></span>  
  
 `ppBytes`  
 <span data-ttu-id="63c52-111">określoną Wskaźnik do lokalizacji, która otrzymuje adres pobranego bloku.</span><span class="sxs-lookup"><span data-stu-id="63c52-111">[out] A pointer to a location that receives the address of the retrieved block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="63c52-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="63c52-112">Remarks</span></span>  
 <span data-ttu-id="63c52-113">Wywołanie `GetSectionBlock` tylko wtedy, gdy istnieją specjalne wymagania sekcji, które nie są obsługiwane przez inne metody.</span><span class="sxs-lookup"><span data-stu-id="63c52-113">Call `GetSectionBlock` only if you have special section requirements that are not handled by other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="63c52-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="63c52-114">Requirements</span></span>  
 <span data-ttu-id="63c52-115">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="63c52-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="63c52-116">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="63c52-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="63c52-117">**Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="63c52-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="63c52-118">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="63c52-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63c52-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="63c52-119">See also</span></span>

- [<span data-ttu-id="63c52-120">ICeeGen — Interfejs</span><span class="sxs-lookup"><span data-stu-id="63c52-120">ICeeGen Interface</span></span>](iceegen-interface.md)
