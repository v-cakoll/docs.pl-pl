---
title: "ICeeGen::GetIlSection — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICeeGen.GetIlSection
api_location: mscoree.dll
api_type: COM
f1_keywords: ICeeGen::GetIlSection
helpviewer_keywords:
- GetIlSection method [.NET Framework metadata]
- ICeeGen::GetIlSection method [.NET Framework metadata]
ms.assetid: 6f2db2ca-203f-4ac3-9530-208642ca385e
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b87936fb099d6e58281162d0a9a75291b0ac0767
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="iceegengetilsection-method"></a><span data-ttu-id="cb74b-102">ICeeGen::GetIlSection — Metoda</span><span class="sxs-lookup"><span data-stu-id="cb74b-102">ICeeGen::GetIlSection Method</span></span>
<span data-ttu-id="cb74b-103">Pobiera część bazy kodu języka pośredniego odwołuje się określony uchwyt.</span><span class="sxs-lookup"><span data-stu-id="cb74b-103">Gets the section of the intermediate language code base referenced by the specified handle.</span></span>  
  
 <span data-ttu-id="cb74b-104">Ta metoda jest przestarzała i nie powinna być używana.</span><span class="sxs-lookup"><span data-stu-id="cb74b-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb74b-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="cb74b-105">Syntax</span></span>  
  
```  
HRESULT GetIlSection (  
    [in] HCEESECTION  *section  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cb74b-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="cb74b-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="cb74b-107">[in] Dojście do sekcji, aby pobrać.</span><span class="sxs-lookup"><span data-stu-id="cb74b-107">[in] The handle to the section to get.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cb74b-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cb74b-108">Requirements</span></span>  
 <span data-ttu-id="cb74b-109">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cb74b-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb74b-110">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="cb74b-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="cb74b-111">**Biblioteka:** używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="cb74b-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="cb74b-112">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb74b-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb74b-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cb74b-113">See Also</span></span>  
 [<span data-ttu-id="cb74b-114">ICeeGen — interfejs</span><span class="sxs-lookup"><span data-stu-id="cb74b-114">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
