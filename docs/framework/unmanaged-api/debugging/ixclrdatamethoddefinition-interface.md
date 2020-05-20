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
ms.openlocfilehash: ebb689eee4a89a70e81d8f9d958e7826c3b3421b
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420958"
---
# <a name="ixclrdatamethoddefinition-interface"></a><span data-ttu-id="62afa-102">IXCLRDataMethodDefinition, interfejs</span><span class="sxs-lookup"><span data-stu-id="62afa-102">IXCLRDataMethodDefinition Interface</span></span>

<span data-ttu-id="62afa-103">Zapewnia metody wykonywania zapytań dotyczących informacji o definicji metody.</span><span class="sxs-lookup"><span data-stu-id="62afa-103">Provides methods for querying information about a method definition.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a><span data-ttu-id="62afa-104">Metody</span><span class="sxs-lookup"><span data-stu-id="62afa-104">Methods</span></span>

<span data-ttu-id="62afa-105">Poniżej przedstawiono metody dostępne w interfejsie.</span><span class="sxs-lookup"><span data-stu-id="62afa-105">The following methods are some of the methods available in the interface.</span></span>

| <span data-ttu-id="62afa-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="62afa-106">Method</span></span>                                                                                                                          | <span data-ttu-id="62afa-107">Opis</span><span class="sxs-lookup"><span data-stu-id="62afa-107">Description</span></span>                                                                                 |
| ------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- |
| [<span data-ttu-id="62afa-108">StartEnumInstances</span><span class="sxs-lookup"><span data-stu-id="62afa-108">StartEnumInstances</span></span>](ixclrdatamethoddefinition-startenuminstances-method.md) | <span data-ttu-id="62afa-109">Zapewnia obsługę wyliczania wystąpień metody dla danego elementu `IXCLRDataAppDomain` .</span><span class="sxs-lookup"><span data-stu-id="62afa-109">Provides a handle for the enumeration of method instances for a given `IXCLRDataAppDomain`.</span></span> |
| [<span data-ttu-id="62afa-110">EnumInstance</span><span class="sxs-lookup"><span data-stu-id="62afa-110">EnumInstance</span></span>](ixclrdatamethoddefinition-enuminstance-method.md)             | <span data-ttu-id="62afa-111">Wylicza wystąpienia tej definicji metody.</span><span class="sxs-lookup"><span data-stu-id="62afa-111">Enumerates the instances of this method definition.</span></span>                                         |
| [<span data-ttu-id="62afa-112">EndEnumInstances</span><span class="sxs-lookup"><span data-stu-id="62afa-112">EndEnumInstances</span></span>](ixclrdatamethoddefinition-endenuminstances-method.md)     | <span data-ttu-id="62afa-113">Zwalnia zasoby używane przez Iteratory wewnętrzne używane podczas wyliczania wystąpień.</span><span class="sxs-lookup"><span data-stu-id="62afa-113">Releases the resources used by internal iterators used during instance enumeration.</span></span>         |

## <a name="remarks"></a><span data-ttu-id="62afa-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="62afa-114">Remarks</span></span>

<span data-ttu-id="62afa-115">Ten interfejs jest wewnątrz środowiska uruchomieniowego i nie jest udostępniany przez żadne nagłówki lub pliki bibliotek.</span><span class="sxs-lookup"><span data-stu-id="62afa-115">This interface lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="62afa-116">Jest to jednak interfejs COM pochodzący z `IUnknown` identyfikatora GUID `AAF60008-FB2C-420b-8FB1-42D244A54A97` , który można uzyskać za pomocą zwykłych mechanizmów com.</span><span class="sxs-lookup"><span data-stu-id="62afa-116">However, it's a COM interface that derives from `IUnknown` with GUID `AAF60008-FB2C-420b-8FB1-42D244A54A97` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="62afa-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="62afa-117">Requirements</span></span>

<span data-ttu-id="62afa-118">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="62afa-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="62afa-119">**Nagłówek:** Dawaj</span><span class="sxs-lookup"><span data-stu-id="62afa-119">**Header:** None</span></span>  
<span data-ttu-id="62afa-120">**Biblioteka:** Dawaj</span><span class="sxs-lookup"><span data-stu-id="62afa-120">**Library:** None</span></span>  
<span data-ttu-id="62afa-121">**.NET Framework wersje:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="62afa-121">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="62afa-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="62afa-122">See also</span></span>

- [<span data-ttu-id="62afa-123">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="62afa-123">Debugging</span></span>](index.md)
- [<span data-ttu-id="62afa-124">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="62afa-124">Debugging Interfaces</span></span>](debugging-interfaces.md)
