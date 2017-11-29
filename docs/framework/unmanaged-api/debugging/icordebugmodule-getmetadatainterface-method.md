---
title: "ICorDebugModule::GetMetaDataInterface — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugModule.GetMetaDataInterface
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugModule::GetMetaDataInterface
helpviewer_keywords:
- ICorDebugModule::GetMetaDatainterface method [.NET Framework debugging]
- GetMetaDatainterface method [.NET Framework debugging]
ms.assetid: 30d906f2-cf35-4fa9-9d4c-0c31b58c9f3a
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f4b1944c68db0cbdd8eb49e10433defc953e4494
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugmodulegetmetadatainterface-method"></a><span data-ttu-id="1ebc6-102">ICorDebugModule::GetMetaDataInterface — Metoda</span><span class="sxs-lookup"><span data-stu-id="1ebc6-102">ICorDebugModule::GetMetaDataInterface Method</span></span>
<span data-ttu-id="1ebc6-103">Pobiera obiekt interfejsu metadanych, który może służyć do sprawdzenia metadane dla modułu.</span><span class="sxs-lookup"><span data-stu-id="1ebc6-103">Gets a metadata interface object that can be used to examine the metadata for the module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ebc6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1ebc6-104">Syntax</span></span>  
  
```  
HRESULT GetMetaDataInterface (  
    [in] REFIID      riid,  
    [out] IUnknown **ppObj  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1ebc6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1ebc6-105">Parameters</span></span>  
 `riid`  
 <span data-ttu-id="1ebc6-106">[in] Identyfikator odwołania, który określa interfejs metadanych.</span><span class="sxs-lookup"><span data-stu-id="1ebc6-106">[in] The reference ID that specifies the metadata interface.</span></span>  
  
 `ppObj`  
 <span data-ttu-id="1ebc6-107">[out] Wskaźnik do adresu `T:IUnknown` obiekt, który jest jednym z [interfejsy metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md).</span><span class="sxs-lookup"><span data-stu-id="1ebc6-107">[out] A pointer to the address of an `T:IUnknown` object that is one of the [metadata interfaces](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1ebc6-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1ebc6-108">Remarks</span></span>  
 <span data-ttu-id="1ebc6-109">Można używać debugera `GetMetaDataInterface` metodę, aby utworzyć kopię oryginalnej metadane dla modułu, które należy wykonać, aby edytować ten moduł.</span><span class="sxs-lookup"><span data-stu-id="1ebc6-109">The debugger can use the `GetMetaDataInterface` method to make a copy of the original metadata for a module, which it must do in order to edit that module.</span></span> <span data-ttu-id="1ebc6-110">Wywołań debugera `GetMetaDataInterface` uzyskanie [IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) obiektu interfejs dla modułu, następnie wywołuje [IMetaDataEmit::SaveToMemory](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetomemory-method.md) można zapisać kopię modułu metadanych w pamięci.</span><span class="sxs-lookup"><span data-stu-id="1ebc6-110">The debugger calls `GetMetaDataInterface` to get an [IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) interface object for the module, then calls [IMetaDataEmit::SaveToMemory](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetomemory-method.md) to save a copy of the module's metadata to memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1ebc6-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1ebc6-111">Requirements</span></span>  
 <span data-ttu-id="1ebc6-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1ebc6-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1ebc6-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1ebc6-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1ebc6-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1ebc6-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1ebc6-115">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1ebc6-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ebc6-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1ebc6-116">See Also</span></span>  
 [<span data-ttu-id="1ebc6-117">Metadane</span><span class="sxs-lookup"><span data-stu-id="1ebc6-117">Metadata</span></span>](../../../../docs/framework/unmanaged-api/metadata/index.md)
