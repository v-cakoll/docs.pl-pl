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
ms.openlocfilehash: d19a4b8116573f2ff6469fe612e7b7736651ff03
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57354534"
---
# <a name="ixclrdataprocessenummethodinstancebyaddress-method"></a><span data-ttu-id="cf614-102">IXCLRDataProcess::EnumMethodInstanceByAddress Method</span><span class="sxs-lookup"><span data-stu-id="cf614-102">IXCLRDataProcess::EnumMethodInstanceByAddress Method</span></span>

<span data-ttu-id="cf614-103">Wylicza wystąpienia metody tego procesu, rozpoczynając od przesunięcia adresu.</span><span class="sxs-lookup"><span data-stu-id="cf614-103">Enumerates the method instances of this process starting at an address offset.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="cf614-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="cf614-104">Syntax</span></span>

```
HRESULT EnumMethodInstanceByAddress(
    [in] CLRDATA_ENUM              *handle,
    [out] IXCLRDataMethodInstance **method
);
```

### <a name="parameters"></a><span data-ttu-id="cf614-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cf614-105">Parameters</span></span>

`handle`\
<span data-ttu-id="cf614-106">[in] Dojście do wyliczania wystąpień metody.</span><span class="sxs-lookup"><span data-stu-id="cf614-106">[in] A handle for enumerating the method instances.</span></span>

`mod`\
<span data-ttu-id="cf614-107">[out] Wystąpienie metody wyliczany.</span><span class="sxs-lookup"><span data-stu-id="cf614-107">[out] The enumerated method instance.</span></span>

## <a name="remarks"></a><span data-ttu-id="cf614-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cf614-108">Remarks</span></span>

<span data-ttu-id="cf614-109">Podana metoda jest częścią `IXCLRDataProcess` interfejs i odnosi się do 28 gniazda tabeli metod wirtualnych.</span><span class="sxs-lookup"><span data-stu-id="cf614-109">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 28th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="cf614-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cf614-110">Requirements</span></span>

<span data-ttu-id="cf614-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cf614-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>   
<span data-ttu-id="cf614-112">**Nagłówek:** Brak</span><span class="sxs-lookup"><span data-stu-id="cf614-112">**Header:** None</span></span>   
<span data-ttu-id="cf614-113">**Biblioteka:** Brak</span><span class="sxs-lookup"><span data-stu-id="cf614-113">**Library:** None</span></span>   
<span data-ttu-id="cf614-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="cf614-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>   
 
## <a name="see-also"></a><span data-ttu-id="cf614-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cf614-115">See also</span></span>
- [<span data-ttu-id="cf614-116">Wyliczenie CLRDataSourceType</span><span class="sxs-lookup"><span data-stu-id="cf614-116">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="cf614-117">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="cf614-117">Debugging</span></span>](index.md)
- [<span data-ttu-id="cf614-118">Interfejs IXCLRDataProcess</span><span class="sxs-lookup"><span data-stu-id="cf614-118">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
