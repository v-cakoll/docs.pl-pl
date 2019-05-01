---
title: DacpModuleData, struktura
ms.date: 02/01/2019
api.name:
- DacpModuleData Structure
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- DacpModuleData Structure
helpviewer.keywords:
- DacpModuleData Structure [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: 752d87c5f4a6b8d854a06be8962ee754cdd4622d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61965961"
---
# <a name="dacpmoduledata-structure"></a><span data-ttu-id="dfc4a-102">DacpModuleData, struktura</span><span class="sxs-lookup"><span data-stu-id="dfc4a-102">DacpModuleData Structure</span></span>

<span data-ttu-id="dfc4a-103">Definiuje bufora transportu dla informacje czasu wykonywania modułu.</span><span class="sxs-lookup"><span data-stu-id="dfc4a-103">Defines a transport buffer for a module's runtime information.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="dfc4a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="dfc4a-104">Syntax</span></span>

```
struct DacpModuleData
{
    CLRDATA_ADDRESS Address;
    CLRDATA_ADDRESS File; 
    CLRDATA_ADDRESS  ilBase;
    char payLoad[132];
};
```

## <a name="members"></a><span data-ttu-id="dfc4a-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="dfc4a-105">Members</span></span>

| <span data-ttu-id="dfc4a-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="dfc4a-106">Member</span></span>    | <span data-ttu-id="dfc4a-107">Opis</span><span class="sxs-lookup"><span data-stu-id="dfc4a-107">Description</span></span>                                                             |
| --------- | ----------------------------------------------------------------------- |
| `Address` | <span data-ttu-id="dfc4a-108">Adres obiektu modułu.</span><span class="sxs-lookup"><span data-stu-id="dfc4a-108">Address of the module object.</span></span>                                           |
| `File`    | <span data-ttu-id="dfc4a-109">Wskaźnik do plików przenośnych plików wykonywalnych (PE).</span><span class="sxs-lookup"><span data-stu-id="dfc4a-109">A pointer to the portable executable (PE) file.</span></span>                       |
| `ilBase`  | <span data-ttu-id="dfc4a-110">Adres załadowanego obrazu podstawowego adresu.</span><span class="sxs-lookup"><span data-stu-id="dfc4a-110">The address of the loaded image's base.</span></span>                                 |
| `payLoad` | <span data-ttu-id="dfc4a-111">Bufor ładunku modułu dodatkowe informacje używane przez środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="dfc4a-111">A payload buffer for additional module information used by the runtime.</span></span> |

## <a name="remarks"></a><span data-ttu-id="dfc4a-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="dfc4a-112">Remarks</span></span>

<span data-ttu-id="dfc4a-113">Ta struktura znajduje się wewnątrz środowiska uruchomieniowego i nie jest dostępna za pośrednictwem wszystkich nagłówków lub pliki biblioteki.</span><span class="sxs-lookup"><span data-stu-id="dfc4a-113">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="dfc4a-114">Aby go użyć, definiują strukturę, jak określono powyżej.</span><span class="sxs-lookup"><span data-stu-id="dfc4a-114">To use it, define the structure as specified above.</span></span>

## <a name="requirements"></a><span data-ttu-id="dfc4a-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="dfc4a-115">Requirements</span></span>
<span data-ttu-id="dfc4a-116">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dfc4a-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="dfc4a-117">**Nagłówek:** Brak</span><span class="sxs-lookup"><span data-stu-id="dfc4a-117">**Header:** None</span></span>  
<span data-ttu-id="dfc4a-118">**Biblioteka:** Brak</span><span class="sxs-lookup"><span data-stu-id="dfc4a-118">**Library:** None</span></span>  
<span data-ttu-id="dfc4a-119">**Wersje programu .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="dfc4a-119">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="dfc4a-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dfc4a-120">See also</span></span>

- [<span data-ttu-id="dfc4a-121">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="dfc4a-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="dfc4a-122">Struktury debugowania</span><span class="sxs-lookup"><span data-stu-id="dfc4a-122">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
