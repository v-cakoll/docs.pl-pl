---
title: "PreBindAssemblyEx — Funkcja"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: PreBindAssemblyEx
api_location: fusion.dll
api_type: DLLExport
f1_keywords: PreBindAssemblyEx
helpviewer_keywords: PreBindAssemblyEx function [.NET Framework fusion]
ms.assetid: bd285233-a4a2-4b52-bbca-0025a60e4864
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c9bd5cb6be2ccfd25d61a8a2f4347b384e1b2567
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="prebindassemblyex-function"></a><span data-ttu-id="27345-102">PreBindAssemblyEx — Funkcja</span><span class="sxs-lookup"><span data-stu-id="27345-102">PreBindAssemblyEx Function</span></span>
<span data-ttu-id="27345-103">Pobiera nazwę wyświetlaną po zastosowaniu zasad dla zestawu.</span><span class="sxs-lookup"><span data-stu-id="27345-103">Gets the post-policy display name for an assembly.</span></span>  
  
 <span data-ttu-id="27345-104">Ta funkcja obsługuje infrastrukturę programu .NET Framework i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="27345-104">This function supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27345-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="27345-105">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="27345-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="27345-106">Parameters</span></span>  
 `pAppCtx`  
 <span data-ttu-id="27345-107">[in] Identyfikuje kontekst aplikacji.</span><span class="sxs-lookup"><span data-stu-id="27345-107">[in] Identifies the application context.</span></span>  
  
 `pName`  
 <span data-ttu-id="27345-108">[in] Określa nazwę zestawu.</span><span class="sxs-lookup"><span data-stu-id="27345-108">[in] Identifies the assembly name.</span></span>  
  
 `pAsmParent`  
 <span data-ttu-id="27345-109">[in] Określa zestaw nadrzędnej.</span><span class="sxs-lookup"><span data-stu-id="27345-109">[in] Identifies the parent assembly.</span></span> <span data-ttu-id="27345-110">Ten parametr jest ignorowany.</span><span class="sxs-lookup"><span data-stu-id="27345-110">This parameter is ignored.</span></span>  
  
 `pwzRuntimeVersion`  
 <span data-ttu-id="27345-111">[in] Identyfikuje wersję środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="27345-111">[in] Identifies the runtime version.</span></span>  
  
 `ppNamePostPolicy`  
 <span data-ttu-id="27345-112">[out] Zawiera nazwę wyświetlaną po zastosowaniu zasad.</span><span class="sxs-lookup"><span data-stu-id="27345-112">[out] Contains the post-policy display name.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="27345-113">[in] Zarezerwowane dla przyszłego rozszerzalności.</span><span class="sxs-lookup"><span data-stu-id="27345-113">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="27345-114">`pvReserved`musi być odwołanie o wartości null.</span><span class="sxs-lookup"><span data-stu-id="27345-114">`pvReserved` must be a null reference.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="27345-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="27345-115">Remarks</span></span>  
 <span data-ttu-id="27345-116">`ppNamePostPolicy` Parametr wyjściowy jest ustawiona tylko wtedy, gdy funkcja zwraca HRESULT FUSION_E_REF_DEF_MISMATCH.</span><span class="sxs-lookup"><span data-stu-id="27345-116">The `ppNamePostPolicy` output parameter is set only if the function returns HRESULT FUSION_E_REF_DEF_MISMATCH.</span></span> <span data-ttu-id="27345-117">W przeciwnym razie ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="27345-117">Otherwise, it is null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="27345-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="27345-118">Requirements</span></span>  
 <span data-ttu-id="27345-119">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="27345-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="27345-120">**Nagłówek:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="27345-120">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="27345-121">**Biblioteka:** uwzględnione jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="27345-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="27345-122">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="27345-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27345-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="27345-123">See Also</span></span>  
 [<span data-ttu-id="27345-124">Łączenie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="27345-124">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
