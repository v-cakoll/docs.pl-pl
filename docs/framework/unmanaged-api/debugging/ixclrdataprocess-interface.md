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
ms.openlocfilehash: e7e53615e38d0ab76f9e7c0a753be3c13780057d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178377"
---
# <a name="ixclrdataprocess-interface"></a><span data-ttu-id="e2ac7-102">IXCLRDataProcess, interfejs</span><span class="sxs-lookup"><span data-stu-id="e2ac7-102">IXCLRDataProcess Interface</span></span>

<span data-ttu-id="e2ac7-103">Zawiera metody wykonywania zapytań o proces.</span><span class="sxs-lookup"><span data-stu-id="e2ac7-103">Provides methods for querying information about a process.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a><span data-ttu-id="e2ac7-104">Metody</span><span class="sxs-lookup"><span data-stu-id="e2ac7-104">Methods</span></span>

| <span data-ttu-id="e2ac7-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="e2ac7-105">Method</span></span>                                                                                                                                               | <span data-ttu-id="e2ac7-106">Opis</span><span class="sxs-lookup"><span data-stu-id="e2ac7-106">Description</span></span>                                                                                     |
| ---------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- |
| [<span data-ttu-id="e2ac7-107">GetAppDomainByUniqueId</span><span class="sxs-lookup"><span data-stu-id="e2ac7-107">GetAppDomainByUniqueId</span></span>](ixclrdataprocess-getappdomainbyuniqueid-method.md)                       | <span data-ttu-id="e2ac7-108">Pobiera `AppDomain` w procesie przez jego unikatowy identyfikator.</span><span class="sxs-lookup"><span data-stu-id="e2ac7-108">Gets an `AppDomain` in a process by its unique id.</span></span>                                              |
| [<span data-ttu-id="e2ac7-109">StartEnumModules</span><span class="sxs-lookup"><span data-stu-id="e2ac7-109">StartEnumModules</span></span>](ixclrdataprocess-startenummodules-method.md)                                   | <span data-ttu-id="e2ac7-110">Zapewnia dojście do wyliczenia modułów procesu.</span><span class="sxs-lookup"><span data-stu-id="e2ac7-110">Provides a handle to enumerate the modules of a process.</span></span>                                        |
| [<span data-ttu-id="e2ac7-111">EnumModule</span><span class="sxs-lookup"><span data-stu-id="e2ac7-111">EnumModule</span></span>](ixclrdataprocess-enummodule-method.md)                                               | <span data-ttu-id="e2ac7-112">Wylicza moduły tego procesu.</span><span class="sxs-lookup"><span data-stu-id="e2ac7-112">Enumerates the modules of this process.</span></span>                                                         |
| [<span data-ttu-id="e2ac7-113">EndEnumModules</span><span class="sxs-lookup"><span data-stu-id="e2ac7-113">EndEnumModules</span></span>](ixclrdataprocess-endenummodules-method.md)                                       | <span data-ttu-id="e2ac7-114">Zwalnia zasoby używane przez wewnętrzne iteratory używane podczas wyliczania modułu.</span><span class="sxs-lookup"><span data-stu-id="e2ac7-114">Releases the resources used by internal iterators used during module enumeration.</span></span>               |
| [<span data-ttu-id="e2ac7-115">StartEnumMethodInstancesByAddress</span><span class="sxs-lookup"><span data-stu-id="e2ac7-115">StartEnumMethodInstancesByAddress</span></span>](ixclrdataprocess-startenummethodinstancesbyaddress-method.md) | <span data-ttu-id="e2ac7-116">Zawiera dojście do wyliczenia `AppDomain` wystąpień metody, począwszy od danego adresu.</span><span class="sxs-lookup"><span data-stu-id="e2ac7-116">Provides a handle to enumerate the method instances of `AppDomain` starting at a given address.</span></span> |
| [<span data-ttu-id="e2ac7-117">EnumMethodInstanceByAddress</span><span class="sxs-lookup"><span data-stu-id="e2ac7-117">EnumMethodInstanceByAddress</span></span>](ixclrdataprocess-enummethodinstancebyaddress-method.md)             | <span data-ttu-id="e2ac7-118">Wylicza wystąpienia metody tego procesu, począwszy od przesunięcia adresu.</span><span class="sxs-lookup"><span data-stu-id="e2ac7-118">Enumerates the method instances of this process starting at an address offset.</span></span>                  |
| [<span data-ttu-id="e2ac7-119">EndEnumMethodInstancesByAddress</span><span class="sxs-lookup"><span data-stu-id="e2ac7-119">EndEnumMethodInstancesByAddress</span></span>](ixclrdataprocess-endenummethodinstancesbyaddress-method.md)     | <span data-ttu-id="e2ac7-120">Zwalnia zasoby używane przez wewnętrzne iteratory używane podczas wyliczania wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="e2ac7-120">Releases the resources used by internal iterators used during instance enumeration.</span></span>             |

## <a name="remarks"></a><span data-ttu-id="e2ac7-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e2ac7-121">Remarks</span></span>

<span data-ttu-id="e2ac7-122">Ten interfejs znajduje się wewnątrz środowiska wykonawczego i nie jest narażony za pośrednictwem żadnych nagłówków lub plików biblioteki.</span><span class="sxs-lookup"><span data-stu-id="e2ac7-122">This interface lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="e2ac7-123">Jednak jest to interfejs COM, który `IUnknown` wywodzi się z guid, `5c552ab6-fc09-4cb3-8e36-22fa03c798b7` które można uzyskać za pośrednictwem zwykłych mechanizmów COM.</span><span class="sxs-lookup"><span data-stu-id="e2ac7-123">However, it's a COM interface that derives from `IUnknown` with GUID `5c552ab6-fc09-4cb3-8e36-22fa03c798b7` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="e2ac7-124">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e2ac7-124">Requirements</span></span>

<span data-ttu-id="e2ac7-125">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e2ac7-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>
<span data-ttu-id="e2ac7-126">**Nagłówek:** Brak</span><span class="sxs-lookup"><span data-stu-id="e2ac7-126">**Header:** None</span></span>  
<span data-ttu-id="e2ac7-127">**Biblioteka:** Brak</span><span class="sxs-lookup"><span data-stu-id="e2ac7-127">**Library:** None</span></span>  
<span data-ttu-id="e2ac7-128">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="e2ac7-128">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="e2ac7-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e2ac7-129">See also</span></span>

- [<span data-ttu-id="e2ac7-130">Debugging</span><span class="sxs-lookup"><span data-stu-id="e2ac7-130">Debugging</span></span>](index.md)
- [<span data-ttu-id="e2ac7-131">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="e2ac7-131">Debugging Interfaces</span></span>](debugging-interfaces.md)
