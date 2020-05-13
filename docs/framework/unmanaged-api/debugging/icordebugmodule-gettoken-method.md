---
title: ICorDebugModule::GetToken — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetToken
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetToken
helpviewer_keywords:
- ICorDebugModule::GetToken method [.NET Framework debugging]
- GetToken method, ICorDebugModule interface [.NET Framework debugging]
ms.assetid: f759f87a-18ae-4c1a-8300-29b803432d0a
topic_type:
- apiref
ms.openlocfilehash: a6aff37a480460bfed7064d59b4c5276daf3207c
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212506"
---
# <a name="icordebugmodulegettoken-method"></a><span data-ttu-id="a2e2b-102">ICorDebugModule::GetToken — Metoda</span><span class="sxs-lookup"><span data-stu-id="a2e2b-102">ICorDebugModule::GetToken Method</span></span>
<span data-ttu-id="a2e2b-103">Pobiera token dla wpisu tabeli dla tego modułu.</span><span class="sxs-lookup"><span data-stu-id="a2e2b-103">Gets the token for the table entry for this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2e2b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a2e2b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetToken(  
    [out] mdModule *pToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a2e2b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a2e2b-105">Parameters</span></span>  
 `pToken`  
 <span data-ttu-id="a2e2b-106">określoną Wskaźnik do `mdModule` tokenu, który odwołuje się do metadanych modułu.</span><span class="sxs-lookup"><span data-stu-id="a2e2b-106">[out] A pointer to the `mdModule` token that references the module's metadata.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a2e2b-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a2e2b-107">Remarks</span></span>  
 <span data-ttu-id="a2e2b-108">Token może być przesłany do interfejsów importu metadanych [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md), [IMetaDataImport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)i [IMetaDataAssemblyImport](../metadata/imetadataassemblyimport-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="a2e2b-108">The token can be passed to the [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md), [IMetaDataImport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md), and [IMetaDataAssemblyImport](../metadata/imetadataassemblyimport-interface.md) metadata import interfaces.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a2e2b-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a2e2b-109">Requirements</span></span>  
 <span data-ttu-id="a2e2b-110">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a2e2b-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a2e2b-111">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a2e2b-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a2e2b-112">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="a2e2b-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a2e2b-113">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a2e2b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2e2b-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a2e2b-114">See also</span></span>

- [<span data-ttu-id="a2e2b-115">Metadane</span><span class="sxs-lookup"><span data-stu-id="a2e2b-115">Metadata</span></span>](../metadata/index.md)
