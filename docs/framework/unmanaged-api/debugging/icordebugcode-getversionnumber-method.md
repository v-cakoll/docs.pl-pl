---
title: "ICorDebugCode::GetVersionNumber — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugCode.GetVersionNumber
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugCode::GetVersionNumber
helpviewer_keywords:
- GetVersionNumber method, ICorDebugCode interface [.NET Framework debugging]
- ICorDebugCode::GetVersionNumber method [.NET Framework debugging]
ms.assetid: c8e02518-679f-4e9f-8a28-ba4a89a3876f
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: cd467f047131bbb078c72db9daca2cbc5a87a7be
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugcodegetversionnumber-method"></a><span data-ttu-id="6b6dc-102">ICorDebugCode::GetVersionNumber — Metoda</span><span class="sxs-lookup"><span data-stu-id="6b6dc-102">ICorDebugCode::GetVersionNumber Method</span></span>
<span data-ttu-id="6b6dc-103">Pobiera numer jedynki, który identyfikuje wersję kodu, który reprezentuje to "ICorDebugCode".</span><span class="sxs-lookup"><span data-stu-id="6b6dc-103">Gets the one-based number that identifies the version of the code that this "ICorDebugCode" represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b6dc-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6b6dc-104">Syntax</span></span>  
  
```  
HRESULT GetVersionNumber (  
    [out] ULONG32    *nVersion  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6b6dc-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6b6dc-105">Parameters</span></span>  
 `nVersion`  
 <span data-ttu-id="6b6dc-106">[out] Wskaźnik do numer wersji kodu.</span><span class="sxs-lookup"><span data-stu-id="6b6dc-106">[out] A pointer to the version number of the code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6b6dc-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6b6dc-107">Remarks</span></span>  
 <span data-ttu-id="6b6dc-108">Numer wersji jest zwiększany zawsze, gdy operacji edit-and-continue (EnC) odbywa się na kodzie.</span><span class="sxs-lookup"><span data-stu-id="6b6dc-108">The version number is incremented each time an edit-and-continue (EnC) operation is performed on the code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6b6dc-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6b6dc-109">Requirements</span></span>  
 <span data-ttu-id="6b6dc-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6b6dc-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6b6dc-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6b6dc-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6b6dc-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6b6dc-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6b6dc-113">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6b6dc-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b6dc-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6b6dc-114">See Also</span></span>  
 
