---
title: Interfejs ISOSDacInterface
ms.date: 01/16/2019
api.name:
- ISOSDacInterface Interface
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- ISOSDacInterface Interface
helpviewer.keywords:
- ISOSDacInterface Interface [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 745ecfbffaad841e1ceb9216802644ba9dd5b94e
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2019
ms.locfileid: "54416098"
---
# <a name="isosdacinterface-interface"></a><span data-ttu-id="fec11-102">Interfejs ISOSDacInterface</span><span class="sxs-lookup"><span data-stu-id="fec11-102">ISOSDacInterface Interface</span></span>

<span data-ttu-id="fec11-103">Udostępnia metody pomocnicze na dostęp do danych z `SOS`.</span><span class="sxs-lookup"><span data-stu-id="fec11-103">Provides helper methods to access data from `SOS`.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a><span data-ttu-id="fec11-104">Metody</span><span class="sxs-lookup"><span data-stu-id="fec11-104">Methods</span></span>

| <span data-ttu-id="fec11-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="fec11-105">Method</span></span>                                                                                                               | <span data-ttu-id="fec11-106">Opis</span><span class="sxs-lookup"><span data-stu-id="fec11-106">Description</span></span>                                                                                                                   |
| -------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------- |
| [<span data-ttu-id="fec11-107">GetMethodDescData</span><span class="sxs-lookup"><span data-stu-id="fec11-107">GetMethodDescData</span></span>](../../../../docs/framework/unmanaged-api/debugging/isosdacinterface-getmethoddescdata-method.md) | <span data-ttu-id="fec11-108">Pobiera dane dla danego [MethodDesc](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md).</span><span class="sxs-lookup"><span data-stu-id="fec11-108">Gets the data for the given [MethodDesc](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md).</span></span> |

## <a name="remarks"></a><span data-ttu-id="fec11-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fec11-109">Remarks</span></span>

<span data-ttu-id="fec11-110">Ten interfejs znajduje się wewnątrz środowiska uruchomieniowego i nie jest dostępna za pośrednictwem wszystkich nagłówków lub pliki biblioteki.</span><span class="sxs-lookup"><span data-stu-id="fec11-110">This interface lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="fec11-111">Jednak jest interfejsem COM, która pochodzi od klasy `IUnknown` o identyfikatorze GUID `436f00f2-b42a-4b9f-870c-e73db66ae930` , można uzyskać za pośrednictwem zwykłych mechanizmów COM.</span><span class="sxs-lookup"><span data-stu-id="fec11-111">However, it's a COM interface that derives from `IUnknown` with GUID `436f00f2-b42a-4b9f-870c-e73db66ae930` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="fec11-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fec11-112">Requirements</span></span>

<span data-ttu-id="fec11-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fec11-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="fec11-114">**Nagłówek:** Brak</span><span class="sxs-lookup"><span data-stu-id="fec11-114">**Header:** None</span></span>  
<span data-ttu-id="fec11-115">**Biblioteka:** Brak</span><span class="sxs-lookup"><span data-stu-id="fec11-115">**Library:** None</span></span>  
<span data-ttu-id="fec11-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="fec11-116">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="fec11-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fec11-117">See Also</span></span>

- [<span data-ttu-id="fec11-118">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="fec11-118">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="fec11-119">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="fec11-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
