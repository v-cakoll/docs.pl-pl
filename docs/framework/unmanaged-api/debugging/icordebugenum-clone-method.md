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
ms.openlocfilehash: 965ce04b02a0eb1ca30aba065b3e372332e08b55
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67752291"
---
# <a name="icordebugenumclone-method"></a><span data-ttu-id="950c7-102">ICorDebugEnum::Clone — Metoda</span><span class="sxs-lookup"><span data-stu-id="950c7-102">ICorDebugEnum::Clone Method</span></span>
<span data-ttu-id="950c7-103">Tworzy kopię tego obiektu ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="950c7-103">Creates a copy of this ICorDebugEnum object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="950c7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="950c7-104">Syntax</span></span>  
  
```cpp  
HRESULT Clone (  
    [out] ICorDebugEnum **ppEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="950c7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="950c7-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="950c7-106">[out] Wskaźnik na adres `ICorDebugEnum` obiektu, który jest kopią tego `ICorDebugEnum` obiektu.</span><span class="sxs-lookup"><span data-stu-id="950c7-106">[out] A pointer to the address of an `ICorDebugEnum` object that is a copy of this `ICorDebugEnum` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="950c7-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="950c7-107">Requirements</span></span>  
 <span data-ttu-id="950c7-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="950c7-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="950c7-109">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="950c7-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="950c7-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="950c7-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="950c7-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="950c7-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
