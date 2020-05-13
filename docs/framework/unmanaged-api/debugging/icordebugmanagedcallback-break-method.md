---
title: ICorDebugManagedCallback::Break — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.Break
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::Break
helpviewer_keywords:
- Break method [.NET Framework debugging]
- ICorDebugManagedCallback::Break method [.NET Framework debugging]
ms.assetid: 7d78a301-82b3-43b2-9d65-3cda3285ae97
topic_type:
- apiref
ms.openlocfilehash: f70a88df00d15729a6bde06b49417b6439f7c0ec
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212467"
---
# <a name="icordebugmanagedcallbackbreak-method"></a><span data-ttu-id="aff72-102">ICorDebugManagedCallback::Break — Metoda</span><span class="sxs-lookup"><span data-stu-id="aff72-102">ICorDebugManagedCallback::Break Method</span></span>

<span data-ttu-id="aff72-103">Powiadamia debuger, gdy <xref:System.Reflection.Emit.OpCodes.Break> zostanie wykonana instrukcja w strumieniu kodu.</span><span class="sxs-lookup"><span data-stu-id="aff72-103">Notifies the debugger when a <xref:System.Reflection.Emit.OpCodes.Break> instruction in the code stream is executed.</span></span>

## <a name="syntax"></a><span data-ttu-id="aff72-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="aff72-104">Syntax</span></span>

```cpp
HRESULT Break (
    [in] ICorDebugAppDomain *pAppDomain,
    [in] ICorDebugThread    *thread
);
```

## <a name="parameters"></a><span data-ttu-id="aff72-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="aff72-105">Parameters</span></span>

`pAppDomain`\
<span data-ttu-id="aff72-106">podczas Wskaźnik do obiektu ICorDebugAppDomain, który reprezentuje domenę aplikacji, która zawiera instrukcję Break.</span><span class="sxs-lookup"><span data-stu-id="aff72-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contains the break instruction.</span></span>

`thread`\
<span data-ttu-id="aff72-107">podczas Wskaźnik do obiektu ICorDebugThread, który reprezentuje wątek, który zawiera instrukcję Break.</span><span class="sxs-lookup"><span data-stu-id="aff72-107">[in] A pointer to an ICorDebugThread object that represents the thread that contains the break instruction.</span></span>

## <a name="requirements"></a><span data-ttu-id="aff72-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="aff72-108">Requirements</span></span>

<span data-ttu-id="aff72-109">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aff72-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="aff72-110">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="aff72-110">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="aff72-111">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="aff72-111">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="aff72-112">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aff72-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="aff72-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="aff72-113">See also</span></span>

- [<span data-ttu-id="aff72-114">ICorDebugManagedCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="aff72-114">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
