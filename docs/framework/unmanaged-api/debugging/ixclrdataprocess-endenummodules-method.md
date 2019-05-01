---
title: Metoda IXCLRDataProcess::EndEnumModules
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
ms.openlocfilehash: de30384b4c12c4fcac3eafe580484685f8a43fa4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61775430"
---
# <a name="ixclrdataprocessendenummodules-method"></a><span data-ttu-id="ef085-102">Metoda IXCLRDataProcess::EndEnumModules</span><span class="sxs-lookup"><span data-stu-id="ef085-102">IXCLRDataProcess::EndEnumModules Method</span></span>

<span data-ttu-id="ef085-103">Zwalnia zasoby używane przez Iteratory wewnętrzny używany podczas wyliczania modułu.</span><span class="sxs-lookup"><span data-stu-id="ef085-103">Releases the resources used by internal iterators used during module enumeration.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="ef085-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ef085-104">Syntax</span></span>

```cpp
HRESULT EndEnumModules(
    [in] CLRDATA_ENUM handle
);
```

## <a name="parameters"></a><span data-ttu-id="ef085-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ef085-105">Parameters</span></span>

`handle`\
<span data-ttu-id="ef085-106">[out] Dojścia wyliczania modułów.</span><span class="sxs-lookup"><span data-stu-id="ef085-106">[out] A handle for enumerating the modules.</span></span>

## <a name="remarks"></a><span data-ttu-id="ef085-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ef085-107">Remarks</span></span>

<span data-ttu-id="ef085-108">Podana metoda jest częścią `IXCLRDataProcess` interfejs i odnosi się do 26 gniazda tabeli metod wirtualnych.</span><span class="sxs-lookup"><span data-stu-id="ef085-108">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 26th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="ef085-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ef085-109">Requirements</span></span>

<span data-ttu-id="ef085-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ef085-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>
<span data-ttu-id="ef085-111">**Nagłówek:** Brak **biblioteki:** Brak **wersje programu .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="ef085-111">**Header:** None **Library:** None **.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="ef085-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ef085-112">See also</span></span>

- [<span data-ttu-id="ef085-113">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="ef085-113">Debugging</span></span>](index.md)
- [<span data-ttu-id="ef085-114">Interfejs IXCLRDataProcess</span><span class="sxs-lookup"><span data-stu-id="ef085-114">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
