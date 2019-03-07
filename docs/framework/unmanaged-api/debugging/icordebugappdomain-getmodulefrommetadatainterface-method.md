---
title: ICorDebugAppDomain::GetModuleFromMetaDataInterface — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain.GetModuleFromMetaDataInterface
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::GetModuleFromMetaDataInterface
helpviewer_keywords:
- ICorDebugAppDomain::GetModuleFromMetaDatainterface method [.NET Framework debugging]
- GetModuleFromMetaDatainterface method [.NET Framework debugging]
ms.assetid: f35225b3-5dda-4d5a-913d-b3373e9ab81e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2eaa48dcc7dad2d66f1a60922c94193120b59b32
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57481359"
---
# <a name="icordebugappdomaingetmodulefrommetadatainterface-method"></a><span data-ttu-id="e15c4-102">ICorDebugAppDomain::GetModuleFromMetaDataInterface — Metoda</span><span class="sxs-lookup"><span data-stu-id="e15c4-102">ICorDebugAppDomain::GetModuleFromMetaDataInterface Method</span></span>
<span data-ttu-id="e15c4-103">Pobiera moduł, który odnosi się do interfejsu określonych metadanych.</span><span class="sxs-lookup"><span data-stu-id="e15c4-103">Gets the module that corresponds to the given metadata interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e15c4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e15c4-104">Syntax</span></span>  
  
```  
HRESULT GetModuleFromMetaDataInterface (  
    [in] IUnknown           *pIMetaData,  
    [out] ICorDebugModule  **ppModule  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e15c4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e15c4-105">Parameters</span></span>  
 `pIMetaData`  
 <span data-ttu-id="e15c4-106">[in] Wskaźnik do obiektu, który jest jednym z [interfejsy metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md).</span><span class="sxs-lookup"><span data-stu-id="e15c4-106">[in] A pointer to an object that is one of the [Metadata interfaces](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md).</span></span>  
  
 `ppModule`  
 <span data-ttu-id="e15c4-107">[out] Wskaźnik na adres obiektu ICorDebugModule, który reprezentuje Moduł odpowiadający interfejsowi określonych metadanych.</span><span class="sxs-lookup"><span data-stu-id="e15c4-107">[out] A pointer to the address of an ICorDebugModule object that represents the module corresponding to the given metadata interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e15c4-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e15c4-108">Requirements</span></span>  
 <span data-ttu-id="e15c4-109">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e15c4-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e15c4-110">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e15c4-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e15c4-111">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e15c4-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e15c4-112">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e15c4-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
