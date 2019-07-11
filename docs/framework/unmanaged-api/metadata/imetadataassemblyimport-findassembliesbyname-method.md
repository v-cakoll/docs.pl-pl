---
title: IMetaDataAssemblyImport::FindAssembliesByName — Metoda
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 315d9aa6f7db51342e71ba3f8fcdc091f7707743
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777978"
---
# <a name="imetadataassemblyimportfindassembliesbyname-method"></a><span data-ttu-id="1df79-102">IMetaDataAssemblyImport::FindAssembliesByName — Metoda</span><span class="sxs-lookup"><span data-stu-id="1df79-102">IMetaDataAssemblyImport::FindAssembliesByName Method</span></span>
<span data-ttu-id="1df79-103">Pobiera tablicę elementów zestawów z określonym `szAssemblyName` parametru, przy użyciu standardowych zasad stosowanych przez środowisko uruchomieniowe języka wspólnego (CLR) do rozpoznawania odwołań.</span><span class="sxs-lookup"><span data-stu-id="1df79-103">Gets an array of assemblies with the specified `szAssemblyName` parameter, using the standard rules employed by the common language runtime (CLR) for resolving references.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1df79-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1df79-104">Syntax</span></span>  
  
```cpp  
HRESULT FindAssembliesByName (  
    [in]  LPCWSTR     szAppBase,   
    [in]  LPCWSTR     szPrivateBin,   
    [in]  LPCWSTR     szAssemblyName,   
    [out] IUnknown    *ppIUnk[],   
    [in]  ULONG       cMax,   
    [out] ULONG       *pcAssemblies  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1df79-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1df79-105">Parameters</span></span>  
 `szAppBase`  
 <span data-ttu-id="1df79-106">[in] Katalog główny, w których należy szukać w danym zestawie.</span><span class="sxs-lookup"><span data-stu-id="1df79-106">[in] The root directory in which to search for the given assembly.</span></span> <span data-ttu-id="1df79-107">Jeśli ta wartość jest równa `null`, `FindAssembliesByName` będzie szukać tylko w globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="1df79-107">If this value is set to `null`, `FindAssembliesByName` will look only in the global assembly cache for the assembly.</span></span>  
  
 `szPrivateBin`  
 <span data-ttu-id="1df79-108">[in] Lista Rozdzielana średnikami (na przykład "bin; bin2"), zestawu podkatalogów w katalogu głównym, w których należy szukać zestawu.</span><span class="sxs-lookup"><span data-stu-id="1df79-108">[in] A list of semicolon-delimited subdirectories (for example, "bin;bin2"), under the root directory, in which to search for the assembly.</span></span> <span data-ttu-id="1df79-109">Te katalogi są sondowany oprócz tych określonych w domyślnych sondowania zasad.</span><span class="sxs-lookup"><span data-stu-id="1df79-109">These directories are probed in addition to those specified in the default probing rules.</span></span>  
  
 `szAssemblyName`  
 <span data-ttu-id="1df79-110">[in] Nazwa zestawu, aby znaleźć.</span><span class="sxs-lookup"><span data-stu-id="1df79-110">[in] The name of the assembly to find.</span></span> <span data-ttu-id="1df79-111">Format ten ciąg jest zdefiniowany w stronie dokumentacji klasy <xref:System.Reflection.AssemblyName>.</span><span class="sxs-lookup"><span data-stu-id="1df79-111">The format of this string is defined in the class reference page for <xref:System.Reflection.AssemblyName>.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="1df79-112">[in] Tablica typu [IUnknown](/cpp/atl/iunknown) w której chcesz umieścić `IMetadataAssemblyImport` wskaźniki interfejsu.</span><span class="sxs-lookup"><span data-stu-id="1df79-112">[in] An array of type [IUnknown](/cpp/atl/iunknown) in which to put the `IMetadataAssemblyImport` interface pointers.</span></span>  
  
 `cMax`  
 <span data-ttu-id="1df79-113">[out] Maksymalna liczba wskaźniki interfejsu, które mogą być umieszczane w `ppIUnk`.</span><span class="sxs-lookup"><span data-stu-id="1df79-113">[out] The maximum number of interface pointers that can be placed in `ppIUnk`.</span></span>  
  
 `pcAssemblies`  
 <span data-ttu-id="1df79-114">[out] Zwrócono liczbę wskaźniki interfejsu.</span><span class="sxs-lookup"><span data-stu-id="1df79-114">[out] The number of interface pointers returned.</span></span> <span data-ttu-id="1df79-115">Oznacza to, że numer wskaźniki interfejsu faktycznie umieszczonych w `ppIUnk`.</span><span class="sxs-lookup"><span data-stu-id="1df79-115">That is, the number of interface pointers actually placed in `ppIUnk`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1df79-116">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="1df79-116">Return Value</span></span>  
  
|<span data-ttu-id="1df79-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1df79-117">HRESULT</span></span>|<span data-ttu-id="1df79-118">Opis</span><span class="sxs-lookup"><span data-stu-id="1df79-118">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="1df79-119">`FindAssembliesByName` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="1df79-119">`FindAssembliesByName` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="1df79-120">Nie ma żadnych zestawów.</span><span class="sxs-lookup"><span data-stu-id="1df79-120">There are no assemblies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1df79-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1df79-121">Remarks</span></span>  
 <span data-ttu-id="1df79-122">Podana nazwa zestawu, `FindAssembliesByName` metoda znajdzie zestawu, wykonując standardowe reguły rozpoznawania odwołań do zestawów.</span><span class="sxs-lookup"><span data-stu-id="1df79-122">Given an assembly name, the `FindAssembliesByName` method finds the assembly by following the standard rules for resolving assembly references.</span></span> <span data-ttu-id="1df79-123">(Aby uzyskać więcej informacji, zobacz [jak środowisko uruchomieniowe lokalizuje zestawy](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).) `FindAssembliesByName` umożliwia obiektowi wywołującemu skonfigurować różne aspekty kontekstu mechanizm rozpoznawania zestawów, takich jak ścieżki wyszukiwania podstawowego i prywatne aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1df79-123">(For more information, see [How the Runtime Locates Assemblies](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).) `FindAssembliesByName` allows the caller to configure various aspects of the assembly resolver context, such as application base and private search path.</span></span>  
  
 <span data-ttu-id="1df79-124">`FindAssembliesByName` Metoda wymaga środowiska CLR do zainicjowania procesu w celu wywołania logiki rozpoznawania zestawu.</span><span class="sxs-lookup"><span data-stu-id="1df79-124">The `FindAssembliesByName` method requires the CLR to be initialized in the process in order to invoke the assembly resolution logic.</span></span> <span data-ttu-id="1df79-125">W związku z tym, należy wywołać [coinitializeee —](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md) (przekazywanie COINITEE_DEFAULT) przed wywołaniem `FindAssembliesByName`, a następnie postępuj zgodnie z wywołaniem [couninitializecor —](../../../../docs/framework/unmanaged-api/hosting/couninitializecor-function.md).</span><span class="sxs-lookup"><span data-stu-id="1df79-125">Therefore, you must call [CoInitializeEE](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md) (passing COINITEE_DEFAULT) before calling `FindAssembliesByName`, and then follow with a call to [CoUninitializeCor](../../../../docs/framework/unmanaged-api/hosting/couninitializecor-function.md).</span></span>  
  
 <span data-ttu-id="1df79-126">`FindAssembliesByName` Zwraca [imetadataimport —](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) wskaźnika do pliku zawierającego manifest zestawu dla nazwy zestawu, który jest przekazywany w.</span><span class="sxs-lookup"><span data-stu-id="1df79-126">`FindAssembliesByName` returns an [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) pointer to the file containing the assembly manifest for the assembly name that is passed in.</span></span> <span data-ttu-id="1df79-127">Jeśli nazwa danego zestawu nie jest w pełni określona (na przykład, jeśli nie ma wersji), może zostać zwrócona wiele zestawów.</span><span class="sxs-lookup"><span data-stu-id="1df79-127">If the given assembly name is not fully specified (for example, if it does not include a version), multiple assemblies might be returned.</span></span>  
  
 <span data-ttu-id="1df79-128">`FindAssembliesByName` najczęściej jest używana przez kompilator, który próbuje odnaleźć przywoływanego zestawu w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="1df79-128">`FindAssembliesByName` is commonly used by a compiler that attempts to find a referenced assembly at compile time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1df79-129">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1df79-129">Requirements</span></span>  
 <span data-ttu-id="1df79-130">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1df79-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1df79-131">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="1df79-131">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1df79-132">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1df79-132">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1df79-133">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1df79-133">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1df79-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1df79-134">See also</span></span>

- [<span data-ttu-id="1df79-135">Sposoby lokalizowania zestawów przez środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="1df79-135">How the Runtime Locates Assemblies</span></span>](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="1df79-136">IMetaDataAssemblyImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="1df79-136">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
