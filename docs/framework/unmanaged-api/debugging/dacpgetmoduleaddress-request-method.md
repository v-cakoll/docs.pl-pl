---
title: DacpGetModuleAddress::Request Method
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
ms.openlocfilehash: 07ad83da2bc608e3c5925664a68eec4a548860e1
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67739231"
---
# <a name="dacpgetmoduleaddressrequest-method"></a><span data-ttu-id="87283-102">DacpGetModuleAddress::Request Method</span><span class="sxs-lookup"><span data-stu-id="87283-102">DacpGetModuleAddress::Request Method</span></span>

<span data-ttu-id="87283-103">Wykonuje żądanie, aby wypełnić struktury ze struktury danego środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="87283-103">Performs a request to populate the structure from the given runtime structure.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="87283-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="87283-104">Syntax</span></span>

```cpp
HRESULT Request(
    [in] IXCLRDataModule* pDataModule
);
```

## <a name="parameters"></a><span data-ttu-id="87283-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="87283-105">Parameters</span></span>

`pDataModule`\
<span data-ttu-id="87283-106">[in] Wskaźnik do modułu danych inicjatora.</span><span class="sxs-lookup"><span data-stu-id="87283-106">[in] A pointer to the seed data module.</span></span>

## <a name="remarks"></a><span data-ttu-id="87283-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="87283-107">Remarks</span></span>

<span data-ttu-id="87283-108">Ta struktura znajduje się wewnątrz środowiska uruchomieniowego i nie jest dostępna za pośrednictwem wszystkich nagłówków lub pliki biblioteki.</span><span class="sxs-lookup"><span data-stu-id="87283-108">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="87283-109">Aby go użyć, najprostszym sposobem jest naśladować wdrożenia:</span><span class="sxs-lookup"><span data-stu-id="87283-109">To use it, the easiest way is to mimic the implementation:</span></span>

- <span data-ttu-id="87283-110">Zwraca wartość uzyskany z wywołania `Request` metody `IXCLRDataModule*` parametru z następującymi parametrami: `((uint32) 0xf0000000, 0, 0, (uint32) sizeof(*this), (uint8*) this)`</span><span class="sxs-lookup"><span data-stu-id="87283-110">Return the value obtained from calling the `Request` method on the `IXCLRDataModule*` parameter with the following parameters: `((uint32) 0xf0000000, 0, 0, (uint32) sizeof(*this), (uint8*) this)`</span></span>

## <a name="requirements"></a><span data-ttu-id="87283-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="87283-111">Requirements</span></span>

<span data-ttu-id="87283-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="87283-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="87283-113">**Nagłówek:** Brak</span><span class="sxs-lookup"><span data-stu-id="87283-113">**Header:** None</span></span>     
<span data-ttu-id="87283-114">**Biblioteka:** Brak</span><span class="sxs-lookup"><span data-stu-id="87283-114">**Library:** None</span></span>  
<span data-ttu-id="87283-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="87283-115">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="87283-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="87283-116">See also</span></span>

- [<span data-ttu-id="87283-117">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="87283-117">Debugging</span></span>](index.md)
- [<span data-ttu-id="87283-118">DacpGetModuleAddress Interface</span><span class="sxs-lookup"><span data-stu-id="87283-118">DacpGetModuleAddress Interface</span></span>](dacpgetmoduleaddress-structure.md)
