---
title: ISOSDacInterface, interfejs
ms.date: 02/01/2019
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
ms.openlocfilehash: ccaf479fc4fb90007b4999e95ee03bdd0529321e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61922151"
---
# <a name="isosdacinterface-interface"></a><span data-ttu-id="ca70c-102">ISOSDacInterface, interfejs</span><span class="sxs-lookup"><span data-stu-id="ca70c-102">ISOSDacInterface Interface</span></span>

<span data-ttu-id="ca70c-103">Udostępnia metody pomocnicze na dostęp do danych z `SOS`.</span><span class="sxs-lookup"><span data-stu-id="ca70c-103">Provides helper methods to access data from `SOS`.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a><span data-ttu-id="ca70c-104">Metody</span><span class="sxs-lookup"><span data-stu-id="ca70c-104">Methods</span></span>

| <span data-ttu-id="ca70c-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="ca70c-105">Method</span></span>                                                                                                               | <span data-ttu-id="ca70c-106">Opis</span><span class="sxs-lookup"><span data-stu-id="ca70c-106">Description</span></span>                                                                                                                   |
| -------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------- |
| [<span data-ttu-id="ca70c-107">GetMethodDescData</span><span class="sxs-lookup"><span data-stu-id="ca70c-107">GetMethodDescData</span></span>](../../../../docs/framework/unmanaged-api/debugging/isosdacinterface-getmethoddescdata-method.md) | <span data-ttu-id="ca70c-108">Pobiera dane dla danego wskaźnika MethodDesc.</span><span class="sxs-lookup"><span data-stu-id="ca70c-108">Gets the data for the given MethodDesc pointer.</span></span> |
| [<span data-ttu-id="ca70c-109">GetMethodDescPtrFromIP</span><span class="sxs-lookup"><span data-stu-id="ca70c-109">GetMethodDescPtrFromIP</span></span>](../../../../docs/framework/unmanaged-api/debugging/isosdacinterface-getmethoddescptrfromip-method.md) | <span data-ttu-id="ca70c-110">Pobiera wskaźnik MethodDesc odpowiadającej metody zawierającą adres instrukcji natywnych.</span><span class="sxs-lookup"><span data-stu-id="ca70c-110">Retrieves the pointer of the MethodDesc corresponding the method containing the given native instruction address.</span></span> |
| [<span data-ttu-id="ca70c-111">GetModuleData</span><span class="sxs-lookup"><span data-stu-id="ca70c-111">GetModuleData</span></span>](../../../../docs/framework/unmanaged-api/debugging/isosdacinterface-getmoduledata-method.md)| <span data-ttu-id="ca70c-112">Pobiera dane, odpowiadające moduł, który został załadowany pod danym adresem.</span><span class="sxs-lookup"><span data-stu-id="ca70c-112">Fetches the data corresponding to the module loaded at a given address.</span></span> |

## <a name="remarks"></a><span data-ttu-id="ca70c-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ca70c-113">Remarks</span></span>

<span data-ttu-id="ca70c-114">Ten interfejs znajduje się wewnątrz środowiska uruchomieniowego i nie jest dostępna za pośrednictwem wszystkich nagłówków lub pliki biblioteki.</span><span class="sxs-lookup"><span data-stu-id="ca70c-114">This interface lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="ca70c-115">Jednak jest interfejsem COM, która pochodzi od klasy `IUnknown` o identyfikatorze GUID `436f00f2-b42a-4b9f-870c-e73db66ae930` , można uzyskać za pośrednictwem zwykłych mechanizmów COM.</span><span class="sxs-lookup"><span data-stu-id="ca70c-115">However, it's a COM interface that derives from `IUnknown` with GUID `436f00f2-b42a-4b9f-870c-e73db66ae930` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="ca70c-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ca70c-116">Requirements</span></span>

<span data-ttu-id="ca70c-117">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ca70c-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="ca70c-118">**Nagłówek:** Brak</span><span class="sxs-lookup"><span data-stu-id="ca70c-118">**Header:** None</span></span>  
<span data-ttu-id="ca70c-119">**Biblioteka:** Brak</span><span class="sxs-lookup"><span data-stu-id="ca70c-119">**Library:** None</span></span>  
<span data-ttu-id="ca70c-120">**Wersje programu .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="ca70c-120">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="ca70c-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ca70c-121">See also</span></span>

- [<span data-ttu-id="ca70c-122">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="ca70c-122">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="ca70c-123">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="ca70c-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
