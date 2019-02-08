---
title: Interfejs ISOSDacInterface
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
ms.sourcegitcommit: 3500c4845f96a91a438a02ef2c6b4eef45a5e2af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/07/2019
ms.locfileid: "55827932"
---
# <a name="isosdacinterface-interface"></a><span data-ttu-id="71453-102">Interfejs ISOSDacInterface</span><span class="sxs-lookup"><span data-stu-id="71453-102">ISOSDacInterface Interface</span></span>

<span data-ttu-id="71453-103">Udostępnia metody pomocnicze na dostęp do danych z `SOS`.</span><span class="sxs-lookup"><span data-stu-id="71453-103">Provides helper methods to access data from `SOS`.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a><span data-ttu-id="71453-104">Metody</span><span class="sxs-lookup"><span data-stu-id="71453-104">Methods</span></span>

| <span data-ttu-id="71453-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="71453-105">Method</span></span>                                                                                                               | <span data-ttu-id="71453-106">Opis</span><span class="sxs-lookup"><span data-stu-id="71453-106">Description</span></span>                                                                                                                   |
| -------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------- |
| [<span data-ttu-id="71453-107">GetMethodDescData</span><span class="sxs-lookup"><span data-stu-id="71453-107">GetMethodDescData</span></span>](../../../../docs/framework/unmanaged-api/debugging/isosdacinterface-getmethoddescdata-method.md) | <span data-ttu-id="71453-108">Pobiera dane dla danego wskaźnika MethodDesc.</span><span class="sxs-lookup"><span data-stu-id="71453-108">Gets the data for the given MethodDesc pointer.</span></span> |
| [<span data-ttu-id="71453-109">GetMethodDescPtrFromIP</span><span class="sxs-lookup"><span data-stu-id="71453-109">GetMethodDescPtrFromIP</span></span>](../../../../docs/framework/unmanaged-api/debugging/isosdacinterface-getmethoddescptrfromip-method.md) | <span data-ttu-id="71453-110">Pobiera wskaźnik MethodDesc odpowiadającej metody zawierającą adres instrukcji natywnych.</span><span class="sxs-lookup"><span data-stu-id="71453-110">Retrieves the pointer of the MethodDesc corresponding the method containing the given native instruction address.</span></span> |
| [<span data-ttu-id="71453-111">GetModuleData</span><span class="sxs-lookup"><span data-stu-id="71453-111">GetModuleData</span></span>](../../../../docs/framework/unmanaged-api/debugging/isosdacinterface-getmoduledata-method.md)| <span data-ttu-id="71453-112">Pobiera dane, odpowiadające moduł, który został załadowany pod danym adresem.</span><span class="sxs-lookup"><span data-stu-id="71453-112">Fetches the data corresponding to the module loaded at a given address.</span></span> |

## <a name="remarks"></a><span data-ttu-id="71453-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="71453-113">Remarks</span></span>

<span data-ttu-id="71453-114">Ten interfejs znajduje się wewnątrz środowiska uruchomieniowego i nie jest dostępna za pośrednictwem wszystkich nagłówków lub pliki biblioteki.</span><span class="sxs-lookup"><span data-stu-id="71453-114">This interface lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="71453-115">Jednak jest interfejsem COM, która pochodzi od klasy `IUnknown` o identyfikatorze GUID `436f00f2-b42a-4b9f-870c-e73db66ae930` , można uzyskać za pośrednictwem zwykłych mechanizmów COM.</span><span class="sxs-lookup"><span data-stu-id="71453-115">However, it's a COM interface that derives from `IUnknown` with GUID `436f00f2-b42a-4b9f-870c-e73db66ae930` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="71453-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="71453-116">Requirements</span></span>

<span data-ttu-id="71453-117">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="71453-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="71453-118">**Nagłówek:** Brak</span><span class="sxs-lookup"><span data-stu-id="71453-118">**Header:** None</span></span>  
<span data-ttu-id="71453-119">**Biblioteka:** Brak</span><span class="sxs-lookup"><span data-stu-id="71453-119">**Library:** None</span></span>  
<span data-ttu-id="71453-120">**Wersje programu .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="71453-120">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="71453-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="71453-121">See also</span></span>

- [<span data-ttu-id="71453-122">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="71453-122">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="71453-123">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="71453-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
