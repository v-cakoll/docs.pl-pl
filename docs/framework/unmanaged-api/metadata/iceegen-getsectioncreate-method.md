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
ms.openlocfilehash: 0cf7b15392c90694db659f6faff6feecbef65466
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008340"
---
# <a name="iceegengetsectioncreate-method"></a><span data-ttu-id="8c711-102">ICeeGen::GetSectionCreate — Metoda</span><span class="sxs-lookup"><span data-stu-id="8c711-102">ICeeGen::GetSectionCreate Method</span></span>
<span data-ttu-id="8c711-103">Generuje i pobiera sekcję kodu przy użyciu podanej wartości Name i flag.</span><span class="sxs-lookup"><span data-stu-id="8c711-103">Generates and gets a code section using the specified name and flag values.</span></span>  
  
 <span data-ttu-id="8c711-104">Ta metoda jest przestarzała i nie powinna być używana.</span><span class="sxs-lookup"><span data-stu-id="8c711-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c711-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="8c711-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSectionCreate (  
    [in]  const char     *name,  
    [in]  DWORD          flags,  
    [out] HCEESECTION    *section  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8c711-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="8c711-106">Parameters</span></span>  
 `name`  
 <span data-ttu-id="8c711-107">podczas Wskaźnik do ciągu, który określa nazwę sekcji, która ma zostać utworzona.</span><span class="sxs-lookup"><span data-stu-id="8c711-107">[in] A pointer to a string that specifies the name of the section to be created.</span></span>  
  
 `flags`  
 <span data-ttu-id="8c711-108">podczas Flagi określające opcje.</span><span class="sxs-lookup"><span data-stu-id="8c711-108">[in] Flags that specify options.</span></span>  
  
 `section`  
 <span data-ttu-id="8c711-109">określoną Wskaźnik do nowo utworzonej sekcji kodu.</span><span class="sxs-lookup"><span data-stu-id="8c711-109">[out] A pointer to the newly created code section.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8c711-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8c711-110">Remarks</span></span>  
 <span data-ttu-id="8c711-111">Wywołanie `GetSectionCreate` tylko wtedy, gdy istnieją specjalne wymagania sekcji, które nie są obsługiwane przez inne metody.</span><span class="sxs-lookup"><span data-stu-id="8c711-111">Call `GetSectionCreate` only if you have special section requirements that are not handled by other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8c711-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8c711-112">Requirements</span></span>  
 <span data-ttu-id="8c711-113">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8c711-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c711-114">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="8c711-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8c711-115">**Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="8c711-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8c711-116">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c711-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c711-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8c711-117">See also</span></span>

- [<span data-ttu-id="8c711-118">ICeeGen — Interfejs</span><span class="sxs-lookup"><span data-stu-id="8c711-118">ICeeGen Interface</span></span>](iceegen-interface.md)
