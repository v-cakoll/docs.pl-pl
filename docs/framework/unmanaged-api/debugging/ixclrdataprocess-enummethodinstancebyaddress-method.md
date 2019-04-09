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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59166442"
---
# <a name="ixclrdataprocessenummethodinstancebyaddress-method"></a><span data-ttu-id="5795d-102">IXCLRDataProcess::EnumMethodInstanceByAddress Method</span><span class="sxs-lookup"><span data-stu-id="5795d-102">IXCLRDataProcess::EnumMethodInstanceByAddress Method</span></span>

<span data-ttu-id="5795d-103">Wylicza wystąpienia metody tego procesu, rozpoczynając od przesunięcia adresu.</span><span class="sxs-lookup"><span data-stu-id="5795d-103">Enumerates the method instances of this process starting at an address offset.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="5795d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5795d-104">Syntax</span></span>

```
HRESULT EnumMethodInstanceByAddress(
    [in] CLRDATA_ENUM              *handle,
    [out] IXCLRDataMethodInstance **method
);
```

## <a name="parameters"></a><span data-ttu-id="5795d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5795d-105">Parameters</span></span>

`handle`\
<span data-ttu-id="5795d-106">[in] Dojście do wyliczania wystąpień metody.</span><span class="sxs-lookup"><span data-stu-id="5795d-106">[in] A handle for enumerating the method instances.</span></span>

`mod`\
<span data-ttu-id="5795d-107">[out] Wystąpienie metody wyliczany.</span><span class="sxs-lookup"><span data-stu-id="5795d-107">[out] The enumerated method instance.</span></span>

## <a name="remarks"></a><span data-ttu-id="5795d-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5795d-108">Remarks</span></span>

<span data-ttu-id="5795d-109">Podana metoda jest częścią `IXCLRDataProcess` interfejs i odnosi się do 28 gniazda tabeli metod wirtualnych.</span><span class="sxs-lookup"><span data-stu-id="5795d-109">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 28th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="5795d-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5795d-110">Requirements</span></span>

<span data-ttu-id="5795d-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5795d-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>   
<span data-ttu-id="5795d-112">**Nagłówek:** Brak</span><span class="sxs-lookup"><span data-stu-id="5795d-112">**Header:** None</span></span>   
<span data-ttu-id="5795d-113">**Biblioteka:** Brak</span><span class="sxs-lookup"><span data-stu-id="5795d-113">**Library:** None</span></span>   
**<span data-ttu-id="5795d-114">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="5795d-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]   
 
## <a name="see-also"></a><span data-ttu-id="5795d-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5795d-115">See also</span></span>

- [<span data-ttu-id="5795d-116">Wyliczenie CLRDataSourceType</span><span class="sxs-lookup"><span data-stu-id="5795d-116">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="5795d-117">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="5795d-117">Debugging</span></span>](index.md)
- [<span data-ttu-id="5795d-118">IXCLRDataProcess, interfejs</span><span class="sxs-lookup"><span data-stu-id="5795d-118">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
