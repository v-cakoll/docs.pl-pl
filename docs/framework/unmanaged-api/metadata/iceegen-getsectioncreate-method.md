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
ms.openlocfilehash: 9768dfd43b6b60df1660c48cb6d6f498b049e256
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61905518"
---
# <a name="iceegengetsectioncreate-method"></a><span data-ttu-id="a2d8b-102">ICeeGen::GetSectionCreate — Metoda</span><span class="sxs-lookup"><span data-stu-id="a2d8b-102">ICeeGen::GetSectionCreate Method</span></span>
<span data-ttu-id="a2d8b-103">Generuje i pobiera sekcję kodu przy użyciu określonej nazwy i wartości flag.</span><span class="sxs-lookup"><span data-stu-id="a2d8b-103">Generates and gets a code section using the specified name and flag values.</span></span>  
  
 <span data-ttu-id="a2d8b-104">Ta metoda jest przestarzała i nie powinna być używana.</span><span class="sxs-lookup"><span data-stu-id="a2d8b-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2d8b-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="a2d8b-105">Syntax</span></span>  
  
```  
HRESULT GetSectionCreate (  
    [in]  const char     *name,  
    [in]  DWORD          flags,  
    [out] HCEESECTION    *section  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a2d8b-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="a2d8b-106">Parameters</span></span>  
 `name`  
 <span data-ttu-id="a2d8b-107">[in] Wskaźnik na ciąg określający nazwę sekcji, który ma zostać utworzony.</span><span class="sxs-lookup"><span data-stu-id="a2d8b-107">[in] A pointer to a string that specifies the name of the section to be created.</span></span>  
  
 `flags`  
 <span data-ttu-id="a2d8b-108">[in] Flagi, które określają opcje.</span><span class="sxs-lookup"><span data-stu-id="a2d8b-108">[in] Flags that specify options.</span></span>  
  
 `section`  
 <span data-ttu-id="a2d8b-109">[out] Wskaźnik do nowo utworzonego kodu sekcji.</span><span class="sxs-lookup"><span data-stu-id="a2d8b-109">[out] A pointer to the newly created code section.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a2d8b-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a2d8b-110">Remarks</span></span>  
 <span data-ttu-id="a2d8b-111">Wywołaj `GetSectionCreate` tylko wtedy, gdy masz sekcją wymagań, które nie są obsługiwane przy użyciu innych metod.</span><span class="sxs-lookup"><span data-stu-id="a2d8b-111">Call `GetSectionCreate` only if you have special section requirements that are not handled by other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a2d8b-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a2d8b-112">Requirements</span></span>  
 <span data-ttu-id="a2d8b-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a2d8b-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a2d8b-114">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="a2d8b-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a2d8b-115">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a2d8b-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a2d8b-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a2d8b-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2d8b-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a2d8b-117">See also</span></span>

- [<span data-ttu-id="a2d8b-118">ICeeGen, interfejs</span><span class="sxs-lookup"><span data-stu-id="a2d8b-118">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
