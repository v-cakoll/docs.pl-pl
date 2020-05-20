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
ms.openlocfilehash: 3c2bc771c0a131329b9403c99a33ca7b79023771
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420854"
---
# <a name="ixclrdatamodule-interface"></a><span data-ttu-id="54fc4-102">IXCLRDataModule, interfejs</span><span class="sxs-lookup"><span data-stu-id="54fc4-102">IXCLRDataModule Interface</span></span>

<span data-ttu-id="54fc4-103">Zapewnia metody wykonywania zapytania o informacje o załadowanym module.</span><span class="sxs-lookup"><span data-stu-id="54fc4-103">Provides methods for querying information about a loaded module.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a><span data-ttu-id="54fc4-104">Metody</span><span class="sxs-lookup"><span data-stu-id="54fc4-104">Methods</span></span>

| <span data-ttu-id="54fc4-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="54fc4-105">Method</span></span>                                                                                                                                | <span data-ttu-id="54fc4-106">Opis</span><span class="sxs-lookup"><span data-stu-id="54fc4-106">Description</span></span>                                                         |
| ------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="54fc4-107">GetMethodDefinitionByToken</span><span class="sxs-lookup"><span data-stu-id="54fc4-107">GetMethodDefinitionByToken</span></span>](ixclrdatamodule-getmethoddefinitionbytoken-method.md) | <span data-ttu-id="54fc4-108">Pobiera definicję metody odpowiadającą danemu tokenowi metadanych.</span><span class="sxs-lookup"><span data-stu-id="54fc4-108">Gets the method definition corresponding to a given metadata token.</span></span> |
| [<span data-ttu-id="54fc4-109">Żądanie</span><span class="sxs-lookup"><span data-stu-id="54fc4-109">Request</span></span>](ixclrdatamodule-request-method.md)                                       | <span data-ttu-id="54fc4-110">Żądania wypełnienia buforu podanego za pomocą danych modułu.</span><span class="sxs-lookup"><span data-stu-id="54fc4-110">Requests to populate the buffer given with the module's data.</span></span>       |
| [<span data-ttu-id="54fc4-111">GetVersionId</span><span class="sxs-lookup"><span data-stu-id="54fc4-111">GetVersionId</span></span>](ixclrdatamodule-getversionid-method.md)                             | <span data-ttu-id="54fc4-112">Pobiera identyfikator wersji modułu.</span><span class="sxs-lookup"><span data-stu-id="54fc4-112">Gets the module's version ID.</span></span>                                       |

## <a name="remarks"></a><span data-ttu-id="54fc4-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="54fc4-113">Remarks</span></span>

<span data-ttu-id="54fc4-114">Ten interfejs jest wewnątrz środowiska uruchomieniowego i nie jest udostępniany przez żadne nagłówki lub pliki bibliotek.</span><span class="sxs-lookup"><span data-stu-id="54fc4-114">This interface lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="54fc4-115">Jest to jednak interfejs COM pochodzący z `IUnknown` identyfikatora GUID `88E32849-0A0A-4cb0-9022-7CD2E9E139E2` , który można uzyskać za pomocą zwykłych mechanizmów com.</span><span class="sxs-lookup"><span data-stu-id="54fc4-115">However, it's a COM interface that derives from `IUnknown` with GUID `88E32849-0A0A-4cb0-9022-7CD2E9E139E2` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="54fc4-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="54fc4-116">Requirements</span></span>

<span data-ttu-id="54fc4-117">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="54fc4-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="54fc4-118">**Nagłówek:** Dawaj</span><span class="sxs-lookup"><span data-stu-id="54fc4-118">**Header:** None</span></span>  
<span data-ttu-id="54fc4-119">**Biblioteka:** Dawaj</span><span class="sxs-lookup"><span data-stu-id="54fc4-119">**Library:** None</span></span>  
<span data-ttu-id="54fc4-120">**.NET Framework wersje:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="54fc4-120">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="54fc4-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="54fc4-121">See also</span></span>

- [<span data-ttu-id="54fc4-122">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="54fc4-122">Debugging</span></span>](index.md)
- [<span data-ttu-id="54fc4-123">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="54fc4-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
