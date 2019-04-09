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
ms.openlocfilehash: 37ff40e1c009b8e1e0509a4a3333d5a2a70bbfd2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59159890"
---
# <a name="destroyiceefilegen-function"></a><span data-ttu-id="c5a0e-102">DestroyICeeFileGen — Funkcja</span><span class="sxs-lookup"><span data-stu-id="c5a0e-102">DestroyICeeFileGen Function</span></span>
<span data-ttu-id="c5a0e-103">Niszczy [ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) obiektu.</span><span class="sxs-lookup"><span data-stu-id="c5a0e-103">Destroys an [ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) object.</span></span>  
  
 <span data-ttu-id="c5a0e-104">Ta funkcja jest przestarzała w [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c5a0e-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5a0e-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="c5a0e-105">Syntax</span></span>  
  
```  
HRESULT DestroyICeeFileGen (  
    [in] ICeeFileGen  **ceeFileGen  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c5a0e-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="c5a0e-106">Parameters</span></span>  
 `ceeFileGen`  
 <span data-ttu-id="c5a0e-107">[in] `ICeeFileGen` Obiektu do zniszczenia.</span><span class="sxs-lookup"><span data-stu-id="c5a0e-107">[in] The `ICeeFileGen` object to destroy.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c5a0e-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="c5a0e-108">Return Value</span></span>  
 <span data-ttu-id="c5a0e-109">Ta metoda zwraca standardowe kody błędów COM.</span><span class="sxs-lookup"><span data-stu-id="c5a0e-109">This method returns standard COM error codes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c5a0e-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c5a0e-110">Remarks</span></span>  
 `DestroyICeeFileGen` <span data-ttu-id="c5a0e-111">niszczy `ICeeFileGen` obiekt utworzony przez [createiceefilegen —](../../../../docs/framework/unmanaged-api/hosting/createiceefilegen-function.md) funkcji.</span><span class="sxs-lookup"><span data-stu-id="c5a0e-111">destroys the `ICeeFileGen` object created by the [CreateICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/createiceefilegen-function.md) function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c5a0e-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c5a0e-112">Requirements</span></span>  
 <span data-ttu-id="c5a0e-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c5a0e-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c5a0e-114">**Nagłówek:** ICeeFileGen.h</span><span class="sxs-lookup"><span data-stu-id="c5a0e-114">**Header:** ICeeFileGen.h</span></span>  
  
 <span data-ttu-id="c5a0e-115">**Biblioteka:** MSCorPE.dll</span><span class="sxs-lookup"><span data-stu-id="c5a0e-115">**Library:** MSCorPE.dll</span></span>  
  
 **<span data-ttu-id="c5a0e-116">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="c5a0e-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c5a0e-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c5a0e-117">See also</span></span>

- [<span data-ttu-id="c5a0e-118">Przestarzałe funkcje hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="c5a0e-118">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
