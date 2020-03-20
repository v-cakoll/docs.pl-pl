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
ms.openlocfilehash: c0f81e3767d4ea3bc336203fbe8c914b4e2bd07b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177799"
---
# <a name="imetadataassemblyimportfindassembliesbyname-method"></a><span data-ttu-id="a300b-102">IMetaDataAssemblyImport::FindAssembliesByName — Metoda</span><span class="sxs-lookup"><span data-stu-id="a300b-102">IMetaDataAssemblyImport::FindAssembliesByName Method</span></span>
<span data-ttu-id="a300b-103">Pobiera tablicę zestawów z `szAssemblyName` określonym parametrem, przy użyciu standardowych reguł używanych przez środowisko uruchomieniowe języka wspólnego (CLR) do rozpoznawania odwołań.</span><span class="sxs-lookup"><span data-stu-id="a300b-103">Gets an array of assemblies with the specified `szAssemblyName` parameter, using the standard rules employed by the common language runtime (CLR) for resolving references.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a300b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a300b-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="a300b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a300b-105">Parameters</span></span>  
 `szAppBase`  
 <span data-ttu-id="a300b-106">[w] Katalog główny, w którym ma być wyszukiwany dany zestaw.</span><span class="sxs-lookup"><span data-stu-id="a300b-106">[in] The root directory in which to search for the given assembly.</span></span> <span data-ttu-id="a300b-107">Jeśli ta wartość `null`jest `FindAssembliesByName` ustawiona na , będzie wyglądać tylko w globalnej pamięci podręcznej zestawów dla zestawu.</span><span class="sxs-lookup"><span data-stu-id="a300b-107">If this value is set to `null`, `FindAssembliesByName` will look only in the global assembly cache for the assembly.</span></span>  
  
 `szPrivateBin`  
 <span data-ttu-id="a300b-108">[w] Lista podkatalogów rozdzielanych średnikami (na przykład "bin;bin2"), w katalogu głównym, w którym ma być wyszukiwana zestaw.</span><span class="sxs-lookup"><span data-stu-id="a300b-108">[in] A list of semicolon-delimited subdirectories (for example, "bin;bin2"), under the root directory, in which to search for the assembly.</span></span> <span data-ttu-id="a300b-109">Katalogi te są badane oprócz tych określonych w domyślnych reguł sondowania.</span><span class="sxs-lookup"><span data-stu-id="a300b-109">These directories are probed in addition to those specified in the default probing rules.</span></span>  
  
 `szAssemblyName`  
 <span data-ttu-id="a300b-110">[w] Nazwa zestawu do znalezienia.</span><span class="sxs-lookup"><span data-stu-id="a300b-110">[in] The name of the assembly to find.</span></span> <span data-ttu-id="a300b-111">Format tego ciągu jest zdefiniowany na <xref:System.Reflection.AssemblyName>stronie odwołania do klasy dla programu .</span><span class="sxs-lookup"><span data-stu-id="a300b-111">The format of this string is defined in the class reference page for <xref:System.Reflection.AssemblyName>.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="a300b-112">[w] Tablica typu [IUnknown,](/cpp/atl/iunknown) w `IMetadataAssemblyImport` którym można umieścić wskaźniki interfejsu.</span><span class="sxs-lookup"><span data-stu-id="a300b-112">[in] An array of type [IUnknown](/cpp/atl/iunknown) in which to put the `IMetadataAssemblyImport` interface pointers.</span></span>  
  
 `cMax`  
 <span data-ttu-id="a300b-113">[na zewnątrz] Maksymalna liczba wskaźników interfejsu, które `ppIUnk`można umieścić w pliku .</span><span class="sxs-lookup"><span data-stu-id="a300b-113">[out] The maximum number of interface pointers that can be placed in `ppIUnk`.</span></span>  
  
 `pcAssemblies`  
 <span data-ttu-id="a300b-114">[na zewnątrz] Zwracana liczba wskaźników interfejsu.</span><span class="sxs-lookup"><span data-stu-id="a300b-114">[out] The number of interface pointers returned.</span></span> <span data-ttu-id="a300b-115">Oznacza to, że liczba wskaźników interfejsu `ppIUnk`faktycznie umieszczone w .</span><span class="sxs-lookup"><span data-stu-id="a300b-115">That is, the number of interface pointers actually placed in `ppIUnk`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a300b-116">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="a300b-116">Return Value</span></span>  
  
|<span data-ttu-id="a300b-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a300b-117">HRESULT</span></span>|<span data-ttu-id="a300b-118">Opis</span><span class="sxs-lookup"><span data-stu-id="a300b-118">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="a300b-119">`FindAssembliesByName`zwrócono pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="a300b-119">`FindAssembliesByName` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="a300b-120">Nie ma żadnych zestawów.</span><span class="sxs-lookup"><span data-stu-id="a300b-120">There are no assemblies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a300b-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a300b-121">Remarks</span></span>  
 <span data-ttu-id="a300b-122">Biorąc pod uwagę `FindAssembliesByName` nazwę zestawu, metoda znajduje zestaw, postępujący zgodnie ze standardowymi regułami rozpoznawania odwołań do zestawu.</span><span class="sxs-lookup"><span data-stu-id="a300b-122">Given an assembly name, the `FindAssembliesByName` method finds the assembly by following the standard rules for resolving assembly references.</span></span> <span data-ttu-id="a300b-123">(Aby uzyskać więcej informacji, zobacz [Jak środowisko wykonawcze lokalizuje zestawy](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).) `FindAssembliesByName` umożliwia wywołującemu skonfigurowanie różnych aspektów kontekstu rozpoznawania nazw zestawu, takich jak baza aplikacji i prywatna ścieżka wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="a300b-123">(For more information, see [How the Runtime Locates Assemblies](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).) `FindAssembliesByName` allows the caller to configure various aspects of the assembly resolver context, such as application base and private search path.</span></span>  
  
 <span data-ttu-id="a300b-124">Metoda `FindAssembliesByName` wymaga CLR do zainicjowania w procesie w celu wywołania logiki rozpoznawania zestawu.</span><span class="sxs-lookup"><span data-stu-id="a300b-124">The `FindAssembliesByName` method requires the CLR to be initialized in the process in order to invoke the assembly resolution logic.</span></span> <span data-ttu-id="a300b-125">W związku z tym należy wywołać [CoInitializeEEE](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md) `FindAssembliesByName`(przekazywanie COINITEE_DEFAULT) przed wywołaniem , a następnie wykonaj połączenie [z CoUninitializeCor](../../../../docs/framework/unmanaged-api/hosting/couninitializecor-function.md).</span><span class="sxs-lookup"><span data-stu-id="a300b-125">Therefore, you must call [CoInitializeEE](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md) (passing COINITEE_DEFAULT) before calling `FindAssembliesByName`, and then follow with a call to [CoUninitializeCor](../../../../docs/framework/unmanaged-api/hosting/couninitializecor-function.md).</span></span>  
  
 <span data-ttu-id="a300b-126">`FindAssembliesByName`zwraca wskaźnik [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) do pliku zawierającego manifest zestawu dla nazwy zestawu, który jest przekazywany.</span><span class="sxs-lookup"><span data-stu-id="a300b-126">`FindAssembliesByName` returns an [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) pointer to the file containing the assembly manifest for the assembly name that is passed in.</span></span> <span data-ttu-id="a300b-127">Jeśli dana nazwa zestawu nie jest w pełni określona (na przykład, jeśli nie zawiera wersji), może zostać zwróconych wiele zestawów.</span><span class="sxs-lookup"><span data-stu-id="a300b-127">If the given assembly name is not fully specified (for example, if it does not include a version), multiple assemblies might be returned.</span></span>  
  
 <span data-ttu-id="a300b-128">`FindAssembliesByName`jest powszechnie używany przez kompilator, który próbuje znaleźć zestaw, do którego istnieje odwołanie w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="a300b-128">`FindAssembliesByName` is commonly used by a compiler that attempts to find a referenced assembly at compile time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a300b-129">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a300b-129">Requirements</span></span>  
 <span data-ttu-id="a300b-130">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a300b-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a300b-131">**Nagłówek:** Okręg wyborczy Cor.h</span><span class="sxs-lookup"><span data-stu-id="a300b-131">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a300b-132">**Biblioteka:** Używany jako zasób w pliku MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a300b-132">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a300b-133">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a300b-133">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a300b-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a300b-134">See also</span></span>

- [<span data-ttu-id="a300b-135">Sposoby lokalizowania zestawów przez środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="a300b-135">How the Runtime Locates Assemblies</span></span>](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="a300b-136">IMetaDataAssemblyImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="a300b-136">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
