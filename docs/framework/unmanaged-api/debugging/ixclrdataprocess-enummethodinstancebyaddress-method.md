---
title: IXCLRDataProcess::EnumMethodInstanceByAddress Method
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
ms.openlocfilehash: a51c709b0b331127b74d98c4dc42e2772fd7f2db
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61775469"
---
# <a name="ixclrdataprocessenummethodinstancebyaddress-method"></a><span data-ttu-id="01310-102">IXCLRDataProcess::EnumMethodInstanceByAddress Method</span><span class="sxs-lookup"><span data-stu-id="01310-102">IXCLRDataProcess::EnumMethodInstanceByAddress Method</span></span>

<span data-ttu-id="01310-103">Wylicza wystąpienia metody tego procesu, rozpoczynając od przesunięcia adresu.</span><span class="sxs-lookup"><span data-stu-id="01310-103">Enumerates the method instances of this process starting at an address offset.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="01310-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="01310-104">Syntax</span></span>

```
HRESULT EnumMethodInstanceByAddress(
    [in] CLRDATA_ENUM              *handle,
    [out] IXCLRDataMethodInstance **method
);
```

## <a name="parameters"></a><span data-ttu-id="01310-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="01310-105">Parameters</span></span>

`handle`\
<span data-ttu-id="01310-106">[in] Dojście do wyliczania wystąpień metody.</span><span class="sxs-lookup"><span data-stu-id="01310-106">[in] A handle for enumerating the method instances.</span></span>

`mod`\
<span data-ttu-id="01310-107">[out] Wystąpienie metody wyliczany.</span><span class="sxs-lookup"><span data-stu-id="01310-107">[out] The enumerated method instance.</span></span>

## <a name="remarks"></a><span data-ttu-id="01310-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="01310-108">Remarks</span></span>

<span data-ttu-id="01310-109">Podana metoda jest częścią `IXCLRDataProcess` interfejs i odnosi się do 28 gniazda tabeli metod wirtualnych.</span><span class="sxs-lookup"><span data-stu-id="01310-109">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 28th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="01310-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="01310-110">Requirements</span></span>

<span data-ttu-id="01310-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="01310-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>   
<span data-ttu-id="01310-112">**Nagłówek:** Brak</span><span class="sxs-lookup"><span data-stu-id="01310-112">**Header:** None</span></span>   
<span data-ttu-id="01310-113">**Biblioteka:** Brak</span><span class="sxs-lookup"><span data-stu-id="01310-113">**Library:** None</span></span>   
<span data-ttu-id="01310-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="01310-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>   
 
## <a name="see-also"></a><span data-ttu-id="01310-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="01310-115">See also</span></span>

- [<span data-ttu-id="01310-116">Wyliczenie CLRDataSourceType</span><span class="sxs-lookup"><span data-stu-id="01310-116">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="01310-117">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="01310-117">Debugging</span></span>](index.md)
- [<span data-ttu-id="01310-118">Interfejs IXCLRDataProcess</span><span class="sxs-lookup"><span data-stu-id="01310-118">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
