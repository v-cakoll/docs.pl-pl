---
title: PreBindAssemblyEx — Funkcja
ms.date: 03/30/2017
api_name:
- PreBindAssemblyEx
api_location:
- fusion.dll
api_type:
- DLLExport
f1_keywords:
- PreBindAssemblyEx
helpviewer_keywords:
- PreBindAssemblyEx function [.NET Framework fusion]
ms.assetid: bd285233-a4a2-4b52-bbca-0025a60e4864
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8251d21fe535f85cc6abd0a7bc6c96ab320007f0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59090241"
---
# <a name="prebindassemblyex-function"></a><span data-ttu-id="2726d-102">PreBindAssemblyEx — Funkcja</span><span class="sxs-lookup"><span data-stu-id="2726d-102">PreBindAssemblyEx Function</span></span>
<span data-ttu-id="2726d-103">Pobiera nazwę wyświetlaną po zastosowaniu zasad dla zestawu.</span><span class="sxs-lookup"><span data-stu-id="2726d-103">Gets the post-policy display name for an assembly.</span></span>  
  
 <span data-ttu-id="2726d-104">Ta funkcja obsługuje infrastrukturę .NET Framework i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="2726d-104">This function supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2726d-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="2726d-105">Syntax</span></span>  
  
```  
HRESULT PreBindAssemblyEx (  
    [in]  IApplicationContext *pAppCtx,  
    [in]  IAssemblyName       *pName,  
    [in]  IAssembly           *pAsmParent,  
    [in]  LPCWSTR             pwzRuntimeVersion,  
    [out] IAssemblyName       **ppNamePostPolicy,  
    [in]  LPVOID              pvReserved  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="2726d-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="2726d-106">Parameters</span></span>  
 `pAppCtx`  
 <span data-ttu-id="2726d-107">[in] Identyfikuje kontekst aplikacji.</span><span class="sxs-lookup"><span data-stu-id="2726d-107">[in] Identifies the application context.</span></span>  
  
 `pName`  
 <span data-ttu-id="2726d-108">[in] Określa nazwę zestawu.</span><span class="sxs-lookup"><span data-stu-id="2726d-108">[in] Identifies the assembly name.</span></span>  
  
 `pAsmParent`  
 <span data-ttu-id="2726d-109">[in] Identyfikuje zestaw nadrzędnej.</span><span class="sxs-lookup"><span data-stu-id="2726d-109">[in] Identifies the parent assembly.</span></span> <span data-ttu-id="2726d-110">Ten parametr jest ignorowany.</span><span class="sxs-lookup"><span data-stu-id="2726d-110">This parameter is ignored.</span></span>  
  
 `pwzRuntimeVersion`  
 <span data-ttu-id="2726d-111">[in] Określa wersję środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="2726d-111">[in] Identifies the runtime version.</span></span>  
  
 `ppNamePostPolicy`  
 <span data-ttu-id="2726d-112">[out] Zawiera nazwę wyświetlaną po zastosowaniu zasad.</span><span class="sxs-lookup"><span data-stu-id="2726d-112">[out] Contains the post-policy display name.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="2726d-113">[in] Zarezerwowane dla przyszłej rozszerzalności.</span><span class="sxs-lookup"><span data-stu-id="2726d-113">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="2726d-114">`pvReserved` musi być odwołanie o wartości null.</span><span class="sxs-lookup"><span data-stu-id="2726d-114">`pvReserved` must be a null reference.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2726d-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2726d-115">Remarks</span></span>  
 <span data-ttu-id="2726d-116">`ppNamePostPolicy` Parametr wyjściowy jest ustawiona tylko wtedy, gdy funkcja zwraca wartość HRESULT FUSION_E_REF_DEF_MISMATCH.</span><span class="sxs-lookup"><span data-stu-id="2726d-116">The `ppNamePostPolicy` output parameter is set only if the function returns HRESULT FUSION_E_REF_DEF_MISMATCH.</span></span> <span data-ttu-id="2726d-117">W przeciwnym razie ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="2726d-117">Otherwise, it is null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2726d-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2726d-118">Requirements</span></span>  
 <span data-ttu-id="2726d-119">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2726d-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2726d-120">**Nagłówek:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="2726d-120">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="2726d-121">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2726d-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2726d-122">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2726d-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2726d-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2726d-123">See also</span></span>

- [<span data-ttu-id="2726d-124">Łączenie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="2726d-124">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
