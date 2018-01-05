---
title: "ICorDebugClass::GetToken — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugClass.GetToken
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugClass::GetToken
helpviewer_keywords:
- GetToken method, ICorDebugClass interface [.NET Framework debugging]
- ICorDebugClass::GetToken method [.NET Framework debugging]
ms.assetid: ee5c848a-eac4-4462-b07a-07ccd76a75df
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 408575c53feb81a2b273bd1064e2d3eaa37c4fb8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugclassgettoken-method"></a><span data-ttu-id="68e30-102">ICorDebugClass::GetToken — Metoda</span><span class="sxs-lookup"><span data-stu-id="68e30-102">ICorDebugClass::GetToken Method</span></span>
<span data-ttu-id="68e30-103">Pobiera `TypeDef` token metadanych, który odwołuje się do definicji tej klasy.</span><span class="sxs-lookup"><span data-stu-id="68e30-103">Gets the `TypeDef` metadata token that references the definition of this class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68e30-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="68e30-104">Syntax</span></span>  
  
```  
HRESULT GetToken (  
    [out] mdTypeDef          *pTypeDef  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="68e30-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="68e30-105">Parameters</span></span>  
 `pTypeDef`  
 <span data-ttu-id="68e30-106">[out] Wskaźnik do `mdTypeDef` token, który odwołuje się do definicji tej klasy.</span><span class="sxs-lookup"><span data-stu-id="68e30-106">[out] A pointer to an `mdTypeDef` token that references the definition of this class.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="68e30-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="68e30-107">Requirements</span></span>  
 <span data-ttu-id="68e30-108">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="68e30-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="68e30-109">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="68e30-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="68e30-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="68e30-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="68e30-111">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="68e30-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68e30-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="68e30-112">See Also</span></span>  
 [<span data-ttu-id="68e30-113">Interfejsy metadanych</span><span class="sxs-lookup"><span data-stu-id="68e30-113">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
