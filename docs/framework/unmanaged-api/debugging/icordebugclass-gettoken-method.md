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
ms.openlocfilehash: 6964c931307a40f384ad8a8e355cab0aad575ec6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125772"
---
# <a name="icordebugclassgettoken-method"></a><span data-ttu-id="7136d-102">ICorDebugClass::GetToken — Metoda</span><span class="sxs-lookup"><span data-stu-id="7136d-102">ICorDebugClass::GetToken Method</span></span>
<span data-ttu-id="7136d-103">Pobiera token metadanych `TypeDef`, który odwołuje się do definicji tej klasy.</span><span class="sxs-lookup"><span data-stu-id="7136d-103">Gets the `TypeDef` metadata token that references the definition of this class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7136d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7136d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetToken (  
    [out] mdTypeDef          *pTypeDef  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7136d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7136d-105">Parameters</span></span>  
 `pTypeDef`  
 <span data-ttu-id="7136d-106">określoną Wskaźnik do tokenu `mdTypeDef`, który odwołuje się do definicji tej klasy.</span><span class="sxs-lookup"><span data-stu-id="7136d-106">[out] A pointer to an `mdTypeDef` token that references the definition of this class.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7136d-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7136d-107">Requirements</span></span>  
 <span data-ttu-id="7136d-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7136d-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7136d-109">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="7136d-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7136d-110">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="7136d-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7136d-111">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7136d-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7136d-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7136d-112">See also</span></span>

- [<span data-ttu-id="7136d-113">Interfejsy metadanych</span><span class="sxs-lookup"><span data-stu-id="7136d-113">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
