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
ms.openlocfilehash: 9f0fda803ba3a1ce35017d85e84b3bf6f567eda0
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976380"
---
# <a name="icordebugenumclone-method"></a><span data-ttu-id="5277c-102">ICorDebugEnum::Clone — Metoda</span><span class="sxs-lookup"><span data-stu-id="5277c-102">ICorDebugEnum::Clone Method</span></span>
<span data-ttu-id="5277c-103">Tworzy kopię tego obiektu ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="5277c-103">Creates a copy of this ICorDebugEnum object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5277c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5277c-104">Syntax</span></span>  
  
```cpp  
HRESULT Clone (  
    [out] ICorDebugEnum **ppEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5277c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5277c-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="5277c-106">określoną Wskaźnik do adresu `ICorDebugEnum` obiektu, który jest kopią tego `ICorDebugEnum` obiektu.</span><span class="sxs-lookup"><span data-stu-id="5277c-106">[out] A pointer to the address of an `ICorDebugEnum` object that is a copy of this `ICorDebugEnum` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5277c-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5277c-107">Requirements</span></span>  
 <span data-ttu-id="5277c-108">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5277c-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5277c-109">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="5277c-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5277c-110">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="5277c-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5277c-111">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5277c-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
