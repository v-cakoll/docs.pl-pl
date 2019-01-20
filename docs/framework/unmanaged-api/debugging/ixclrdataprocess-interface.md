---
title: Interfejs IXCLRDataProcess
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
ms.openlocfilehash: 8c98dd42b4ac5593d96478c2286f49ad216a4bc1
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2019
ms.locfileid: "54416167"
---
# <a name="ixclrdataprocess-interface"></a><span data-ttu-id="afdda-102">Interfejs IXCLRDataProcess</span><span class="sxs-lookup"><span data-stu-id="afdda-102">IXCLRDataProcess Interface</span></span>

<span data-ttu-id="afdda-103">Udostępnia metody do wykonywania zapytań informacji dotyczących procesu.</span><span class="sxs-lookup"><span data-stu-id="afdda-103">Provides methods for querying information about a process.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a><span data-ttu-id="afdda-104">Metody</span><span class="sxs-lookup"><span data-stu-id="afdda-104">Methods</span></span>

| <span data-ttu-id="afdda-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="afdda-105">Method</span></span>                                                                                                                                               | <span data-ttu-id="afdda-106">Opis</span><span class="sxs-lookup"><span data-stu-id="afdda-106">Description</span></span>                                                                                     |
| ---------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- |
| [<span data-ttu-id="afdda-107">GetAppDomainByUniqueId</span><span class="sxs-lookup"><span data-stu-id="afdda-107">GetAppDomainByUniqueId</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-getappdomainbyuniqueid-method.md)                       | <span data-ttu-id="afdda-108">Pobiera `AppDomain` w procesie według unikatowego identyfikatora.</span><span class="sxs-lookup"><span data-stu-id="afdda-108">Gets an `AppDomain` in a process by its unique id.</span></span>                                              |
| [<span data-ttu-id="afdda-109">StartEnumModules</span><span class="sxs-lookup"><span data-stu-id="afdda-109">StartEnumModules</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-startenummodules-method.md)                                   | <span data-ttu-id="afdda-110">Zawiera dojście do wyliczenia modułów procesu.</span><span class="sxs-lookup"><span data-stu-id="afdda-110">Provides a handle to enumerate the modules of a process.</span></span>                                        |
| [<span data-ttu-id="afdda-111">EnumModule</span><span class="sxs-lookup"><span data-stu-id="afdda-111">EnumModule</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-enummodule-method.md)                                               | <span data-ttu-id="afdda-112">Wylicza moduły tego procesu.</span><span class="sxs-lookup"><span data-stu-id="afdda-112">Enumerates the modules of this process.</span></span>                                                         |
| [<span data-ttu-id="afdda-113">EndEnumModules</span><span class="sxs-lookup"><span data-stu-id="afdda-113">EndEnumModules</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-endenummodules-method.md)                                       | <span data-ttu-id="afdda-114">Zwalnia zasoby używane przez Iteratory wewnętrzny używany podczas wyliczania modułu.</span><span class="sxs-lookup"><span data-stu-id="afdda-114">Releases the resources used by internal iterators used during module enumeration.</span></span>               |
| [<span data-ttu-id="afdda-115">StartEnumMethodInstancesByAddress</span><span class="sxs-lookup"><span data-stu-id="afdda-115">StartEnumMethodInstancesByAddress</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-startenummethodinstancesbyaddress-method.md) | <span data-ttu-id="afdda-116">Udostępnia dojścia wyliczania wystąpień metoda `AppDomain` Rozpoczynanie pod danym adresem.</span><span class="sxs-lookup"><span data-stu-id="afdda-116">Provides a handle to enumerate the method instances of `AppDomain` starting at a given address.</span></span> |
| [<span data-ttu-id="afdda-117">EnumMethodInstanceByAddress</span><span class="sxs-lookup"><span data-stu-id="afdda-117">EnumMethodInstanceByAddress</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-enummethodinstancebyaddress-method.md)             | <span data-ttu-id="afdda-118">Wylicza wystąpienia metody tego procesu, rozpoczynając od przesunięcia adresu.</span><span class="sxs-lookup"><span data-stu-id="afdda-118">Enumerates the method instances of this process starting at an address offset.</span></span>                  |
| [<span data-ttu-id="afdda-119">EndEnumMethodInstancesByAddress</span><span class="sxs-lookup"><span data-stu-id="afdda-119">EndEnumMethodInstancesByAddress</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-endenummethodinstancesbyaddress-method.md)     | <span data-ttu-id="afdda-120">Zwalnia zasoby używane przez Iteratory wewnętrzny używany podczas wyliczania wystąpień.</span><span class="sxs-lookup"><span data-stu-id="afdda-120">Releases the resources used by internal iterators used during instance enumeration.</span></span>             |

## <a name="remarks"></a><span data-ttu-id="afdda-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="afdda-121">Remarks</span></span>

<span data-ttu-id="afdda-122">Ten interfejs znajduje się wewnątrz środowiska uruchomieniowego i nie jest dostępna za pośrednictwem wszystkich nagłówków lub pliki biblioteki.</span><span class="sxs-lookup"><span data-stu-id="afdda-122">This interface lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="afdda-123">Jednak jest interfejsem COM, która pochodzi od klasy `IUnknown` o identyfikatorze GUID `5c552ab6-fc09-4cb3-8e36-22fa03c798b7` , można uzyskać za pośrednictwem zwykłych mechanizmów COM.</span><span class="sxs-lookup"><span data-stu-id="afdda-123">However, it's a COM interface that derives from `IUnknown` with GUID `5c552ab6-fc09-4cb3-8e36-22fa03c798b7` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="afdda-124">Wymagania</span><span class="sxs-lookup"><span data-stu-id="afdda-124">Requirements</span></span>

<span data-ttu-id="afdda-125">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="afdda-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>   
<span data-ttu-id="afdda-126">**Nagłówek:** Brak</span><span class="sxs-lookup"><span data-stu-id="afdda-126">**Header:** None</span></span>  
<span data-ttu-id="afdda-127">**Biblioteka:** Brak</span><span class="sxs-lookup"><span data-stu-id="afdda-127">**Library:** None</span></span>  
<span data-ttu-id="afdda-128">**Wersje programu .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="afdda-128">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="afdda-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="afdda-129">See Also</span></span>

- [<span data-ttu-id="afdda-130">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="afdda-130">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="afdda-131">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="afdda-131">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
