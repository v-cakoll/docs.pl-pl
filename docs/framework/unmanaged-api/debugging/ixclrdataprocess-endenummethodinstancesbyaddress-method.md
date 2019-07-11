---
title: IXCLRDataProcess::EndEnumMethodInstancesByAddress Method
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
ms.openlocfilehash: 378095aa2b363f4003a5372b4158df27412655e1
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67757853"
---
# <a name="ixclrdataprocessendenummethodinstancesbyaddress-method"></a><span data-ttu-id="e9322-102">IXCLRDataProcess::EndEnumMethodInstancesByAddress Method</span><span class="sxs-lookup"><span data-stu-id="e9322-102">IXCLRDataProcess::EndEnumMethodInstancesByAddress Method</span></span>

<span data-ttu-id="e9322-103">Zwalnia zasoby używane przez Iteratory wewnętrzny używany podczas wyliczania wystąpień.</span><span class="sxs-lookup"><span data-stu-id="e9322-103">Releases the resources used by internal iterators used during instance enumeration.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="e9322-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e9322-104">Syntax</span></span>

```cpp
HRESULT EndEnumMethodInstancesByAddress(
    [in] CLRDATA_ENUM handle
);
```

## <a name="parameters"></a><span data-ttu-id="e9322-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e9322-105">Parameters</span></span>

`handle`\
<span data-ttu-id="e9322-106">[out] Dojście do wyliczania wystąpień metody.</span><span class="sxs-lookup"><span data-stu-id="e9322-106">[out] A handle for enumerating the method instances.</span></span>

## <a name="remarks"></a><span data-ttu-id="e9322-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e9322-107">Remarks</span></span>

<span data-ttu-id="e9322-108">Podana metoda jest częścią `IXCLRDataProcess` interfejs i odnosi się do 29 gniazda tabeli metod wirtualnych.</span><span class="sxs-lookup"><span data-stu-id="e9322-108">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 29th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="e9322-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e9322-109">Requirements</span></span>

<span data-ttu-id="e9322-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e9322-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="e9322-111">**Nagłówek:** Brak</span><span class="sxs-lookup"><span data-stu-id="e9322-111">**Header:** None</span></span>  
<span data-ttu-id="e9322-112">**Biblioteka:** Brak</span><span class="sxs-lookup"><span data-stu-id="e9322-112">**Library:** None</span></span>  
<span data-ttu-id="e9322-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="e9322-113">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="e9322-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e9322-114">See also</span></span>

- [<span data-ttu-id="e9322-115">Wyliczenie CLRDataSourceType</span><span class="sxs-lookup"><span data-stu-id="e9322-115">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="e9322-116">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="e9322-116">Debugging</span></span>](index.md)
- [<span data-ttu-id="e9322-117">Interfejs IXCLRDataProcess</span><span class="sxs-lookup"><span data-stu-id="e9322-117">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
