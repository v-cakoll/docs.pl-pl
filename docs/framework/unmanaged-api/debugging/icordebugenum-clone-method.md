---
title: ICorDebugEnum::Clone — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugEnum.Clone
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEnum::Clone
helpviewer_keywords:
- Clone method, ICorDebugEnum interface [.NET Framework debugging]
- ICorDebugEnum::Clone method [.NET Framework debugging]
ms.assetid: 57eefaf3-75cf-4496-bc94-88c0706861b7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5d1226f64df379b5c40304221e9e66eebcdb17b4
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57479240"
---
# <a name="icordebugenumclone-method"></a><span data-ttu-id="bab25-102">ICorDebugEnum::Clone — Metoda</span><span class="sxs-lookup"><span data-stu-id="bab25-102">ICorDebugEnum::Clone Method</span></span>
<span data-ttu-id="bab25-103">Tworzy kopię tego obiektu ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="bab25-103">Creates a copy of this ICorDebugEnum object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bab25-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="bab25-104">Syntax</span></span>  
  
```  
HRESULT Clone (  
    [out] ICorDebugEnum **ppEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bab25-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bab25-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="bab25-106">[out] Wskaźnik na adres `ICorDebugEnum` obiektu, który jest kopią tego `ICorDebugEnum` obiektu.</span><span class="sxs-lookup"><span data-stu-id="bab25-106">[out] A pointer to the address of an `ICorDebugEnum` object that is a copy of this `ICorDebugEnum` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bab25-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bab25-107">Requirements</span></span>  
 <span data-ttu-id="bab25-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bab25-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bab25-109">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bab25-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bab25-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bab25-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bab25-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bab25-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
