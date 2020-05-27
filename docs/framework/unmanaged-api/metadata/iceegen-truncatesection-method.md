---
title: ICeeGen::TruncateSection — Metoda
ms.date: 03/30/2017
api_name:
- ICeeGen.TruncateSection
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::TruncateSection
helpviewer_keywords:
- TruncateSection method [.NET Framework metadata]
- ICeeGen::TruncateSection method [.NET Framework metadata]
ms.assetid: 0451d752-1e5c-4c9a-8bad-6cd35b7ba3df
topic_type:
- apiref
ms.openlocfilehash: 387f5f01f2d2589c0b34e50b69398e1feb0e77e0
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008251"
---
# <a name="iceegentruncatesection-method"></a><span data-ttu-id="62f3b-102">ICeeGen::TruncateSection — Metoda</span><span class="sxs-lookup"><span data-stu-id="62f3b-102">ICeeGen::TruncateSection Method</span></span>
<span data-ttu-id="62f3b-103">Obcina określoną sekcję kodu o określoną długość.</span><span class="sxs-lookup"><span data-stu-id="62f3b-103">Truncates the specified code section by the specified length.</span></span>  
  
 <span data-ttu-id="62f3b-104">Ta metoda jest przestarzała i nie powinna być używana.</span><span class="sxs-lookup"><span data-stu-id="62f3b-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62f3b-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="62f3b-105">Syntax</span></span>  
  
```cpp  
HRESULT TruncateSection (  
    [in]  HCEESECTION     section,  
    [in]  ULONG           len  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="62f3b-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="62f3b-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="62f3b-107">podczas Sekcja do obcięcia.</span><span class="sxs-lookup"><span data-stu-id="62f3b-107">[in] The section to truncate.</span></span>  
  
 `len`  
 <span data-ttu-id="62f3b-108">podczas Długość w bajtach, przez którą ma zostać obcięta sekcja.</span><span class="sxs-lookup"><span data-stu-id="62f3b-108">[in] The length, in bytes, by which to truncate the section.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="62f3b-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="62f3b-109">Remarks</span></span>  
 <span data-ttu-id="62f3b-110">Wywołanie `TruncateSection` tylko wtedy, gdy istnieją specjalne wymagania sekcji, które nie są obsługiwane przez inne metody.</span><span class="sxs-lookup"><span data-stu-id="62f3b-110">Call `TruncateSection` only if you have special section requirements that are not handled by other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="62f3b-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="62f3b-111">Requirements</span></span>  
 <span data-ttu-id="62f3b-112">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="62f3b-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="62f3b-113">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="62f3b-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="62f3b-114">**Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="62f3b-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="62f3b-115">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="62f3b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62f3b-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="62f3b-116">See also</span></span>

- [<span data-ttu-id="62f3b-117">ICeeGen — Interfejs</span><span class="sxs-lookup"><span data-stu-id="62f3b-117">ICeeGen Interface</span></span>](iceegen-interface.md)
