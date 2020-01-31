---
title: IXCLRDataModule, interfejs
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
ms.openlocfilehash: 8757642db6c4375cf55d1f7288669c4c8a752a38
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790393"
---
# <a name="ixclrdatamodule-interface"></a><span data-ttu-id="dff02-102">IXCLRDataModule, interfejs</span><span class="sxs-lookup"><span data-stu-id="dff02-102">IXCLRDataModule Interface</span></span>

<span data-ttu-id="dff02-103">Zapewnia metody wykonywania zapytania o informacje o załadowanym module.</span><span class="sxs-lookup"><span data-stu-id="dff02-103">Provides methods for querying information about a loaded module.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a><span data-ttu-id="dff02-104">Metody</span><span class="sxs-lookup"><span data-stu-id="dff02-104">Methods</span></span>

| <span data-ttu-id="dff02-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="dff02-105">Method</span></span>                                                                                                                                | <span data-ttu-id="dff02-106">Opis</span><span class="sxs-lookup"><span data-stu-id="dff02-106">Description</span></span>                                                         |
| ------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="dff02-107">GetMethodDefinitionByToken</span><span class="sxs-lookup"><span data-stu-id="dff02-107">GetMethodDefinitionByToken</span></span>](ixclrdatamodule-getmethoddefinitionbytoken-method.md) | <span data-ttu-id="dff02-108">Pobiera definicję metody odpowiadającą danemu tokenowi metadanych.</span><span class="sxs-lookup"><span data-stu-id="dff02-108">Gets the method definition corresponding to a given metadata token.</span></span> |
| [<span data-ttu-id="dff02-109">Żądanie</span><span class="sxs-lookup"><span data-stu-id="dff02-109">Request</span></span>](ixclrdatamodule-request-method.md)                                       | <span data-ttu-id="dff02-110">Żądania wypełnienia buforu podanego za pomocą danych modułu.</span><span class="sxs-lookup"><span data-stu-id="dff02-110">Requests to populate the buffer given with the module's data.</span></span>       |
| [<span data-ttu-id="dff02-111">GetVersionId</span><span class="sxs-lookup"><span data-stu-id="dff02-111">GetVersionId</span></span>](ixclrdatamodule-getversionid-method.md)                             | <span data-ttu-id="dff02-112">Pobiera identyfikator wersji modułu.</span><span class="sxs-lookup"><span data-stu-id="dff02-112">Gets the module's version ID.</span></span>                                       |

## <a name="remarks"></a><span data-ttu-id="dff02-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="dff02-113">Remarks</span></span>

<span data-ttu-id="dff02-114">Ten interfejs jest wewnątrz środowiska uruchomieniowego i nie jest udostępniany przez żadne nagłówki lub pliki bibliotek.</span><span class="sxs-lookup"><span data-stu-id="dff02-114">This interface lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="dff02-115">Jest to jednak interfejs COM, który pochodzi od `IUnknown` z identyfikatorem GUID `88E32849-0A0A-4cb0-9022-7CD2E9E139E2`, który można uzyskać za pomocą zwykłych mechanizmów COM.</span><span class="sxs-lookup"><span data-stu-id="dff02-115">However, it's a COM interface that derives from `IUnknown` with GUID `88E32849-0A0A-4cb0-9022-7CD2E9E139E2` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="dff02-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="dff02-116">Requirements</span></span>

<span data-ttu-id="dff02-117">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dff02-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="dff02-118">**Nagłówek:** Dawaj</span><span class="sxs-lookup"><span data-stu-id="dff02-118">**Header:** None</span></span>  
<span data-ttu-id="dff02-119">**Biblioteka:** Dawaj</span><span class="sxs-lookup"><span data-stu-id="dff02-119">**Library:** None</span></span>  
<span data-ttu-id="dff02-120">**Wersje .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="dff02-120">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="dff02-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dff02-121">See also</span></span>

- [<span data-ttu-id="dff02-122">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="dff02-122">Debugging</span></span>](index.md)
- [<span data-ttu-id="dff02-123">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="dff02-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
