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
ms.openlocfilehash: 1cf4d82200709971201da60d06d0cb929641a104
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501888"
---
# <a name="icordebugmodulegettoken-method"></a><span data-ttu-id="fdf4f-102">ICorDebugModule::GetToken — Metoda</span><span class="sxs-lookup"><span data-stu-id="fdf4f-102">ICorDebugModule::GetToken Method</span></span>
<span data-ttu-id="fdf4f-103">Pobiera token dla wpisu tabeli dla tego modułu.</span><span class="sxs-lookup"><span data-stu-id="fdf4f-103">Gets the token for the table entry for this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fdf4f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fdf4f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetToken(  
    [out] mdModule *pToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fdf4f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fdf4f-105">Parameters</span></span>  
 `pToken`  
 <span data-ttu-id="fdf4f-106">określoną Wskaźnik do `mdModule` tokenu, który odwołuje się do metadanych modułu.</span><span class="sxs-lookup"><span data-stu-id="fdf4f-106">[out] A pointer to the `mdModule` token that references the module's metadata.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fdf4f-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fdf4f-107">Remarks</span></span>  
 <span data-ttu-id="fdf4f-108">Token może być przesłany do interfejsów importu metadanych [IMetaDataImport](../metadata/imetadataimport-interface.md), [IMetaDataImport2](../metadata/imetadataimport2-interface.md)i [IMetaDataAssemblyImport](../metadata/imetadataassemblyimport-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="fdf4f-108">The token can be passed to the [IMetaDataImport](../metadata/imetadataimport-interface.md), [IMetaDataImport2](../metadata/imetadataimport2-interface.md), and [IMetaDataAssemblyImport](../metadata/imetadataassemblyimport-interface.md) metadata import interfaces.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fdf4f-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fdf4f-109">Requirements</span></span>  
 <span data-ttu-id="fdf4f-110">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fdf4f-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fdf4f-111">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="fdf4f-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fdf4f-112">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="fdf4f-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fdf4f-113">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fdf4f-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fdf4f-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fdf4f-114">See also</span></span>

- [<span data-ttu-id="fdf4f-115">Metadane</span><span class="sxs-lookup"><span data-stu-id="fdf4f-115">Metadata</span></span>](../metadata/index.md)
