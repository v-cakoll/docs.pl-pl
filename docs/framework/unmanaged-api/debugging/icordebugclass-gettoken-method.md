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
ms.openlocfilehash: d6dc245a53c9ec7cbe56e20313abc4269e33f45c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54582321"
---
# <a name="icordebugclassgettoken-method"></a><span data-ttu-id="94b00-102">ICorDebugClass::GetToken — Metoda</span><span class="sxs-lookup"><span data-stu-id="94b00-102">ICorDebugClass::GetToken Method</span></span>
<span data-ttu-id="94b00-103">Pobiera `TypeDef` token metadanych, który odwołuje się do definicji tej klasy.</span><span class="sxs-lookup"><span data-stu-id="94b00-103">Gets the `TypeDef` metadata token that references the definition of this class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94b00-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="94b00-104">Syntax</span></span>  
  
```  
HRESULT GetToken (  
    [out] mdTypeDef          *pTypeDef  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="94b00-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="94b00-105">Parameters</span></span>  
 `pTypeDef`  
 <span data-ttu-id="94b00-106">[out] Wskaźnik do `mdTypeDef` token, który odwołuje się do definicji tej klasy.</span><span class="sxs-lookup"><span data-stu-id="94b00-106">[out] A pointer to an `mdTypeDef` token that references the definition of this class.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="94b00-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="94b00-107">Requirements</span></span>  
 <span data-ttu-id="94b00-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="94b00-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="94b00-109">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="94b00-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="94b00-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="94b00-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="94b00-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="94b00-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94b00-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="94b00-112">See also</span></span>
- [<span data-ttu-id="94b00-113">Interfejsy metadanych</span><span class="sxs-lookup"><span data-stu-id="94b00-113">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
