---
title: IXCLRDataMethodInstance, interfejs
ms.date: 02/01/2019
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
ms.openlocfilehash: f62cbdc4b3e73f0c27492f7ed20b35378654d399
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61775508"
---
# <a name="ixclrdatamethodinstance-interface"></a><span data-ttu-id="cd5a1-102">IXCLRDataMethodInstance, interfejs</span><span class="sxs-lookup"><span data-stu-id="cd5a1-102">IXCLRDataMethodInstance Interface</span></span>

<span data-ttu-id="cd5a1-103">Udostępnia metody do wykonywania zapytań o wystąpienie metody.</span><span class="sxs-lookup"><span data-stu-id="cd5a1-103">Provides methods for querying information about a method instance.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a><span data-ttu-id="cd5a1-104">Metody</span><span class="sxs-lookup"><span data-stu-id="cd5a1-104">Methods</span></span>

| <span data-ttu-id="cd5a1-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="cd5a1-105">Method</span></span>                                                                                                                  | <span data-ttu-id="cd5a1-106">Opis</span><span class="sxs-lookup"><span data-stu-id="cd5a1-106">Description</span></span>                                 |
| ----------------------------------------------------------------------------------------------------------------------- | ------------------------------------------- |
| [<span data-ttu-id="cd5a1-107">GetILAddressMap</span><span class="sxs-lookup"><span data-stu-id="cd5a1-107">GetILAddressMap</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamethodinstance-getiladdressmap-method.md) | <span data-ttu-id="cd5a1-108">Pobiera IL, aby informacje dotyczące mapowania adresu.</span><span class="sxs-lookup"><span data-stu-id="cd5a1-108">Gets the IL to address mapping information.</span></span> |
| [<span data-ttu-id="cd5a1-109">GetRepresentativeEntryAddress</span><span class="sxs-lookup"><span data-stu-id="cd5a1-109">GetRepresentativeEntryAddress</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamethodinstance-getrepresentativeentryaddress-method.md) | <span data-ttu-id="cd5a1-110">Pobiera najbardziej reprezentatywnej adres punktu wejścia dla natywnej kompilacji wszystkie możliwe punkty wejścia dla metody.</span><span class="sxs-lookup"><span data-stu-id="cd5a1-110">Gets the most representative entry point address for the native compilation of all the possible entry points for a method.</span></span> |

## <a name="remarks"></a><span data-ttu-id="cd5a1-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cd5a1-111">Remarks</span></span>

<span data-ttu-id="cd5a1-112">Ten interfejs znajduje się wewnątrz środowiska uruchomieniowego i nie jest dostępna za pośrednictwem wszystkich nagłówków lub pliki biblioteki.</span><span class="sxs-lookup"><span data-stu-id="cd5a1-112">This interface lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="cd5a1-113">Jednak jest interfejsem COM, która pochodzi od klasy `IUnknown` o identyfikatorze GUID `ECD73800-22CA-4b0d-AB55-E9BA7E6318A5` , można uzyskać za pośrednictwem zwykłych mechanizmów COM.</span><span class="sxs-lookup"><span data-stu-id="cd5a1-113">However, it's a COM interface that derives from `IUnknown` with GUID `ECD73800-22CA-4b0d-AB55-E9BA7E6318A5` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="cd5a1-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cd5a1-114">Requirements</span></span>

<span data-ttu-id="cd5a1-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cd5a1-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="cd5a1-116">**Nagłówek:** Brak</span><span class="sxs-lookup"><span data-stu-id="cd5a1-116">**Header:** None</span></span>  
<span data-ttu-id="cd5a1-117">**Biblioteka:** Brak</span><span class="sxs-lookup"><span data-stu-id="cd5a1-117">**Library:** None</span></span>  
<span data-ttu-id="cd5a1-118">**Wersje programu .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="cd5a1-118">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="cd5a1-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cd5a1-119">See also</span></span>

- [<span data-ttu-id="cd5a1-120">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="cd5a1-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="cd5a1-121">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="cd5a1-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
