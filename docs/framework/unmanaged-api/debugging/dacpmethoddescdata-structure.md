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
ms.openlocfilehash: d623fe862eaf5902fd89d0e512dd07f73a03246f
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860818"
---
# <a name="dacpmethoddescdata-structure"></a><span data-ttu-id="4cb75-102">DacpMethodDescData, struktura</span><span class="sxs-lookup"><span data-stu-id="4cb75-102">DacpMethodDescData Structure</span></span>

<span data-ttu-id="4cb75-103">Definiuje bufor transportu dla informacji o środowisku uruchomieniowym metody.</span><span class="sxs-lookup"><span data-stu-id="4cb75-103">Defines a transport buffer for a method's runtime information.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="4cb75-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4cb75-104">Syntax</span></span>

```cpp
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

## <a name="members"></a><span data-ttu-id="4cb75-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="4cb75-105">Members</span></span>

| <span data-ttu-id="4cb75-106">Członek</span><span class="sxs-lookup"><span data-stu-id="4cb75-106">Member</span></span>                       | <span data-ttu-id="4cb75-107">Opis</span><span class="sxs-lookup"><span data-stu-id="4cb75-107">Description</span></span>                                                                                     |
| ---------------------------- | ----------------------------------------------------------------------------------------------- |
| `bHasNativeCode`             | <span data-ttu-id="4cb75-108">Wskazuje, czy środowisko uruchomieniowe ma kod natywny dla danego wystąpienia metody.</span><span class="sxs-lookup"><span data-stu-id="4cb75-108">Indicates if the runtime has native code available for the given instantiation of the method.</span></span> |
| `bIsDynamic`                 | <span data-ttu-id="4cb75-109">Wskazuje, czy metoda jest generowana dynamicznie przy użyciu uproszczonego generowania kodu.</span><span class="sxs-lookup"><span data-stu-id="4cb75-109">Indicates if the method is generated dynamically through lightweight code generation.</span></span>           |
| `wSlotNumber`                | <span data-ttu-id="4cb75-110">Numer gniazda metody w tabeli metod.</span><span class="sxs-lookup"><span data-stu-id="4cb75-110">The method's slot number in the method table.</span></span>                                                   |
| `NativeCodeAddr`             | <span data-ttu-id="4cb75-111">Początkowy adres macierzysty metody.</span><span class="sxs-lookup"><span data-stu-id="4cb75-111">The method's initial native address.</span></span>                                                            |
| `data`                       | <span data-ttu-id="4cb75-112">Wskaźnik do bufora używanego wewnętrznie przez środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="4cb75-112">Pointer to a buffer used internally by the runtime.</span></span>                                             |
| `MethodDescPtr`              | <span data-ttu-id="4cb75-113">Wskaźnik do `MethodDesc` w środowisku uruchomieniowym.</span><span class="sxs-lookup"><span data-stu-id="4cb75-113">Pointer to the `MethodDesc` in the runtime.</span></span>                                                     |
| `nativeCodeInfo`             | <span data-ttu-id="4cb75-114">Wskaźnik do buforu używany wewnętrznie przez środowisko uruchomieniowe do śledzenia metod.</span><span class="sxs-lookup"><span data-stu-id="4cb75-114">Pointer to a buffer used internally by the runtime to track methods.</span></span>                            |
| `moduleInfo`                 | <span data-ttu-id="4cb75-115">Wskaźnik do buforu używany wewnętrznie przez środowisko uruchomieniowe w celu uzyskania informacji o modułach.</span><span class="sxs-lookup"><span data-stu-id="4cb75-115">Pointer to a buffer used internally by the runtime for module information.</span></span>                      |
| `MDToken`                    | <span data-ttu-id="4cb75-116">Token skojarzony z daną metodą.</span><span class="sxs-lookup"><span data-stu-id="4cb75-116">Token associated with the given method.</span></span>                                                         |
| `payloadGC`                  | <span data-ttu-id="4cb75-117">Wskaźnik do buforu wyrzucania elementów bezużytecznych używanego wewnętrznie przez środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="4cb75-117">Pointer to a garbage collection buffer used internally by the runtime.</span></span>                          |
| `payloadGC2`                 | <span data-ttu-id="4cb75-118">Wskaźnik do buforu wyrzucania elementów bezużytecznych używanego wewnętrznie przez środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="4cb75-118">Pointer to a garbage collection buffer used internally by the runtime.</span></span>                          |
| `managedDynamicMethodObject` | <span data-ttu-id="4cb75-119">Jeśli metoda jest dynamiczna, środowisko uruchomieniowe używa tego buforu wewnętrznie do śledzenia informacji.</span><span class="sxs-lookup"><span data-stu-id="4cb75-119">If the method is dynamic, the runtime uses this buffer internally for information tracking.</span></span>     |
| `requestedIP`                | <span data-ttu-id="4cb75-120">Służy do wypełniania struktury na żądanie, gdy zostanie udzielony adres kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="4cb75-120">Used to populate the structure per request when given a native code address.</span></span>                    |
| `rejitDataCurrent`           | <span data-ttu-id="4cb75-121">Informacje o najnowszej wersji Instrumentacji metody.</span><span class="sxs-lookup"><span data-stu-id="4cb75-121">Information about the latest instrumented version of the method.</span></span>                                   |
| `rejitDataRequested`         | <span data-ttu-id="4cb75-122">ReJIT informacje o żądanym adresie macierzystym.</span><span class="sxs-lookup"><span data-stu-id="4cb75-122">Rejit information for the requested native address.</span></span>                                             |
| `cJittedRejitVersions`       | <span data-ttu-id="4cb75-123">Liczba przypadków, gdy metoda została rejitted przez instrumentację.</span><span class="sxs-lookup"><span data-stu-id="4cb75-123">Number of times the method has been rejitted through instrumentation.</span></span>                           |

## <a name="remarks"></a><span data-ttu-id="4cb75-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4cb75-124">Remarks</span></span>

<span data-ttu-id="4cb75-125">Ta struktura jest w czasie wykonywania i nie jest udostępniana za pomocą żadnych plików nagłówkowych ani bibliotek.</span><span class="sxs-lookup"><span data-stu-id="4cb75-125">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="4cb75-126">Aby go użyć, Zdefiniuj strukturę zgodnie z powyższym opisem.</span><span class="sxs-lookup"><span data-stu-id="4cb75-126">To use it, define the structure as specified above.</span></span>

## <a name="requirements"></a><span data-ttu-id="4cb75-127">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4cb75-127">Requirements</span></span>
<span data-ttu-id="4cb75-128">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4cb75-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="4cb75-129">**Nagłówek:** Dawaj</span><span class="sxs-lookup"><span data-stu-id="4cb75-129">**Header:** None</span></span>  
<span data-ttu-id="4cb75-130">**Biblioteka:** Dawaj</span><span class="sxs-lookup"><span data-stu-id="4cb75-130">**Library:** None</span></span>  
<span data-ttu-id="4cb75-131">**.NET Framework wersje:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="4cb75-131">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="4cb75-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4cb75-132">See also</span></span>

- [<span data-ttu-id="4cb75-133">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="4cb75-133">Debugging</span></span>](index.md)
- [<span data-ttu-id="4cb75-134">Struktury debugowania</span><span class="sxs-lookup"><span data-stu-id="4cb75-134">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="4cb75-135">Standardowe typy danych</span><span class="sxs-lookup"><span data-stu-id="4cb75-135">Common Data Types</span></span>](../common-data-types-unmanaged-api-reference.md)
