---
title: ICorDebugSymbolProvider, interfejs
ms.date: 03/30/2017
ms.assetid: 85b24196-b6c6-4bda-9de3-47180bd6ff96
ms.openlocfilehash: 6f7a8a2b12c047b956a3b6e85fe8365e0360b3f2
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791532"
---
# <a name="icordebugsymbolprovider-interface"></a><span data-ttu-id="42319-102">ICorDebugSymbolProvider, interfejs</span><span class="sxs-lookup"><span data-stu-id="42319-102">ICorDebugSymbolProvider Interface</span></span>
<span data-ttu-id="42319-103">Dostarcza metody, których można użyć do pobrania informacji o symbolach debugowania.</span><span class="sxs-lookup"><span data-stu-id="42319-103">Provides methods that can be used to retrieve debug symbol information.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="42319-104">Metody</span><span class="sxs-lookup"><span data-stu-id="42319-104">Methods</span></span>  
  
|<span data-ttu-id="42319-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="42319-105">Method</span></span>|<span data-ttu-id="42319-106">Opis</span><span class="sxs-lookup"><span data-stu-id="42319-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="42319-107">GetAssemblyImageBytes, metoda</span><span class="sxs-lookup"><span data-stu-id="42319-107">GetAssemblyImageBytes Method</span></span>](icordebugsymbolprovider-getassemblyimagebytes-method.md)|<span data-ttu-id="42319-108">Odczytuje dane z scalonego zestawu, uwzględniając względny adres wirtualny (RVA) w scalonym zestawie.</span><span class="sxs-lookup"><span data-stu-id="42319-108">Reads data from a merged assembly given a relative virtual address (RVA) in the merged assembly.</span></span>|  
|[<span data-ttu-id="42319-109">GetAssemblyImageMetadata, metoda</span><span class="sxs-lookup"><span data-stu-id="42319-109">GetAssemblyImageMetadata Method</span></span>](icordebugsymbolprovider-getassemblyimagemetadata-method.md)|<span data-ttu-id="42319-110">Zwraca metadane z scalonego zestawu.</span><span class="sxs-lookup"><span data-stu-id="42319-110">Returns the metadata from a merged assembly.</span></span>|  
|[<span data-ttu-id="42319-111">GetCodeRange, metoda</span><span class="sxs-lookup"><span data-stu-id="42319-111">GetCodeRange Method</span></span>](icordebugsymbolprovider-getcoderange-method.md)|<span data-ttu-id="42319-112">Pobiera adres początkowy i rozmiar metody z przyznanym adresem wirtualnym (RVA) w metodzie.</span><span class="sxs-lookup"><span data-stu-id="42319-112">Gets the method start address and size given a relative virtual address (RVA) in a method.</span></span>|  
|[<span data-ttu-id="42319-113">GetInstanceFieldSymbols, metoda</span><span class="sxs-lookup"><span data-stu-id="42319-113">GetInstanceFieldSymbols Method</span></span>](icordebugsymbolprovider-getinstancefieldsymbols-method.md)|<span data-ttu-id="42319-114">Pobiera symbole pól wystąpienia, które odpowiadają sygnaturze elementu TypeSpec.</span><span class="sxs-lookup"><span data-stu-id="42319-114">Gets the instance field symbols that correspond to a typespec signature.</span></span>|  
|[<span data-ttu-id="42319-115">GetMergedAssemblyRecords, metoda</span><span class="sxs-lookup"><span data-stu-id="42319-115">GetMergedAssemblyRecords Method</span></span>](icordebugsymbolprovider-getmergedassemblyrecords-method.md)|<span data-ttu-id="42319-116">Pobiera rekordy symboli dla wszystkich scalonych zestawów.</span><span class="sxs-lookup"><span data-stu-id="42319-116">Gets the symbol records for all the merged assemblies.</span></span>|  
|[<span data-ttu-id="42319-117">GetMethodLocalSymbols, metoda</span><span class="sxs-lookup"><span data-stu-id="42319-117">GetMethodLocalSymbols Method</span></span>](icordebugsymbolprovider-getmethodlocalsymbols-method.md)|<span data-ttu-id="42319-118">Pobiera symbole lokalne metody z uwzględnieniem względnego adresu wirtualnego (RVA) tej metody.</span><span class="sxs-lookup"><span data-stu-id="42319-118">Gets a method's local symbols given the relative virtual address (RVA) of that method.</span></span>|  
|[<span data-ttu-id="42319-119">GetMethodParameterSymbols, metoda</span><span class="sxs-lookup"><span data-stu-id="42319-119">GetMethodParameterSymbols Method</span></span>](icordebugsymbolprovider-getmethodparametersymbols-method.md)|<span data-ttu-id="42319-120">Pobiera symbole parametrów metody z uwzględnieniem względnego adresu wirtualnego (RVA) tej metody.</span><span class="sxs-lookup"><span data-stu-id="42319-120">Gets a method's parameter symbols given the relative virtual address (RVA) of that method.</span></span>|  
|[<span data-ttu-id="42319-121">GetMethodProps, metoda</span><span class="sxs-lookup"><span data-stu-id="42319-121">GetMethodProps Method</span></span>](icordebugsymbolprovider-getmethodprops-method.md)|<span data-ttu-id="42319-122">Zwraca informacje o właściwościach metody, takich jak token metadanych metody i informacje o jego ogólnych parametrach, w którym znajduje się względny adres wirtualny (RVA) w tej metodzie.</span><span class="sxs-lookup"><span data-stu-id="42319-122">Returns information about method properties, such as the method's metadata token and information about its generic parameters, given a relative virtual address (RVA) in that method.</span></span>|  
|[<span data-ttu-id="42319-123">GetObjectSize, metoda</span><span class="sxs-lookup"><span data-stu-id="42319-123">GetObjectSize Method</span></span>](icordebugsymbolprovider-getobjectsize-method.md)|<span data-ttu-id="42319-124">Zwraca rozmiar obiektu na podstawie jego podpisu elementu TypeSpec.</span><span class="sxs-lookup"><span data-stu-id="42319-124">Returns the object size for an object based on its typespec signature.</span></span>|  
|[<span data-ttu-id="42319-125">GetStaticFieldSymbols, metoda</span><span class="sxs-lookup"><span data-stu-id="42319-125">GetStaticFieldSymbols Method</span></span>](icordebugsymbolprovider-getstaticfieldsymbols-method.md)|<span data-ttu-id="42319-126">Pobiera symbole pól statycznych, które odpowiadają sygnaturze elementu TypeSpec.</span><span class="sxs-lookup"><span data-stu-id="42319-126">Gets the static field symbols that correspond to a typespec signature.</span></span>|  
|[<span data-ttu-id="42319-127">GetTypeProps, metoda</span><span class="sxs-lookup"><span data-stu-id="42319-127">GetTypeProps Method</span></span>](icordebugsymbolprovider-gettypeprops-method.md)|<span data-ttu-id="42319-128">Zwraca informacje o właściwościach typu, takich jak liczba podpisów jego parametrów ogólnych, z uwzględnieniem względnego adresu wirtualnego (RVA) w tabeli jednoelementowej.</span><span class="sxs-lookup"><span data-stu-id="42319-128">Returns information about a type's properties, such as the number of signature of its generic parameters, given a relative virtual address (RVA) in a vtable.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="42319-129">Uwagi</span><span class="sxs-lookup"><span data-stu-id="42319-129">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="42319-130">Ten interfejs jest dostępny tylko dla .NET Native.</span><span class="sxs-lookup"><span data-stu-id="42319-130">This interface is available with .NET Native only.</span></span> <span data-ttu-id="42319-131">W przypadku zaimplementowania tego interfejsu dla scenariuszy ICorDebug poza .NET Native, środowisko uruchomieniowe języka wspólnego zignoruje ten interfejs.</span><span class="sxs-lookup"><span data-stu-id="42319-131">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="42319-132">Wymagania</span><span class="sxs-lookup"><span data-stu-id="42319-132">Requirements</span></span>  
 <span data-ttu-id="42319-133">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="42319-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="42319-134">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="42319-134">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="42319-135">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="42319-135">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="42319-136">**Wersje .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="42319-136">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42319-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="42319-137">See also</span></span>

- [<span data-ttu-id="42319-138">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="42319-138">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="42319-139">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="42319-139">Debugging</span></span>](index.md)
