---
title: "PreBindAssemblyEx — Funkcja"
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 05977db8e01d00af6e160cb2993867cf83eb24c1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="prebindassemblyex-function"></a><span data-ttu-id="bdb8a-102">PreBindAssemblyEx — Funkcja</span><span class="sxs-lookup"><span data-stu-id="bdb8a-102">PreBindAssemblyEx Function</span></span>
<span data-ttu-id="bdb8a-103">Pobiera nazwę wyświetlaną po zastosowaniu zasad dla zestawu.</span><span class="sxs-lookup"><span data-stu-id="bdb8a-103">Gets the post-policy display name for an assembly.</span></span>  
  
 <span data-ttu-id="bdb8a-104">Ta funkcja obsługuje infrastrukturę programu .NET Framework i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="bdb8a-104">This function supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bdb8a-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="bdb8a-105">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="bdb8a-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="bdb8a-106">Parameters</span></span>  
 `pAppCtx`  
 <span data-ttu-id="bdb8a-107">[in] Identyfikuje kontekst aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bdb8a-107">[in] Identifies the application context.</span></span>  
  
 `pName`  
 <span data-ttu-id="bdb8a-108">[in] Określa nazwę zestawu.</span><span class="sxs-lookup"><span data-stu-id="bdb8a-108">[in] Identifies the assembly name.</span></span>  
  
 `pAsmParent`  
 <span data-ttu-id="bdb8a-109">[in] Określa zestaw nadrzędnej.</span><span class="sxs-lookup"><span data-stu-id="bdb8a-109">[in] Identifies the parent assembly.</span></span> <span data-ttu-id="bdb8a-110">Ten parametr jest ignorowany.</span><span class="sxs-lookup"><span data-stu-id="bdb8a-110">This parameter is ignored.</span></span>  
  
 `pwzRuntimeVersion`  
 <span data-ttu-id="bdb8a-111">[in] Identyfikuje wersję środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="bdb8a-111">[in] Identifies the runtime version.</span></span>  
  
 `ppNamePostPolicy`  
 <span data-ttu-id="bdb8a-112">[out] Zawiera nazwę wyświetlaną po zastosowaniu zasad.</span><span class="sxs-lookup"><span data-stu-id="bdb8a-112">[out] Contains the post-policy display name.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="bdb8a-113">[in] Zarezerwowane dla przyszłego rozszerzalności.</span><span class="sxs-lookup"><span data-stu-id="bdb8a-113">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="bdb8a-114">`pvReserved`musi być odwołanie o wartości null.</span><span class="sxs-lookup"><span data-stu-id="bdb8a-114">`pvReserved` must be a null reference.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bdb8a-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bdb8a-115">Remarks</span></span>  
 <span data-ttu-id="bdb8a-116">`ppNamePostPolicy` Parametr wyjściowy jest ustawiona tylko wtedy, gdy funkcja zwraca HRESULT FUSION_E_REF_DEF_MISMATCH.</span><span class="sxs-lookup"><span data-stu-id="bdb8a-116">The `ppNamePostPolicy` output parameter is set only if the function returns HRESULT FUSION_E_REF_DEF_MISMATCH.</span></span> <span data-ttu-id="bdb8a-117">W przeciwnym razie ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="bdb8a-117">Otherwise, it is null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bdb8a-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bdb8a-118">Requirements</span></span>  
 <span data-ttu-id="bdb8a-119">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bdb8a-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bdb8a-120">**Nagłówek:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="bdb8a-120">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="bdb8a-121">**Biblioteka:** uwzględnione jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="bdb8a-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="bdb8a-122">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bdb8a-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bdb8a-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bdb8a-123">See Also</span></span>  
 [<span data-ttu-id="bdb8a-124">Łączenie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="bdb8a-124">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
