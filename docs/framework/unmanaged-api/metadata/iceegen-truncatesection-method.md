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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 994f6668de3040cc9f2381356d6db06c18c9e984
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67745882"
---
# <a name="iceegentruncatesection-method"></a><span data-ttu-id="493e7-102">ICeeGen::TruncateSection — Metoda</span><span class="sxs-lookup"><span data-stu-id="493e7-102">ICeeGen::TruncateSection Method</span></span>
<span data-ttu-id="493e7-103">Obcina sekcję kodu określonego przez określony czas.</span><span class="sxs-lookup"><span data-stu-id="493e7-103">Truncates the specified code section by the specified length.</span></span>  
  
 <span data-ttu-id="493e7-104">Ta metoda jest przestarzała i nie powinna być używana.</span><span class="sxs-lookup"><span data-stu-id="493e7-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="493e7-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="493e7-105">Syntax</span></span>  
  
```cpp  
HRESULT TruncateSection (  
    [in]  HCEESECTION     section,  
    [in]  ULONG           len  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="493e7-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="493e7-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="493e7-107">[in] Sekcja obcięcia.</span><span class="sxs-lookup"><span data-stu-id="493e7-107">[in] The section to truncate.</span></span>  
  
 `len`  
 <span data-ttu-id="493e7-108">[in] Długość w bajtach, według którego ma zostać obcięta sekcji.</span><span class="sxs-lookup"><span data-stu-id="493e7-108">[in] The length, in bytes, by which to truncate the section.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="493e7-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="493e7-109">Remarks</span></span>  
 <span data-ttu-id="493e7-110">Wywołaj `TruncateSection` tylko wtedy, gdy masz sekcją wymagań, które nie są obsługiwane przy użyciu innych metod.</span><span class="sxs-lookup"><span data-stu-id="493e7-110">Call `TruncateSection` only if you have special section requirements that are not handled by other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="493e7-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="493e7-111">Requirements</span></span>  
 <span data-ttu-id="493e7-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="493e7-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="493e7-113">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="493e7-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="493e7-114">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="493e7-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="493e7-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="493e7-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="493e7-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="493e7-116">See also</span></span>

- [<span data-ttu-id="493e7-117">ICeeGen, interfejs</span><span class="sxs-lookup"><span data-stu-id="493e7-117">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
