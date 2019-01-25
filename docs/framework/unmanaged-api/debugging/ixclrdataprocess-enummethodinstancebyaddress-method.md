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
ms.openlocfilehash: 825cb8ea94bee980f9e10b90cddf04db32c1a33f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54491912"
---
# <a name="ixclrdataprocessenummethodinstancebyaddress-method"></a><span data-ttu-id="7be9c-102">IXCLRDataProcess::EnumMethodInstanceByAddress Method</span><span class="sxs-lookup"><span data-stu-id="7be9c-102">IXCLRDataProcess::EnumMethodInstanceByAddress Method</span></span>

<span data-ttu-id="7be9c-103">Wylicza wystąpienia metody tego procesu, rozpoczynając od przesunięcia adresu.</span><span class="sxs-lookup"><span data-stu-id="7be9c-103">Enumerates the method instances of this process starting at an address offset.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="7be9c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7be9c-104">Syntax</span></span>

```
HRESULT EnumMethodInstanceByAddress(
    [in] CLRDATA_ENUM              *handle,
    [out] IXCLRDataMethodInstance **method
);
```

### <a name="parameters"></a><span data-ttu-id="7be9c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7be9c-105">Parameters</span></span>

<span data-ttu-id="7be9c-106">`handle` [in] Dojście do wyliczania wystąpień metody.</span><span class="sxs-lookup"><span data-stu-id="7be9c-106">`handle` [in] A handle for enumerating the method instances.</span></span>

<span data-ttu-id="7be9c-107">`mod` [out] Wystąpienie metody wyliczany.</span><span class="sxs-lookup"><span data-stu-id="7be9c-107">`mod` [out] The enumerated method instance.</span></span>

## <a name="remarks"></a><span data-ttu-id="7be9c-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7be9c-108">Remarks</span></span>

<span data-ttu-id="7be9c-109">Podana metoda jest częścią `IXCLRDataProcess` interfejs i odnosi się do 28 gniazda tabeli metod wirtualnych.</span><span class="sxs-lookup"><span data-stu-id="7be9c-109">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 28th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="7be9c-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7be9c-110">Requirements</span></span>

<span data-ttu-id="7be9c-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7be9c-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>   
<span data-ttu-id="7be9c-112">**Nagłówek:** Brak</span><span class="sxs-lookup"><span data-stu-id="7be9c-112">**Header:** None</span></span>   
<span data-ttu-id="7be9c-113">**Biblioteka:** Brak</span><span class="sxs-lookup"><span data-stu-id="7be9c-113">**Library:** None</span></span>   
<span data-ttu-id="7be9c-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="7be9c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>   
 
## <a name="see-also"></a><span data-ttu-id="7be9c-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7be9c-115">See also</span></span>
- [<span data-ttu-id="7be9c-116">Wyliczenie CLRDataSourceType</span><span class="sxs-lookup"><span data-stu-id="7be9c-116">CLRDataSourceType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="7be9c-117">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="7be9c-117">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="7be9c-118">Interfejs IXCLRDataProcess</span><span class="sxs-lookup"><span data-stu-id="7be9c-118">IXCLRDataProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-interface.md)
