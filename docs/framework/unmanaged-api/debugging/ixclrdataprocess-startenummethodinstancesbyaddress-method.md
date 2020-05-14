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
ms.openlocfilehash: e28fa73300e147ac07a2d325fbf517480bb73797
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2020
ms.locfileid: "83394949"
---
# <a name="ixclrdataprocessstartenummethodinstancesbyaddress-method"></a><span data-ttu-id="94ea2-102">IXCLRDataProcess:: StartEnumMethodInstancesByAddress, Metoda</span><span class="sxs-lookup"><span data-stu-id="94ea2-102">IXCLRDataProcess::StartEnumMethodInstancesByAddress Method</span></span>

<span data-ttu-id="94ea2-103">Udostępnia dojście do wyliczenia wystąpień metod, `AppDomain` Zaczynając od danego adresu.</span><span class="sxs-lookup"><span data-stu-id="94ea2-103">Provides a handle to enumerate the method instances of `AppDomain` starting at a given address.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="94ea2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="94ea2-104">Syntax</span></span>

```cpp
HRESULT StartEnumMethodInstancesByAddress(
    [in] CLRDATA_ADDRESS     address,
    [in] IXCLRDataAppDomain *appDomain,
    [out] CLRDATA_ENUM      *handle
);
```

## <a name="parameters"></a><span data-ttu-id="94ea2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="94ea2-105">Parameters</span></span>

`address`\
<span data-ttu-id="94ea2-106">podczas Adres pierwszego wystąpienia metody.</span><span class="sxs-lookup"><span data-stu-id="94ea2-106">[in] The address of the first method instance.</span></span>

`appDomain`\
<span data-ttu-id="94ea2-107">podczas Obiekt AppDomain wystąpień metody.</span><span class="sxs-lookup"><span data-stu-id="94ea2-107">[in] The AppDomain of the method instances.</span></span>

`handle`\
<span data-ttu-id="94ea2-108">określoną Dojście do wyliczania wystąpień metod.</span><span class="sxs-lookup"><span data-stu-id="94ea2-108">[out] A handle for enumerating the method instances.</span></span>

## <a name="remarks"></a><span data-ttu-id="94ea2-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="94ea2-109">Remarks</span></span>

<span data-ttu-id="94ea2-110">Podana metoda jest częścią `IXCLRDataProcess` interfejsu i odnosi się do dwudziestego miejsca w tabeli metody wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="94ea2-110">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 28th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="94ea2-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="94ea2-111">Requirements</span></span>

<span data-ttu-id="94ea2-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="94ea2-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="94ea2-113">**Nagłówek:** Dawaj</span><span class="sxs-lookup"><span data-stu-id="94ea2-113">**Header:** None</span></span>  
<span data-ttu-id="94ea2-114">**Biblioteka:** Dawaj</span><span class="sxs-lookup"><span data-stu-id="94ea2-114">**Library:** None</span></span>  
<span data-ttu-id="94ea2-115">**.NET Framework wersje:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="94ea2-115">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="94ea2-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="94ea2-116">See also</span></span>

- [<span data-ttu-id="94ea2-117">CLRDataSourceType, Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="94ea2-117">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="94ea2-118">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="94ea2-118">Debugging</span></span>](index.md)
- [<span data-ttu-id="94ea2-119">IXCLRDataProcess, interfejs</span><span class="sxs-lookup"><span data-stu-id="94ea2-119">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
