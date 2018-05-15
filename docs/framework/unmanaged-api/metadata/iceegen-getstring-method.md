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
ms.openlocfilehash: f7ac5ef95ca3705b11cfda51d7fd1aca7400abc4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="iceegengetstring-method"></a><span data-ttu-id="ad45c-102">ICeeGen::GetString — Metoda</span><span class="sxs-lookup"><span data-stu-id="ad45c-102">ICeeGen::GetString Method</span></span>
<span data-ttu-id="ad45c-103">Pobiera ciąg przechowywanych na określony wirtualny adres względny.</span><span class="sxs-lookup"><span data-stu-id="ad45c-103">Gets the string stored at the specified relative virtual address.</span></span>  
  
 <span data-ttu-id="ad45c-104">Ta metoda jest przestarzała i nie powinna być używana.</span><span class="sxs-lookup"><span data-stu-id="ad45c-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad45c-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="ad45c-105">Syntax</span></span>  
  
```  
HRESULT GetString (  
    [in]  ULONG      RVA,   
    [out] LPWSTR     *lpString  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ad45c-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="ad45c-106">Parameters</span></span>  
 `RVA`  
 <span data-ttu-id="ad45c-107">[in] Wirtualny adres względny ciągu do zwrócenia.</span><span class="sxs-lookup"><span data-stu-id="ad45c-107">[in] The relative virtual address of the string to return.</span></span>  
  
 `lpString`  
 <span data-ttu-id="ad45c-108">[out] Zwracany ciąg.</span><span class="sxs-lookup"><span data-stu-id="ad45c-108">[out] The returned string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ad45c-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ad45c-109">Requirements</span></span>  
 <span data-ttu-id="ad45c-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ad45c-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ad45c-111">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ad45c-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ad45c-112">**Biblioteka:** używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ad45c-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ad45c-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ad45c-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad45c-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ad45c-114">See Also</span></span>  
 [<span data-ttu-id="ad45c-115">ICeeGen, interfejs</span><span class="sxs-lookup"><span data-stu-id="ad45c-115">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
