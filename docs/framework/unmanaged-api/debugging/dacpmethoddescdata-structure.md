---
title: DacpMethodDescData, struktura
ms.date: 02/01/2019
api.name:
- DacpMethodDescData Structure
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- DacpMethodDescData Structure
helpviewer.keywords:
- DacpMethodDescData Structure [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: 567dc3942f79b6bfd29338b9103083aa64e66451
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61965934"
---
# <a name="dacpmethoddescdata-structure"></a><span data-ttu-id="f5f61-102">DacpMethodDescData, struktura</span><span class="sxs-lookup"><span data-stu-id="f5f61-102">DacpMethodDescData Structure</span></span>

<span data-ttu-id="f5f61-103">Definiuje bufora transportu dla metody środowiska uruchomieniowego informacje.</span><span class="sxs-lookup"><span data-stu-id="f5f61-103">Defines a transport buffer for a method's runtime information.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="f5f61-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f5f61-104">Syntax</span></span>

```
struct DacpMethodDescData
{
    int             bHasNativeCode;
    int             bIsDynamic;
    unsigned short  wSlotNumber;
    CLRDATA_ADDRESS NativeCodeAddr;
    CLRDATA_ADDRESS data;
    CLRDATA_ADDRESS MethodDescPtr;
    CLRDATA_ADDRESS nativeCodeInfo;
    CLRDATA_ADDRESS moduleInfo;
    mdToken         MDToken;
    CLRDATA_ADDRESS payloadGC;
    CLRDATA_ADDRESS payloadGC2;
    CLRDATA_ADDRESS managedDynamicMethodObject;
    CLRDATA_ADDRESS requestedIP;
    DacpReJitData   rejitDataCurrent;
    DacpReJitData   rejitDataRequested;
    unsigned long   cJittedRejitVersions;
};
```

## <a name="members"></a><span data-ttu-id="f5f61-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="f5f61-105">Members</span></span>

| <span data-ttu-id="f5f61-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="f5f61-106">Member</span></span>                       | <span data-ttu-id="f5f61-107">Opis</span><span class="sxs-lookup"><span data-stu-id="f5f61-107">Description</span></span>                                                                                     |
| ---------------------------- | ----------------------------------------------------------------------------------------------- |
| `bHasNativeCode`             | <span data-ttu-id="f5f61-108">Wskazuje, czy środowisko uruchomieniowe jest kodu natywnego, które są dostępne dla danego wystąpienia metody.</span><span class="sxs-lookup"><span data-stu-id="f5f61-108">Indicates if the runtime has native code available for the given instantiation of the method.</span></span> |
| `bIsDynamic`                 | <span data-ttu-id="f5f61-109">Wskazuje, jeśli metoda jest generowany dynamicznie za pośrednictwem generowania kodu uproszczone.</span><span class="sxs-lookup"><span data-stu-id="f5f61-109">Indicates if the method is generated dynamically through lightweight code generation.</span></span>           |
| `wSlotNumber`                | <span data-ttu-id="f5f61-110">Numer gniazda metody w tabeli metod.</span><span class="sxs-lookup"><span data-stu-id="f5f61-110">The method's slot number in the method table.</span></span>                                                   |
| `NativeCodeAddr`             | <span data-ttu-id="f5f61-111">Metoda początkowej adresu natywnego.</span><span class="sxs-lookup"><span data-stu-id="f5f61-111">The method's initial native address.</span></span>                                                            |
| `data`                       | <span data-ttu-id="f5f61-112">Wskaźnik do buforu używana wewnętrznie w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="f5f61-112">Pointer to a buffer used internally by the runtime.</span></span>                                             |
| `MethodDescPtr`              | <span data-ttu-id="f5f61-113">Wskaźnik do `MethodDesc` w środowisku uruchomieniowym.</span><span class="sxs-lookup"><span data-stu-id="f5f61-113">Pointer to the `MethodDesc` in the runtime.</span></span>                                                     |
| `nativeCodeInfo`             | <span data-ttu-id="f5f61-114">Wskaźnik do buforu używana wewnętrznie przez środowisko uruchomieniowe w celu śledzenia metody.</span><span class="sxs-lookup"><span data-stu-id="f5f61-114">Pointer to a buffer used internally by the runtime to track methods.</span></span>                            |
| `moduleInfo`                 | <span data-ttu-id="f5f61-115">Wskaźnik do buforu używana wewnętrznie przez środowisko uruchomieniowe, aby uzyskać informacje o module.</span><span class="sxs-lookup"><span data-stu-id="f5f61-115">Pointer to a buffer used internally by the runtime for module information.</span></span>                      |
| `MDToken`                    | <span data-ttu-id="f5f61-116">Token skojarzony z danej metody.</span><span class="sxs-lookup"><span data-stu-id="f5f61-116">Token associated with the given method.</span></span>                                                         |
| `payloadGC`                  | <span data-ttu-id="f5f61-117">Wskaźnik do buforu kolekcji wyrzucania elementów używana wewnętrznie w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="f5f61-117">Pointer to a garbage collection buffer used internally by the runtime.</span></span>                          |
| `payloadGC2`                 | <span data-ttu-id="f5f61-118">Wskaźnik do buforu kolekcji wyrzucania elementów używana wewnętrznie w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="f5f61-118">Pointer to a garbage collection buffer used internally by the runtime.</span></span>                          |
| `managedDynamicMethodObject` | <span data-ttu-id="f5f61-119">Jeśli metoda jest dynamiczny, środowisko wykonawcze używa tego buforu wewnętrznie informacji śledzenia.</span><span class="sxs-lookup"><span data-stu-id="f5f61-119">If the method is dynamic, the runtime uses this buffer internally for information tracking.</span></span>     |
| `requestedIP`                | <span data-ttu-id="f5f61-120">Używany do wypełniania struktury na żądanie, gdy podano adres kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="f5f61-120">Used to populate the structure per request when given a native code address.</span></span>                    |
| `rejitDataCurrent`           | <span data-ttu-id="f5f61-121">Informacje o najnowszych instrumentowanej wersji metody.</span><span class="sxs-lookup"><span data-stu-id="f5f61-121">Information about the latest instrumented version of the method.</span></span>                                   |
| `rejitDataRequested`         | <span data-ttu-id="f5f61-122">Rejit informacji dla żądanego adresu natywnego.</span><span class="sxs-lookup"><span data-stu-id="f5f61-122">Rejit information for the requested native address.</span></span>                                             |
| `cJittedRejitVersions`       | <span data-ttu-id="f5f61-123">Liczba przypadków, gdy metoda została rejitted za pomocą Instrumentacji.</span><span class="sxs-lookup"><span data-stu-id="f5f61-123">Number of times the method has been rejitted through instrumentation.</span></span>                           |

## <a name="remarks"></a><span data-ttu-id="f5f61-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f5f61-124">Remarks</span></span>

<span data-ttu-id="f5f61-125">Ta struktura znajduje się wewnątrz środowiska uruchomieniowego i nie jest dostępna za pośrednictwem wszystkich nagłówków lub pliki biblioteki.</span><span class="sxs-lookup"><span data-stu-id="f5f61-125">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="f5f61-126">Aby go użyć, definiują strukturę, jak określono powyżej.</span><span class="sxs-lookup"><span data-stu-id="f5f61-126">To use it, define the structure as specified above.</span></span>

## <a name="requirements"></a><span data-ttu-id="f5f61-127">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f5f61-127">Requirements</span></span>
<span data-ttu-id="f5f61-128">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f5f61-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="f5f61-129">**Nagłówek:** Brak</span><span class="sxs-lookup"><span data-stu-id="f5f61-129">**Header:** None</span></span>  
<span data-ttu-id="f5f61-130">**Biblioteka:** Brak</span><span class="sxs-lookup"><span data-stu-id="f5f61-130">**Library:** None</span></span>  
<span data-ttu-id="f5f61-131">**Wersje programu .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="f5f61-131">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="f5f61-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f5f61-132">See also</span></span>

- [<span data-ttu-id="f5f61-133">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="f5f61-133">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="f5f61-134">Struktury debugowania</span><span class="sxs-lookup"><span data-stu-id="f5f61-134">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="f5f61-135">Standardowe typy danych</span><span class="sxs-lookup"><span data-stu-id="f5f61-135">Common Data Types</span></span>](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md)
