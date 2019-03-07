---
title: ICorDebugClass::GetToken — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugClass.GetToken
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugClass::GetToken
helpviewer_keywords:
- GetToken method, ICorDebugClass interface [.NET Framework debugging]
- ICorDebugClass::GetToken method [.NET Framework debugging]
ms.assetid: ee5c848a-eac4-4462-b07a-07ccd76a75df
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f7532c34dca070b07bd3124002eaf72a2f939238
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57493066"
---
# <a name="icordebugclassgettoken-method"></a><span data-ttu-id="f042a-102">ICorDebugClass::GetToken — Metoda</span><span class="sxs-lookup"><span data-stu-id="f042a-102">ICorDebugClass::GetToken Method</span></span>
<span data-ttu-id="f042a-103">Pobiera `TypeDef` token metadanych, który odwołuje się do definicji tej klasy.</span><span class="sxs-lookup"><span data-stu-id="f042a-103">Gets the `TypeDef` metadata token that references the definition of this class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f042a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f042a-104">Syntax</span></span>  
  
```  
HRESULT GetToken (  
    [out] mdTypeDef          *pTypeDef  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f042a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f042a-105">Parameters</span></span>  
 `pTypeDef`  
 <span data-ttu-id="f042a-106">[out] Wskaźnik do `mdTypeDef` token, który odwołuje się do definicji tej klasy.</span><span class="sxs-lookup"><span data-stu-id="f042a-106">[out] A pointer to an `mdTypeDef` token that references the definition of this class.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f042a-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f042a-107">Requirements</span></span>  
 <span data-ttu-id="f042a-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f042a-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f042a-109">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f042a-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f042a-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f042a-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f042a-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f042a-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f042a-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f042a-112">See also</span></span>
- [<span data-ttu-id="f042a-113">Interfejsy metadanych</span><span class="sxs-lookup"><span data-stu-id="f042a-113">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
