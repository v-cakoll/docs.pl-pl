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
- GetVersion method, ICorDebugProcess2 interface [.NET Framework debugging]
- ICorDebugProcess2::GetVersion method [.NET Framework debugging]
ms.assetid: e11d5a75-61d9-4548-aedf-79c26079bd17
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 07f3be81431201a4bb6011ea9b8f973061d3d101
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57361242"
---
# <a name="icordebugprocess2getversion-method"></a><span data-ttu-id="fb4b3-102">ICorDebugProcess2::GetVersion — Metoda</span><span class="sxs-lookup"><span data-stu-id="fb4b3-102">ICorDebugProcess2::GetVersion Method</span></span>

<span data-ttu-id="fb4b3-103">Pobiera numer wersji środowisko uruchomieniowe języka wspólnego (CLR), który jest uruchomiony w ramach tego procesu.</span><span class="sxs-lookup"><span data-stu-id="fb4b3-103">Gets the version number of the common language runtime (CLR) that is running in this process.</span></span>

## <a name="syntax"></a><span data-ttu-id="fb4b3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fb4b3-104">Syntax</span></span>

```cpp
HRESULT GetVersion (
    [out] COR_VERSION     *version
);
```

## <a name="parameters"></a><span data-ttu-id="fb4b3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fb4b3-105">Parameters</span></span>

`version`\
<span data-ttu-id="fb4b3-106">[out] Wskaźnik do cor_version — struktura, która przechowuje numer wersji środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="fb4b3-106">[out] A pointer to a COR_VERSION structure that stores the version number of the runtime.</span></span>

## <a name="remarks"></a><span data-ttu-id="fb4b3-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fb4b3-107">Remarks</span></span>

<span data-ttu-id="fb4b3-108">`GetVersion` Metoda zwraca kod błędu, jeśli nie środowiska wykonawczego został załadowany w procesie.</span><span class="sxs-lookup"><span data-stu-id="fb4b3-108">The `GetVersion` method returns an error code if no runtime has been loaded in the process.</span></span>

## <a name="requirements"></a><span data-ttu-id="fb4b3-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fb4b3-109">Requirements</span></span>

<span data-ttu-id="fb4b3-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fb4b3-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="fb4b3-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fb4b3-111">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="fb4b3-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fb4b3-112">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="fb4b3-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fb4b3-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
