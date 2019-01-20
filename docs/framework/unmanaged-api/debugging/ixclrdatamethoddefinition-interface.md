---
title: Interfejs IXCLRDataMethodDefinition
ms.date: 01/16/2019
api.name:
- IXCLRDataMethodDefinition Interface
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataMethodDefinition Interface
helpviewer.keywords:
- IXCLRDataMethodDefinition Interface [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 4265db62b11453d9fc087928adb0cc0c05c052ca
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2019
ms.locfileid: "54416158"
---
# <a name="ixclrdatamethoddefinition-interface"></a><span data-ttu-id="3e318-102">Interfejs IXCLRDataMethodDefinition</span><span class="sxs-lookup"><span data-stu-id="3e318-102">IXCLRDataMethodDefinition Interface</span></span>

<span data-ttu-id="3e318-103">Udostępnia metody do wykonywania zapytań o definicję metody.</span><span class="sxs-lookup"><span data-stu-id="3e318-103">Provides methods for querying information about a method definition.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a><span data-ttu-id="3e318-104">Metody</span><span class="sxs-lookup"><span data-stu-id="3e318-104">Methods</span></span>

<span data-ttu-id="3e318-105">Poniższych metod przedstawiono niektóre z dostępnych metod w interfejsie.</span><span class="sxs-lookup"><span data-stu-id="3e318-105">The following methods are some of the methods available in the interface.</span></span>

| <span data-ttu-id="3e318-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="3e318-106">Method</span></span>                                                                                                                          | <span data-ttu-id="3e318-107">Opis</span><span class="sxs-lookup"><span data-stu-id="3e318-107">Description</span></span>                                                                                 |
| ------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- |
| [<span data-ttu-id="3e318-108">StartEnumInstances</span><span class="sxs-lookup"><span data-stu-id="3e318-108">StartEnumInstances</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamethoddefinition-startenuminstances-method.md) | <span data-ttu-id="3e318-109">Udostępnia dojścia wyliczania wystąpień metody dla danego `IXCLRDataAppDomain`.</span><span class="sxs-lookup"><span data-stu-id="3e318-109">Provides a handle for the enumeration of method instances for a given `IXCLRDataAppDomain`.</span></span> |
| [<span data-ttu-id="3e318-110">EnumInstance</span><span class="sxs-lookup"><span data-stu-id="3e318-110">EnumInstance</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamethoddefinition-enuminstance-method.md)             | <span data-ttu-id="3e318-111">Wylicza wystąpień tę definicję metody.</span><span class="sxs-lookup"><span data-stu-id="3e318-111">Enumerates the instances of this method definition.</span></span>                                         |
| [<span data-ttu-id="3e318-112">EndEnumInstances</span><span class="sxs-lookup"><span data-stu-id="3e318-112">EndEnumInstances</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamethoddefinition-endenuminstances-method.md)     | <span data-ttu-id="3e318-113">Zwalnia zasoby używane przez Iteratory wewnętrzny używany podczas wyliczania wystąpień.</span><span class="sxs-lookup"><span data-stu-id="3e318-113">Releases the resources used by internal iterators used during instance enumeration.</span></span>         |

## <a name="remarks"></a><span data-ttu-id="3e318-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3e318-114">Remarks</span></span>

<span data-ttu-id="3e318-115">Ten interfejs znajduje się wewnątrz środowiska uruchomieniowego i nie jest dostępna za pośrednictwem wszystkich nagłówków lub pliki biblioteki.</span><span class="sxs-lookup"><span data-stu-id="3e318-115">This interface lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="3e318-116">Jednak jest interfejsem COM, która pochodzi od klasy `IUnknown` o identyfikatorze GUID `AAF60008-FB2C-420b-8FB1-42D244A54A97` , można uzyskać za pośrednictwem zwykłych mechanizmów COM.</span><span class="sxs-lookup"><span data-stu-id="3e318-116">However, it's a COM interface that derives from `IUnknown` with GUID `AAF60008-FB2C-420b-8FB1-42D244A54A97` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="3e318-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3e318-117">Requirements</span></span>

<span data-ttu-id="3e318-118">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3e318-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="3e318-119">**Nagłówek:** Brak</span><span class="sxs-lookup"><span data-stu-id="3e318-119">**Header:** None</span></span>  
<span data-ttu-id="3e318-120">**Biblioteka:** Brak</span><span class="sxs-lookup"><span data-stu-id="3e318-120">**Library:** None</span></span>  
<span data-ttu-id="3e318-121">**Wersje programu .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="3e318-121">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="3e318-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3e318-122">See Also</span></span>

- [<span data-ttu-id="3e318-123">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="3e318-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="3e318-124">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="3e318-124">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
