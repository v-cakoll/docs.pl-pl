---
title: "ICeeGen::GetSectionCreate — Metoda"
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
- ICeeGen.GetSectionCreate
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetSectionCreate
helpviewer_keywords:
- ICeeGen::GetSectionCreate method [.NET Framework metadata]
- GetSectionCreate method [.NET Framework metadata]
ms.assetid: 154b2460-59ce-4874-a9f2-1b3353486ac5
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a069f65d3059bfa427ea20623ff9a2ac4049fd39
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="iceegengetsectioncreate-method"></a><span data-ttu-id="9d644-102">ICeeGen::GetSectionCreate — Metoda</span><span class="sxs-lookup"><span data-stu-id="9d644-102">ICeeGen::GetSectionCreate Method</span></span>
<span data-ttu-id="9d644-103">Generuje i pobiera sekcji kodu przy użyciu określonej nazwy i wartości flag.</span><span class="sxs-lookup"><span data-stu-id="9d644-103">Generates and gets a code section using the specified name and flag values.</span></span>  
  
 <span data-ttu-id="9d644-104">Ta metoda jest przestarzała i nie powinna być używana.</span><span class="sxs-lookup"><span data-stu-id="9d644-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d644-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="9d644-105">Syntax</span></span>  
  
```  
HRESULT GetSectionCreate (  
    [in]  const char     *name,  
    [in]  DWORD          flags,  
    [out] HCEESECTION    *section  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9d644-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="9d644-106">Parameters</span></span>  
 `name`  
 <span data-ttu-id="9d644-107">[in] Wskaźnik do ciąg określający nazwę sekcji do utworzenia.</span><span class="sxs-lookup"><span data-stu-id="9d644-107">[in] A pointer to a string that specifies the name of the section to be created.</span></span>  
  
 `flags`  
 <span data-ttu-id="9d644-108">[in] Flagi, które określają opcje.</span><span class="sxs-lookup"><span data-stu-id="9d644-108">[in] Flags that specify options.</span></span>  
  
 `section`  
 <span data-ttu-id="9d644-109">[out] Wskaźnik do nowo utworzonego kodu sekcji.</span><span class="sxs-lookup"><span data-stu-id="9d644-109">[out] A pointer to the newly created code section.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9d644-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9d644-110">Remarks</span></span>  
 <span data-ttu-id="9d644-111">Wywołanie `GetSectionCreate` tylko wtedy, gdy sekcja specjalne wymagania, które nie są obsługiwane za pomocą innych metod.</span><span class="sxs-lookup"><span data-stu-id="9d644-111">Call `GetSectionCreate` only if you have special section requirements that are not handled by other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d644-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9d644-112">Requirements</span></span>  
 <span data-ttu-id="9d644-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9d644-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d644-114">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="9d644-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9d644-115">**Biblioteka:** używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9d644-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9d644-116">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d644-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d644-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9d644-117">See Also</span></span>  
 [<span data-ttu-id="9d644-118">ICeeGen, interfejs</span><span class="sxs-lookup"><span data-stu-id="9d644-118">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
