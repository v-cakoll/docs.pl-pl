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
ms.openlocfilehash: daf674c0340998c0fd518e0f1af721bbe9ff653c
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490474"
---
# <a name="destroyiceefilegen-function"></a><span data-ttu-id="1cb5b-102">DestroyICeeFileGen — Funkcja</span><span class="sxs-lookup"><span data-stu-id="1cb5b-102">DestroyICeeFileGen Function</span></span>
<span data-ttu-id="1cb5b-103">Niszczy [ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) obiektu.</span><span class="sxs-lookup"><span data-stu-id="1cb5b-103">Destroys an [ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) object.</span></span>  
  
 <span data-ttu-id="1cb5b-104">Ta funkcja jest przestarzała w programie .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="1cb5b-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1cb5b-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="1cb5b-105">Syntax</span></span>  
  
```  
HRESULT DestroyICeeFileGen (  
    [in] ICeeFileGen  **ceeFileGen  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1cb5b-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="1cb5b-106">Parameters</span></span>  
 `ceeFileGen`  
 <span data-ttu-id="1cb5b-107">[in] `ICeeFileGen` Obiektu do zniszczenia.</span><span class="sxs-lookup"><span data-stu-id="1cb5b-107">[in] The `ICeeFileGen` object to destroy.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1cb5b-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="1cb5b-108">Return Value</span></span>  
 <span data-ttu-id="1cb5b-109">Ta metoda zwraca standardowe kody błędów COM.</span><span class="sxs-lookup"><span data-stu-id="1cb5b-109">This method returns standard COM error codes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1cb5b-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1cb5b-110">Remarks</span></span>  
 <span data-ttu-id="1cb5b-111">`DestroyICeeFileGen` niszczy `ICeeFileGen` obiekt utworzony przez [createiceefilegen —](../../../../docs/framework/unmanaged-api/hosting/createiceefilegen-function.md) funkcji.</span><span class="sxs-lookup"><span data-stu-id="1cb5b-111">`DestroyICeeFileGen` destroys the `ICeeFileGen` object created by the [CreateICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/createiceefilegen-function.md) function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1cb5b-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1cb5b-112">Requirements</span></span>  
 <span data-ttu-id="1cb5b-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1cb5b-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1cb5b-114">**Nagłówek:** ICeeFileGen.h</span><span class="sxs-lookup"><span data-stu-id="1cb5b-114">**Header:** ICeeFileGen.h</span></span>  
  
 <span data-ttu-id="1cb5b-115">**Biblioteka:** MSCorPE.dll</span><span class="sxs-lookup"><span data-stu-id="1cb5b-115">**Library:** MSCorPE.dll</span></span>  
  
 <span data-ttu-id="1cb5b-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1cb5b-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1cb5b-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1cb5b-117">See also</span></span>

- [<span data-ttu-id="1cb5b-118">Przestarzałe funkcje hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="1cb5b-118">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
