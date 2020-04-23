---
title: DacpGetModuleAddress::Metoda żądania
ms.date: 01/16/2019
api.name:
- DacpGetModuleAddress::Request Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- DacpGetModuleAddress::Request Method
helpviewer.keywords:
- DacpGetModuleAddress::Request Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 4dbe6a2c295e5afae1b6761f0c7b695fdb906428
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102910"
---
# <a name="dacpgetmoduleaddressrequest-method"></a><span data-ttu-id="085ca-102">DacpGetModuleAddress::Metoda żądania</span><span class="sxs-lookup"><span data-stu-id="085ca-102">DacpGetModuleAddress::Request Method</span></span>

<span data-ttu-id="085ca-103">Wykonuje żądanie, aby wypełnić strukturę z danej struktury środowiska wykonawczego.</span><span class="sxs-lookup"><span data-stu-id="085ca-103">Performs a request to populate the structure from the given runtime structure.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="085ca-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="085ca-104">Syntax</span></span>

```cpp
HRESULT Request(
    [in] IXCLRDataModule* pDataModule
);
```

## <a name="parameters"></a><span data-ttu-id="085ca-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="085ca-105">Parameters</span></span>

`pDataModule`\
<span data-ttu-id="085ca-106">[w] Wskaźnik do modułu danych źródłowych.</span><span class="sxs-lookup"><span data-stu-id="085ca-106">[in] A pointer to the seed data module.</span></span>

## <a name="remarks"></a><span data-ttu-id="085ca-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="085ca-107">Remarks</span></span>

<span data-ttu-id="085ca-108">Ta struktura znajduje się wewnątrz środowiska wykonawczego i nie jest narażona za pośrednictwem żadnych nagłówków lub plików biblioteki.</span><span class="sxs-lookup"><span data-stu-id="085ca-108">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="085ca-109">Aby go użyć, najprostszym sposobem jest naśladowanie implementacji:</span><span class="sxs-lookup"><span data-stu-id="085ca-109">To use it, the easiest way is to mimic the implementation:</span></span>

- <span data-ttu-id="085ca-110">Zwraca wartość uzyskaną `Request` z wywołania metody na parametr z `IXCLRDataModule*` następującymi parametrami:`((uint32) 0xf0000000, 0, 0, (uint32) sizeof(*this), (uint8*) this)`</span><span class="sxs-lookup"><span data-stu-id="085ca-110">Return the value obtained from calling the `Request` method on the `IXCLRDataModule*` parameter with the following parameters: `((uint32) 0xf0000000, 0, 0, (uint32) sizeof(*this), (uint8*) this)`</span></span>

## <a name="requirements"></a><span data-ttu-id="085ca-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="085ca-111">Requirements</span></span>

<span data-ttu-id="085ca-112">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md)</span><span class="sxs-lookup"><span data-stu-id="085ca-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md)</span></span>\
<span data-ttu-id="085ca-113">**Nagłówek:** Brak</span><span class="sxs-lookup"><span data-stu-id="085ca-113">**Header:** None</span></span>\
<span data-ttu-id="085ca-114">**Biblioteka:** Brak</span><span class="sxs-lookup"><span data-stu-id="085ca-114">**Library:** None</span></span>\
<span data-ttu-id="085ca-115">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="085ca-115">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="085ca-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="085ca-116">See also</span></span>

- [<span data-ttu-id="085ca-117">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="085ca-117">Debugging</span></span>](index.md)
- [<span data-ttu-id="085ca-118">Struktura DacpGetModuleAddress</span><span class="sxs-lookup"><span data-stu-id="085ca-118">DacpGetModuleAddress structure</span></span>](dacpgetmoduleaddress-structure.md)
