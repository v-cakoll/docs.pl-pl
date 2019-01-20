---
title: Interfejs IXCLRDataModule
ms.date: 01/16/2019
api.name:
- IXCLRDataModule Interface
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataModule Interface
helpviewer.keywords:
- IXCLRDataModule Interface [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: e306834166051ae48fd283d51f18d9458091578f
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2019
ms.locfileid: "54416173"
---
# <a name="ixclrdatamodule-interface"></a><span data-ttu-id="c8982-102">Interfejs IXCLRDataModule</span><span class="sxs-lookup"><span data-stu-id="c8982-102">IXCLRDataModule Interface</span></span>

<span data-ttu-id="c8982-103">Udostępnia metody do wykonywania zapytań o załadowanym module.</span><span class="sxs-lookup"><span data-stu-id="c8982-103">Provides methods for querying information about a loaded module.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a><span data-ttu-id="c8982-104">Metody</span><span class="sxs-lookup"><span data-stu-id="c8982-104">Methods</span></span>

| <span data-ttu-id="c8982-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="c8982-105">Method</span></span>                                                                                                                                | <span data-ttu-id="c8982-106">Opis</span><span class="sxs-lookup"><span data-stu-id="c8982-106">Description</span></span>                                                         |
| ------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="c8982-107">GetMethodDefinitionByToken</span><span class="sxs-lookup"><span data-stu-id="c8982-107">GetMethodDefinitionByToken</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamodule-getmethoddefinitionbytoken-method.md) | <span data-ttu-id="c8982-108">Pobiera definicję metody odpowiadającej token określonych metadanych.</span><span class="sxs-lookup"><span data-stu-id="c8982-108">Gets the method definition corresponding to a given metadata token.</span></span> |
| [<span data-ttu-id="c8982-109">Żądanie</span><span class="sxs-lookup"><span data-stu-id="c8982-109">Request</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamodule-request-method.md)                                       | <span data-ttu-id="c8982-110">Żądania do buforu, biorąc pod uwagę przy użyciu danych modułu wypełniania.</span><span class="sxs-lookup"><span data-stu-id="c8982-110">Requests to populate the buffer given with the module's data.</span></span>       |
| [<span data-ttu-id="c8982-111">GetVersionId</span><span class="sxs-lookup"><span data-stu-id="c8982-111">GetVersionId</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamodule-getversionid-method.md)                             | <span data-ttu-id="c8982-112">Pobiera identyfikatorem wersji modułu.</span><span class="sxs-lookup"><span data-stu-id="c8982-112">Gets the module's version ID.</span></span>                                       |

## <a name="remarks"></a><span data-ttu-id="c8982-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c8982-113">Remarks</span></span>

<span data-ttu-id="c8982-114">Ten interfejs znajduje się wewnątrz środowiska uruchomieniowego i nie jest dostępna za pośrednictwem wszystkich nagłówków lub pliki biblioteki.</span><span class="sxs-lookup"><span data-stu-id="c8982-114">This interface lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="c8982-115">Jednak jest interfejsem COM, która pochodzi od klasy `IUnknown` o identyfikatorze GUID `88E32849-0A0A-4cb0-9022-7CD2E9E139E2` , można uzyskać za pośrednictwem zwykłych mechanizmów COM.</span><span class="sxs-lookup"><span data-stu-id="c8982-115">However, it's a COM interface that derives from `IUnknown` with GUID `88E32849-0A0A-4cb0-9022-7CD2E9E139E2` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="c8982-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c8982-116">Requirements</span></span>

<span data-ttu-id="c8982-117">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c8982-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="c8982-118">**Nagłówek:** Brak</span><span class="sxs-lookup"><span data-stu-id="c8982-118">**Header:** None</span></span>  
<span data-ttu-id="c8982-119">**Biblioteka:** Brak</span><span class="sxs-lookup"><span data-stu-id="c8982-119">**Library:** None</span></span>  
<span data-ttu-id="c8982-120">**Wersje programu .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="c8982-120">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="c8982-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c8982-121">See Also</span></span>

- [<span data-ttu-id="c8982-122">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="c8982-122">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="c8982-123">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="c8982-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
