---
title: LoadTypeLibWithResolver — Funkcja
ms.date: 03/30/2017
api_name:
- LoadTypeLibWithResolver
api_location:
- TlbRef.dll
api_type:
- DLLExport
f1_keywords:
- LoadTypeLibWithResolver
helpviewer_keywords:
- LoadTypeLibWithResolver function [.NET Framework]
ms.assetid: 7123a89b-eb9b-463a-a552-a081e33b0a3a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5d2f5ad2afb2e73acead82369782f142aa10aac3
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782713"
---
# <a name="loadtypelibwithresolver-function"></a><span data-ttu-id="8e896-102">LoadTypeLibWithResolver — Funkcja</span><span class="sxs-lookup"><span data-stu-id="8e896-102">LoadTypeLibWithResolver Function</span></span>
<span data-ttu-id="8e896-103">Ładuje bibliotekę typów i korzysta z podanym [itypelibresolver — interfejs](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) rozpoznać wszystkie biblioteki typu wewnętrznie odwołania.</span><span class="sxs-lookup"><span data-stu-id="8e896-103">Loads a type library and uses the supplied [ITypeLibResolver interface](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) to resolve any internally referenced type libraries.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e896-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8e896-104">Syntax</span></span>  
  
```cpp  
HRESULT LoadTypeLibWithResolver(  
    [in]  LPCOLESTR           szFile,  
    [in]  REGKIND             regkind,  
    [in]  ITypeLibResolver   *pTlbResolver,  
    [out] ITypeLib          **pptlib);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8e896-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8e896-105">Parameters</span></span>  
 `szFile`  
 <span data-ttu-id="8e896-106">[in] Ścieżka pliku biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="8e896-106">[in] The file path of the type library.</span></span>  
  
 `regkind`  
 <span data-ttu-id="8e896-107">[in] A [wyliczenie REGKIND](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/ne-oleauto-tagregkind) flagi, które kontroluje sposób zrejestrowanej biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="8e896-107">[in] A [REGKIND enumeration](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/ne-oleauto-tagregkind) flag that controls how the type library is registered.</span></span> <span data-ttu-id="8e896-108">Jego możliwe wartości to:</span><span class="sxs-lookup"><span data-stu-id="8e896-108">Its possible values are:</span></span>  
  
- <span data-ttu-id="8e896-109">`REGKIND_DEFAULT`: Użyj domyślnego zachowania rejestracji.</span><span class="sxs-lookup"><span data-stu-id="8e896-109">`REGKIND_DEFAULT`: Use default registration behavior.</span></span>  
  
- <span data-ttu-id="8e896-110">`REGKIND_REGISTER`: Zarejestruj tego typu biblioteki.</span><span class="sxs-lookup"><span data-stu-id="8e896-110">`REGKIND_REGISTER`: Register this type library.</span></span>  
  
- <span data-ttu-id="8e896-111">`REGKIND_NONE`: Nie rejestruj tej biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="8e896-111">`REGKIND_NONE`: Do not register this type library.</span></span>  
  
 `pTlbResolver`  
 <span data-ttu-id="8e896-112">[in] Wskaźnik do implementacji [itypelibresolver — interfejs](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md).</span><span class="sxs-lookup"><span data-stu-id="8e896-112">[in] A pointer to the implementation of the [ITypeLibResolver interface](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md).</span></span>  
  
 `pptlib`  
 <span data-ttu-id="8e896-113">[out] Odwołanie do biblioteki typów, który jest ładowany.</span><span class="sxs-lookup"><span data-stu-id="8e896-113">[out] A reference to the type library that is being loaded.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8e896-114">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="8e896-114">Return Value</span></span>  
 <span data-ttu-id="8e896-115">Jedna z wartości HRESULT, wymienione w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="8e896-115">One of the HRESULT values listed in the following table.</span></span>  
  
|<span data-ttu-id="8e896-116">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="8e896-116">Return value</span></span>|<span data-ttu-id="8e896-117">Znaczenie</span><span class="sxs-lookup"><span data-stu-id="8e896-117">Meaning</span></span>|  
|------------------|-------------|  
|`S_OK`|<span data-ttu-id="8e896-118">Powodzenie.</span><span class="sxs-lookup"><span data-stu-id="8e896-118">Success.</span></span>|  
|`E_OUTOFMEMORY`|<span data-ttu-id="8e896-119">Za mało pamięci.</span><span class="sxs-lookup"><span data-stu-id="8e896-119">Out of memory.</span></span>|  
|`E_POINTER`|<span data-ttu-id="8e896-120">Co najmniej jeden ze wskaźników są nieprawidłowe.</span><span class="sxs-lookup"><span data-stu-id="8e896-120">One or more of the pointers are invalid.</span></span>|  
|`E_INVALIDARG`|<span data-ttu-id="8e896-121">Co najmniej jeden z argumentów są nieprawidłowe.</span><span class="sxs-lookup"><span data-stu-id="8e896-121">One or more of the arguments are invalid.</span></span>|  
|`TYPE_E_IOERROR`|<span data-ttu-id="8e896-122">Funkcja nie można zapisać do pliku.</span><span class="sxs-lookup"><span data-stu-id="8e896-122">The function could not write to the file.</span></span>|  
|`TYPE_E_REGISTRYACCESS`|<span data-ttu-id="8e896-123">Nie można otworzyć bazy danych rejestracji systemu.</span><span class="sxs-lookup"><span data-stu-id="8e896-123">The system registration database could not be opened.</span></span>|  
|`TYPE_E_INVALIDSTATE`|<span data-ttu-id="8e896-124">Nie można otworzyć biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="8e896-124">The type library could not be opened.</span></span>|  
|`TYPE_E_CANTLOADLIBRARY`|<span data-ttu-id="8e896-125">Nie można załadować biblioteki typów lub DLL.</span><span class="sxs-lookup"><span data-stu-id="8e896-125">The type library or DLL could not be loaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8e896-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8e896-126">Remarks</span></span>  
 <span data-ttu-id="8e896-127">[Tlbexp.exe (Eksporter biblioteki typów)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md) wywołania `LoadTypeLibWithResolver` funkcji w procesie konwersji zestawu do typu biblioteki.</span><span class="sxs-lookup"><span data-stu-id="8e896-127">The [Tlbexp.exe (Type Library Exporter)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md) calls the `LoadTypeLibWithResolver` function during the assembly-to-type-library conversion process.</span></span>  
  
 <span data-ttu-id="8e896-128">Ta funkcja ładuje określonej biblioteki typu przy użyciu minimalnego dostępu do rejestru.</span><span class="sxs-lookup"><span data-stu-id="8e896-128">This function loads the specified type library with minimal access to the registry.</span></span> <span data-ttu-id="8e896-129">Funkcja następnie sprawdza, czy biblioteki typów dla wewnętrznie odwołania biblioteki typów, z których każdy musi być załadowane i dodawane do biblioteki typu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="8e896-129">The function then examines the type library for internally referenced type libraries, each of which must be loaded and added to the parent type library.</span></span>  
  
 <span data-ttu-id="8e896-130">Przed załadowaniem przywoływanej biblioteki typów, ścieżki pliku odwołania muszą zostać rozwiązane do pełnej ścieżki pliku.</span><span class="sxs-lookup"><span data-stu-id="8e896-130">Before a referenced type library can be loaded, its reference file path must be resolved to a full file path.</span></span> <span data-ttu-id="8e896-131">Jest to realizowane za pośrednictwem [resolvetypelib — metoda](../../../../docs/framework/unmanaged-api/tlbexp/resolvetypelib-method.md) dostarczanym przez [itypelibresolver — interfejs](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md), która jest przekazywana w `pTlbResolver` parametru.</span><span class="sxs-lookup"><span data-stu-id="8e896-131">This is accomplished through the [ResolveTypeLib method](../../../../docs/framework/unmanaged-api/tlbexp/resolvetypelib-method.md) that is provided by the [ITypeLibResolver interface](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md), which is passed in the `pTlbResolver` parameter.</span></span>  
  
 <span data-ttu-id="8e896-132">Gdy znana jest pełną ścieżką do pliku biblioteki typów w przywoływanych, `LoadTypeLibWithResolver` funkcji ładuje i dodaje przywoływanej biblioteki typów do biblioteki typów nadrzędnego, tworzenie biblioteki typów wzorca połączone.</span><span class="sxs-lookup"><span data-stu-id="8e896-132">When the full file path of the referenced type library is known, the `LoadTypeLibWithResolver` function loads and adds the referenced type library to the parent type library, creating a combined master type library.</span></span>  
  
 <span data-ttu-id="8e896-133">Po funkcji rozpoznaje i ładuje wszystkie biblioteki wewnętrznie odwołanie typu, zwraca odwołanie do biblioteki wzorca rozpoznany typ w `pptlib` parametru.</span><span class="sxs-lookup"><span data-stu-id="8e896-133">After the function resolves and loads all internally referenced type libraries, it returns a reference to the master resolved type library in the `pptlib` parameter.</span></span>  
  
 <span data-ttu-id="8e896-134">`LoadTypeLibWithResolver` Funkcja jest zazwyczaj wywoływana przez [Tlbexp.exe (Eksporter biblioteki typów)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md), który dostarcza własnego wewnętrznego [itypelibresolver — interfejs](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) implementacji `pTlbResolver` parametr.</span><span class="sxs-lookup"><span data-stu-id="8e896-134">The `LoadTypeLibWithResolver` function is generally called by the [Tlbexp.exe (Type Library Exporter)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md), which supplies its own internal [ITypeLibResolver interface](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) implementation in the `pTlbResolver` parameter.</span></span>  
  
 <span data-ttu-id="8e896-135">Jeśli wywołasz `LoadTypeLibWithResolver` bezpośrednio, należy podać własne [itypelibresolver — interfejs](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) implementacji.</span><span class="sxs-lookup"><span data-stu-id="8e896-135">If you call `LoadTypeLibWithResolver` directly, you must supply your own [ITypeLibResolver interface](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) implementation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8e896-136">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8e896-136">Requirements</span></span>  
 <span data-ttu-id="8e896-137">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8e896-137">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8e896-138">**Nagłówek:** TlbRef.h</span><span class="sxs-lookup"><span data-stu-id="8e896-138">**Header:** TlbRef.h</span></span>  
  
 <span data-ttu-id="8e896-139">**Biblioteka:** TlbRef.lib</span><span class="sxs-lookup"><span data-stu-id="8e896-139">**Library:** TlbRef.lib</span></span>  
  
 <span data-ttu-id="8e896-140">**Wersja programu .NET framework:** 3.5, 3.0, 2.0</span><span class="sxs-lookup"><span data-stu-id="8e896-140">**.NET Framework Version:** 3.5, 3.0, 2.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e896-141">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8e896-141">See also</span></span>

- [<span data-ttu-id="8e896-142">Tlbexp, funkcje pomocy</span><span class="sxs-lookup"><span data-stu-id="8e896-142">Tlbexp Helper Functions</span></span>](../../../../docs/framework/unmanaged-api/tlbexp/index.md)
- [<span data-ttu-id="8e896-143">LoadTypeLibEx — funkcja</span><span class="sxs-lookup"><span data-stu-id="8e896-143">LoadTypeLibEx Function</span></span>](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-loadtypelibex)
