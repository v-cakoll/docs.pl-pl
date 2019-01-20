---
title: Interfejs IXCLRDataMethodInstance
ms.date: 01/16/2019
api.name:
- IXCLRDataMethodInstance Interface
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataMethodInstance Interface
helpviewer.keywords:
- IXCLRDataMethodInstance Interface [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 5bf724bc76591ae59c073b5b9a788ca065f51dc0
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2019
ms.locfileid: "54416101"
---
# <a name="ixclrdatamethodinstance-interface"></a><span data-ttu-id="739e2-102">Interfejs IXCLRDataMethodInstance</span><span class="sxs-lookup"><span data-stu-id="739e2-102">IXCLRDataMethodInstance Interface</span></span>

<span data-ttu-id="739e2-103">Udostępnia metody do wykonywania zapytań o wystąpienie metody.</span><span class="sxs-lookup"><span data-stu-id="739e2-103">Provides methods for querying information about a method instance.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a><span data-ttu-id="739e2-104">Metody</span><span class="sxs-lookup"><span data-stu-id="739e2-104">Methods</span></span>

| <span data-ttu-id="739e2-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="739e2-105">Method</span></span>                                                                                                                  | <span data-ttu-id="739e2-106">Opis</span><span class="sxs-lookup"><span data-stu-id="739e2-106">Description</span></span>                                 |
| ----------------------------------------------------------------------------------------------------------------------- | ------------------------------------------- |
| [<span data-ttu-id="739e2-107">GetILAddressMap</span><span class="sxs-lookup"><span data-stu-id="739e2-107">GetILAddressMap</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamethodinstance-getiladdressmap-method.md) | <span data-ttu-id="739e2-108">Pobiera IL, aby informacje dotyczące mapowania adresu.</span><span class="sxs-lookup"><span data-stu-id="739e2-108">Gets the IL to address mapping information.</span></span> |

## <a name="remarks"></a><span data-ttu-id="739e2-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="739e2-109">Remarks</span></span>

<span data-ttu-id="739e2-110">Ten interfejs znajduje się wewnątrz środowiska uruchomieniowego i nie jest dostępna za pośrednictwem wszystkich nagłówków lub pliki biblioteki.</span><span class="sxs-lookup"><span data-stu-id="739e2-110">This interface lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="739e2-111">Jednak jest interfejsem COM, która pochodzi od klasy `IUnknown` o identyfikatorze GUID `ECD73800-22CA-4b0d-AB55-E9BA7E6318A5` , można uzyskać za pośrednictwem zwykłych mechanizmów COM.</span><span class="sxs-lookup"><span data-stu-id="739e2-111">However, it's a COM interface that derives from `IUnknown` with GUID `ECD73800-22CA-4b0d-AB55-E9BA7E6318A5` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="739e2-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="739e2-112">Requirements</span></span>

<span data-ttu-id="739e2-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="739e2-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="739e2-114">**Nagłówek:** Brak</span><span class="sxs-lookup"><span data-stu-id="739e2-114">**Header:** None</span></span>  
<span data-ttu-id="739e2-115">**Biblioteka:** Brak</span><span class="sxs-lookup"><span data-stu-id="739e2-115">**Library:** None</span></span>  
<span data-ttu-id="739e2-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="739e2-116">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="739e2-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="739e2-117">See Also</span></span>

- [<span data-ttu-id="739e2-118">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="739e2-118">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="739e2-119">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="739e2-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
