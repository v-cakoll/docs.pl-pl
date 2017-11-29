---
title: "ICeeGen::GetString — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICeeGen.GetString
api_location: mscoree.dll
api_type: COM
f1_keywords: ICeeGen::GetString
helpviewer_keywords:
- ICeeGen::GetString method [.NET Framework metadata]
- GetString method, ICeeGen interface [.NET Framework metadata]
ms.assetid: 7cc22562-128c-440a-9147-55ff20f173d7
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: f7afe07309850a564ec75e69c07f63a3210f3810
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="iceegengetstring-method"></a><span data-ttu-id="d66b0-102">ICeeGen::GetString — Metoda</span><span class="sxs-lookup"><span data-stu-id="d66b0-102">ICeeGen::GetString Method</span></span>
<span data-ttu-id="d66b0-103">Pobiera ciąg przechowywanych na określony wirtualny adres względny.</span><span class="sxs-lookup"><span data-stu-id="d66b0-103">Gets the string stored at the specified relative virtual address.</span></span>  
  
 <span data-ttu-id="d66b0-104">Ta metoda jest przestarzała i nie powinna być używana.</span><span class="sxs-lookup"><span data-stu-id="d66b0-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d66b0-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="d66b0-105">Syntax</span></span>  
  
```  
HRESULT GetString (  
    [in]  ULONG      RVA,   
    [out] LPWSTR     *lpString  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d66b0-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="d66b0-106">Parameters</span></span>  
 `RVA`  
 <span data-ttu-id="d66b0-107">[in] Wirtualny adres względny ciągu do zwrócenia.</span><span class="sxs-lookup"><span data-stu-id="d66b0-107">[in] The relative virtual address of the string to return.</span></span>  
  
 `lpString`  
 <span data-ttu-id="d66b0-108">[out] Zwracany ciąg.</span><span class="sxs-lookup"><span data-stu-id="d66b0-108">[out] The returned string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d66b0-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d66b0-109">Requirements</span></span>  
 <span data-ttu-id="d66b0-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d66b0-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d66b0-111">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="d66b0-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d66b0-112">**Biblioteka:** używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d66b0-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d66b0-113">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d66b0-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d66b0-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d66b0-114">See Also</span></span>  
 [<span data-ttu-id="d66b0-115">ICeeGen — interfejs</span><span class="sxs-lookup"><span data-stu-id="d66b0-115">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
