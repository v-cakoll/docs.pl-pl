---
title: ICorDebugCode::GetSize — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugCode.GetSize
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::GetSize
helpviewer_keywords:
- GetSize method, ICorDebugCode interface [.NET Framework debugging]
- ICorDebugCode::GetSize method [.NET Framework debugging]
ms.assetid: 115bc6de-f5e2-4e8e-bb38-c7cf54045434
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 25349f7c8274b818df2cd1bc5d67856e31efecc4
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395546"
---
# <a name="icordebugcodegetsize-method"></a><span data-ttu-id="f7c89-102">ICorDebugCode::GetSize — Metoda</span><span class="sxs-lookup"><span data-stu-id="f7c89-102">ICorDebugCode::GetSize Method</span></span>

<span data-ttu-id="f7c89-103">Pobiera rozmiar (w bajtach) kodu binarnego reprezentowanego przez ten "ICorDebugCode".</span><span class="sxs-lookup"><span data-stu-id="f7c89-103">Gets the size, in bytes, of the binary code represented by this "ICorDebugCode".</span></span>

## <a name="syntax"></a><span data-ttu-id="f7c89-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f7c89-104">Syntax</span></span>

```cpp
HRESULT GetSize (
    [out] ULONG32    *pcBytes
);
```

## <a name="parameters"></a><span data-ttu-id="f7c89-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f7c89-105">Parameters</span></span>

`pcBytes`  
<span data-ttu-id="f7c89-106">określoną Wskaźnik do rozmiaru, w bajtach, kodu binarnego, który reprezentuje ten obiekt `ICorDebugCode`.</span><span class="sxs-lookup"><span data-stu-id="f7c89-106">[out] A pointer to the size, in bytes, of the binary code that this `ICorDebugCode` object represents.</span></span>

## <a name="requirements"></a><span data-ttu-id="f7c89-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f7c89-107">Requirements</span></span>

<span data-ttu-id="f7c89-108">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f7c89-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="f7c89-109">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f7c89-109">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="f7c89-110">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="f7c89-110">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="f7c89-111">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f7c89-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
