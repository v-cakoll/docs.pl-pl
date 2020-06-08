---
title: ICorDebugModule::GetMetaDataInterface — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetMetaDataInterface
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetMetaDataInterface
helpviewer_keywords:
- ICorDebugModule::GetMetaDatainterface method [.NET Framework debugging]
- GetMetaDatainterface method [.NET Framework debugging]
ms.assetid: 30d906f2-cf35-4fa9-9d4c-0c31b58c9f3a
topic_type:
- apiref
ms.openlocfilehash: f5d0dd7a99087b21a5f827e4dce0f6342ae7b25a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501771"
---
# <a name="icordebugmodulegetmetadatainterface-method"></a><span data-ttu-id="c527c-102">ICorDebugModule::GetMetaDataInterface — Metoda</span><span class="sxs-lookup"><span data-stu-id="c527c-102">ICorDebugModule::GetMetaDataInterface Method</span></span>
<span data-ttu-id="c527c-103">Pobiera obiekt interfejsu metadanych, którego można użyć do sprawdzenia metadanych dla modułu.</span><span class="sxs-lookup"><span data-stu-id="c527c-103">Gets a metadata interface object that can be used to examine the metadata for the module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c527c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c527c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMetaDataInterface (  
    [in] REFIID      riid,  
    [out] IUnknown **ppObj  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c527c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c527c-105">Parameters</span></span>  
 `riid`  
 <span data-ttu-id="c527c-106">podczas Identyfikator odwołania, który określa interfejs metadanych.</span><span class="sxs-lookup"><span data-stu-id="c527c-106">[in] The reference ID that specifies the metadata interface.</span></span>  
  
 `ppObj`  
 <span data-ttu-id="c527c-107">określoną Wskaźnik do adresu `T:IUnknown` obiektu, który jest jednym z [interfejsów metadanych](../metadata/metadata-interfaces.md).</span><span class="sxs-lookup"><span data-stu-id="c527c-107">[out] A pointer to the address of an `T:IUnknown` object that is one of the [metadata interfaces](../metadata/metadata-interfaces.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c527c-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c527c-108">Remarks</span></span>  
 <span data-ttu-id="c527c-109">Debuger może użyć `GetMetaDataInterface` metody, aby utworzyć kopię oryginalnych metadanych dla modułu, który musi wykonać w celu edytowania tego modułu.</span><span class="sxs-lookup"><span data-stu-id="c527c-109">The debugger can use the `GetMetaDataInterface` method to make a copy of the original metadata for a module, which it must do in order to edit that module.</span></span> <span data-ttu-id="c527c-110">Debuger wywołuje `GetMetaDataInterface` , aby uzyskać obiekt interfejsu [IMetaDataEmit](../metadata/imetadataemit-interface.md) dla modułu, a następnie wywołuje [IMetaDataEmit:: SaveToMemory —](../metadata/imetadataemit-savetomemory-method.md) , aby zapisać kopię metadanych modułu w pamięci.</span><span class="sxs-lookup"><span data-stu-id="c527c-110">The debugger calls `GetMetaDataInterface` to get an [IMetaDataEmit](../metadata/imetadataemit-interface.md) interface object for the module, then calls [IMetaDataEmit::SaveToMemory](../metadata/imetadataemit-savetomemory-method.md) to save a copy of the module's metadata to memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c527c-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c527c-111">Requirements</span></span>  
 <span data-ttu-id="c527c-112">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c527c-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c527c-113">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c527c-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c527c-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="c527c-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c527c-115">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c527c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c527c-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c527c-116">See also</span></span>

- [<span data-ttu-id="c527c-117">Metadane</span><span class="sxs-lookup"><span data-stu-id="c527c-117">Metadata</span></span>](../metadata/index.md)
