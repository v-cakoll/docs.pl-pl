---
title: IXCLRDataProcess, interfejs
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess Interface
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess Interface
helpviewer.keywords:
- IXCLRDataProcess Interface [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 6a6def8fc10f04b89aa8d8c735025b01f9b6ddfb
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420763"
---
# <a name="ixclrdataprocess-interface"></a><span data-ttu-id="ebcb5-102">IXCLRDataProcess, interfejs</span><span class="sxs-lookup"><span data-stu-id="ebcb5-102">IXCLRDataProcess Interface</span></span>

<span data-ttu-id="ebcb5-103">Dostarcza metody do wykonywania zapytań dotyczących informacji o procesie.</span><span class="sxs-lookup"><span data-stu-id="ebcb5-103">Provides methods for querying information about a process.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a><span data-ttu-id="ebcb5-104">Metody</span><span class="sxs-lookup"><span data-stu-id="ebcb5-104">Methods</span></span>

| <span data-ttu-id="ebcb5-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="ebcb5-105">Method</span></span>                                                                                                                                               | <span data-ttu-id="ebcb5-106">Opis</span><span class="sxs-lookup"><span data-stu-id="ebcb5-106">Description</span></span>                                                                                     |
| ---------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- |
| [<span data-ttu-id="ebcb5-107">GetAppDomainByUniqueId</span><span class="sxs-lookup"><span data-stu-id="ebcb5-107">GetAppDomainByUniqueId</span></span>](ixclrdataprocess-getappdomainbyuniqueid-method.md)                       | <span data-ttu-id="ebcb5-108">Pobiera `AppDomain` w procesie według jego unikatowego identyfikatora.</span><span class="sxs-lookup"><span data-stu-id="ebcb5-108">Gets an `AppDomain` in a process by its unique id.</span></span>                                              |
| [<span data-ttu-id="ebcb5-109">StartEnumModules</span><span class="sxs-lookup"><span data-stu-id="ebcb5-109">StartEnumModules</span></span>](ixclrdataprocess-startenummodules-method.md)                                   | <span data-ttu-id="ebcb5-110">Udostępnia dojście do wyliczenia modułów procesu.</span><span class="sxs-lookup"><span data-stu-id="ebcb5-110">Provides a handle to enumerate the modules of a process.</span></span>                                        |
| [<span data-ttu-id="ebcb5-111">EnumModule</span><span class="sxs-lookup"><span data-stu-id="ebcb5-111">EnumModule</span></span>](ixclrdataprocess-enummodule-method.md)                                               | <span data-ttu-id="ebcb5-112">Wylicza moduły tego procesu.</span><span class="sxs-lookup"><span data-stu-id="ebcb5-112">Enumerates the modules of this process.</span></span>                                                         |
| [<span data-ttu-id="ebcb5-113">EndEnumModules</span><span class="sxs-lookup"><span data-stu-id="ebcb5-113">EndEnumModules</span></span>](ixclrdataprocess-endenummodules-method.md)                                       | <span data-ttu-id="ebcb5-114">Zwalnia zasoby używane przez Iteratory wewnętrzne używane podczas wyliczania modułu.</span><span class="sxs-lookup"><span data-stu-id="ebcb5-114">Releases the resources used by internal iterators used during module enumeration.</span></span>               |
| [<span data-ttu-id="ebcb5-115">StartEnumMethodInstancesByAddress</span><span class="sxs-lookup"><span data-stu-id="ebcb5-115">StartEnumMethodInstancesByAddress</span></span>](ixclrdataprocess-startenummethodinstancesbyaddress-method.md) | <span data-ttu-id="ebcb5-116">Udostępnia dojście do wyliczenia wystąpień metod, `AppDomain` Zaczynając od danego adresu.</span><span class="sxs-lookup"><span data-stu-id="ebcb5-116">Provides a handle to enumerate the method instances of `AppDomain` starting at a given address.</span></span> |
| [<span data-ttu-id="ebcb5-117">EnumMethodInstanceByAddress</span><span class="sxs-lookup"><span data-stu-id="ebcb5-117">EnumMethodInstanceByAddress</span></span>](ixclrdataprocess-enummethodinstancebyaddress-method.md)             | <span data-ttu-id="ebcb5-118">Wylicza wystąpienia metody tego procesu, rozpoczynając od przesunięcia adresu.</span><span class="sxs-lookup"><span data-stu-id="ebcb5-118">Enumerates the method instances of this process starting at an address offset.</span></span>                  |
| [<span data-ttu-id="ebcb5-119">EndEnumMethodInstancesByAddress</span><span class="sxs-lookup"><span data-stu-id="ebcb5-119">EndEnumMethodInstancesByAddress</span></span>](ixclrdataprocess-endenummethodinstancesbyaddress-method.md)     | <span data-ttu-id="ebcb5-120">Zwalnia zasoby używane przez Iteratory wewnętrzne używane podczas wyliczania wystąpień.</span><span class="sxs-lookup"><span data-stu-id="ebcb5-120">Releases the resources used by internal iterators used during instance enumeration.</span></span>             |

## <a name="remarks"></a><span data-ttu-id="ebcb5-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ebcb5-121">Remarks</span></span>

<span data-ttu-id="ebcb5-122">Ten interfejs jest wewnątrz środowiska uruchomieniowego i nie jest udostępniany przez żadne nagłówki lub pliki bibliotek.</span><span class="sxs-lookup"><span data-stu-id="ebcb5-122">This interface lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="ebcb5-123">Jest to jednak interfejs COM pochodzący z `IUnknown` identyfikatora GUID `5c552ab6-fc09-4cb3-8e36-22fa03c798b7` , który można uzyskać za pomocą zwykłych mechanizmów com.</span><span class="sxs-lookup"><span data-stu-id="ebcb5-123">However, it's a COM interface that derives from `IUnknown` with GUID `5c552ab6-fc09-4cb3-8e36-22fa03c798b7` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="ebcb5-124">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ebcb5-124">Requirements</span></span>

<span data-ttu-id="ebcb5-125">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ebcb5-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>
<span data-ttu-id="ebcb5-126">**Nagłówek:** Dawaj</span><span class="sxs-lookup"><span data-stu-id="ebcb5-126">**Header:** None</span></span>  
<span data-ttu-id="ebcb5-127">**Biblioteka:** Dawaj</span><span class="sxs-lookup"><span data-stu-id="ebcb5-127">**Library:** None</span></span>  
<span data-ttu-id="ebcb5-128">**.NET Framework wersje:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="ebcb5-128">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="ebcb5-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ebcb5-129">See also</span></span>

- [<span data-ttu-id="ebcb5-130">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="ebcb5-130">Debugging</span></span>](index.md)
- [<span data-ttu-id="ebcb5-131">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="ebcb5-131">Debugging Interfaces</span></span>](debugging-interfaces.md)
