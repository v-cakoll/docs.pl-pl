---
title: ICorDebugProcess2::GetVersion — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2.GetVersion
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2::GetVersion
helpviewer_keywords:
- GetVersion method, ICorDebugProcess2 nterface [.NET Framework debugging]
- ICorDebugProcess2::GetVersion method [.NET Framework debugging]
ms.assetid: e11d5a75-61d9-4548-aedf-79c26079bd17
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c1e1f850e85099a466c497a8fcc822bce9510f69
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33416383"
---
# <a name="icordebugprocess2getversion-method"></a><span data-ttu-id="363a1-102">ICorDebugProcess2::GetVersion — Metoda</span><span class="sxs-lookup"><span data-stu-id="363a1-102">ICorDebugProcess2::GetVersion Method</span></span>
<span data-ttu-id="363a1-103">Pobiera numer wersji środowisko uruchomieniowe języka wspólnego (CLR) działającej w tym procesie.</span><span class="sxs-lookup"><span data-stu-id="363a1-103">Gets the version number of the common language runtime (CLR) that is running in this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="363a1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="363a1-104">Syntax</span></span>  
  
```  
HRESULT GetVersion (  
    [out] COR_VERSION     *version  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="363a1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="363a1-105">Parameters</span></span>  
 `version`  
 <span data-ttu-id="363a1-106">[out] Wskaźnik do cor_version — struktura, która przechowuje numer wersji środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="363a1-106">[out] A pointer to a COR_VERSION structure that stores the version number of the runtime.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="363a1-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="363a1-107">Remarks</span></span>  
 <span data-ttu-id="363a1-108">`GetVersion` — Metoda zwraca kod błędu, jeśli nie środowiska wykonawczego został załadowany w procesie.</span><span class="sxs-lookup"><span data-stu-id="363a1-108">The `GetVersion` method returns an error code if no runtime has been loaded in the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="363a1-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="363a1-109">Requirements</span></span>  
 <span data-ttu-id="363a1-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="363a1-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="363a1-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="363a1-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="363a1-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="363a1-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="363a1-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="363a1-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
