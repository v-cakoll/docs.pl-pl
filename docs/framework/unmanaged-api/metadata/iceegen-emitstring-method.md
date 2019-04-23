---
title: ICeeGen::EmitString — Metoda
ms.date: 03/30/2017
api_name:
- ICeeGen.EmitString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::EmitString
helpviewer_keywords:
- EmitString method [.NET Framework metadata]
- ICeeGen::EmitString method [.NET Framework metadata]
ms.assetid: ad2710a7-edb8-4493-8619-3fce235e3334
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1eabf5631fcfe7a187d0e203d64c7a7f4f5a819a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59209960"
---
# <a name="iceegenemitstring-method"></a><span data-ttu-id="e850c-102">ICeeGen::EmitString — Metoda</span><span class="sxs-lookup"><span data-stu-id="e850c-102">ICeeGen::EmitString Method</span></span>
<span data-ttu-id="e850c-103">Emituje określonego ciągu w kodzie podstawowym.</span><span class="sxs-lookup"><span data-stu-id="e850c-103">Emits the specified string into the code base.</span></span>  
  
 <span data-ttu-id="e850c-104">Ta metoda jest przestarzała i nie powinna być używana.</span><span class="sxs-lookup"><span data-stu-id="e850c-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e850c-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="e850c-105">Syntax</span></span>  
  
```  
HRESULT EmitString (  
    [in]  LPWSTR    lpString,  
    [out] ULONG     *RVA  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e850c-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="e850c-106">Parameters</span></span>  
 `lpString`  
 <span data-ttu-id="e850c-107">[in] Ciąg do emitowania.</span><span class="sxs-lookup"><span data-stu-id="e850c-107">[in] The string to emit.</span></span>  
  
 `RVA`  
 <span data-ttu-id="e850c-108">[out] Wirtualny adres względny emitowany ciągu.</span><span class="sxs-lookup"><span data-stu-id="e850c-108">[out] The relative virtual address of the emitted string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e850c-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e850c-109">Requirements</span></span>  
 <span data-ttu-id="e850c-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e850c-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e850c-111">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="e850c-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e850c-112">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e850c-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e850c-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e850c-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e850c-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e850c-114">See also</span></span>

- [<span data-ttu-id="e850c-115">ICeeGen, interfejs</span><span class="sxs-lookup"><span data-stu-id="e850c-115">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
