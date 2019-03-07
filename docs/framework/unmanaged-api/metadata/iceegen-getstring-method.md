---
title: ICeeGen::GetString — Metoda
ms.date: 03/30/2017
api_name:
- ICeeGen.GetString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetString
helpviewer_keywords:
- ICeeGen::GetString method [.NET Framework metadata]
- GetString method, ICeeGen interface [.NET Framework metadata]
ms.assetid: 7cc22562-128c-440a-9147-55ff20f173d7
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bf3f781e23d0787d01a1ef04b41b2c38eaaa9e0d
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57479340"
---
# <a name="iceegengetstring-method"></a><span data-ttu-id="be543-102">ICeeGen::GetString — Metoda</span><span class="sxs-lookup"><span data-stu-id="be543-102">ICeeGen::GetString Method</span></span>
<span data-ttu-id="be543-103">Pobiera ciąg przechowywaną w określonej względny adres wirtualny.</span><span class="sxs-lookup"><span data-stu-id="be543-103">Gets the string stored at the specified relative virtual address.</span></span>  
  
 <span data-ttu-id="be543-104">Ta metoda jest przestarzała i nie powinna być używana.</span><span class="sxs-lookup"><span data-stu-id="be543-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be543-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="be543-105">Syntax</span></span>  
  
```  
HRESULT GetString (  
    [in]  ULONG      RVA,   
    [out] LPWSTR     *lpString  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="be543-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="be543-106">Parameters</span></span>  
 `RVA`  
 <span data-ttu-id="be543-107">[in] Wirtualny adres względny ciągu do zwrócenia.</span><span class="sxs-lookup"><span data-stu-id="be543-107">[in] The relative virtual address of the string to return.</span></span>  
  
 `lpString`  
 <span data-ttu-id="be543-108">[out] Zwracanego ciągu.</span><span class="sxs-lookup"><span data-stu-id="be543-108">[out] The returned string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="be543-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="be543-109">Requirements</span></span>  
 <span data-ttu-id="be543-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="be543-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="be543-111">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="be543-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="be543-112">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="be543-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="be543-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="be543-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be543-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="be543-114">See also</span></span>
- [<span data-ttu-id="be543-115">ICeeGen, interfejs</span><span class="sxs-lookup"><span data-stu-id="be543-115">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
