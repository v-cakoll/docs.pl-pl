---
title: IXCLRDataMethodDefinition, interfejs
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
ms.openlocfilehash: 708c681a98113a406249a360c2fc81087e5b97f8
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790428"
---
# <a name="ixclrdatamethoddefinition-interface"></a><span data-ttu-id="5946d-102">IXCLRDataMethodDefinition, interfejs</span><span class="sxs-lookup"><span data-stu-id="5946d-102">IXCLRDataMethodDefinition Interface</span></span>

<span data-ttu-id="5946d-103">Zapewnia metody wykonywania zapytań dotyczących informacji o definicji metody.</span><span class="sxs-lookup"><span data-stu-id="5946d-103">Provides methods for querying information about a method definition.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a><span data-ttu-id="5946d-104">Metody</span><span class="sxs-lookup"><span data-stu-id="5946d-104">Methods</span></span>

<span data-ttu-id="5946d-105">Poniżej przedstawiono metody dostępne w interfejsie.</span><span class="sxs-lookup"><span data-stu-id="5946d-105">The following methods are some of the methods available in the interface.</span></span>

| <span data-ttu-id="5946d-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="5946d-106">Method</span></span>                                                                                                                          | <span data-ttu-id="5946d-107">Opis</span><span class="sxs-lookup"><span data-stu-id="5946d-107">Description</span></span>                                                                                 |
| ------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- |
| [<span data-ttu-id="5946d-108">StartEnumInstances</span><span class="sxs-lookup"><span data-stu-id="5946d-108">StartEnumInstances</span></span>](ixclrdatamethoddefinition-startenuminstances-method.md) | <span data-ttu-id="5946d-109">Zapewnia obsługę wyliczania wystąpień metody dla danego `IXCLRDataAppDomain`.</span><span class="sxs-lookup"><span data-stu-id="5946d-109">Provides a handle for the enumeration of method instances for a given `IXCLRDataAppDomain`.</span></span> |
| [<span data-ttu-id="5946d-110">EnumInstance</span><span class="sxs-lookup"><span data-stu-id="5946d-110">EnumInstance</span></span>](ixclrdatamethoddefinition-enuminstance-method.md)             | <span data-ttu-id="5946d-111">Wylicza wystąpienia tej definicji metody.</span><span class="sxs-lookup"><span data-stu-id="5946d-111">Enumerates the instances of this method definition.</span></span>                                         |
| [<span data-ttu-id="5946d-112">EndEnumInstances</span><span class="sxs-lookup"><span data-stu-id="5946d-112">EndEnumInstances</span></span>](ixclrdatamethoddefinition-endenuminstances-method.md)     | <span data-ttu-id="5946d-113">Zwalnia zasoby używane przez Iteratory wewnętrzne używane podczas wyliczania wystąpień.</span><span class="sxs-lookup"><span data-stu-id="5946d-113">Releases the resources used by internal iterators used during instance enumeration.</span></span>         |

## <a name="remarks"></a><span data-ttu-id="5946d-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5946d-114">Remarks</span></span>

<span data-ttu-id="5946d-115">Ten interfejs jest wewnątrz środowiska uruchomieniowego i nie jest udostępniany przez żadne nagłówki lub pliki bibliotek.</span><span class="sxs-lookup"><span data-stu-id="5946d-115">This interface lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="5946d-116">Jest to jednak interfejs COM, który pochodzi od `IUnknown` z identyfikatorem GUID `AAF60008-FB2C-420b-8FB1-42D244A54A97`, który można uzyskać za pomocą zwykłych mechanizmów COM.</span><span class="sxs-lookup"><span data-stu-id="5946d-116">However, it's a COM interface that derives from `IUnknown` with GUID `AAF60008-FB2C-420b-8FB1-42D244A54A97` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="5946d-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5946d-117">Requirements</span></span>

<span data-ttu-id="5946d-118">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5946d-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="5946d-119">**Nagłówek:** Dawaj</span><span class="sxs-lookup"><span data-stu-id="5946d-119">**Header:** None</span></span>  
<span data-ttu-id="5946d-120">**Biblioteka:** Dawaj</span><span class="sxs-lookup"><span data-stu-id="5946d-120">**Library:** None</span></span>  
<span data-ttu-id="5946d-121">**Wersje .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="5946d-121">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="5946d-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5946d-122">See also</span></span>

- [<span data-ttu-id="5946d-123">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="5946d-123">Debugging</span></span>](index.md)
- [<span data-ttu-id="5946d-124">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="5946d-124">Debugging Interfaces</span></span>](debugging-interfaces.md)
