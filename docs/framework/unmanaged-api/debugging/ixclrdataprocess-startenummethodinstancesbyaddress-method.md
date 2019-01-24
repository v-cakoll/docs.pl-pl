---
title: Metoda IXCLRDataProcess::StartEnumMethodInstancesByAddress
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess::StartEnumMethodInstancesByAddress Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::StartEnumMethodInstancesByAddress Method
helpviewer.keywords:
- IXCLRDataProcess::StartEnumMethodInstancesByAddress Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 9afbf0665b114169661a74b60c744203d160fed3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54662624"
---
# <a name="ixclrdataprocessstartenummethodinstancesbyaddress-method"></a><span data-ttu-id="e3b2a-102">Metoda IXCLRDataProcess::StartEnumMethodInstancesByAddress</span><span class="sxs-lookup"><span data-stu-id="e3b2a-102">IXCLRDataProcess::StartEnumMethodInstancesByAddress Method</span></span>

<span data-ttu-id="e3b2a-103">Udostępnia dojścia wyliczania wystąpień metoda `AppDomain` Rozpoczynanie pod danym adresem.</span><span class="sxs-lookup"><span data-stu-id="e3b2a-103">Provides a handle to enumerate the method instances of `AppDomain` starting at a given address.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="e3b2a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e3b2a-104">Syntax</span></span>

```
HRESULT StartEnumMethodInstancesByAddress(
    [in] CLRDATA_ADDRESS     address,
    [in] IXCLRDataAppDomain *appDomain,
    [out] CLRDATA_ENUM      *handle
);
```

### <a name="parameters"></a><span data-ttu-id="e3b2a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e3b2a-105">Parameters</span></span>

<span data-ttu-id="e3b2a-106">`address` [in] Adres pierwszego wystąpienia metody.</span><span class="sxs-lookup"><span data-stu-id="e3b2a-106">`address` [in] The address of the first method instance.</span></span>

<span data-ttu-id="e3b2a-107">`appDomain` [in] Element AppDomain wystąpienia metody.</span><span class="sxs-lookup"><span data-stu-id="e3b2a-107">`appDomain` [in] The AppDomain of the method instances.</span></span>

<span data-ttu-id="e3b2a-108">`handle` [out] Dojście do wyliczania wystąpień metody.</span><span class="sxs-lookup"><span data-stu-id="e3b2a-108">`handle` [out] A handle for enumerating the method instances.</span></span>

## <a name="remarks"></a><span data-ttu-id="e3b2a-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e3b2a-109">Remarks</span></span>

<span data-ttu-id="e3b2a-110">Podana metoda jest częścią `IXCLRDataProcess` interfejs i odnosi się do 27 gniazda tabeli metod wirtualnych.</span><span class="sxs-lookup"><span data-stu-id="e3b2a-110">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 27th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="e3b2a-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e3b2a-111">Requirements</span></span>

<span data-ttu-id="e3b2a-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e3b2a-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="e3b2a-113">**Nagłówek:** Brak</span><span class="sxs-lookup"><span data-stu-id="e3b2a-113">**Header:** None</span></span>  
<span data-ttu-id="e3b2a-114">**Biblioteka:** Brak</span><span class="sxs-lookup"><span data-stu-id="e3b2a-114">**Library:** None</span></span>  
<span data-ttu-id="e3b2a-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="e3b2a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="e3b2a-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e3b2a-116">See also</span></span>

- [<span data-ttu-id="e3b2a-117">Wyliczenie CLRDataSourceType</span><span class="sxs-lookup"><span data-stu-id="e3b2a-117">CLRDataSourceType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="e3b2a-118">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="e3b2a-118">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="e3b2a-119">Interfejs IXCLRDataProcess</span><span class="sxs-lookup"><span data-stu-id="e3b2a-119">IXCLRDataProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-interface.md)
