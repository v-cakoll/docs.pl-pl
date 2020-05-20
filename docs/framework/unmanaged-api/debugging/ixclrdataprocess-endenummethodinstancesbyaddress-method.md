---
title: 'IXCLRDataProcess:: EndEnumMethodInstancesByAddress, Metoda'
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess::EndEnumMethodInstancesByAddress Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::EndEnumMethodInstancesByAddress Method
helpviewer.keywords:
- IXCLRDataProcess::EndEnumMethodInstancesByAddress Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 5960d08ccfc09010a20d28a22c2e2f3f5b339c7d
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420829"
---
# <a name="ixclrdataprocessendenummethodinstancesbyaddress-method"></a><span data-ttu-id="2b4d2-102">IXCLRDataProcess:: EndEnumMethodInstancesByAddress, Metoda</span><span class="sxs-lookup"><span data-stu-id="2b4d2-102">IXCLRDataProcess::EndEnumMethodInstancesByAddress Method</span></span>

<span data-ttu-id="2b4d2-103">Zwalnia zasoby używane przez Iteratory wewnętrzne używane podczas wyliczania wystąpień.</span><span class="sxs-lookup"><span data-stu-id="2b4d2-103">Releases the resources used by internal iterators used during instance enumeration.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="2b4d2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2b4d2-104">Syntax</span></span>

```cpp
HRESULT EndEnumMethodInstancesByAddress(
    [in] CLRDATA_ENUM handle
);
```

## <a name="parameters"></a><span data-ttu-id="2b4d2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2b4d2-105">Parameters</span></span>

`handle`\
<span data-ttu-id="2b4d2-106">określoną Dojście do wyliczania wystąpień metod.</span><span class="sxs-lookup"><span data-stu-id="2b4d2-106">[out] A handle for enumerating the method instances.</span></span>

## <a name="remarks"></a><span data-ttu-id="2b4d2-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2b4d2-107">Remarks</span></span>

<span data-ttu-id="2b4d2-108">Podana metoda jest częścią `IXCLRDataProcess` interfejsu i odpowiada 30emu gnieździe tabeli metody wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="2b4d2-108">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 30th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="2b4d2-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2b4d2-109">Requirements</span></span>

<span data-ttu-id="2b4d2-110">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2b4d2-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="2b4d2-111">**Nagłówek:** Dawaj</span><span class="sxs-lookup"><span data-stu-id="2b4d2-111">**Header:** None</span></span>  
<span data-ttu-id="2b4d2-112">**Biblioteka:** Dawaj</span><span class="sxs-lookup"><span data-stu-id="2b4d2-112">**Library:** None</span></span>  
<span data-ttu-id="2b4d2-113">**.NET Framework wersje:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="2b4d2-113">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="2b4d2-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2b4d2-114">See also</span></span>

- [<span data-ttu-id="2b4d2-115">CLRDataSourceType, Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="2b4d2-115">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="2b4d2-116">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="2b4d2-116">Debugging</span></span>](index.md)
- [<span data-ttu-id="2b4d2-117">IXCLRDataProcess, interfejs</span><span class="sxs-lookup"><span data-stu-id="2b4d2-117">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
