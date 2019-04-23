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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 37710fbb7acc50b80d7acebe4194b019c0b64660
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59102599"
---
# <a name="icordebugmodulegetmetadatainterface-method"></a><span data-ttu-id="1ce77-102">ICorDebugModule::GetMetaDataInterface — Metoda</span><span class="sxs-lookup"><span data-stu-id="1ce77-102">ICorDebugModule::GetMetaDataInterface Method</span></span>
<span data-ttu-id="1ce77-103">Pobiera obiekt interfejsu metadanych, który może służyć do badać metadane dla modułu.</span><span class="sxs-lookup"><span data-stu-id="1ce77-103">Gets a metadata interface object that can be used to examine the metadata for the module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ce77-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1ce77-104">Syntax</span></span>  
  
```  
HRESULT GetMetaDataInterface (  
    [in] REFIID      riid,  
    [out] IUnknown **ppObj  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1ce77-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1ce77-105">Parameters</span></span>  
 `riid`  
 <span data-ttu-id="1ce77-106">[in] Identyfikator odwołania, który określa interfejs metadanych.</span><span class="sxs-lookup"><span data-stu-id="1ce77-106">[in] The reference ID that specifies the metadata interface.</span></span>  
  
 `ppObj`  
 <span data-ttu-id="1ce77-107">[out] Wskaźnik na adres `T:IUnknown` obiekt, który jest jednym z [interfejsy metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md).</span><span class="sxs-lookup"><span data-stu-id="1ce77-107">[out] A pointer to the address of an `T:IUnknown` object that is one of the [metadata interfaces](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1ce77-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1ce77-108">Remarks</span></span>  
 <span data-ttu-id="1ce77-109">Można użyć debugera `GetMetaDataInterface` metodę, aby utworzyć kopię odpowiednich oryginalnych metadanych dla modułu, który należy wykonać w celu edytowania tego modułu.</span><span class="sxs-lookup"><span data-stu-id="1ce77-109">The debugger can use the `GetMetaDataInterface` method to make a copy of the original metadata for a module, which it must do in order to edit that module.</span></span> <span data-ttu-id="1ce77-110">Wywołuje debugera `GetMetaDataInterface` można pobrać [IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) obiektu interfejsu modułu, następnie wywołuje [IMetaDataEmit::SaveToMemory](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetomemory-method.md) można zapisać kopię modułu metadanych w pamięci.</span><span class="sxs-lookup"><span data-stu-id="1ce77-110">The debugger calls `GetMetaDataInterface` to get an [IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) interface object for the module, then calls [IMetaDataEmit::SaveToMemory](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetomemory-method.md) to save a copy of the module's metadata to memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1ce77-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1ce77-111">Requirements</span></span>  
 <span data-ttu-id="1ce77-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1ce77-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1ce77-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1ce77-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1ce77-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1ce77-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1ce77-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1ce77-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ce77-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1ce77-116">See also</span></span>

- [<span data-ttu-id="1ce77-117">Metadane</span><span class="sxs-lookup"><span data-stu-id="1ce77-117">Metadata</span></span>](../../../../docs/framework/unmanaged-api/metadata/index.md)
