---
title: ICeeGen::GetSectionCreate — Metoda
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 03de69d51b520ae2d8be6c7f450f0541c52c36a2
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57472437"
---
# <a name="iceegengetsectioncreate-method"></a><span data-ttu-id="124c9-102">ICeeGen::GetSectionCreate — Metoda</span><span class="sxs-lookup"><span data-stu-id="124c9-102">ICeeGen::GetSectionCreate Method</span></span>
<span data-ttu-id="124c9-103">Generuje i pobiera sekcję kodu przy użyciu określonej nazwy i wartości flag.</span><span class="sxs-lookup"><span data-stu-id="124c9-103">Generates and gets a code section using the specified name and flag values.</span></span>  
  
 <span data-ttu-id="124c9-104">Ta metoda jest przestarzała i nie powinna być używana.</span><span class="sxs-lookup"><span data-stu-id="124c9-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="124c9-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="124c9-105">Syntax</span></span>  
  
```  
HRESULT GetSectionCreate (  
    [in]  const char     *name,  
    [in]  DWORD          flags,  
    [out] HCEESECTION    *section  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="124c9-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="124c9-106">Parameters</span></span>  
 `name`  
 <span data-ttu-id="124c9-107">[in] Wskaźnik na ciąg określający nazwę sekcji, który ma zostać utworzony.</span><span class="sxs-lookup"><span data-stu-id="124c9-107">[in] A pointer to a string that specifies the name of the section to be created.</span></span>  
  
 `flags`  
 <span data-ttu-id="124c9-108">[in] Flagi, które określają opcje.</span><span class="sxs-lookup"><span data-stu-id="124c9-108">[in] Flags that specify options.</span></span>  
  
 `section`  
 <span data-ttu-id="124c9-109">[out] Wskaźnik do nowo utworzonego kodu sekcji.</span><span class="sxs-lookup"><span data-stu-id="124c9-109">[out] A pointer to the newly created code section.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="124c9-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="124c9-110">Remarks</span></span>  
 <span data-ttu-id="124c9-111">Wywołaj `GetSectionCreate` tylko wtedy, gdy masz sekcją wymagań, które nie są obsługiwane przy użyciu innych metod.</span><span class="sxs-lookup"><span data-stu-id="124c9-111">Call `GetSectionCreate` only if you have special section requirements that are not handled by other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="124c9-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="124c9-112">Requirements</span></span>  
 <span data-ttu-id="124c9-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="124c9-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="124c9-114">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="124c9-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="124c9-115">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="124c9-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="124c9-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="124c9-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="124c9-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="124c9-117">See also</span></span>
- [<span data-ttu-id="124c9-118">ICeeGen, interfejs</span><span class="sxs-lookup"><span data-stu-id="124c9-118">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
