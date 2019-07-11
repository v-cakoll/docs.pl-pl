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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 30097ff0cd92253897a366a5a18f305eddb06b5b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67763518"
---
# <a name="icordebugmodulegettoken-method"></a><span data-ttu-id="f1517-102">ICorDebugModule::GetToken — Metoda</span><span class="sxs-lookup"><span data-stu-id="f1517-102">ICorDebugModule::GetToken Method</span></span>
<span data-ttu-id="f1517-103">Pobiera token dla wpisu tabeli dla tego modułu.</span><span class="sxs-lookup"><span data-stu-id="f1517-103">Gets the token for the table entry for this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1517-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f1517-104">Syntax</span></span>  
  
```cpp  
HRESULT GetToken(  
    [out] mdModule *pToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f1517-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f1517-105">Parameters</span></span>  
 `pToken`  
 <span data-ttu-id="f1517-106">[out] Wskaźnik do `mdModule` token, który odwołuje się do metadanych modułu.</span><span class="sxs-lookup"><span data-stu-id="f1517-106">[out] A pointer to the `mdModule` token that references the module's metadata.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f1517-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f1517-107">Remarks</span></span>  
 <span data-ttu-id="f1517-108">Token może być przekazywany do [imetadataimport —](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md), [imetadataimport2 —](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md), i [imetadataassemblyimport —](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interfejsy Importowanie metadanych.</span><span class="sxs-lookup"><span data-stu-id="f1517-108">The token can be passed to the [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md), [IMetaDataImport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md), and [IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) metadata import interfaces.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f1517-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f1517-109">Requirements</span></span>  
 <span data-ttu-id="f1517-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f1517-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f1517-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f1517-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f1517-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f1517-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f1517-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f1517-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1517-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f1517-114">See also</span></span>

- [<span data-ttu-id="f1517-115">Metadane</span><span class="sxs-lookup"><span data-stu-id="f1517-115">Metadata</span></span>](../../../../docs/framework/unmanaged-api/metadata/index.md)
