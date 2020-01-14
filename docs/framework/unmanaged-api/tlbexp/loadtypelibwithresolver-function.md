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
ms.openlocfilehash: adbb5eca3b7ffa36d0c963d0dacc3b2afdb664d4
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/14/2020
ms.locfileid: "75935563"
---
# <a name="loadtypelibwithresolver-function"></a><span data-ttu-id="bd7e9-102">LoadTypeLibWithResolver — Funkcja</span><span class="sxs-lookup"><span data-stu-id="bd7e9-102">LoadTypeLibWithResolver Function</span></span>
<span data-ttu-id="bd7e9-103">Ładuje bibliotekę typów i używa dostarczonego [interfejsu ITypeLibResolver](itypelibresolver-interface.md) do rozpoznawania wszelkich wewnętrznie przywoływanych bibliotek typów.</span><span class="sxs-lookup"><span data-stu-id="bd7e9-103">Loads a type library and uses the supplied [ITypeLibResolver interface](itypelibresolver-interface.md) to resolve any internally referenced type libraries.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd7e9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="bd7e9-104">Syntax</span></span>  
  
```cpp  
HRESULT LoadTypeLibWithResolver(  
    [in]  LPCOLESTR           szFile,  
    [in]  REGKIND             regkind,  
    [in]  ITypeLibResolver   *pTlbResolver,  
    [out] ITypeLib          **pptlib);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bd7e9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bd7e9-105">Parameters</span></span>  
 `szFile`  
 <span data-ttu-id="bd7e9-106">podczas Ścieżka pliku biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="bd7e9-106">[in] The file path of the type library.</span></span>  
  
 `regkind`  
 <span data-ttu-id="bd7e9-107">podczas Flaga [wyliczenia REGKIND](/windows/win32/api/oleauto/ne-oleauto-regkind) , która kontroluje sposób rejestrowania biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="bd7e9-107">[in] A [REGKIND enumeration](/windows/win32/api/oleauto/ne-oleauto-regkind) flag that controls how the type library is registered.</span></span> <span data-ttu-id="bd7e9-108">Możliwe wartości to:</span><span class="sxs-lookup"><span data-stu-id="bd7e9-108">Its possible values are:</span></span>  
  
- <span data-ttu-id="bd7e9-109">`REGKIND_DEFAULT`: Użyj domyślnego zachowania rejestrowania.</span><span class="sxs-lookup"><span data-stu-id="bd7e9-109">`REGKIND_DEFAULT`: Use default registration behavior.</span></span>  
  
- <span data-ttu-id="bd7e9-110">`REGKIND_REGISTER`: Zarejestruj tę bibliotekę typów.</span><span class="sxs-lookup"><span data-stu-id="bd7e9-110">`REGKIND_REGISTER`: Register this type library.</span></span>  
  
- <span data-ttu-id="bd7e9-111">`REGKIND_NONE`: nie Rejestruj tej biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="bd7e9-111">`REGKIND_NONE`: Do not register this type library.</span></span>  
  
 `pTlbResolver`  
 <span data-ttu-id="bd7e9-112">podczas Wskaźnik do implementacji [interfejsu ITypeLibResolver](itypelibresolver-interface.md).</span><span class="sxs-lookup"><span data-stu-id="bd7e9-112">[in] A pointer to the implementation of the [ITypeLibResolver interface](itypelibresolver-interface.md).</span></span>  
  
 `pptlib`  
 <span data-ttu-id="bd7e9-113">określoną Odwołanie do biblioteki typów, która jest ładowana.</span><span class="sxs-lookup"><span data-stu-id="bd7e9-113">[out] A reference to the type library that is being loaded.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bd7e9-114">Wartość zwrócona</span><span class="sxs-lookup"><span data-stu-id="bd7e9-114">Return Value</span></span>  
 <span data-ttu-id="bd7e9-115">Jedna z wartości HRESULT wymienionych w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="bd7e9-115">One of the HRESULT values listed in the following table.</span></span>  
  
|<span data-ttu-id="bd7e9-116">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="bd7e9-116">Return value</span></span>|<span data-ttu-id="bd7e9-117">Znaczenie</span><span class="sxs-lookup"><span data-stu-id="bd7e9-117">Meaning</span></span>|  
|------------------|-------------|  
|`S_OK`|<span data-ttu-id="bd7e9-118">Powodzenie.</span><span class="sxs-lookup"><span data-stu-id="bd7e9-118">Success.</span></span>|  
|`E_OUTOFMEMORY`|<span data-ttu-id="bd7e9-119">Za mało pamięci.</span><span class="sxs-lookup"><span data-stu-id="bd7e9-119">Out of memory.</span></span>|  
|`E_POINTER`|<span data-ttu-id="bd7e9-120">Co najmniej jeden wskaźnik jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="bd7e9-120">One or more of the pointers are invalid.</span></span>|  
|`E_INVALIDARG`|<span data-ttu-id="bd7e9-121">Co najmniej jeden z argumentów jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="bd7e9-121">One or more of the arguments are invalid.</span></span>|  
|`TYPE_E_IOERROR`|<span data-ttu-id="bd7e9-122">Funkcja nie może wykonać zapisu w pliku.</span><span class="sxs-lookup"><span data-stu-id="bd7e9-122">The function could not write to the file.</span></span>|  
|`TYPE_E_REGISTRYACCESS`|<span data-ttu-id="bd7e9-123">Nie można otworzyć bazy danych rejestracji systemu.</span><span class="sxs-lookup"><span data-stu-id="bd7e9-123">The system registration database could not be opened.</span></span>|  
|`TYPE_E_INVALIDSTATE`|<span data-ttu-id="bd7e9-124">Nie można otworzyć biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="bd7e9-124">The type library could not be opened.</span></span>|  
|`TYPE_E_CANTLOADLIBRARY`|<span data-ttu-id="bd7e9-125">Nie można załadować biblioteki typów lub biblioteki DLL.</span><span class="sxs-lookup"><span data-stu-id="bd7e9-125">The type library or DLL could not be loaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bd7e9-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bd7e9-126">Remarks</span></span>  
 <span data-ttu-id="bd7e9-127">[Tlbexp. exe (Eksporter biblioteki typów)](../../tools/tlbexp-exe-type-library-exporter.md) wywołuje funkcję `LoadTypeLibWithResolver` w procesie konwersji zestawu na typ biblioteki.</span><span class="sxs-lookup"><span data-stu-id="bd7e9-127">The [Tlbexp.exe (Type Library Exporter)](../../tools/tlbexp-exe-type-library-exporter.md) calls the `LoadTypeLibWithResolver` function during the assembly-to-type-library conversion process.</span></span>  
  
 <span data-ttu-id="bd7e9-128">Ta funkcja ładuje określoną bibliotekę typów o minimalnym dostępie do rejestru.</span><span class="sxs-lookup"><span data-stu-id="bd7e9-128">This function loads the specified type library with minimal access to the registry.</span></span> <span data-ttu-id="bd7e9-129">Funkcja następnie analizuje bibliotekę typów dla wewnętrznie przywoływanych bibliotek typów, z których każdy musi być załadowany i dodany do biblioteki typów nadrzędnych.</span><span class="sxs-lookup"><span data-stu-id="bd7e9-129">The function then examines the type library for internally referenced type libraries, each of which must be loaded and added to the parent type library.</span></span>  
  
 <span data-ttu-id="bd7e9-130">Przed załadowaniem przywoływanej biblioteki typów, jej ścieżka do pliku odniesienia musi zostać rozpoznana jako pełna ścieżka pliku.</span><span class="sxs-lookup"><span data-stu-id="bd7e9-130">Before a referenced type library can be loaded, its reference file path must be resolved to a full file path.</span></span> <span data-ttu-id="bd7e9-131">Jest to realizowane za pomocą [metody ResolveTypeLib —](resolvetypelib-method.md) dostarczonej przez [interfejs ITypeLibResolver](itypelibresolver-interface.md), który jest przekazywany w parametrze `pTlbResolver`.</span><span class="sxs-lookup"><span data-stu-id="bd7e9-131">This is accomplished through the [ResolveTypeLib method](resolvetypelib-method.md) that is provided by the [ITypeLibResolver interface](itypelibresolver-interface.md), which is passed in the `pTlbResolver` parameter.</span></span>  
  
 <span data-ttu-id="bd7e9-132">Gdy znana jest pełna ścieżka do pliku z przywoływaną biblioteką typów, funkcja `LoadTypeLibWithResolver` ładuje i dodaje przywoływaną bibliotekę typów do biblioteki typów nadrzędnych, tworząc połączoną bibliotekę typów głównych.</span><span class="sxs-lookup"><span data-stu-id="bd7e9-132">When the full file path of the referenced type library is known, the `LoadTypeLibWithResolver` function loads and adds the referenced type library to the parent type library, creating a combined master type library.</span></span>  
  
 <span data-ttu-id="bd7e9-133">Po rozpoznaniu i załadowaniu wszystkich wewnętrznie przywoływanych bibliotek typów funkcja zwraca odwołanie do głównej, rozwiązanej biblioteki typów w parametrze `pptlib`.</span><span class="sxs-lookup"><span data-stu-id="bd7e9-133">After the function resolves and loads all internally referenced type libraries, it returns a reference to the master resolved type library in the `pptlib` parameter.</span></span>  
  
 <span data-ttu-id="bd7e9-134">Funkcja `LoadTypeLibWithResolver` jest zazwyczaj wywoływana przez [Tlbexp. exe (Eksporter biblioteki typów)](../../tools/tlbexp-exe-type-library-exporter.md), która dostarcza własną wewnętrzną implementację [interfejsu ITypeLibResolver](itypelibresolver-interface.md) w parametrze `pTlbResolver`.</span><span class="sxs-lookup"><span data-stu-id="bd7e9-134">The `LoadTypeLibWithResolver` function is generally called by the [Tlbexp.exe (Type Library Exporter)](../../tools/tlbexp-exe-type-library-exporter.md), which supplies its own internal [ITypeLibResolver interface](itypelibresolver-interface.md) implementation in the `pTlbResolver` parameter.</span></span>  
  
 <span data-ttu-id="bd7e9-135">W przypadku wywołania `LoadTypeLibWithResolver` bezpośrednio należy podać własną implementację [interfejsu ITypeLibResolver](itypelibresolver-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="bd7e9-135">If you call `LoadTypeLibWithResolver` directly, you must supply your own [ITypeLibResolver interface](itypelibresolver-interface.md) implementation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bd7e9-136">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bd7e9-136">Requirements</span></span>  
 <span data-ttu-id="bd7e9-137">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bd7e9-137">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bd7e9-138">**Nagłówek:** TlbRef. h</span><span class="sxs-lookup"><span data-stu-id="bd7e9-138">**Header:** TlbRef.h</span></span>  
  
 <span data-ttu-id="bd7e9-139">**Biblioteka:** TlbRef. lib</span><span class="sxs-lookup"><span data-stu-id="bd7e9-139">**Library:** TlbRef.lib</span></span>  
  
 <span data-ttu-id="bd7e9-140">**Wersja .NET Framework:** 3,5, 3,0, 2,0</span><span class="sxs-lookup"><span data-stu-id="bd7e9-140">**.NET Framework Version:** 3.5, 3.0, 2.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd7e9-141">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bd7e9-141">See also</span></span>

- [<span data-ttu-id="bd7e9-142">Tlbexp, funkcje pomocy</span><span class="sxs-lookup"><span data-stu-id="bd7e9-142">Tlbexp Helper Functions</span></span>](index.md)
- [<span data-ttu-id="bd7e9-143">LoadTypeLibEx, funkcja</span><span class="sxs-lookup"><span data-stu-id="bd7e9-143">LoadTypeLibEx Function</span></span>](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-loadtypelibex)
