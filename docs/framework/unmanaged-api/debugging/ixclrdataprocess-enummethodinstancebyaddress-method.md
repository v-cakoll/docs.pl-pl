---
title: Metoda IXCLCLDATaProcess::EnumMethodInstanceByAddress Metoda
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
ms.openlocfilehash: afc5fc377dd45d5e8d4d2d7b3385ca0524df69e1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176659"
---
# <a name="ixclrdataprocessenummethodinstancebyaddress-method"></a><span data-ttu-id="43b97-102">Metoda IXCLCLDATaProcess::EnumMethodInstanceByAddress Metoda</span><span class="sxs-lookup"><span data-stu-id="43b97-102">IXCLRDataProcess::EnumMethodInstanceByAddress Method</span></span>

<span data-ttu-id="43b97-103">Wylicza wystąpienia metody tego procesu, począwszy od przesunięcia adresu.</span><span class="sxs-lookup"><span data-stu-id="43b97-103">Enumerates the method instances of this process starting at an address offset.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="43b97-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="43b97-104">Syntax</span></span>

```cpp
HRESULT EnumMethodInstanceByAddress(
    [in] CLRDATA_ENUM              *handle,
    [out] IXCLRDataMethodInstance **method
);
```

## <a name="parameters"></a><span data-ttu-id="43b97-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="43b97-105">Parameters</span></span>

`handle`\
<span data-ttu-id="43b97-106">[w] Dojście do wyliczania wystąpień metody.</span><span class="sxs-lookup"><span data-stu-id="43b97-106">[in] A handle for enumerating the method instances.</span></span>

`mod`\
<span data-ttu-id="43b97-107">[na zewnątrz] Wystąpienie metody wyliczonej.</span><span class="sxs-lookup"><span data-stu-id="43b97-107">[out] The enumerated method instance.</span></span>

## <a name="remarks"></a><span data-ttu-id="43b97-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="43b97-108">Remarks</span></span>

<span data-ttu-id="43b97-109">Podana metoda jest `IXCLRDataProcess` częścią interfejsu i odpowiada 28-cie gniazdo tabeli metody wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="43b97-109">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 28th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="43b97-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="43b97-110">Requirements</span></span>

<span data-ttu-id="43b97-111">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="43b97-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>
<span data-ttu-id="43b97-112">**Nagłówek:** Brak **biblioteki:** Brak **wersji programu .NET Framework:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="43b97-112">**Header:** None **Library:** None **.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="43b97-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="43b97-113">See also</span></span>

- [<span data-ttu-id="43b97-114">Wyliczanie CLRDataSourceType</span><span class="sxs-lookup"><span data-stu-id="43b97-114">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="43b97-115">Debugging</span><span class="sxs-lookup"><span data-stu-id="43b97-115">Debugging</span></span>](index.md)
- [<span data-ttu-id="43b97-116">IXCLRDataProcess, interfejs</span><span class="sxs-lookup"><span data-stu-id="43b97-116">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
