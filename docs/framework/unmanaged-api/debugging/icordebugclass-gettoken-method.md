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
ms.openlocfilehash: 3433f5f69927afb501c2596571f138e3a69fabb6
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894125"
---
# <a name="icordebugclassgettoken-method"></a><span data-ttu-id="580ab-102">ICorDebugClass::GetToken — Metoda</span><span class="sxs-lookup"><span data-stu-id="580ab-102">ICorDebugClass::GetToken Method</span></span>
<span data-ttu-id="580ab-103">Pobiera token `TypeDef` metadanych odwołujący się do definicji tej klasy.</span><span class="sxs-lookup"><span data-stu-id="580ab-103">Gets the `TypeDef` metadata token that references the definition of this class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="580ab-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="580ab-104">Syntax</span></span>  
  
```cpp  
HRESULT GetToken (  
    [out] mdTypeDef          *pTypeDef  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="580ab-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="580ab-105">Parameters</span></span>  
 `pTypeDef`  
 <span data-ttu-id="580ab-106">określoną Wskaźnik do `mdTypeDef` tokenu, który odwołuje się do definicji tej klasy.</span><span class="sxs-lookup"><span data-stu-id="580ab-106">[out] A pointer to an `mdTypeDef` token that references the definition of this class.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="580ab-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="580ab-107">Requirements</span></span>  
 <span data-ttu-id="580ab-108">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="580ab-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="580ab-109">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="580ab-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="580ab-110">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="580ab-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="580ab-111">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="580ab-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="580ab-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="580ab-112">See also</span></span>

- [<span data-ttu-id="580ab-113">Interfejsy metadanych</span><span class="sxs-lookup"><span data-stu-id="580ab-113">Metadata Interfaces</span></span>](../metadata/metadata-interfaces.md)
