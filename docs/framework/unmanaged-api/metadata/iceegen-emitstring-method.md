---
title: "ICeeGen::EmitString — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICeeGen.EmitString
api_location: mscoree.dll
api_type: COM
f1_keywords: ICeeGen::EmitString
helpviewer_keywords:
- EmitString method [.NET Framework metadata]
- ICeeGen::EmitString method [.NET Framework metadata]
ms.assetid: ad2710a7-edb8-4493-8619-3fce235e3334
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: f988e54a37212beeeebfbef15e6b148021e0b759
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="iceegenemitstring-method"></a><span data-ttu-id="58b18-102">ICeeGen::EmitString — Metoda</span><span class="sxs-lookup"><span data-stu-id="58b18-102">ICeeGen::EmitString Method</span></span>
<span data-ttu-id="58b18-103">Emituje określonego ciągu w bazie kodu.</span><span class="sxs-lookup"><span data-stu-id="58b18-103">Emits the specified string into the code base.</span></span>  
  
 <span data-ttu-id="58b18-104">Ta metoda jest przestarzała i nie powinna być używana.</span><span class="sxs-lookup"><span data-stu-id="58b18-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58b18-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="58b18-105">Syntax</span></span>  
  
```  
HRESULT EmitString (  
    [in]  LPWSTR    lpString,  
    [out] ULONG     *RVA  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="58b18-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="58b18-106">Parameters</span></span>  
 `lpString`  
 <span data-ttu-id="58b18-107">[in] Ciąg do emisji.</span><span class="sxs-lookup"><span data-stu-id="58b18-107">[in] The string to emit.</span></span>  
  
 `RVA`  
 <span data-ttu-id="58b18-108">[out] Wirtualny adres względny emitowany ciągu.</span><span class="sxs-lookup"><span data-stu-id="58b18-108">[out] The relative virtual address of the emitted string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="58b18-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="58b18-109">Requirements</span></span>  
 <span data-ttu-id="58b18-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="58b18-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="58b18-111">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="58b18-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="58b18-112">**Biblioteka:** używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="58b18-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="58b18-113">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="58b18-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58b18-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="58b18-114">See Also</span></span>  
 [<span data-ttu-id="58b18-115">ICeeGen — interfejs</span><span class="sxs-lookup"><span data-stu-id="58b18-115">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
