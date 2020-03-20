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
ms.openlocfilehash: a494b1aaa762549528e92ab93d18929ef73eb8da
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176087"
---
# <a name="iceegengetsectionblock-method"></a><span data-ttu-id="d145a-102">ICeeGen::GetSectionBlock — Metoda</span><span class="sxs-lookup"><span data-stu-id="d145a-102">ICeeGen::GetSectionBlock Method</span></span>
<span data-ttu-id="d145a-103">Pobiera blok sekcji bazy kodu.</span><span class="sxs-lookup"><span data-stu-id="d145a-103">Gets a section block of the code base.</span></span>  
  
 <span data-ttu-id="d145a-104">Ta metoda jest przestarzała i nie powinna być używana.</span><span class="sxs-lookup"><span data-stu-id="d145a-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d145a-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="d145a-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSectionBlock (  
    [in]  HCEESECTION    section,
    [in]  ULONG          len,  
    [in]  ULONG          align     = 1,  
    [out] void           **ppBytes = 0  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="d145a-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="d145a-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="d145a-107">[w] Sekcja, z której ma być pobierana blokada bazy kodu.</span><span class="sxs-lookup"><span data-stu-id="d145a-107">[in] The section from which to retrieve a block of the code base.</span></span>  
  
 `len`  
 <span data-ttu-id="d145a-108">[w] Długość bloku do pobrania.</span><span class="sxs-lookup"><span data-stu-id="d145a-108">[in] The length of the block to be retrieved.</span></span>  
  
 `align`  
 <span data-ttu-id="d145a-109">[w] Bajt względem początku sekcji, z którym należy wyrównać pierwszy bajt bloku.</span><span class="sxs-lookup"><span data-stu-id="d145a-109">[in] The byte, relative to the beginning of the section, with which to align the first byte of the block.</span></span> <span data-ttu-id="d145a-110">Jest to położenie bloku w sekcji.</span><span class="sxs-lookup"><span data-stu-id="d145a-110">This is the position of the block within the section.</span></span>  
  
 `ppBytes`  
 <span data-ttu-id="d145a-111">[na zewnątrz] Wskaźnik do lokalizacji, która odbiera adres pobranego bloku.</span><span class="sxs-lookup"><span data-stu-id="d145a-111">[out] A pointer to a location that receives the address of the retrieved block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d145a-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d145a-112">Remarks</span></span>  
 <span data-ttu-id="d145a-113">Wywołaj `GetSectionBlock` tylko wtedy, gdy masz specjalne wymagania sekcji, które nie są obsługiwane przez inne metody.</span><span class="sxs-lookup"><span data-stu-id="d145a-113">Call `GetSectionBlock` only if you have special section requirements that are not handled by other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d145a-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d145a-114">Requirements</span></span>  
 <span data-ttu-id="d145a-115">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d145a-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d145a-116">**Nagłówek:** Okręg wyborczy Cor.h</span><span class="sxs-lookup"><span data-stu-id="d145a-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d145a-117">**Biblioteka:** Używany jako zasób w pliku MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d145a-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d145a-118">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d145a-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d145a-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d145a-119">See also</span></span>

- [<span data-ttu-id="d145a-120">ICeeGen — Interfejs</span><span class="sxs-lookup"><span data-stu-id="d145a-120">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
