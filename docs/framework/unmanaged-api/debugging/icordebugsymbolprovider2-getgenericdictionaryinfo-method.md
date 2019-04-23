---
title: Metoda ICorDebugSymbolProvider2::GetGenericDictionaryInfo
ms.date: 03/30/2017
ms.assetid: ba28fe4e-5491-4670-bff7-7fde572d7593
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f171af8dbfa4e812711e95e5587b314753cd9350
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59216824"
---
# <a name="icordebugsymbolprovider2getgenericdictionaryinfo-method"></a><span data-ttu-id="6f93f-102">Metoda ICorDebugSymbolProvider2::GetGenericDictionaryInfo</span><span class="sxs-lookup"><span data-stu-id="6f93f-102">ICorDebugSymbolProvider2::GetGenericDictionaryInfo Method</span></span>
<span data-ttu-id="6f93f-103">Pobiera mapę generyczny słownik.</span><span class="sxs-lookup"><span data-stu-id="6f93f-103">Retrieves a generic dictionary map.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f93f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6f93f-104">Syntax</span></span>  
  
```  
HRESULT GetGenericDictionaryInfo(  
   [out] ICorDebugMemoryBuffer** ppMemoryBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6f93f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6f93f-105">Parameters</span></span>  
 `ppMemoryBuffer`  
 <span data-ttu-id="6f93f-106">[out] Wskaźnik na adres [ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md) obiekt zawierający mapy generyczny słownik.</span><span class="sxs-lookup"><span data-stu-id="6f93f-106">[out] A pointer to the address of an [ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md) object containing the generic dictionary map.</span></span> <span data-ttu-id="6f93f-107">Zobacz sekcję Spostrzeżenia, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="6f93f-107">See the Remarks section for more information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6f93f-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6f93f-108">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6f93f-109">Ta metoda jest tylko dostępne z architekturą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="6f93f-109">This method is available with .NET Native only.</span></span>  
  
 <span data-ttu-id="6f93f-110">Mapa zawiera dwie sekcje najwyższego poziomu:</span><span class="sxs-lookup"><span data-stu-id="6f93f-110">The map consists of two top-level sections:</span></span>  
  
-   <span data-ttu-id="6f93f-111">A [katalogu](#Directory) zawierający względnych adresów wirtualnych (RVA) słowników wszystkie zawarte w tej mapie.</span><span class="sxs-lookup"><span data-stu-id="6f93f-111">A [directory](#Directory) containing the relative virtual addresses (RVA) of all dictionaries included in this map.</span></span>  
  
-   <span data-ttu-id="6f93f-112">-Bajtami [sterty](#Heap) zawierający informacje dotyczące tworzenia wystąpienia obiektu.</span><span class="sxs-lookup"><span data-stu-id="6f93f-112">A byte-aligned [heap](#Heap) that contains object instantiation information.</span></span> <span data-ttu-id="6f93f-113">Rozpoczyna się natychmiast po ostatni wpis katalogu.</span><span class="sxs-lookup"><span data-stu-id="6f93f-113">It starts immediately after the last directory entry.</span></span>  
  
<a name="Directory"></a>   
## <a name="the-directory"></a><span data-ttu-id="6f93f-114">Katalog</span><span class="sxs-lookup"><span data-stu-id="6f93f-114">The Directory</span></span>  
 <span data-ttu-id="6f93f-115">Każdy wpis w katalogu, który odwołuje się do przesunięcia wewnątrz sterty; oznacza to, że jest przesunięcie względem początku sterty.</span><span class="sxs-lookup"><span data-stu-id="6f93f-115">Each entry in the directory refers to an offset inside the heap; that is, it is an offset that is relative to the start of the heap.</span></span> <span data-ttu-id="6f93f-116">Wartość poszczególne wpisy nie jest zawsze unikatowa. istnieje możliwość dla wielu wpisów w katalogu wskaż samo przesunięcie w stosie.</span><span class="sxs-lookup"><span data-stu-id="6f93f-116">The value of individual entries is not necessarily unique; it is possible for multiple directory entries to point to the same offset in the heap.</span></span>  
  
 <span data-ttu-id="6f93f-117">Część katalogu mapy generyczny słownik ma następującą strukturę:</span><span class="sxs-lookup"><span data-stu-id="6f93f-117">The directory portion of the generic dictionary map has the following structure:</span></span>  
  
-   <span data-ttu-id="6f93f-118">Pierwsze 4 bajty zawiera liczbę pozycji słownika (oznacza to, że liczba względnych adresów wirtualnych w słowniku).</span><span class="sxs-lookup"><span data-stu-id="6f93f-118">The first 4 bytes contains the number of dictionary entries (that is, the number of relative virtual addresses in the dictionary).</span></span> <span data-ttu-id="6f93f-119">Firma Microsoft będzie odnosił się do tej wartości jako *N*. Jeśli ustawiono bit wysokiej, wpisy są sortowane według względny adres wirtualny, w kolejności rosnącej.</span><span class="sxs-lookup"><span data-stu-id="6f93f-119">We will refer to this value as *N*. If the high bit is set, the entries are sorted by relative virtual address in ascending order.</span></span>  
  
-   <span data-ttu-id="6f93f-120">*N* postępuj zgodnie z wpisy w katalogu.</span><span class="sxs-lookup"><span data-stu-id="6f93f-120">The *N* directory entries follow.</span></span> <span data-ttu-id="6f93f-121">Każdy wpis składa się z 8 bajtów w dwa segmenty 4-bajtowych:</span><span class="sxs-lookup"><span data-stu-id="6f93f-121">Each entry consists of 8 bytes, in two 4-byte segments:</span></span>  
  
    -   <span data-ttu-id="6f93f-122">Bajty 0 – 3: ADRES RVA; względny adres wirtualny słownika.</span><span class="sxs-lookup"><span data-stu-id="6f93f-122">Bytes 0-3: RVA; the dictionary's relative virtual address.</span></span>  
  
    -   <span data-ttu-id="6f93f-123">Bajty 4 – 7: Przesunięcie; przesunięcie względem początku sterty.</span><span class="sxs-lookup"><span data-stu-id="6f93f-123">Bytes 4-7: Offset; an offset relative to the start of the heap.</span></span>  
  
<a name="Heap"></a>   
## <a name="the-heap"></a><span data-ttu-id="6f93f-124">Sterty</span><span class="sxs-lookup"><span data-stu-id="6f93f-124">The Heap</span></span>  
 <span data-ttu-id="6f93f-125">Rozmiar sterty, może zostać obliczony przez czytnik strumienia poprzez odjęcie długość strumienia od rozmiaru katalogu + 4.</span><span class="sxs-lookup"><span data-stu-id="6f93f-125">The heap’s size can be computed by a stream reader by subtracting the length of the stream from the directory size + 4.</span></span> <span data-ttu-id="6f93f-126">Innymi słowy:</span><span class="sxs-lookup"><span data-stu-id="6f93f-126">In other words:</span></span>  
  
```  
Heap Size = Stream.Length – (Directory Size + 4)  
```  
  
 <span data-ttu-id="6f93f-127">gdzie jest rozmiar katalogu `N * 8`.</span><span class="sxs-lookup"><span data-stu-id="6f93f-127">where the directory size is `N * 8`.</span></span>  
  
 <span data-ttu-id="6f93f-128">Format dla każdego elementu informacji podczas tworzenia wystąpienia na stosie jest następujący:</span><span class="sxs-lookup"><span data-stu-id="6f93f-128">The format for each instantiation information item on the heap is:</span></span>  
  
-   <span data-ttu-id="6f93f-129">Długość tego elementu informacji podczas tworzenia wystąpienia w bajtach Format skompresowanych metadanych ECMA.</span><span class="sxs-lookup"><span data-stu-id="6f93f-129">The length of this instantiation information item in bytes in compressed ECMA metadata format.</span></span> <span data-ttu-id="6f93f-130">Wartość nie obejmuje to informacje o długości.</span><span class="sxs-lookup"><span data-stu-id="6f93f-130">The value excludes this length information.</span></span>  
  
-   <span data-ttu-id="6f93f-131">Liczba typów ogólnych podczas tworzenia wystąpienia lub *T*, format skompresowanych metadanych ECMA.</span><span class="sxs-lookup"><span data-stu-id="6f93f-131">The number of generic instantiation types, or *T*, in compressed ECMA metadata format.</span></span>  
  
-   <span data-ttu-id="6f93f-132">*T* typów, w każdym reprezentowane w formacie podpisu typu ECMA.</span><span class="sxs-lookup"><span data-stu-id="6f93f-132">*T* types, each represented in ECMA type signature format.</span></span>  
  
 <span data-ttu-id="6f93f-133">Włączenie długość dla każdego elementu sterty umożliwia proste sortowanie sekcji katalogu bez wywierania wpływu na stosie.</span><span class="sxs-lookup"><span data-stu-id="6f93f-133">The inclusion of the length for each heap element enables simple sorting of the directory section without affecting the heap.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6f93f-134">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6f93f-134">Requirements</span></span>  
 <span data-ttu-id="6f93f-135">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6f93f-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6f93f-136">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6f93f-136">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6f93f-137">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6f93f-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6f93f-138">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6f93f-138">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f93f-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6f93f-139">See also</span></span>

- [<span data-ttu-id="6f93f-140">ICorDebugSymbolProvider2, interfejs</span><span class="sxs-lookup"><span data-stu-id="6f93f-140">ICorDebugSymbolProvider2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-interface.md)
- [<span data-ttu-id="6f93f-141">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="6f93f-141">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
