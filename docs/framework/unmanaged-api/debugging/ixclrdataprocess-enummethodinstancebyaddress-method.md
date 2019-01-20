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
ms.openlocfilehash: b42939e8e64e75337478ace67a9a91c6a03a94e3
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2019
ms.locfileid: "54416177"
---
# <a name="ixclrdataprocessenummethodinstancebyaddress-method"></a><span data-ttu-id="2bbba-102">IXCLRDataProcess::EnumMethodInstanceByAddress Method</span><span class="sxs-lookup"><span data-stu-id="2bbba-102">IXCLRDataProcess::EnumMethodInstanceByAddress Method</span></span>

<span data-ttu-id="2bbba-103">Wylicza wystąpienia metody tego procesu, rozpoczynając od przesunięcia adresu.</span><span class="sxs-lookup"><span data-stu-id="2bbba-103">Enumerates the method instances of this process starting at an address offset.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="2bbba-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2bbba-104">Syntax</span></span>

```
HRESULT EnumMethodInstanceByAddress(
    [in] CLRDATA_ENUM              *handle,
    [out] IXCLRDataMethodInstance **method
);
```

### <a name="parameters"></a><span data-ttu-id="2bbba-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2bbba-105">Parameters</span></span>

<span data-ttu-id="2bbba-106">`handle` [in] Dojście do wyliczania wystąpień metody.</span><span class="sxs-lookup"><span data-stu-id="2bbba-106">`handle` [in] A handle for enumerating the method instances.</span></span>

<span data-ttu-id="2bbba-107">`mod` [out] Wystąpienie metody wyliczany.</span><span class="sxs-lookup"><span data-stu-id="2bbba-107">`mod` [out] The enumerated method instance.</span></span>

## <a name="remarks"></a><span data-ttu-id="2bbba-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2bbba-108">Remarks</span></span>

<span data-ttu-id="2bbba-109">Podana metoda jest częścią `IXCLRDataProcess` interfejs i odnosi się do 28 gniazda tabeli metod wirtualnych.</span><span class="sxs-lookup"><span data-stu-id="2bbba-109">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 28th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="2bbba-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2bbba-110">Requirements</span></span>

<span data-ttu-id="2bbba-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2bbba-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>   
<span data-ttu-id="2bbba-112">**Nagłówek:** Brak</span><span class="sxs-lookup"><span data-stu-id="2bbba-112">**Header:** None</span></span>   
<span data-ttu-id="2bbba-113">**Biblioteka:** Brak</span><span class="sxs-lookup"><span data-stu-id="2bbba-113">**Library:** None</span></span>   
<span data-ttu-id="2bbba-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="2bbba-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>   
 
## <a name="see-also"></a><span data-ttu-id="2bbba-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2bbba-115">See Also</span></span>
- [<span data-ttu-id="2bbba-116">Wyliczenie CLRDataSourceType</span><span class="sxs-lookup"><span data-stu-id="2bbba-116">CLRDataSourceType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="2bbba-117">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="2bbba-117">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="2bbba-118">Interfejs IXCLRDataProcess</span><span class="sxs-lookup"><span data-stu-id="2bbba-118">IXCLRDataProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-interface.md)
