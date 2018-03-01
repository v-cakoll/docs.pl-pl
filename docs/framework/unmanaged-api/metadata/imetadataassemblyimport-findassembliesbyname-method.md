---
title: "IMetaDataAssemblyImport::FindAssembliesByName — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IMetaDataAssemblyImport.FindAssembliesByName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::FindAssembliesByName
helpviewer_keywords:
- FindAssembliesByName method [.NET Framework metadata]
- IMetaDataAssemblyImport::FindAssembliesByName method [.NET Framework metadata]
ms.assetid: 4db97cf9-e4c1-4233-8efa-cbdc0e14a8e4
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4d6518fdcf1bef8eaea74818f69f46bb6df26e31
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataassemblyimportfindassembliesbyname-method"></a><span data-ttu-id="6d38f-102">IMetaDataAssemblyImport::FindAssembliesByName — Metoda</span><span class="sxs-lookup"><span data-stu-id="6d38f-102">IMetaDataAssemblyImport::FindAssembliesByName Method</span></span>
<span data-ttu-id="6d38f-103">Pobiera tablicę zestawy z określonym `szAssemblyName` parametr, przy użyciu standardowych zasad stosowanych przez środowisko uruchomieniowe języka wspólnego (CLR) do rozpoznawania odwołań.</span><span class="sxs-lookup"><span data-stu-id="6d38f-103">Gets an array of assemblies with the specified `szAssemblyName` parameter, using the standard rules employed by the common language runtime (CLR) for resolving references.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d38f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6d38f-104">Syntax</span></span>  
  
```  
HRESULT FindAssembliesByName (  
    [in]  LPCWSTR     szAppBase,   
    [in]  LPCWSTR     szPrivateBin,   
    [in]  LPCWSTR     szAssemblyName,   
    [out] IUnknown    *ppIUnk[],   
    [in]  ULONG       cMax,   
    [out] ULONG       *pcAssemblies  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6d38f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6d38f-105">Parameters</span></span>  
 `szAppBase`  
 <span data-ttu-id="6d38f-106">[in] Katalog główny wyszukiwania dla danego zestawu.</span><span class="sxs-lookup"><span data-stu-id="6d38f-106">[in] The root directory in which to search for the given assembly.</span></span> <span data-ttu-id="6d38f-107">Jeśli ta wartość jest równa `null`, `FindAssembliesByName` będzie szukać tylko w pamięci podręcznej GAC zestawu.</span><span class="sxs-lookup"><span data-stu-id="6d38f-107">If this value is set to `null`, `FindAssembliesByName` will look only in the global assembly cache for the assembly.</span></span>  
  
 `szPrivateBin`  
 <span data-ttu-id="6d38f-108">[in] Lista Rozdzielana średnikami podkatalogi (na przykład "bin; pojemnik 2"), w obszarze katalogu głównego, w których będą poszukiwane zestawu.</span><span class="sxs-lookup"><span data-stu-id="6d38f-108">[in] A list of semicolon-delimited subdirectories (for example, "bin;bin2"), under the root directory, in which to search for the assembly.</span></span> <span data-ttu-id="6d38f-109">Te katalogi są sondowany oprócz tych określonych w domyślnym sondowanie zasad.</span><span class="sxs-lookup"><span data-stu-id="6d38f-109">These directories are probed in addition to those specified in the default probing rules.</span></span>  
  
 `szAssemblyName`  
 <span data-ttu-id="6d38f-110">[in] Nazwa zestawu można znaleźć.</span><span class="sxs-lookup"><span data-stu-id="6d38f-110">[in] The name of the assembly to find.</span></span> <span data-ttu-id="6d38f-111">Format ten ciąg jest zdefiniowany w odwołaniu klasy dla <xref:System.Reflection.AssemblyName>.</span><span class="sxs-lookup"><span data-stu-id="6d38f-111">The format of this string is defined in the class reference page for <xref:System.Reflection.AssemblyName>.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="6d38f-112">[in] Tablica typu <<!--zzxref:IUnknown --> `IUnknown`> w której chcesz umieścić `IMetadataAssemblyImport` wskaźniki interfejsu.</span><span class="sxs-lookup"><span data-stu-id="6d38f-112">[in] An array of type <<!--zzxref:IUnknown --> `IUnknown`> in which to put the `IMetadataAssemblyImport` interface pointers.</span></span>  
  
 `cMax`  
 <span data-ttu-id="6d38f-113">[out] Maksymalna liczba wskaźniki interfejsu, które można umieścić w `ppIUnk`.</span><span class="sxs-lookup"><span data-stu-id="6d38f-113">[out] The maximum number of interface pointers that can be placed in `ppIUnk`.</span></span>  
  
 `pcAssemblies`  
 <span data-ttu-id="6d38f-114">[out] Zwrócono liczbę wskaźniki interfejsu.</span><span class="sxs-lookup"><span data-stu-id="6d38f-114">[out] The number of interface pointers returned.</span></span> <span data-ttu-id="6d38f-115">Oznacza to, że liczba wskaźniki interfejsu faktycznie umieszczonych w `ppIUnk`.</span><span class="sxs-lookup"><span data-stu-id="6d38f-115">That is, the number of interface pointers actually placed in `ppIUnk`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6d38f-116">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="6d38f-116">Return Value</span></span>  
  
|<span data-ttu-id="6d38f-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6d38f-117">HRESULT</span></span>|<span data-ttu-id="6d38f-118">Opis</span><span class="sxs-lookup"><span data-stu-id="6d38f-118">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="6d38f-119">`FindAssembliesByName`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="6d38f-119">`FindAssembliesByName` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="6d38f-120">Nie ma żadnych zestawów.</span><span class="sxs-lookup"><span data-stu-id="6d38f-120">There are no assemblies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6d38f-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6d38f-121">Remarks</span></span>  
 <span data-ttu-id="6d38f-122">Podana nazwa zestawu `FindAssembliesByName` metoda znajdzie zestawu wykonując standardowych zasad rozpoznawania odwołań do zestawu.</span><span class="sxs-lookup"><span data-stu-id="6d38f-122">Given an assembly name, the `FindAssembliesByName` method finds the assembly by following the standard rules for resolving assembly references.</span></span> <span data-ttu-id="6d38f-123">(Aby uzyskać więcej informacji, zobacz [jak zestawy środowiska wykonawczego lokalizuje](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).) `FindAssembliesByName` umożliwia obiekt wywołujący, aby skonfigurować różne aspekty kontekst rozpoznawania zestawu, takie jak ścieżka wyszukiwania podstawowego i prywatnych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6d38f-123">(For more information, see [How the Runtime Locates Assemblies](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).) `FindAssembliesByName` allows the caller to configure various aspects of the assembly resolver context, such as application base and private search path.</span></span>  
  
 <span data-ttu-id="6d38f-124">`FindAssembliesByName` Metoda wymaga środowiska CLR do zainicjowania procesu w celu wywołania logiki rozpoznawania zestawu.</span><span class="sxs-lookup"><span data-stu-id="6d38f-124">The `FindAssembliesByName` method requires the CLR to be initialized in the process in order to invoke the assembly resolution logic.</span></span> <span data-ttu-id="6d38f-125">W związku z tym należy wywołać [CoInitializeEE](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md) (przekazywanie COINITEE_DEFAULT) przed wywołaniem `FindAssembliesByName`, a następnie postępuj zgodnie z wywołaniem do [CoUninitializeCor](../../../../docs/framework/unmanaged-api/hosting/couninitializecor-function.md).</span><span class="sxs-lookup"><span data-stu-id="6d38f-125">Therefore, you must call [CoInitializeEE](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md) (passing COINITEE_DEFAULT) before calling `FindAssembliesByName`, and then follow with a call to [CoUninitializeCor](../../../../docs/framework/unmanaged-api/hosting/couninitializecor-function.md).</span></span>  
  
 <span data-ttu-id="6d38f-126">`FindAssembliesByName`Zwraca [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) wskaźnika do pliku zawierającego manifest zestawu dla nazwy zestawu, który jest przekazywany w.</span><span class="sxs-lookup"><span data-stu-id="6d38f-126">`FindAssembliesByName` returns an [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) pointer to the file containing the assembly manifest for the assembly name that is passed in.</span></span> <span data-ttu-id="6d38f-127">Jeśli podana nazwa zestawu nie określono pełni (na przykład, jeśli nie ma wersji), może być zwrócony wiele zestawów.</span><span class="sxs-lookup"><span data-stu-id="6d38f-127">If the given assembly name is not fully specified (for example, if it does not include a version), multiple assemblies might be returned.</span></span>  
  
 <span data-ttu-id="6d38f-128">`FindAssembliesByName`to powszechnie używane przez kompilator, który próbuje odnaleźć przywoływanego zestawu w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="6d38f-128">`FindAssembliesByName` is commonly used by a compiler that attempts to find a referenced assembly at compile time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6d38f-129">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6d38f-129">Requirements</span></span>  
 <span data-ttu-id="6d38f-130">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6d38f-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6d38f-131">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="6d38f-131">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6d38f-132">**Biblioteka:** używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6d38f-132">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6d38f-133">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d38f-133">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d38f-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6d38f-134">See Also</span></span>  
 [<span data-ttu-id="6d38f-135">Sposoby lokalizowania zestawów przez środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="6d38f-135">How the Runtime Locates Assemblies</span></span>](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [<span data-ttu-id="6d38f-136">IMetaDataAssemblyImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="6d38f-136">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
