---
title: Interfejs IXCLRDataMethodInstance
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
ms.openlocfilehash: 03be79e6300afa6d25a005b0a21b8c2bf15d27be
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/01/2019
ms.locfileid: "57202278"
---
# <a name="ixclrdatamethodinstance-interface"></a><span data-ttu-id="84420-102">Interfejs IXCLRDataMethodInstance</span><span class="sxs-lookup"><span data-stu-id="84420-102">IXCLRDataMethodInstance Interface</span></span>

<span data-ttu-id="84420-103">Udostępnia metody do wykonywania zapytań o wystąpienie metody.</span><span class="sxs-lookup"><span data-stu-id="84420-103">Provides methods for querying information about a method instance.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a><span data-ttu-id="84420-104">Metody</span><span class="sxs-lookup"><span data-stu-id="84420-104">Methods</span></span>

| <span data-ttu-id="84420-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="84420-105">Method</span></span>                                                                                                                  | <span data-ttu-id="84420-106">Opis</span><span class="sxs-lookup"><span data-stu-id="84420-106">Description</span></span>                                 |
| ----------------------------------------------------------------------------------------------------------------------- | ------------------------------------------- |
| [<span data-ttu-id="84420-107">GetILAddressMap</span><span class="sxs-lookup"><span data-stu-id="84420-107">GetILAddressMap</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamethodinstance-getiladdressmap-method.md) | <span data-ttu-id="84420-108">Pobiera IL, aby informacje dotyczące mapowania adresu.</span><span class="sxs-lookup"><span data-stu-id="84420-108">Gets the IL to address mapping information.</span></span> |
| [<span data-ttu-id="84420-109">GetRepresentativeEntryAddress</span><span class="sxs-lookup"><span data-stu-id="84420-109">GetRepresentativeEntryAddress</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamethodinstance-getrepresentativeentryaddress-method.md) | <span data-ttu-id="84420-110">Pobiera najbardziej reprezentatywnej adres punktu wejścia dla natywnej kompilacji wszystkie możliwe punkty wejścia dla metody.</span><span class="sxs-lookup"><span data-stu-id="84420-110">Gets the most representative entry point address for the native compilation of all the possible entry points for a method.</span></span> |


## <a name="remarks"></a><span data-ttu-id="84420-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="84420-111">Remarks</span></span>

<span data-ttu-id="84420-112">Ten interfejs znajduje się wewnątrz środowiska uruchomieniowego i nie jest dostępna za pośrednictwem wszystkich nagłówków lub pliki biblioteki.</span><span class="sxs-lookup"><span data-stu-id="84420-112">This interface lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="84420-113">Jednak jest interfejsem COM, która pochodzi od klasy `IUnknown` o identyfikatorze GUID `ECD73800-22CA-4b0d-AB55-E9BA7E6318A5` , można uzyskać za pośrednictwem zwykłych mechanizmów COM.</span><span class="sxs-lookup"><span data-stu-id="84420-113">However, it's a COM interface that derives from `IUnknown` with GUID `ECD73800-22CA-4b0d-AB55-E9BA7E6318A5` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="84420-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="84420-114">Requirements</span></span>

<span data-ttu-id="84420-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="84420-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="84420-116">**Nagłówek:** Brak</span><span class="sxs-lookup"><span data-stu-id="84420-116">**Header:** None</span></span>  
<span data-ttu-id="84420-117">**Biblioteka:** Brak</span><span class="sxs-lookup"><span data-stu-id="84420-117">**Library:** None</span></span>  
<span data-ttu-id="84420-118">**Wersje programu .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="84420-118">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="84420-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="84420-119">See also</span></span>

- [<span data-ttu-id="84420-120">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="84420-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="84420-121">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="84420-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
