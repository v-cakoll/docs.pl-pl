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
ms.openlocfilehash: 50ad55674360d7b880af3ddf701cf17005f30ce7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54722741"
---
# <a name="ixclrdataprocessendenummodules-method"></a><span data-ttu-id="448d1-102">Metoda IXCLRDataProcess::EndEnumModules</span><span class="sxs-lookup"><span data-stu-id="448d1-102">IXCLRDataProcess::EndEnumModules Method</span></span>

<span data-ttu-id="448d1-103">Zwalnia zasoby używane przez Iteratory wewnętrzny używany podczas wyliczania modułu.</span><span class="sxs-lookup"><span data-stu-id="448d1-103">Releases the resources used by internal iterators used during module enumeration.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="448d1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="448d1-104">Syntax</span></span>
```
HRESULT EndEnumModules(
    [in] CLRDATA_ENUM handle
);
```

### <a name="parameters"></a><span data-ttu-id="448d1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="448d1-105">Parameters</span></span>
<span data-ttu-id="448d1-106">`handle` [out] Dojścia wyliczania modułów.</span><span class="sxs-lookup"><span data-stu-id="448d1-106">`handle` [out] A handle for enumerating the modules.</span></span>

## <a name="remarks"></a><span data-ttu-id="448d1-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="448d1-107">Remarks</span></span>

<span data-ttu-id="448d1-108">Podana metoda jest częścią `IXCLRDataProcess` interfejs i odnosi się do 26 gniazda tabeli metod wirtualnych.</span><span class="sxs-lookup"><span data-stu-id="448d1-108">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 26th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="448d1-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="448d1-109">Requirements</span></span>

<span data-ttu-id="448d1-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="448d1-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>   
<span data-ttu-id="448d1-111">**Nagłówek:** Brak</span><span class="sxs-lookup"><span data-stu-id="448d1-111">**Header:** None</span></span>   
<span data-ttu-id="448d1-112">**Biblioteka:** Brak</span><span class="sxs-lookup"><span data-stu-id="448d1-112">**Library:** None</span></span>   
<span data-ttu-id="448d1-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="448d1-113">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>   

## <a name="see-also"></a><span data-ttu-id="448d1-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="448d1-114">See also</span></span>

- [<span data-ttu-id="448d1-115">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="448d1-115">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="448d1-116">Interfejs IXCLRDataProcess</span><span class="sxs-lookup"><span data-stu-id="448d1-116">IXCLRDataProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-interface.md)
