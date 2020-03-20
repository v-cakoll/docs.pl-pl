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
ms.openlocfilehash: c24bdce64eb7e208bf3830940d7beab1ebf92e78
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179189"
---
# <a name="dacpmoduledata-structure"></a><span data-ttu-id="f6d7c-102">DacpModuleData, struktura</span><span class="sxs-lookup"><span data-stu-id="f6d7c-102">DacpModuleData Structure</span></span>

<span data-ttu-id="f6d7c-103">Definiuje bufor transportu dla informacji o czasie wykonywania modułu.</span><span class="sxs-lookup"><span data-stu-id="f6d7c-103">Defines a transport buffer for a module's runtime information.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="f6d7c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f6d7c-104">Syntax</span></span>

```cpp
struct DacpModuleData
{
    CLRDATA_ADDRESS Address;
    CLRDATA_ADDRESS File;
    CLRDATA_ADDRESS  ilBase;
    char payLoad[132];
};
```

## <a name="members"></a><span data-ttu-id="f6d7c-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="f6d7c-105">Members</span></span>

| <span data-ttu-id="f6d7c-106">Członek</span><span class="sxs-lookup"><span data-stu-id="f6d7c-106">Member</span></span>    | <span data-ttu-id="f6d7c-107">Opis</span><span class="sxs-lookup"><span data-stu-id="f6d7c-107">Description</span></span>                                                             |
| --------- | ----------------------------------------------------------------------- |
| `Address` | <span data-ttu-id="f6d7c-108">Adres obiektu modułu.</span><span class="sxs-lookup"><span data-stu-id="f6d7c-108">Address of the module object.</span></span>                                           |
| `File`    | <span data-ttu-id="f6d7c-109">Wskaźnik do przenośnego pliku wykonywalnego (PE).</span><span class="sxs-lookup"><span data-stu-id="f6d7c-109">A pointer to the portable executable (PE) file.</span></span>                       |
| `ilBase`  | <span data-ttu-id="f6d7c-110">Adres bazy załadowanego obrazu.</span><span class="sxs-lookup"><span data-stu-id="f6d7c-110">The address of the loaded image's base.</span></span>                                 |
| `payLoad` | <span data-ttu-id="f6d7c-111">Bufor ładunku dla dodatkowych informacji o module używanym przez środowisko wykonawcze.</span><span class="sxs-lookup"><span data-stu-id="f6d7c-111">A payload buffer for additional module information used by the runtime.</span></span> |

## <a name="remarks"></a><span data-ttu-id="f6d7c-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f6d7c-112">Remarks</span></span>

<span data-ttu-id="f6d7c-113">Ta struktura znajduje się wewnątrz środowiska wykonawczego i nie jest narażona za pośrednictwem żadnych nagłówków lub plików biblioteki.</span><span class="sxs-lookup"><span data-stu-id="f6d7c-113">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="f6d7c-114">Aby go użyć, należy zdefiniować strukturę, jak określono powyżej.</span><span class="sxs-lookup"><span data-stu-id="f6d7c-114">To use it, define the structure as specified above.</span></span>

## <a name="requirements"></a><span data-ttu-id="f6d7c-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f6d7c-115">Requirements</span></span>
<span data-ttu-id="f6d7c-116">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f6d7c-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="f6d7c-117">**Nagłówek:** Brak</span><span class="sxs-lookup"><span data-stu-id="f6d7c-117">**Header:** None</span></span>  
<span data-ttu-id="f6d7c-118">**Biblioteka:** Brak</span><span class="sxs-lookup"><span data-stu-id="f6d7c-118">**Library:** None</span></span>  
<span data-ttu-id="f6d7c-119">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="f6d7c-119">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="f6d7c-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f6d7c-120">See also</span></span>

- [<span data-ttu-id="f6d7c-121">Debugging</span><span class="sxs-lookup"><span data-stu-id="f6d7c-121">Debugging</span></span>](index.md)
- [<span data-ttu-id="f6d7c-122">Struktury debugowania</span><span class="sxs-lookup"><span data-stu-id="f6d7c-122">Debugging Structures</span></span>](debugging-structures.md)
