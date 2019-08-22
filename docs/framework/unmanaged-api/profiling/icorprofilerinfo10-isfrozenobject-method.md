---
title: 'ICorProfilerInfo10:: iszamarzniętobject'
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo10.IsFrozenObject
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: d212c06c7ddc9f22095c0b95f19fd1083482435c
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69661222"
---
# <a name="icorprofilerinfo10isfrozenobject-method"></a><span data-ttu-id="37afb-102">ICorProfilerInfo10:: iszamarzniętobject — Metoda</span><span class="sxs-lookup"><span data-stu-id="37afb-102">ICorProfilerInfo10::IsFrozenObject Method</span></span>

<span data-ttu-id="37afb-103">Przy użyciu identyfikatora ObjectID określa, czy obiekt znajduje się w segmencie tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="37afb-103">Given an ObjectID, determines whether the object is in a read-only segment.</span></span>

## <a name="syntax"></a><span data-ttu-id="37afb-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="37afb-104">Syntax</span></span>

```cpp
HRESULT IsFrozenObject( [in]  ObjectID objectId,
                        [out] BOOL *pbFrozen);
```

#### <a name="parameters"></a><span data-ttu-id="37afb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="37afb-105">Parameters</span></span>

`objectId` \
<span data-ttu-id="37afb-106">podczas Obiekt do sprawdzenia.</span><span class="sxs-lookup"><span data-stu-id="37afb-106">[in] The object to examine.</span></span>

`pbFrozen` \
<span data-ttu-id="37afb-107">określoną Wskazuje `BOOL` , czy obiekt znajduje się w segmencie tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="37afb-107">[out] A `BOOL` indicating if the object is in a read-only segment.</span></span>

## <a name="requirements"></a><span data-ttu-id="37afb-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="37afb-108">Requirements</span></span>

<span data-ttu-id="37afb-109">**Poszczególnych** Zobacz [obsługiwane systemy operacyjne .NET Core](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).</span><span class="sxs-lookup"><span data-stu-id="37afb-109">**Platforms:** See [.NET Core supported operating systems](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).</span></span>

<span data-ttu-id="37afb-110">**Nagłówki** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="37afb-110">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="37afb-111">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="37afb-111">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="37afb-112">**Wersje .NET:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="37afb-112">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="37afb-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="37afb-113">See also</span></span>

- [<span data-ttu-id="37afb-114">ICorProfilerInfo10, interfejs</span><span class="sxs-lookup"><span data-stu-id="37afb-114">ICorProfilerInfo10 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-interface.md)
