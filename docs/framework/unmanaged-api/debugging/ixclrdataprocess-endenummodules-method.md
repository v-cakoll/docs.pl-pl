---
title: 'IXCLRDataProcess:: EndEnumModules, Metoda'
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess::EndEnumModules Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::EndEnumModules Method
helpviewer.keywords:
- IXCLRDataProcess::EndEnumModules Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 9a7a23e53f5c2bc7d643046830cf335fec780f11
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420841"
---
# <a name="ixclrdataprocessendenummodules-method"></a><span data-ttu-id="32b0f-102">IXCLRDataProcess:: EndEnumModules, Metoda</span><span class="sxs-lookup"><span data-stu-id="32b0f-102">IXCLRDataProcess::EndEnumModules Method</span></span>

<span data-ttu-id="32b0f-103">Zwalnia zasoby używane przez Iteratory wewnętrzne używane podczas wyliczania modułu.</span><span class="sxs-lookup"><span data-stu-id="32b0f-103">Releases the resources used by internal iterators used during module enumeration.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="32b0f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="32b0f-104">Syntax</span></span>

```cpp
HRESULT EndEnumModules(
    [in] CLRDATA_ENUM handle
);
```

## <a name="parameters"></a><span data-ttu-id="32b0f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="32b0f-105">Parameters</span></span>

`handle`\
<span data-ttu-id="32b0f-106">określoną Dojście do wyliczania modułów.</span><span class="sxs-lookup"><span data-stu-id="32b0f-106">[out] A handle for enumerating the modules.</span></span>

## <a name="remarks"></a><span data-ttu-id="32b0f-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="32b0f-107">Remarks</span></span>

<span data-ttu-id="32b0f-108">Podana metoda jest częścią `IXCLRDataProcess` interfejsu i odpowiada 26emu miejscu tabeli metody wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="32b0f-108">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 26th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="32b0f-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="32b0f-109">Requirements</span></span>

<span data-ttu-id="32b0f-110">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="32b0f-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>
<span data-ttu-id="32b0f-111">**Nagłówek:** Brak **biblioteki:** brak **.NET Framework wersje:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="32b0f-111">**Header:** None **Library:** None **.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="32b0f-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="32b0f-112">See also</span></span>

- [<span data-ttu-id="32b0f-113">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="32b0f-113">Debugging</span></span>](index.md)
- [<span data-ttu-id="32b0f-114">IXCLRDataProcess, interfejs</span><span class="sxs-lookup"><span data-stu-id="32b0f-114">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
