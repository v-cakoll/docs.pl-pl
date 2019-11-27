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
ms.openlocfilehash: c12d3a7a7d1e52529435361aa12e22e4edeecf03
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448288"
---
# <a name="imetadataassemblyimportfindassembliesbyname-method"></a><span data-ttu-id="cc1dc-102">IMetaDataAssemblyImport::FindAssembliesByName — Metoda</span><span class="sxs-lookup"><span data-stu-id="cc1dc-102">IMetaDataAssemblyImport::FindAssembliesByName Method</span></span>
<span data-ttu-id="cc1dc-103">Pobiera tablicę zestawów z określonym parametrem `szAssemblyName` przy użyciu standardowych reguł używanych przez środowisko uruchomieniowe języka wspólnego (CLR) do rozpoznawania odwołań.</span><span class="sxs-lookup"><span data-stu-id="cc1dc-103">Gets an array of assemblies with the specified `szAssemblyName` parameter, using the standard rules employed by the common language runtime (CLR) for resolving references.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc1dc-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="cc1dc-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="cc1dc-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cc1dc-105">Parameters</span></span>  
 `szAppBase`  
 <span data-ttu-id="cc1dc-106">podczas Katalog główny, w którym ma zostać wyszukany dany zestaw.</span><span class="sxs-lookup"><span data-stu-id="cc1dc-106">[in] The root directory in which to search for the given assembly.</span></span> <span data-ttu-id="cc1dc-107">Jeśli ta wartość jest ustawiona na `null`, `FindAssembliesByName` będzie wyglądać tylko w globalnej pamięci podręcznej zestawów zestawu.</span><span class="sxs-lookup"><span data-stu-id="cc1dc-107">If this value is set to `null`, `FindAssembliesByName` will look only in the global assembly cache for the assembly.</span></span>  
  
 `szPrivateBin`  
 <span data-ttu-id="cc1dc-108">podczas Rozdzielana średnikami lista podkatalogów (na przykład "bin; BIN2"), w katalogu głównym, w którym ma zostać wyszukany zestaw.</span><span class="sxs-lookup"><span data-stu-id="cc1dc-108">[in] A list of semicolon-delimited subdirectories (for example, "bin;bin2"), under the root directory, in which to search for the assembly.</span></span> <span data-ttu-id="cc1dc-109">Te katalogi są badane dodatkowo do tych, które są określone w domyślnych regułach sondowania.</span><span class="sxs-lookup"><span data-stu-id="cc1dc-109">These directories are probed in addition to those specified in the default probing rules.</span></span>  
  
 `szAssemblyName`  
 <span data-ttu-id="cc1dc-110">podczas Nazwa zestawu do znalezienia.</span><span class="sxs-lookup"><span data-stu-id="cc1dc-110">[in] The name of the assembly to find.</span></span> <span data-ttu-id="cc1dc-111">Format tego ciągu jest definiowany na stronie odniesienia klasy dla <xref:System.Reflection.AssemblyName>.</span><span class="sxs-lookup"><span data-stu-id="cc1dc-111">The format of this string is defined in the class reference page for <xref:System.Reflection.AssemblyName>.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="cc1dc-112">podczas Tablica typu [IUnknown](/cpp/atl/iunknown) , w której mają zostać umieszczone `IMetadataAssemblyImport` wskaźniki interfejsu.</span><span class="sxs-lookup"><span data-stu-id="cc1dc-112">[in] An array of type [IUnknown](/cpp/atl/iunknown) in which to put the `IMetadataAssemblyImport` interface pointers.</span></span>  
  
 `cMax`  
 <span data-ttu-id="cc1dc-113">określoną Maksymalna liczba wskaźników interfejsu, które można umieścić w `ppIUnk`.</span><span class="sxs-lookup"><span data-stu-id="cc1dc-113">[out] The maximum number of interface pointers that can be placed in `ppIUnk`.</span></span>  
  
 `pcAssemblies`  
 <span data-ttu-id="cc1dc-114">określoną Liczba zwróconych wskaźników interfejsu.</span><span class="sxs-lookup"><span data-stu-id="cc1dc-114">[out] The number of interface pointers returned.</span></span> <span data-ttu-id="cc1dc-115">Oznacza to, że liczba wskaźników interfejsu faktycznie umieszczonych w `ppIUnk`.</span><span class="sxs-lookup"><span data-stu-id="cc1dc-115">That is, the number of interface pointers actually placed in `ppIUnk`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cc1dc-116">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="cc1dc-116">Return Value</span></span>  
  
|<span data-ttu-id="cc1dc-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="cc1dc-117">HRESULT</span></span>|<span data-ttu-id="cc1dc-118">Opis</span><span class="sxs-lookup"><span data-stu-id="cc1dc-118">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="cc1dc-119">`FindAssembliesByName` pomyślnie zwrócone.</span><span class="sxs-lookup"><span data-stu-id="cc1dc-119">`FindAssembliesByName` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="cc1dc-120">Brak zestawów.</span><span class="sxs-lookup"><span data-stu-id="cc1dc-120">There are no assemblies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cc1dc-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cc1dc-121">Remarks</span></span>  
 <span data-ttu-id="cc1dc-122">Podaną nazwę zestawu, Metoda `FindAssembliesByName` odnajduje zestaw według standardowych reguł rozpoznawania odwołań do zestawów.</span><span class="sxs-lookup"><span data-stu-id="cc1dc-122">Given an assembly name, the `FindAssembliesByName` method finds the assembly by following the standard rules for resolving assembly references.</span></span> <span data-ttu-id="cc1dc-123">(Aby uzyskać więcej informacji, zobacz [jak środowisko uruchomieniowe lokalizuje zestawy](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).) `FindAssembliesByName` pozwala wywołującemu konfigurować różne aspekty kontekstu programu rozpoznawania nazw, takie jak ścieżka do bazy aplikacji i wyszukiwania prywatnego.</span><span class="sxs-lookup"><span data-stu-id="cc1dc-123">(For more information, see [How the Runtime Locates Assemblies](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).) `FindAssembliesByName` allows the caller to configure various aspects of the assembly resolver context, such as application base and private search path.</span></span>  
  
 <span data-ttu-id="cc1dc-124">Metoda `FindAssembliesByName` wymaga zainicjowania środowiska CLR w procesie w celu wywołania logiki rozpoznawania zestawu.</span><span class="sxs-lookup"><span data-stu-id="cc1dc-124">The `FindAssembliesByName` method requires the CLR to be initialized in the process in order to invoke the assembly resolution logic.</span></span> <span data-ttu-id="cc1dc-125">W związku z tym przed wywołaniem `FindAssembliesByName`należy wywołać [CoInitializeEE —](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md) (przekazując COINITEE_DEFAULT), a następnie wykonać wywołanie [CoUninitializeCor —](../../../../docs/framework/unmanaged-api/hosting/couninitializecor-function.md).</span><span class="sxs-lookup"><span data-stu-id="cc1dc-125">Therefore, you must call [CoInitializeEE](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md) (passing COINITEE_DEFAULT) before calling `FindAssembliesByName`, and then follow with a call to [CoUninitializeCor](../../../../docs/framework/unmanaged-api/hosting/couninitializecor-function.md).</span></span>  
  
 <span data-ttu-id="cc1dc-126">`FindAssembliesByName` zwraca wskaźnik [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) do pliku zawierającego manifest zestawu dla nazwy zestawu, która została przeniesiona.</span><span class="sxs-lookup"><span data-stu-id="cc1dc-126">`FindAssembliesByName` returns an [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) pointer to the file containing the assembly manifest for the assembly name that is passed in.</span></span> <span data-ttu-id="cc1dc-127">Jeśli podana nazwa zestawu nie jest w pełni określona (na przykład jeśli nie zawiera wersji), można zwrócić wiele zestawów.</span><span class="sxs-lookup"><span data-stu-id="cc1dc-127">If the given assembly name is not fully specified (for example, if it does not include a version), multiple assemblies might be returned.</span></span>  
  
 <span data-ttu-id="cc1dc-128">`FindAssembliesByName` jest często używany przez kompilator, który próbuje znaleźć przywoływany zestaw w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="cc1dc-128">`FindAssembliesByName` is commonly used by a compiler that attempts to find a referenced assembly at compile time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cc1dc-129">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cc1dc-129">Requirements</span></span>  
 <span data-ttu-id="cc1dc-130">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cc1dc-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cc1dc-131">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="cc1dc-131">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="cc1dc-132">**Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="cc1dc-132">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="cc1dc-133">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cc1dc-133">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc1dc-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cc1dc-134">See also</span></span>

- [<span data-ttu-id="cc1dc-135">Sposoby lokalizowania zestawów przez środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="cc1dc-135">How the Runtime Locates Assemblies</span></span>](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="cc1dc-136">IMetaDataAssemblyImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="cc1dc-136">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
