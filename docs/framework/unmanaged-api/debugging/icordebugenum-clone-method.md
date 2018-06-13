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
ms.openlocfilehash: da16a22c71c1fac1932f74a9af18fbc30eb326f4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33410835"
---
# <a name="icordebugenumclone-method"></a><span data-ttu-id="d4d8b-102">ICorDebugEnum::Clone — Metoda</span><span class="sxs-lookup"><span data-stu-id="d4d8b-102">ICorDebugEnum::Clone Method</span></span>
<span data-ttu-id="d4d8b-103">Tworzy kopię tego obiektu ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="d4d8b-103">Creates a copy of this ICorDebugEnum object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4d8b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d4d8b-104">Syntax</span></span>  
  
```  
HRESULT Clone (  
    [out] ICorDebugEnum **ppEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d4d8b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d4d8b-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="d4d8b-106">[out] Wskaźnik do adresu `ICorDebugEnum` obiektu, który jest kopią tego `ICorDebugEnum` obiektu.</span><span class="sxs-lookup"><span data-stu-id="d4d8b-106">[out] A pointer to the address of an `ICorDebugEnum` object that is a copy of this `ICorDebugEnum` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d4d8b-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d4d8b-107">Requirements</span></span>  
 <span data-ttu-id="d4d8b-108">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d4d8b-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d4d8b-109">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d4d8b-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d4d8b-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d4d8b-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d4d8b-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d4d8b-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
