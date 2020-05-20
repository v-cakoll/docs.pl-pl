---
title: 'IXCLRDataProcess:: StartEnumMethodInstancesByAddress, Metoda'
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
ms.openlocfilehash: 52d533f1c86b34b7b9febade8590e7ab58d8221e
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420738"
---
# <a name="ixclrdataprocessstartenummethodinstancesbyaddress-method"></a><span data-ttu-id="618e3-102">IXCLRDataProcess:: StartEnumMethodInstancesByAddress, Metoda</span><span class="sxs-lookup"><span data-stu-id="618e3-102">IXCLRDataProcess::StartEnumMethodInstancesByAddress Method</span></span>

<span data-ttu-id="618e3-103">Udostępnia dojście do wyliczenia wystąpień metod, `AppDomain` Zaczynając od danego adresu.</span><span class="sxs-lookup"><span data-stu-id="618e3-103">Provides a handle to enumerate the method instances of `AppDomain` starting at a given address.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="618e3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="618e3-104">Syntax</span></span>

```cpp
HRESULT StartEnumMethodInstancesByAddress(
    [in] CLRDATA_ADDRESS     address,
    [in] IXCLRDataAppDomain *appDomain,
    [out] CLRDATA_ENUM      *handle
);
```

## <a name="parameters"></a><span data-ttu-id="618e3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="618e3-105">Parameters</span></span>

`address`\
<span data-ttu-id="618e3-106">podczas Adres pierwszego wystąpienia metody.</span><span class="sxs-lookup"><span data-stu-id="618e3-106">[in] The address of the first method instance.</span></span>

`appDomain`\
<span data-ttu-id="618e3-107">podczas Obiekt AppDomain wystąpień metody.</span><span class="sxs-lookup"><span data-stu-id="618e3-107">[in] The AppDomain of the method instances.</span></span>

`handle`\
<span data-ttu-id="618e3-108">określoną Dojście do wyliczania wystąpień metod.</span><span class="sxs-lookup"><span data-stu-id="618e3-108">[out] A handle for enumerating the method instances.</span></span>

## <a name="remarks"></a><span data-ttu-id="618e3-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="618e3-109">Remarks</span></span>

<span data-ttu-id="618e3-110">Podana metoda jest częścią `IXCLRDataProcess` interfejsu i odnosi się do dwudziestego miejsca w tabeli metody wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="618e3-110">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 28th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="618e3-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="618e3-111">Requirements</span></span>

<span data-ttu-id="618e3-112">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="618e3-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="618e3-113">**Nagłówek:** Dawaj</span><span class="sxs-lookup"><span data-stu-id="618e3-113">**Header:** None</span></span>  
<span data-ttu-id="618e3-114">**Biblioteka:** Dawaj</span><span class="sxs-lookup"><span data-stu-id="618e3-114">**Library:** None</span></span>  
<span data-ttu-id="618e3-115">**.NET Framework wersje:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="618e3-115">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="618e3-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="618e3-116">See also</span></span>

- [<span data-ttu-id="618e3-117">CLRDataSourceType, Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="618e3-117">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="618e3-118">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="618e3-118">Debugging</span></span>](index.md)
- [<span data-ttu-id="618e3-119">IXCLRDataProcess, interfejs</span><span class="sxs-lookup"><span data-stu-id="618e3-119">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
