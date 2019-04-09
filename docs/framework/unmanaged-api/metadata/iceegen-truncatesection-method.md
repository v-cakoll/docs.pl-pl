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
ms.openlocfilehash: 1036d6080bf17eea288724c7980ce53dfa2121f7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59116324"
---
# <a name="iceegentruncatesection-method"></a><span data-ttu-id="71de6-102">ICeeGen::TruncateSection — Metoda</span><span class="sxs-lookup"><span data-stu-id="71de6-102">ICeeGen::TruncateSection Method</span></span>
<span data-ttu-id="71de6-103">Obcina sekcję kodu określonego przez określony czas.</span><span class="sxs-lookup"><span data-stu-id="71de6-103">Truncates the specified code section by the specified length.</span></span>  
  
 <span data-ttu-id="71de6-104">Ta metoda jest przestarzała i nie powinna być używana.</span><span class="sxs-lookup"><span data-stu-id="71de6-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71de6-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="71de6-105">Syntax</span></span>  
  
```  
HRESULT TruncateSection (  
    [in]  HCEESECTION     section,  
    [in]  ULONG           len  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="71de6-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="71de6-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="71de6-107">[in] Sekcja obcięcia.</span><span class="sxs-lookup"><span data-stu-id="71de6-107">[in] The section to truncate.</span></span>  
  
 `len`  
 <span data-ttu-id="71de6-108">[in] Długość w bajtach, według którego ma zostać obcięta sekcji.</span><span class="sxs-lookup"><span data-stu-id="71de6-108">[in] The length, in bytes, by which to truncate the section.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="71de6-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="71de6-109">Remarks</span></span>  
 <span data-ttu-id="71de6-110">Wywołaj `TruncateSection` tylko wtedy, gdy masz sekcją wymagań, które nie są obsługiwane przy użyciu innych metod.</span><span class="sxs-lookup"><span data-stu-id="71de6-110">Call `TruncateSection` only if you have special section requirements that are not handled by other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="71de6-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="71de6-111">Requirements</span></span>  
 <span data-ttu-id="71de6-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="71de6-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="71de6-113">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="71de6-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="71de6-114">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="71de6-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="71de6-115">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="71de6-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="71de6-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="71de6-116">See also</span></span>

- [<span data-ttu-id="71de6-117">ICeeGen — Interfejs</span><span class="sxs-lookup"><span data-stu-id="71de6-117">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
