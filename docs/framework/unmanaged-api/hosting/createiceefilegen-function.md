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
ms.openlocfilehash: de27851b4afc3eccad46531848c68723bff346d5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136824"
---
# <a name="createiceefilegen-function"></a><span data-ttu-id="62c82-102">CreateICeeFileGen — Funkcja</span><span class="sxs-lookup"><span data-stu-id="62c82-102">CreateICeeFileGen Function</span></span>
<span data-ttu-id="62c82-103">Tworzy obiekt [ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) .</span><span class="sxs-lookup"><span data-stu-id="62c82-103">Creates an [ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) object.</span></span>  
  
 <span data-ttu-id="62c82-104">Ta funkcja jest przestarzała w .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="62c82-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62c82-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="62c82-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateICeeFileGen (  
    [out] ICeeFileGen  **ceeFileGen  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="62c82-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="62c82-106">Parameters</span></span>  
 `ceeFileGen`  
 <span data-ttu-id="62c82-107">określoną Wskaźnik do adresu nowego obiektu `ICeeFileGen`.</span><span class="sxs-lookup"><span data-stu-id="62c82-107">[out] A pointer to the address of a new `ICeeFileGen` object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="62c82-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="62c82-108">Return Value</span></span>  
 <span data-ttu-id="62c82-109">Ta metoda zwraca standardowe kody błędów COM.</span><span class="sxs-lookup"><span data-stu-id="62c82-109">This method returns standard COM error codes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="62c82-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="62c82-110">Remarks</span></span>  
 <span data-ttu-id="62c82-111">Obiekt `ICeeFileGen` jest używany do tworzenia przenośnych plików wykonywalnych (PE) środowiska uruchomieniowego języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="62c82-111">The `ICeeFileGen` object is used to create common language runtime (CLR) portable executable (PE) files.</span></span>  
  
 <span data-ttu-id="62c82-112">Wywołaj funkcję [DestroyICeeFileGen —](../../../../docs/framework/unmanaged-api/hosting/destroyiceefilegen-function.md) , aby zniszczyć obiekt `ICeeFileGen` po zakończeniu.</span><span class="sxs-lookup"><span data-stu-id="62c82-112">Call the [DestroyICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/destroyiceefilegen-function.md) function to destroy the `ICeeFileGen` object when finished.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="62c82-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="62c82-113">Requirements</span></span>  
 <span data-ttu-id="62c82-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="62c82-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="62c82-115">**Nagłówek:** ICeeFileGen. h</span><span class="sxs-lookup"><span data-stu-id="62c82-115">**Header:** ICeeFileGen.h</span></span>  
  
 <span data-ttu-id="62c82-116">**Biblioteka:** MSCorPE. dll</span><span class="sxs-lookup"><span data-stu-id="62c82-116">**Library:** MSCorPE.dll</span></span>  
  
 <span data-ttu-id="62c82-117">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="62c82-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62c82-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="62c82-118">See also</span></span>

- [<span data-ttu-id="62c82-119">Przestarzałe funkcje hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="62c82-119">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
