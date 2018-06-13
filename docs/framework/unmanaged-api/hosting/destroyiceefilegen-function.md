---
title: DestroyICeeFileGen — Funkcja
ms.date: 03/30/2017
api_name:
- DestroyICeeFileGen
api_location:
- mscoree.dll
- mscorpehost.dll
- mscorpe.dll
api_type:
- COM
f1_keywords:
- DestroyICeeFileGen
helpviewer_keywords:
- DestroyICeeFileGen function [.NET Framework hosting]
ms.assetid: dc1e2235-e721-4cb2-a0b8-6b0c030d7bab
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8e108dd925432b8ec193863de4cb085dad50cdd1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33429076"
---
# <a name="destroyiceefilegen-function"></a><span data-ttu-id="9ad6c-102">DestroyICeeFileGen — Funkcja</span><span class="sxs-lookup"><span data-stu-id="9ad6c-102">DestroyICeeFileGen Function</span></span>
<span data-ttu-id="9ad6c-103">Niszczy [ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) obiektu.</span><span class="sxs-lookup"><span data-stu-id="9ad6c-103">Destroys an [ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) object.</span></span>  
  
 <span data-ttu-id="9ad6c-104">Ta funkcja jest przestarzała w [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9ad6c-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ad6c-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="9ad6c-105">Syntax</span></span>  
  
```  
HRESULT DestroyICeeFileGen (  
    [in] ICeeFileGen  **ceeFileGen  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9ad6c-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="9ad6c-106">Parameters</span></span>  
 `ceeFileGen`  
 <span data-ttu-id="9ad6c-107">[in] `ICeeFileGen` Obiektu do zniszczenia.</span><span class="sxs-lookup"><span data-stu-id="9ad6c-107">[in] The `ICeeFileGen` object to destroy.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9ad6c-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="9ad6c-108">Return Value</span></span>  
 <span data-ttu-id="9ad6c-109">Ta metoda zwraca standardowe kody błędów COM.</span><span class="sxs-lookup"><span data-stu-id="9ad6c-109">This method returns standard COM error codes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9ad6c-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9ad6c-110">Remarks</span></span>  
 <span data-ttu-id="9ad6c-111">`DestroyICeeFileGen` niszczy `ICeeFileGen` obiekt utworzony przez [CreateICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/createiceefilegen-function.md) funkcji.</span><span class="sxs-lookup"><span data-stu-id="9ad6c-111">`DestroyICeeFileGen` destroys the `ICeeFileGen` object created by the [CreateICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/createiceefilegen-function.md) function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9ad6c-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9ad6c-112">Requirements</span></span>  
 <span data-ttu-id="9ad6c-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9ad6c-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ad6c-114">**Nagłówek:** ICeeFileGen.h</span><span class="sxs-lookup"><span data-stu-id="9ad6c-114">**Header:** ICeeFileGen.h</span></span>  
  
 <span data-ttu-id="9ad6c-115">**Biblioteka:** MSCorPE.dll</span><span class="sxs-lookup"><span data-stu-id="9ad6c-115">**Library:** MSCorPE.dll</span></span>  
  
 <span data-ttu-id="9ad6c-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9ad6c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ad6c-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9ad6c-117">See Also</span></span>  
 [<span data-ttu-id="9ad6c-118">Przestarzałe funkcje hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="9ad6c-118">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
