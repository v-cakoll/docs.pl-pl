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
ms.openlocfilehash: 3cc3b0258381b10c27dd58bee66dbb6b2cf5b2c8
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57351089"
---
# <a name="dacpgetmoduleaddressrequest-method"></a><span data-ttu-id="0c41d-102">DacpGetModuleAddress::Request Method</span><span class="sxs-lookup"><span data-stu-id="0c41d-102">DacpGetModuleAddress::Request Method</span></span>

<span data-ttu-id="0c41d-103">Wykonuje żądanie, aby wypełnić struktury ze struktury danego środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="0c41d-103">Performs a request to populate the structure from the given runtime structure.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="0c41d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0c41d-104">Syntax</span></span>

```
HRESULT Request(
    [in] IXCLRDataModule* pDataModule
);
```

## <a name="parameters"></a><span data-ttu-id="0c41d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0c41d-105">Parameters</span></span>

`pDataModule`\
<span data-ttu-id="0c41d-106">[in] Wskaźnik do modułu danych inicjatora.</span><span class="sxs-lookup"><span data-stu-id="0c41d-106">[in] A pointer to the seed data module.</span></span>

## <a name="remarks"></a><span data-ttu-id="0c41d-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0c41d-107">Remarks</span></span>

<span data-ttu-id="0c41d-108">Ta struktura znajduje się wewnątrz środowiska uruchomieniowego i nie jest dostępna za pośrednictwem wszystkich nagłówków lub pliki biblioteki.</span><span class="sxs-lookup"><span data-stu-id="0c41d-108">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="0c41d-109">Aby go użyć, najprostszym sposobem jest naśladować wdrożenia:</span><span class="sxs-lookup"><span data-stu-id="0c41d-109">To use it, the easiest way is to mimic the implementation:</span></span>

- <span data-ttu-id="0c41d-110">Zwraca wartość uzyskany z wywołania `Request` metody `IXCLRDataModule*` parametru z następującymi parametrami: `((uint32) 0xf0000000, 0, 0, (uint32) sizeof(*this), (uint8*) this)`</span><span class="sxs-lookup"><span data-stu-id="0c41d-110">Return the value obtained from calling the `Request` method on the `IXCLRDataModule*` parameter with the following parameters: `((uint32) 0xf0000000, 0, 0, (uint32) sizeof(*this), (uint8*) this)`</span></span>


## <a name="requirements"></a><span data-ttu-id="0c41d-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0c41d-111">Requirements</span></span>

<span data-ttu-id="0c41d-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0c41d-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="0c41d-113">**Nagłówek:** Brak</span><span class="sxs-lookup"><span data-stu-id="0c41d-113">**Header:** None</span></span>     
<span data-ttu-id="0c41d-114">**Biblioteka:** Brak</span><span class="sxs-lookup"><span data-stu-id="0c41d-114">**Library:** None</span></span>  
<span data-ttu-id="0c41d-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="0c41d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="0c41d-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0c41d-116">See also</span></span>

- [<span data-ttu-id="0c41d-117">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="0c41d-117">Debugging</span></span>](index.md)
- [<span data-ttu-id="0c41d-118">DacpGetModuleAddress Interface</span><span class="sxs-lookup"><span data-stu-id="0c41d-118">DacpGetModuleAddress Interface</span></span>](dacpgetmoduleaddress-structure.md)