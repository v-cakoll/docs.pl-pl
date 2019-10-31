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
ms.openlocfilehash: 4eb878b61b72378bc6870af7f2cd09f0b6943b13
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136503"
---
# <a name="destroyiceefilegen-function"></a><span data-ttu-id="d18c6-102">DestroyICeeFileGen — Funkcja</span><span class="sxs-lookup"><span data-stu-id="d18c6-102">DestroyICeeFileGen Function</span></span>
<span data-ttu-id="d18c6-103">Niszczy obiekt [ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) .</span><span class="sxs-lookup"><span data-stu-id="d18c6-103">Destroys an [ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) object.</span></span>  
  
 <span data-ttu-id="d18c6-104">Ta funkcja jest przestarzała w .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="d18c6-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d18c6-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="d18c6-105">Syntax</span></span>  
  
```cpp  
HRESULT DestroyICeeFileGen (  
    [in] ICeeFileGen  **ceeFileGen  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d18c6-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="d18c6-106">Parameters</span></span>  
 `ceeFileGen`  
 <span data-ttu-id="d18c6-107">podczas Obiekt `ICeeFileGen` do zniszczenia.</span><span class="sxs-lookup"><span data-stu-id="d18c6-107">[in] The `ICeeFileGen` object to destroy.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d18c6-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="d18c6-108">Return Value</span></span>  
 <span data-ttu-id="d18c6-109">Ta metoda zwraca standardowe kody błędów COM.</span><span class="sxs-lookup"><span data-stu-id="d18c6-109">This method returns standard COM error codes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d18c6-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d18c6-110">Remarks</span></span>  
 <span data-ttu-id="d18c6-111">`DestroyICeeFileGen` niszczy obiekt `ICeeFileGen` utworzony przez funkcję [CreateICeeFileGen —](../../../../docs/framework/unmanaged-api/hosting/createiceefilegen-function.md) .</span><span class="sxs-lookup"><span data-stu-id="d18c6-111">`DestroyICeeFileGen` destroys the `ICeeFileGen` object created by the [CreateICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/createiceefilegen-function.md) function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d18c6-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d18c6-112">Requirements</span></span>  
 <span data-ttu-id="d18c6-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d18c6-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d18c6-114">**Nagłówek:** ICeeFileGen. h</span><span class="sxs-lookup"><span data-stu-id="d18c6-114">**Header:** ICeeFileGen.h</span></span>  
  
 <span data-ttu-id="d18c6-115">**Biblioteka:** MSCorPE. dll</span><span class="sxs-lookup"><span data-stu-id="d18c6-115">**Library:** MSCorPE.dll</span></span>  
  
 <span data-ttu-id="d18c6-116">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d18c6-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d18c6-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d18c6-117">See also</span></span>

- [<span data-ttu-id="d18c6-118">Przestarzałe funkcje hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="d18c6-118">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
