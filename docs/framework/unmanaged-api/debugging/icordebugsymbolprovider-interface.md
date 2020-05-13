---
title: ICorDebugSymbolProvider, interfejs
ms.date: 03/30/2017
ms.assetid: 85b24196-b6c6-4bda-9de3-47180bd6ff96
ms.openlocfilehash: 25faad4f4bc67b57c339bc63d1a18ab4d275cd71
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379343"
---
# <a name="icordebugsymbolprovider-interface"></a><span data-ttu-id="7e27a-102">ICorDebugSymbolProvider, interfejs</span><span class="sxs-lookup"><span data-stu-id="7e27a-102">ICorDebugSymbolProvider Interface</span></span>
<span data-ttu-id="7e27a-103">Dostarcza metody, których można użyć do pobrania informacji o symbolach debugowania.</span><span class="sxs-lookup"><span data-stu-id="7e27a-103">Provides methods that can be used to retrieve debug symbol information.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7e27a-104">Metody</span><span class="sxs-lookup"><span data-stu-id="7e27a-104">Methods</span></span>  
  
|<span data-ttu-id="7e27a-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="7e27a-105">Method</span></span>|<span data-ttu-id="7e27a-106">Opis</span><span class="sxs-lookup"><span data-stu-id="7e27a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7e27a-107">GetAssemblyImageBytes, metoda</span><span class="sxs-lookup"><span data-stu-id="7e27a-107">GetAssemblyImageBytes Method</span></span>](icordebugsymbolprovider-getassemblyimagebytes-method.md)|<span data-ttu-id="7e27a-108">Odczytuje dane z scalonego zestawu, uwzględniając względny adres wirtualny (RVA) w scalonym zestawie.</span><span class="sxs-lookup"><span data-stu-id="7e27a-108">Reads data from a merged assembly given a relative virtual address (RVA) in the merged assembly.</span></span>|  
|[<span data-ttu-id="7e27a-109">GetAssemblyImageMetadata, metoda</span><span class="sxs-lookup"><span data-stu-id="7e27a-109">GetAssemblyImageMetadata Method</span></span>](icordebugsymbolprovider-getassemblyimagemetadata-method.md)|<span data-ttu-id="7e27a-110">Zwraca metadane z scalonego zestawu.</span><span class="sxs-lookup"><span data-stu-id="7e27a-110">Returns the metadata from a merged assembly.</span></span>|  
|[<span data-ttu-id="7e27a-111">GetCodeRange, metoda</span><span class="sxs-lookup"><span data-stu-id="7e27a-111">GetCodeRange Method</span></span>](icordebugsymbolprovider-getcoderange-method.md)|<span data-ttu-id="7e27a-112">Pobiera adres początkowy i rozmiar metody z przyznanym adresem wirtualnym (RVA) w metodzie.</span><span class="sxs-lookup"><span data-stu-id="7e27a-112">Gets the method start address and size given a relative virtual address (RVA) in a method.</span></span>|  
|[<span data-ttu-id="7e27a-113">GetInstanceFieldSymbols, metoda</span><span class="sxs-lookup"><span data-stu-id="7e27a-113">GetInstanceFieldSymbols Method</span></span>](icordebugsymbolprovider-getinstancefieldsymbols-method.md)|<span data-ttu-id="7e27a-114">Pobiera symbole pól wystąpienia, które odpowiadają sygnaturze elementu TypeSpec.</span><span class="sxs-lookup"><span data-stu-id="7e27a-114">Gets the instance field symbols that correspond to a typespec signature.</span></span>|  
|[<span data-ttu-id="7e27a-115">GetMergedAssemblyRecords, metoda</span><span class="sxs-lookup"><span data-stu-id="7e27a-115">GetMergedAssemblyRecords Method</span></span>](icordebugsymbolprovider-getmergedassemblyrecords-method.md)|<span data-ttu-id="7e27a-116">Pobiera rekordy symboli dla wszystkich scalonych zestawów.</span><span class="sxs-lookup"><span data-stu-id="7e27a-116">Gets the symbol records for all the merged assemblies.</span></span>|  
|[<span data-ttu-id="7e27a-117">GetMethodLocalSymbols, metoda</span><span class="sxs-lookup"><span data-stu-id="7e27a-117">GetMethodLocalSymbols Method</span></span>](icordebugsymbolprovider-getmethodlocalsymbols-method.md)|<span data-ttu-id="7e27a-118">Pobiera symbole lokalne metody z uwzględnieniem względnego adresu wirtualnego (RVA) tej metody.</span><span class="sxs-lookup"><span data-stu-id="7e27a-118">Gets a method's local symbols given the relative virtual address (RVA) of that method.</span></span>|  
|[<span data-ttu-id="7e27a-119">GetMethodParameterSymbols, metoda</span><span class="sxs-lookup"><span data-stu-id="7e27a-119">GetMethodParameterSymbols Method</span></span>](icordebugsymbolprovider-getmethodparametersymbols-method.md)|<span data-ttu-id="7e27a-120">Pobiera symbole parametrów metody z uwzględnieniem względnego adresu wirtualnego (RVA) tej metody.</span><span class="sxs-lookup"><span data-stu-id="7e27a-120">Gets a method's parameter symbols given the relative virtual address (RVA) of that method.</span></span>|  
|[<span data-ttu-id="7e27a-121">GetMethodProps, metoda</span><span class="sxs-lookup"><span data-stu-id="7e27a-121">GetMethodProps Method</span></span>](icordebugsymbolprovider-getmethodprops-method.md)|<span data-ttu-id="7e27a-122">Zwraca informacje o właściwościach metody, takich jak token metadanych metody i informacje o jego ogólnych parametrach, w którym znajduje się względny adres wirtualny (RVA) w tej metodzie.</span><span class="sxs-lookup"><span data-stu-id="7e27a-122">Returns information about method properties, such as the method's metadata token and information about its generic parameters, given a relative virtual address (RVA) in that method.</span></span>|  
|[<span data-ttu-id="7e27a-123">GetObjectSize — Metoda</span><span class="sxs-lookup"><span data-stu-id="7e27a-123">GetObjectSize Method</span></span>](icordebugsymbolprovider-getobjectsize-method.md)|<span data-ttu-id="7e27a-124">Zwraca rozmiar obiektu na podstawie jego podpisu elementu TypeSpec.</span><span class="sxs-lookup"><span data-stu-id="7e27a-124">Returns the object size for an object based on its typespec signature.</span></span>|  
|[<span data-ttu-id="7e27a-125">GetStaticFieldSymbols, metoda</span><span class="sxs-lookup"><span data-stu-id="7e27a-125">GetStaticFieldSymbols Method</span></span>](icordebugsymbolprovider-getstaticfieldsymbols-method.md)|<span data-ttu-id="7e27a-126">Pobiera symbole pól statycznych, które odpowiadają sygnaturze elementu TypeSpec.</span><span class="sxs-lookup"><span data-stu-id="7e27a-126">Gets the static field symbols that correspond to a typespec signature.</span></span>|  
|[<span data-ttu-id="7e27a-127">GetTypeProps, metoda</span><span class="sxs-lookup"><span data-stu-id="7e27a-127">GetTypeProps Method</span></span>](icordebugsymbolprovider-gettypeprops-method.md)|<span data-ttu-id="7e27a-128">Zwraca informacje o właściwościach typu, takich jak liczba podpisów jego parametrów ogólnych, z uwzględnieniem względnego adresu wirtualnego (RVA) w tabeli jednoelementowej.</span><span class="sxs-lookup"><span data-stu-id="7e27a-128">Returns information about a type's properties, such as the number of signature of its generic parameters, given a relative virtual address (RVA) in a vtable.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7e27a-129">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7e27a-129">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7e27a-130">Ten interfejs jest dostępny tylko dla .NET Native.</span><span class="sxs-lookup"><span data-stu-id="7e27a-130">This interface is available with .NET Native only.</span></span> <span data-ttu-id="7e27a-131">W przypadku zaimplementowania tego interfejsu dla scenariuszy ICorDebug poza .NET Native, środowisko uruchomieniowe języka wspólnego zignoruje ten interfejs.</span><span class="sxs-lookup"><span data-stu-id="7e27a-131">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7e27a-132">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7e27a-132">Requirements</span></span>  
 <span data-ttu-id="7e27a-133">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7e27a-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7e27a-134">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="7e27a-134">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7e27a-135">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="7e27a-135">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7e27a-136">**.NET Framework wersje:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7e27a-136">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e27a-137">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7e27a-137">See also</span></span>

- [<span data-ttu-id="7e27a-138">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="7e27a-138">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="7e27a-139">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="7e27a-139">Debugging</span></span>](index.md)
