---
title: CreateAssemblyCache — Funkcja
ms.date: 03/30/2017
api_name:
- CreateAssemblyCache
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- CreateAssemblyCache
helpviewer_keywords:
- CreateAssemblyCache function [.NET Framework fusion]
ms.assetid: 348c7c8c-8578-46ae-97cf-480d6015c3c6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c855d6f85c3cbfa6d81a1fbce3ef5b83abb3f583
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795410"
---
# <a name="createassemblycache-function"></a><span data-ttu-id="eb8ae-102">CreateAssemblyCache — Funkcja</span><span class="sxs-lookup"><span data-stu-id="eb8ae-102">CreateAssemblyCache Function</span></span>
<span data-ttu-id="eb8ae-103">Pobiera wskaźnik do nowego wystąpienia [IAssemblyCache](iassemblycache-interface.md) , które reprezentuje globalną pamięć podręczną zestawów.</span><span class="sxs-lookup"><span data-stu-id="eb8ae-103">Gets a pointer to a new [IAssemblyCache](iassemblycache-interface.md) instance that represents the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb8ae-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="eb8ae-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateAssemblyCache (  
    [out] IAssemblyCache  **ppAsmCache,  
    [in]  DWORD           dwReserved  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="eb8ae-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="eb8ae-105">Parameters</span></span>  
 `ppAsmCache`  
 <span data-ttu-id="eb8ae-106">określoną Zwrócony `IAssemblyCache` wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="eb8ae-106">[out] The returned `IAssemblyCache` pointer.</span></span>  
  
 `dwReserved`  
 <span data-ttu-id="eb8ae-107">podczas Zarezerwowane do użytku w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="eb8ae-107">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="eb8ae-108">`dwReserved`musi mieć wartość 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="eb8ae-108">`dwReserved` must be 0 (zero).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eb8ae-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="eb8ae-109">Requirements</span></span>  
 <span data-ttu-id="eb8ae-110">**Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eb8ae-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eb8ae-111">**Nagłówki** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="eb8ae-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="eb8ae-112">**Biblioteki** Uwzględnione jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="eb8ae-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="eb8ae-113">**.NET Framework wersje:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eb8ae-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb8ae-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="eb8ae-114">See also</span></span>

- [<span data-ttu-id="eb8ae-115">IAssemblyCache, interfejs</span><span class="sxs-lookup"><span data-stu-id="eb8ae-115">IAssemblyCache Interface</span></span>](iassemblycache-interface.md)
- [<span data-ttu-id="eb8ae-116">Łączenie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="eb8ae-116">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
- [<span data-ttu-id="eb8ae-117">Global Assembly Cache</span><span class="sxs-lookup"><span data-stu-id="eb8ae-117">Global Assembly Cache</span></span>](../../app-domains/gac.md)
