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
ms.openlocfilehash: 96968de84182b74f7baa89d5dfc12a4797ade595
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779227"
---
# <a name="createiceefilegen-function"></a><span data-ttu-id="7dfa1-102">CreateICeeFileGen — Funkcja</span><span class="sxs-lookup"><span data-stu-id="7dfa1-102">CreateICeeFileGen Function</span></span>
<span data-ttu-id="7dfa1-103">Tworzy [ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) obiektu.</span><span class="sxs-lookup"><span data-stu-id="7dfa1-103">Creates an [ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) object.</span></span>  
  
 <span data-ttu-id="7dfa1-104">Ta funkcja jest przestarzała w programie .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="7dfa1-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7dfa1-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="7dfa1-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateICeeFileGen (  
    [out] ICeeFileGen  **ceeFileGen  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7dfa1-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="7dfa1-106">Parameters</span></span>  
 `ceeFileGen`  
 <span data-ttu-id="7dfa1-107">[out] Wskaźnik do adresów nowej `ICeeFileGen` obiektu.</span><span class="sxs-lookup"><span data-stu-id="7dfa1-107">[out] A pointer to the address of a new `ICeeFileGen` object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7dfa1-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="7dfa1-108">Return Value</span></span>  
 <span data-ttu-id="7dfa1-109">Ta metoda zwraca standardowe kody błędów COM.</span><span class="sxs-lookup"><span data-stu-id="7dfa1-109">This method returns standard COM error codes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7dfa1-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7dfa1-110">Remarks</span></span>  
 <span data-ttu-id="7dfa1-111">`ICeeFileGen` Obiekt jest używany do tworzenia języka wspólnego plików przenośnych plików wykonywalnych (PE) środowiska uruchomieniowego (języka wspólnego CLR).</span><span class="sxs-lookup"><span data-stu-id="7dfa1-111">The `ICeeFileGen` object is used to create common language runtime (CLR) portable executable (PE) files.</span></span>  
  
 <span data-ttu-id="7dfa1-112">Wywołaj [destroyiceefilegen —](../../../../docs/framework/unmanaged-api/hosting/destroyiceefilegen-function.md) funkcję, aby zniszczyć `ICeeFileGen` obiektu po zakończeniu.</span><span class="sxs-lookup"><span data-stu-id="7dfa1-112">Call the [DestroyICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/destroyiceefilegen-function.md) function to destroy the `ICeeFileGen` object when finished.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7dfa1-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7dfa1-113">Requirements</span></span>  
 <span data-ttu-id="7dfa1-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7dfa1-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7dfa1-115">**Nagłówek:** ICeeFileGen.h</span><span class="sxs-lookup"><span data-stu-id="7dfa1-115">**Header:** ICeeFileGen.h</span></span>  
  
 <span data-ttu-id="7dfa1-116">**Biblioteka:** MSCorPE.dll</span><span class="sxs-lookup"><span data-stu-id="7dfa1-116">**Library:** MSCorPE.dll</span></span>  
  
 <span data-ttu-id="7dfa1-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7dfa1-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7dfa1-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7dfa1-118">See also</span></span>

- [<span data-ttu-id="7dfa1-119">Przestarzałe funkcje hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="7dfa1-119">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
