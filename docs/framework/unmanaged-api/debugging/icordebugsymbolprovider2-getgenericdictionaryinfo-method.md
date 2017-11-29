---
title: "ICorDebugSymbolProvider2::GetGenericDictionaryInfo — metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: ba28fe4e-5491-4670-bff7-7fde572d7593
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e0c4192c94d70bd9406607d645716e4dd6f8b957
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugsymbolprovider2getgenericdictionaryinfo-method"></a><span data-ttu-id="6df48-102">ICorDebugSymbolProvider2::GetGenericDictionaryInfo — metoda</span><span class="sxs-lookup"><span data-stu-id="6df48-102">ICorDebugSymbolProvider2::GetGenericDictionaryInfo Method</span></span>
<span data-ttu-id="6df48-103">Pobiera mapy ogólnego słownika.</span><span class="sxs-lookup"><span data-stu-id="6df48-103">Retrieves a generic dictionary map.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6df48-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6df48-104">Syntax</span></span>  
  
```  
HRESULT GetGenericDictionaryInfo(  
   [out] ICorDebugMemoryBuffer** ppMemoryBuffer  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6df48-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6df48-105">Parameters</span></span>  
 `ppMemoryBuffer`  
 <span data-ttu-id="6df48-106">[out] Wskaźnik do adresu [ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md) obiektu zawierającego mapy ogólnego słownika.</span><span class="sxs-lookup"><span data-stu-id="6df48-106">[out] A pointer to the address of an [ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md) object containing the generic dictionary map.</span></span> <span data-ttu-id="6df48-107">Zobacz sekcję Spostrzeżenia, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="6df48-107">See the Remarks section for more information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6df48-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6df48-108">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6df48-109">Ta metoda jest tylko dostępne z platformą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="6df48-109">This method is available with .NET Native only.</span></span>  
  
 <span data-ttu-id="6df48-110">Mapy składa się z dwóch części najwyższego poziomu:</span><span class="sxs-lookup"><span data-stu-id="6df48-110">The map consists of two top-level sections:</span></span>  
  
-   <span data-ttu-id="6df48-111">A [katalogu](#Directory) zawierający względnych adresów wirtualnych (RVA) wszystkich słowników uwzględnione na tej mapie.</span><span class="sxs-lookup"><span data-stu-id="6df48-111">A [directory](#Directory) containing the relative virtual addresses (RVA) of all dictionaries included in this map.</span></span>  
  
-   <span data-ttu-id="6df48-112">Wyrównane bajtów [sterty](#Heap) zawiera informacje dotyczące tworzenia wystąpienia obiektu.</span><span class="sxs-lookup"><span data-stu-id="6df48-112">A byte-aligned [heap](#Heap) that contains object instantiation information.</span></span> <span data-ttu-id="6df48-113">Rozpoczyna się od razu po ostatnim wpisu w katalogu.</span><span class="sxs-lookup"><span data-stu-id="6df48-113">It starts immediately after the last directory entry.</span></span>  
  
<a name="Directory"></a>   
## <a name="the-directory"></a><span data-ttu-id="6df48-114">Katalog</span><span class="sxs-lookup"><span data-stu-id="6df48-114">The Directory</span></span>  
 <span data-ttu-id="6df48-115">Każdy wpis w katalogu, który odwołuje się do przesunięcia w stercie; oznacza to, że jest wartość przesunięcia względem początku sterty.</span><span class="sxs-lookup"><span data-stu-id="6df48-115">Each entry in the directory refers to an offset inside the heap; that is, it is an offset that is relative to the start of the heap.</span></span> <span data-ttu-id="6df48-116">Wartość poszczególne pozycje nie jest zawsze unikatowa. istnieje możliwość wiele wpisów w katalogu wskaż tego samego przesunięcie w stosie.</span><span class="sxs-lookup"><span data-stu-id="6df48-116">The value of individual entries is not necessarily unique; it is possible for multiple directory entries to point to the same offset in the heap.</span></span>  
  
 <span data-ttu-id="6df48-117">Części katalogu mapy słownika ogólnego ma następującą strukturę:</span><span class="sxs-lookup"><span data-stu-id="6df48-117">The directory portion of the generic dictionary map has the following structure:</span></span>  
  
-   <span data-ttu-id="6df48-118">Pierwsze 4 bajty zawiera liczbę wpisy słownika (oznacza to, że liczba względną wirtualnych adresów w słowniku).</span><span class="sxs-lookup"><span data-stu-id="6df48-118">The first 4 bytes contains the number of dictionary entries (that is, the number of relative virtual addresses in the dictionary).</span></span> <span data-ttu-id="6df48-119">Odnoszą się do tej wartości jako *N*. Jeśli ustawiono bit wysoka, dane są sortowane według wirtualny adres względny w kolejności rosnącej.</span><span class="sxs-lookup"><span data-stu-id="6df48-119">We will refer to this value as *N*. If the high bit is set, the entries are sorted by relative virtual address in ascending order.</span></span>  
  
-   <span data-ttu-id="6df48-120">*N* wykonaj wpisów w katalogu.</span><span class="sxs-lookup"><span data-stu-id="6df48-120">The *N* directory entries follow.</span></span> <span data-ttu-id="6df48-121">Każdy wpis zawiera 8 bajtów w dwóch segmentów 4-bajtowych:</span><span class="sxs-lookup"><span data-stu-id="6df48-121">Each entry consists of 8 bytes, in two 4-byte segments:</span></span>  
  
    -   <span data-ttu-id="6df48-122">Liczba bajtów 0-3: Adres RVA; adres względny wirtualnego słownika.</span><span class="sxs-lookup"><span data-stu-id="6df48-122">Bytes 0-3: RVA; the dictionary's relative virtual address.</span></span>  
  
    -   <span data-ttu-id="6df48-123">Bajty 4-7: przesunięcie; przesunięcie względem początku sterty.</span><span class="sxs-lookup"><span data-stu-id="6df48-123">Bytes 4-7: Offset; an offset relative to the start of the heap.</span></span>  
  
<a name="Heap"></a>   
## <a name="the-heap"></a><span data-ttu-id="6df48-124">Sterty</span><span class="sxs-lookup"><span data-stu-id="6df48-124">The Heap</span></span>  
 <span data-ttu-id="6df48-125">Rozmiar sterty można obliczyć przez odjęcie długość strumienia od rozmiaru katalogu + 4 przez czytnik strumienia.</span><span class="sxs-lookup"><span data-stu-id="6df48-125">The heap’s size can be computed by a stream reader by subtracting the length of the stream from the directory size + 4.</span></span> <span data-ttu-id="6df48-126">Innymi słowy:</span><span class="sxs-lookup"><span data-stu-id="6df48-126">In other words:</span></span>  
  
```  
Heap Size = Stream.Length – (Directory Size + 4)  
```  
  
 <span data-ttu-id="6df48-127">gdzie jest rozmiar katalogu `N * 8`.</span><span class="sxs-lookup"><span data-stu-id="6df48-127">where the directory size is `N * 8`.</span></span>  
  
 <span data-ttu-id="6df48-128">Format dla każdego wystąpienia elementu informacje na stercie jest:</span><span class="sxs-lookup"><span data-stu-id="6df48-128">The format for each instantiation information item on the heap is:</span></span>  
  
-   <span data-ttu-id="6df48-129">Długość tego wystąpienia elementu informacji w bajtach Format skompresowanych metadanych ECMA.</span><span class="sxs-lookup"><span data-stu-id="6df48-129">The length of this instantiation information item in bytes in compressed ECMA metadata format.</span></span> <span data-ttu-id="6df48-130">Wartość nie obejmuje informacji długości.</span><span class="sxs-lookup"><span data-stu-id="6df48-130">The value excludes this length information.</span></span>  
  
-   <span data-ttu-id="6df48-131">Liczba typów konkretyzacja rodzajowa lub *T*, format skompresowanych metadanych ECMA.</span><span class="sxs-lookup"><span data-stu-id="6df48-131">The number of generic instantiation types, or *T*, in compressed ECMA metadata format.</span></span>  
  
-   <span data-ttu-id="6df48-132">*T* typów, każdy reprezentowany w formacie sygnatury typu ECMA.</span><span class="sxs-lookup"><span data-stu-id="6df48-132">*T* types, each represented in ECMA type signature format.</span></span>  
  
 <span data-ttu-id="6df48-133">Włączenie długość dla każdego elementu sterty umożliwia proste sortowanie sekcji katalogu bez wpływu na stercie.</span><span class="sxs-lookup"><span data-stu-id="6df48-133">The inclusion of the length for each heap element enables simple sorting of the directory section without affecting the heap.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6df48-134">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6df48-134">Requirements</span></span>  
 <span data-ttu-id="6df48-135">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6df48-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6df48-136">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6df48-136">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6df48-137">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6df48-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6df48-138">**Wersje programu .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6df48-138">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6df48-139">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6df48-139">See Also</span></span>  
 [<span data-ttu-id="6df48-140">Interfejs ICorDebugSymbolProvider2</span><span class="sxs-lookup"><span data-stu-id="6df48-140">ICorDebugSymbolProvider2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-interface.md)  
 [<span data-ttu-id="6df48-141">Interfejsy debugowania</span><span class="sxs-lookup"><span data-stu-id="6df48-141">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
