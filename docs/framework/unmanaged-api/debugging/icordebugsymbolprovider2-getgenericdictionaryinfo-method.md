---
title: 'ICorDebugSymbolProvider2:: GetGenericDictionaryInfo, Metoda'
ms.date: 03/30/2017
ms.assetid: ba28fe4e-5491-4670-bff7-7fde572d7593
ms.openlocfilehash: c9f7206cac54d64c28eb50d81fea00a6f3c494d4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133632"
---
# <a name="icordebugsymbolprovider2getgenericdictionaryinfo-method"></a><span data-ttu-id="40376-102">ICorDebugSymbolProvider2:: GetGenericDictionaryInfo, Metoda</span><span class="sxs-lookup"><span data-stu-id="40376-102">ICorDebugSymbolProvider2::GetGenericDictionaryInfo Method</span></span>

<span data-ttu-id="40376-103">Pobiera mapę ogólnego słownika.</span><span class="sxs-lookup"><span data-stu-id="40376-103">Retrieves a generic dictionary map.</span></span>

## <a name="syntax"></a><span data-ttu-id="40376-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="40376-104">Syntax</span></span>

```cpp
HRESULT GetGenericDictionaryInfo(
   [out] ICorDebugMemoryBuffer** ppMemoryBuffer
);
```

## <a name="parameters"></a><span data-ttu-id="40376-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="40376-105">Parameters</span></span>

`ppMemoryBuffer`\
<span data-ttu-id="40376-106">określoną Wskaźnik do adresu obiektu [ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md) zawierającego mapę ogólnego słownika.</span><span class="sxs-lookup"><span data-stu-id="40376-106">[out] A pointer to the address of an [ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md) object containing the generic dictionary map.</span></span> <span data-ttu-id="40376-107">Zobacz sekcję Spostrzeżenia, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="40376-107">See the Remarks section for more information.</span></span>

## <a name="remarks"></a><span data-ttu-id="40376-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="40376-108">Remarks</span></span>

> [!NOTE]
> <span data-ttu-id="40376-109">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="40376-109">This method is available with .NET Native only.</span></span>

<span data-ttu-id="40376-110">Mapa składa się z dwóch sekcji najwyższego poziomu:</span><span class="sxs-lookup"><span data-stu-id="40376-110">The map consists of two top-level sections:</span></span>

- <span data-ttu-id="40376-111">[Katalog](#Directory) zawierający względne adresy wirtualne (RVA) wszystkich słowników uwzględnionych w tej mapie.</span><span class="sxs-lookup"><span data-stu-id="40376-111">A [directory](#Directory) containing the relative virtual addresses (RVA) of all dictionaries included in this map.</span></span>

- <span data-ttu-id="40376-112">[Stos](#Heap) wyrównany do bajtów zawierający informacje o tworzeniu wystąpienia obiektu.</span><span class="sxs-lookup"><span data-stu-id="40376-112">A byte-aligned [heap](#Heap) that contains object instantiation information.</span></span> <span data-ttu-id="40376-113">Rozpocznie się natychmiast po ostatnim wpisie w katalogu.</span><span class="sxs-lookup"><span data-stu-id="40376-113">It starts immediately after the last directory entry.</span></span>

<a name="Directory"></a>

## <a name="the-directory"></a><span data-ttu-id="40376-114">Katalog</span><span class="sxs-lookup"><span data-stu-id="40376-114">The Directory</span></span>

<span data-ttu-id="40376-115">Każdy wpis w katalogu odnosi się do przesunięcia wewnątrz sterty; oznacza to, że jest to przesunięcie odnoszące się do początku sterty.</span><span class="sxs-lookup"><span data-stu-id="40376-115">Each entry in the directory refers to an offset inside the heap; that is, it is an offset that is relative to the start of the heap.</span></span> <span data-ttu-id="40376-116">Wartość poszczególnych wpisów nie musi być unikatowa. Istnieje możliwość, że wiele wpisów katalogu wskazuje na to samo przesunięcie w stercie.</span><span class="sxs-lookup"><span data-stu-id="40376-116">The value of individual entries is not necessarily unique; it is possible for multiple directory entries to point to the same offset in the heap.</span></span>

<span data-ttu-id="40376-117">Część katalogu ogólnego mapowania słownika ma następującą strukturę:</span><span class="sxs-lookup"><span data-stu-id="40376-117">The directory portion of the generic dictionary map has the following structure:</span></span>

- <span data-ttu-id="40376-118">Pierwsze 4 bajty zawierają liczbę wpisów słownika (czyli liczbę względnych adresów wirtualnych w słowniku).</span><span class="sxs-lookup"><span data-stu-id="40376-118">The first 4 bytes contains the number of dictionary entries (that is, the number of relative virtual addresses in the dictionary).</span></span> <span data-ttu-id="40376-119">Ta wartość zostanie odwołująca się do tej wartości jako *N*. Jeśli jest ustawiony wysoki bit, wpisy są sortowane według względnych adresów wirtualnych w kolejności rosnącej.</span><span class="sxs-lookup"><span data-stu-id="40376-119">We will refer to this value as *N*. If the high bit is set, the entries are sorted by relative virtual address in ascending order.</span></span>

- <span data-ttu-id="40376-120">Wpisy katalogu *N* są następujące.</span><span class="sxs-lookup"><span data-stu-id="40376-120">The *N* directory entries follow.</span></span> <span data-ttu-id="40376-121">Każdy wpis składa się z 8 bajtów w dwóch segmentach 4-bajtowych:</span><span class="sxs-lookup"><span data-stu-id="40376-121">Each entry consists of 8 bytes, in two 4-byte segments:</span></span>

  - <span data-ttu-id="40376-122">Bajty 0-3: RVA; względny adres wirtualny słownika.</span><span class="sxs-lookup"><span data-stu-id="40376-122">Bytes 0-3: RVA; the dictionary's relative virtual address.</span></span>

  - <span data-ttu-id="40376-123">Bajty 4-7: przesunięcie; przesunięcie względem początku sterty.</span><span class="sxs-lookup"><span data-stu-id="40376-123">Bytes 4-7: Offset; an offset relative to the start of the heap.</span></span>

<a name="Heap"></a>

## <a name="the-heap"></a><span data-ttu-id="40376-124">Sterta</span><span class="sxs-lookup"><span data-stu-id="40376-124">The Heap</span></span>

<span data-ttu-id="40376-125">Rozmiar sterty może być obliczany przez czytnik strumienia przez odjęcie długości strumienia od rozmiaru katalogu + 4.</span><span class="sxs-lookup"><span data-stu-id="40376-125">The heap’s size can be computed by a stream reader by subtracting the length of the stream from the directory size + 4.</span></span> <span data-ttu-id="40376-126">Innymi słowy:</span><span class="sxs-lookup"><span data-stu-id="40376-126">In other words:</span></span>

```csharp
Heap Size = Stream.Length – (Directory Size + 4)
```

<span data-ttu-id="40376-127">miejsce, w którym rozmiar katalogu jest `N * 8`.</span><span class="sxs-lookup"><span data-stu-id="40376-127">where the directory size is `N * 8`.</span></span>

<span data-ttu-id="40376-128">Format każdego elementu informacji o tworzeniu wystąpienia na stercie to:</span><span class="sxs-lookup"><span data-stu-id="40376-128">The format for each instantiation information item on the heap is:</span></span>

- <span data-ttu-id="40376-129">Długość tego elementu informacji o tworzeniu wystąpienia w bajtach w skompresowanym formacie metadanych ECMA.</span><span class="sxs-lookup"><span data-stu-id="40376-129">The length of this instantiation information item in bytes in compressed ECMA metadata format.</span></span> <span data-ttu-id="40376-130">Ta wartość wyklucza informacje o długości.</span><span class="sxs-lookup"><span data-stu-id="40376-130">The value excludes this length information.</span></span>

- <span data-ttu-id="40376-131">Liczba typów ogólnych wystąpień wystąpienia lub *T*w formacie skompresowanego metadanych ECMA.</span><span class="sxs-lookup"><span data-stu-id="40376-131">The number of generic instantiation types, or *T*, in compressed ECMA metadata format.</span></span>

- <span data-ttu-id="40376-132">Typy *T* , każdy reprezentowane w formacie sygnatury typu ECMA.</span><span class="sxs-lookup"><span data-stu-id="40376-132">*T* types, each represented in ECMA type signature format.</span></span>

<span data-ttu-id="40376-133">Włączenie długości dla każdego elementu sterty umożliwia proste sortowanie sekcji katalogu bez wpływu na stertę.</span><span class="sxs-lookup"><span data-stu-id="40376-133">The inclusion of the length for each heap element enables simple sorting of the directory section without affecting the heap.</span></span>

## <a name="requirements"></a><span data-ttu-id="40376-134">Wymagania</span><span class="sxs-lookup"><span data-stu-id="40376-134">Requirements</span></span>

<span data-ttu-id="40376-135">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="40376-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="40376-136">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="40376-136">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="40376-137">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="40376-137">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="40376-138">**Wersje .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="40376-138">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="40376-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="40376-139">See also</span></span>

- [<span data-ttu-id="40376-140">ICorDebugSymbolProvider2, interfejs</span><span class="sxs-lookup"><span data-stu-id="40376-140">ICorDebugSymbolProvider2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-interface.md)
- [<span data-ttu-id="40376-141">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="40376-141">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
