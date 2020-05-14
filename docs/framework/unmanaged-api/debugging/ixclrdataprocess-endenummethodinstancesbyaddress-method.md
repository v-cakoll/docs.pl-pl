---
title: 'IXCLRDataProcess:: EndEnumMethodInstancesByAddress, Metoda'
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
ms.openlocfilehash: 04ce8f44b0c9f532951666de7bfb9de475c14746
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2020
ms.locfileid: "83395258"
---
# <a name="ixclrdataprocessendenummethodinstancesbyaddress-method"></a><span data-ttu-id="fa669-102">IXCLRDataProcess:: EndEnumMethodInstancesByAddress, Metoda</span><span class="sxs-lookup"><span data-stu-id="fa669-102">IXCLRDataProcess::EndEnumMethodInstancesByAddress Method</span></span>

<span data-ttu-id="fa669-103">Zwalnia zasoby używane przez Iteratory wewnętrzne używane podczas wyliczania wystąpień.</span><span class="sxs-lookup"><span data-stu-id="fa669-103">Releases the resources used by internal iterators used during instance enumeration.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="fa669-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fa669-104">Syntax</span></span>

```cpp
HRESULT EndEnumMethodInstancesByAddress(
    [in] CLRDATA_ENUM handle
);
```

## <a name="parameters"></a><span data-ttu-id="fa669-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fa669-105">Parameters</span></span>

`handle`\
<span data-ttu-id="fa669-106">określoną Dojście do wyliczania wystąpień metod.</span><span class="sxs-lookup"><span data-stu-id="fa669-106">[out] A handle for enumerating the method instances.</span></span>

## <a name="remarks"></a><span data-ttu-id="fa669-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fa669-107">Remarks</span></span>

<span data-ttu-id="fa669-108">Podana metoda jest częścią `IXCLRDataProcess` interfejsu i odpowiada 30emu gnieździe tabeli metody wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="fa669-108">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 30th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="fa669-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fa669-109">Requirements</span></span>

<span data-ttu-id="fa669-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fa669-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="fa669-111">**Nagłówek:** Dawaj</span><span class="sxs-lookup"><span data-stu-id="fa669-111">**Header:** None</span></span>  
<span data-ttu-id="fa669-112">**Biblioteka:** Dawaj</span><span class="sxs-lookup"><span data-stu-id="fa669-112">**Library:** None</span></span>  
<span data-ttu-id="fa669-113">**.NET Framework wersje:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="fa669-113">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="fa669-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fa669-114">See also</span></span>

- [<span data-ttu-id="fa669-115">CLRDataSourceType, Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="fa669-115">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="fa669-116">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="fa669-116">Debugging</span></span>](index.md)
- [<span data-ttu-id="fa669-117">IXCLRDataProcess, interfejs</span><span class="sxs-lookup"><span data-stu-id="fa669-117">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
