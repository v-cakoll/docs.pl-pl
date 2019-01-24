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
ms.openlocfilehash: c8d6e36687fd43bbc59304eee64dd42eb78101e3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54676526"
---
# <a name="ixclrdatamodule-interface"></a><span data-ttu-id="a27e8-102">Interfejs IXCLRDataModule</span><span class="sxs-lookup"><span data-stu-id="a27e8-102">IXCLRDataModule Interface</span></span>

<span data-ttu-id="a27e8-103">Udostępnia metody do wykonywania zapytań o załadowanym module.</span><span class="sxs-lookup"><span data-stu-id="a27e8-103">Provides methods for querying information about a loaded module.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a><span data-ttu-id="a27e8-104">Metody</span><span class="sxs-lookup"><span data-stu-id="a27e8-104">Methods</span></span>

| <span data-ttu-id="a27e8-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="a27e8-105">Method</span></span>                                                                                                                                | <span data-ttu-id="a27e8-106">Opis</span><span class="sxs-lookup"><span data-stu-id="a27e8-106">Description</span></span>                                                         |
| ------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="a27e8-107">GetMethodDefinitionByToken</span><span class="sxs-lookup"><span data-stu-id="a27e8-107">GetMethodDefinitionByToken</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamodule-getmethoddefinitionbytoken-method.md) | <span data-ttu-id="a27e8-108">Pobiera definicję metody odpowiadającej token określonych metadanych.</span><span class="sxs-lookup"><span data-stu-id="a27e8-108">Gets the method definition corresponding to a given metadata token.</span></span> |
| [<span data-ttu-id="a27e8-109">Żądanie</span><span class="sxs-lookup"><span data-stu-id="a27e8-109">Request</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamodule-request-method.md)                                       | <span data-ttu-id="a27e8-110">Żądania do buforu, biorąc pod uwagę przy użyciu danych modułu wypełniania.</span><span class="sxs-lookup"><span data-stu-id="a27e8-110">Requests to populate the buffer given with the module's data.</span></span>       |
| [<span data-ttu-id="a27e8-111">GetVersionId</span><span class="sxs-lookup"><span data-stu-id="a27e8-111">GetVersionId</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamodule-getversionid-method.md)                             | <span data-ttu-id="a27e8-112">Pobiera identyfikatorem wersji modułu.</span><span class="sxs-lookup"><span data-stu-id="a27e8-112">Gets the module's version ID.</span></span>                                       |

## <a name="remarks"></a><span data-ttu-id="a27e8-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a27e8-113">Remarks</span></span>

<span data-ttu-id="a27e8-114">Ten interfejs znajduje się wewnątrz środowiska uruchomieniowego i nie jest dostępna za pośrednictwem wszystkich nagłówków lub pliki biblioteki.</span><span class="sxs-lookup"><span data-stu-id="a27e8-114">This interface lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="a27e8-115">Jednak jest interfejsem COM, która pochodzi od klasy `IUnknown` o identyfikatorze GUID `88E32849-0A0A-4cb0-9022-7CD2E9E139E2` , można uzyskać za pośrednictwem zwykłych mechanizmów COM.</span><span class="sxs-lookup"><span data-stu-id="a27e8-115">However, it's a COM interface that derives from `IUnknown` with GUID `88E32849-0A0A-4cb0-9022-7CD2E9E139E2` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="a27e8-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a27e8-116">Requirements</span></span>

<span data-ttu-id="a27e8-117">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a27e8-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="a27e8-118">**Nagłówek:** Brak</span><span class="sxs-lookup"><span data-stu-id="a27e8-118">**Header:** None</span></span>  
<span data-ttu-id="a27e8-119">**Biblioteka:** Brak</span><span class="sxs-lookup"><span data-stu-id="a27e8-119">**Library:** None</span></span>  
<span data-ttu-id="a27e8-120">**Wersje programu .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="a27e8-120">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="a27e8-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a27e8-121">See also</span></span>

- [<span data-ttu-id="a27e8-122">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="a27e8-122">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="a27e8-123">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="a27e8-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
