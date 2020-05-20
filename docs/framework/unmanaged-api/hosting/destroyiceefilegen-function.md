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
ms.openlocfilehash: ff7e7b299d185b8db263d2076c1e075b87b487fc
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616401"
---
# <a name="destroyiceefilegen-function"></a><span data-ttu-id="120ee-102">DestroyICeeFileGen — Funkcja</span><span class="sxs-lookup"><span data-stu-id="120ee-102">DestroyICeeFileGen Function</span></span>
<span data-ttu-id="120ee-103">Niszczy obiekt [ICeeFileGen](iceefilegen-class.md) .</span><span class="sxs-lookup"><span data-stu-id="120ee-103">Destroys an [ICeeFileGen](iceefilegen-class.md) object.</span></span>  
  
 <span data-ttu-id="120ee-104">Ta funkcja jest przestarzała w .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="120ee-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="120ee-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="120ee-105">Syntax</span></span>  
  
```cpp  
HRESULT DestroyICeeFileGen (  
    [in] ICeeFileGen  **ceeFileGen  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="120ee-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="120ee-106">Parameters</span></span>  
 `ceeFileGen`  
 <span data-ttu-id="120ee-107">podczas `ICeeFileGen`Obiekt do zniszczenia.</span><span class="sxs-lookup"><span data-stu-id="120ee-107">[in] The `ICeeFileGen` object to destroy.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="120ee-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="120ee-108">Return Value</span></span>  
 <span data-ttu-id="120ee-109">Ta metoda zwraca standardowe kody błędów COM.</span><span class="sxs-lookup"><span data-stu-id="120ee-109">This method returns standard COM error codes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="120ee-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="120ee-110">Remarks</span></span>  
 <span data-ttu-id="120ee-111">`DestroyICeeFileGen`niszczy `ICeeFileGen` obiekt utworzony przez funkcję [CreateICeeFileGen —](createiceefilegen-function.md) .</span><span class="sxs-lookup"><span data-stu-id="120ee-111">`DestroyICeeFileGen` destroys the `ICeeFileGen` object created by the [CreateICeeFileGen](createiceefilegen-function.md) function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="120ee-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="120ee-112">Requirements</span></span>  
 <span data-ttu-id="120ee-113">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="120ee-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="120ee-114">**Nagłówek:** ICeeFileGen. h</span><span class="sxs-lookup"><span data-stu-id="120ee-114">**Header:** ICeeFileGen.h</span></span>  
  
 <span data-ttu-id="120ee-115">**Biblioteka:** MSCorPE. dll</span><span class="sxs-lookup"><span data-stu-id="120ee-115">**Library:** MSCorPE.dll</span></span>  
  
 <span data-ttu-id="120ee-116">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="120ee-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="120ee-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="120ee-117">See also</span></span>

- [<span data-ttu-id="120ee-118">Przestarzałe funkcje hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="120ee-118">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
