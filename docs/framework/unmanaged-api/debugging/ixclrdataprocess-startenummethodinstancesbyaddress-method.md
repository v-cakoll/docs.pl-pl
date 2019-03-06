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
ms.openlocfilehash: 8d0494e53705493de814ed4d4caa869e1e8a700f
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57374573"
---
# <a name="ixclrdataprocessstartenummethodinstancesbyaddress-method"></a><span data-ttu-id="1a572-102">Metoda IXCLRDataProcess::StartEnumMethodInstancesByAddress</span><span class="sxs-lookup"><span data-stu-id="1a572-102">IXCLRDataProcess::StartEnumMethodInstancesByAddress Method</span></span>

<span data-ttu-id="1a572-103">Udostępnia dojścia wyliczania wystąpień metoda `AppDomain` Rozpoczynanie pod danym adresem.</span><span class="sxs-lookup"><span data-stu-id="1a572-103">Provides a handle to enumerate the method instances of `AppDomain` starting at a given address.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="1a572-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1a572-104">Syntax</span></span>

```
HRESULT StartEnumMethodInstancesByAddress(
    [in] CLRDATA_ADDRESS     address,
    [in] IXCLRDataAppDomain *appDomain,
    [out] CLRDATA_ENUM      *handle
);
```

### <a name="parameters"></a><span data-ttu-id="1a572-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1a572-105">Parameters</span></span>

`address`\
<span data-ttu-id="1a572-106">[in] Adres pierwszego wystąpienia metody.</span><span class="sxs-lookup"><span data-stu-id="1a572-106">[in] The address of the first method instance.</span></span>

`appDomain`\
<span data-ttu-id="1a572-107">[in] Element AppDomain wystąpienia metody.</span><span class="sxs-lookup"><span data-stu-id="1a572-107">[in] The AppDomain of the method instances.</span></span>

`handle`\
<span data-ttu-id="1a572-108">[out] Dojście do wyliczania wystąpień metody.</span><span class="sxs-lookup"><span data-stu-id="1a572-108">[out] A handle for enumerating the method instances.</span></span>

## <a name="remarks"></a><span data-ttu-id="1a572-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1a572-109">Remarks</span></span>

<span data-ttu-id="1a572-110">Podana metoda jest częścią `IXCLRDataProcess` interfejs i odnosi się do 27 gniazda tabeli metod wirtualnych.</span><span class="sxs-lookup"><span data-stu-id="1a572-110">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 27th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="1a572-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1a572-111">Requirements</span></span>

<span data-ttu-id="1a572-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1a572-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="1a572-113">**Nagłówek:** Brak</span><span class="sxs-lookup"><span data-stu-id="1a572-113">**Header:** None</span></span>  
<span data-ttu-id="1a572-114">**Biblioteka:** Brak</span><span class="sxs-lookup"><span data-stu-id="1a572-114">**Library:** None</span></span>  
<span data-ttu-id="1a572-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="1a572-115">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="1a572-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1a572-116">See also</span></span>

- [<span data-ttu-id="1a572-117">Wyliczenie CLRDataSourceType</span><span class="sxs-lookup"><span data-stu-id="1a572-117">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="1a572-118">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="1a572-118">Debugging</span></span>](index.md)
- [<span data-ttu-id="1a572-119">Interfejs IXCLRDataProcess</span><span class="sxs-lookup"><span data-stu-id="1a572-119">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
