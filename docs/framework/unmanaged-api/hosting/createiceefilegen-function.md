---
title: CreateICeeFileGen — Funkcja
ms.date: 03/30/2017
api_name:
- CreateICeeFileGen
api_location:
- mscoree.dll
- mscorpehost.dll
- mscorpe.dll
api_type:
- COM
f1_keywords:
- CreateICeeFileGen
helpviewer_keywords:
- CreateICeeFileGen function [.NET Framework hosting]
ms.assetid: e36e1fd8-8456-4359-bdc3-3ec1765f041f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 566f73335861a8eb769b21a254e0e93b51a78d02
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59151817"
---
# <a name="createiceefilegen-function"></a><span data-ttu-id="e0715-102">CreateICeeFileGen — Funkcja</span><span class="sxs-lookup"><span data-stu-id="e0715-102">CreateICeeFileGen Function</span></span>
<span data-ttu-id="e0715-103">Tworzy [ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) obiektu.</span><span class="sxs-lookup"><span data-stu-id="e0715-103">Creates an [ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) object.</span></span>  
  
 <span data-ttu-id="e0715-104">Ta funkcja jest przestarzała w [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e0715-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0715-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="e0715-105">Syntax</span></span>  
  
```  
HRESULT CreateICeeFileGen (  
    [out] ICeeFileGen  **ceeFileGen  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e0715-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="e0715-106">Parameters</span></span>  
 `ceeFileGen`  
 <span data-ttu-id="e0715-107">[out] Wskaźnik do adresów nowej `ICeeFileGen` obiektu.</span><span class="sxs-lookup"><span data-stu-id="e0715-107">[out] A pointer to the address of a new `ICeeFileGen` object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e0715-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="e0715-108">Return Value</span></span>  
 <span data-ttu-id="e0715-109">Ta metoda zwraca standardowe kody błędów COM.</span><span class="sxs-lookup"><span data-stu-id="e0715-109">This method returns standard COM error codes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e0715-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e0715-110">Remarks</span></span>  
 <span data-ttu-id="e0715-111">`ICeeFileGen` Obiekt jest używany do tworzenia języka wspólnego plików przenośnych plików wykonywalnych (PE) środowiska uruchomieniowego (języka wspólnego CLR).</span><span class="sxs-lookup"><span data-stu-id="e0715-111">The `ICeeFileGen` object is used to create common language runtime (CLR) portable executable (PE) files.</span></span>  
  
 <span data-ttu-id="e0715-112">Wywołaj [destroyiceefilegen —](../../../../docs/framework/unmanaged-api/hosting/destroyiceefilegen-function.md) funkcję, aby zniszczyć `ICeeFileGen` obiektu po zakończeniu.</span><span class="sxs-lookup"><span data-stu-id="e0715-112">Call the [DestroyICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/destroyiceefilegen-function.md) function to destroy the `ICeeFileGen` object when finished.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e0715-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e0715-113">Requirements</span></span>  
 <span data-ttu-id="e0715-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e0715-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e0715-115">**Nagłówek:** ICeeFileGen.h</span><span class="sxs-lookup"><span data-stu-id="e0715-115">**Header:** ICeeFileGen.h</span></span>  
  
 <span data-ttu-id="e0715-116">**Biblioteka:** MSCorPE.dll</span><span class="sxs-lookup"><span data-stu-id="e0715-116">**Library:** MSCorPE.dll</span></span>  
  
 **<span data-ttu-id="e0715-117">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="e0715-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e0715-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e0715-118">See also</span></span>

- [<span data-ttu-id="e0715-119">Przestarzałe funkcje hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="e0715-119">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
