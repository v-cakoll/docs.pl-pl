---
title: 'IXCLRDataProcess:: EnumMethodInstanceByAddress, Metoda'
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess::EnumMethodInstanceByAddress Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::EnumMethodInstanceByAddress Method
helpviewer.keywords:
- IXCLRDataProcess::EnumMethodInstanceByAddress Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 142099ae5cf9637cc28e8c82aabcd831cc8f0f52
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420802"
---
# <a name="ixclrdataprocessenummethodinstancebyaddress-method"></a><span data-ttu-id="cde5b-102">IXCLRDataProcess:: EnumMethodInstanceByAddress, Metoda</span><span class="sxs-lookup"><span data-stu-id="cde5b-102">IXCLRDataProcess::EnumMethodInstanceByAddress Method</span></span>

<span data-ttu-id="cde5b-103">Wylicza wystąpienia metody tego procesu, rozpoczynając od przesunięcia adresu.</span><span class="sxs-lookup"><span data-stu-id="cde5b-103">Enumerates the method instances of this process starting at an address offset.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="cde5b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="cde5b-104">Syntax</span></span>

```cpp
HRESULT EnumMethodInstanceByAddress(
    [in] CLRDATA_ENUM              *handle,
    [out] IXCLRDataMethodInstance **method
);
```

## <a name="parameters"></a><span data-ttu-id="cde5b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cde5b-105">Parameters</span></span>

`handle`\
<span data-ttu-id="cde5b-106">podczas Dojście do wyliczania wystąpień metod.</span><span class="sxs-lookup"><span data-stu-id="cde5b-106">[in] A handle for enumerating the method instances.</span></span>

`mod`\
<span data-ttu-id="cde5b-107">określoną Wystąpienie metody z wyliczeniem.</span><span class="sxs-lookup"><span data-stu-id="cde5b-107">[out] The enumerated method instance.</span></span>

## <a name="remarks"></a><span data-ttu-id="cde5b-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cde5b-108">Remarks</span></span>

<span data-ttu-id="cde5b-109">Podana metoda jest częścią `IXCLRDataProcess` interfejsu i odpowiada 29 w gnieździe tabeli metody wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="cde5b-109">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 29th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="cde5b-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cde5b-110">Requirements</span></span>

<span data-ttu-id="cde5b-111">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cde5b-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>
<span data-ttu-id="cde5b-112">**Nagłówek:** Brak **biblioteki:** brak **.NET Framework wersje:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="cde5b-112">**Header:** None **Library:** None **.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="cde5b-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cde5b-113">See also</span></span>

- [<span data-ttu-id="cde5b-114">CLRDataSourceType, Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="cde5b-114">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="cde5b-115">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="cde5b-115">Debugging</span></span>](index.md)
- [<span data-ttu-id="cde5b-116">IXCLRDataProcess, interfejs</span><span class="sxs-lookup"><span data-stu-id="cde5b-116">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
