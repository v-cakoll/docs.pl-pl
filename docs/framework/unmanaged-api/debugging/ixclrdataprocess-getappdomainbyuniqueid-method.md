---
title: 'IXCLRDataProcess:: GetAppDomainByUniqueId, Metoda'
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess::GetAppDomainByUniqueId Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::GetAppDomainByUniqueId Method
helpviewer.keywords:
- IXCLRDataProcess::GetAppDomainByUniqueId Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: bb02ffed09cbcc31e653bfd3165050c247908c5d
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420789"
---
# <a name="ixclrdataprocessgetappdomainbyuniqueid-method"></a><span data-ttu-id="6117b-102">IXCLRDataProcess:: GetAppDomainByUniqueId, Metoda</span><span class="sxs-lookup"><span data-stu-id="6117b-102">IXCLRDataProcess::GetAppDomainByUniqueId Method</span></span>

<span data-ttu-id="6117b-103">Pobiera `AppDomain` w procesie na podstawie jego unikatowego identyfikatora.</span><span class="sxs-lookup"><span data-stu-id="6117b-103">Gets an `AppDomain` in a process based on its unique identifier.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="6117b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6117b-104">Syntax</span></span>

```cpp
HRESULT GetAppDomainByUniqueID(
    [in] ULONG64               id,
    [out] IXCLRDataAppDomain **appDomain
);
```

## <a name="parameters"></a><span data-ttu-id="6117b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6117b-105">Parameters</span></span>

`id`\
<span data-ttu-id="6117b-106">podczas Unikatowy identyfikator domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="6117b-106">[in] The unique identifier of the AppDomain</span></span>

`appDomain`\
<span data-ttu-id="6117b-107">określoną Domena aplikacji</span><span class="sxs-lookup"><span data-stu-id="6117b-107">[out] The AppDomain</span></span>

## <a name="remarks"></a><span data-ttu-id="6117b-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6117b-108">Remarks</span></span>

<span data-ttu-id="6117b-109">Podana metoda jest częścią `IXCLRDataProcess` interfejsu i odpowiada dwudziestemu gnieździe tabeli metody wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="6117b-109">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 20th slot of the virtual method table.</span></span> <span data-ttu-id="6117b-110">`IXCLRDataAppDomain*`Zwracana wartość jest używana do interakcji z innymi interfejsami API.</span><span class="sxs-lookup"><span data-stu-id="6117b-110">The `IXCLRDataAppDomain*` returned is used for interaction with other APIs.</span></span>

## <a name="requirements"></a><span data-ttu-id="6117b-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6117b-111">Requirements</span></span>

<span data-ttu-id="6117b-112">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6117b-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>
<span data-ttu-id="6117b-113">**Nagłówek:** Brak **biblioteki:** brak **.NET Framework wersje:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="6117b-113">**Header:** None **Library:** None **.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="6117b-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6117b-114">See also</span></span>

- [<span data-ttu-id="6117b-115">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="6117b-115">Debugging</span></span>](index.md)
- [<span data-ttu-id="6117b-116">IXCLRDataProcess, interfejs</span><span class="sxs-lookup"><span data-stu-id="6117b-116">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
