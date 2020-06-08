---
title: IMetaDataInfo::GetFileMapping — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataInfo.GetFileMapping
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataInfo::GetFileMapping
helpviewer_keywords:
- IMetaDataInfo::GetFileMapping method [.NET Framework metadata]
- GetFileMapping method [.NET Framework metadata]
ms.assetid: 2868dfec-c992-4606-88bb-a8e0b6b18271
topic_type:
- apiref
ms.openlocfilehash: 5ef5d9ae3da4dff13a461162f0ba3466d3d8192c
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501264"
---
# <a name="imetadatainfogetfilemapping-method"></a><span data-ttu-id="5faf7-102">IMetaDataInfo::GetFileMapping — Metoda</span><span class="sxs-lookup"><span data-stu-id="5faf7-102">IMetaDataInfo::GetFileMapping Method</span></span>
<span data-ttu-id="5faf7-103">Pobiera region pamięci zamapowanego pliku i typ mapowania.</span><span class="sxs-lookup"><span data-stu-id="5faf7-103">Gets the memory region of the mapped file, and the type of mapping.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5faf7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5faf7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFileMapping (  
    [out] const void           **ppvData,
    [out] ULONGLONG            *pcbData,
    [out] DWORD                *pdwMappingType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5faf7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5faf7-105">Parameters</span></span>  
 `ppvData`  
 <span data-ttu-id="5faf7-106">określoną Wskaźnik do początku zamapowanego pliku.</span><span class="sxs-lookup"><span data-stu-id="5faf7-106">[out] A pointer to the start of the mapped file.</span></span>  
  
 `pcbData`  
 <span data-ttu-id="5faf7-107">określoną Rozmiar zamapowanego regionu.</span><span class="sxs-lookup"><span data-stu-id="5faf7-107">[out] The size of the mapped region.</span></span> <span data-ttu-id="5faf7-108">Jeśli `pdwMappingType` jest `fmFlat` , jest to rozmiar pliku.</span><span class="sxs-lookup"><span data-stu-id="5faf7-108">If `pdwMappingType` is `fmFlat`, this is the size of the file.</span></span>  
  
 `pdwMappingType`  
 <span data-ttu-id="5faf7-109">określoną Wartość [CorFileMapping —](corfilemapping-enumeration.md) , która wskazuje typ mapowania.</span><span class="sxs-lookup"><span data-stu-id="5faf7-109">[out] A [CorFileMapping](corfilemapping-enumeration.md) value that indicates the type of mapping.</span></span> <span data-ttu-id="5faf7-110">Bieżąca implementacja środowiska uruchomieniowego języka wspólnego (CLR) zawsze zwraca wartość `fmFlat` .</span><span class="sxs-lookup"><span data-stu-id="5faf7-110">The current implementation of the common language runtime (CLR) always returns `fmFlat`.</span></span> <span data-ttu-id="5faf7-111">Inne wartości są zarezerwowane do użytku w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="5faf7-111">Other values are reserved for future use.</span></span> <span data-ttu-id="5faf7-112">Należy jednak zawsze zweryfikować zwracaną wartość, ponieważ inne wartości mogą być włączone w przyszłych wersjach lub wersjach usługi.</span><span class="sxs-lookup"><span data-stu-id="5faf7-112">However, you should always verify the returned value, because other values may be enabled in future versions or service releases.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5faf7-113">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="5faf7-113">Return Value</span></span>  
  
|<span data-ttu-id="5faf7-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5faf7-114">HRESULT</span></span>|<span data-ttu-id="5faf7-115">Opis</span><span class="sxs-lookup"><span data-stu-id="5faf7-115">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="5faf7-116">Wszystkie dane wyjściowe są wypełnione.</span><span class="sxs-lookup"><span data-stu-id="5faf7-116">All outputs are filled.</span></span>|  
|`E_INVALIDARG`|<span data-ttu-id="5faf7-117">Jako wartość argumentu przekazano wartość NULL.</span><span class="sxs-lookup"><span data-stu-id="5faf7-117">NULL was passed as an argument value.</span></span>|  
|`COR_E_NOTSUPPORTED`|<span data-ttu-id="5faf7-118">Implementacja środowiska CLR nie może dostarczyć informacji o regionie pamięci.</span><span class="sxs-lookup"><span data-stu-id="5faf7-118">The CLR implementation cannot provide information about the memory region.</span></span> <span data-ttu-id="5faf7-119">Może się to zdarzyć z następujących powodów:</span><span class="sxs-lookup"><span data-stu-id="5faf7-119">This can happen for the following reasons:</span></span><br /><br /> <span data-ttu-id="5faf7-120">-Zakres metadanych został otwarty z `ofWrite` `ofCopyMemory` flagą or.</span><span class="sxs-lookup"><span data-stu-id="5faf7-120">-   The metadata scope was opened with the `ofWrite` or `ofCopyMemory` flag.</span></span><br /><span data-ttu-id="5faf7-121">-Zakres metadanych został otwarty bez `ofReadOnly` flagi.</span><span class="sxs-lookup"><span data-stu-id="5faf7-121">-   The metadata scope was opened without the `ofReadOnly` flag.</span></span><br /><span data-ttu-id="5faf7-122">-Metoda [IMetaDataDispenser:: OpenScopeOnMemory —](imetadatadispenser-openscopeonmemory-method.md) została użyta do otwarcia tylko części metadanych pliku.</span><span class="sxs-lookup"><span data-stu-id="5faf7-122">-   The [IMetaDataDispenser::OpenScopeOnMemory](imetadatadispenser-openscopeonmemory-method.md) method was used to open only the metadata portion of the file.</span></span><br /><span data-ttu-id="5faf7-123">-Plik nie jest przenośnym plikiem wykonywalnym (PE).</span><span class="sxs-lookup"><span data-stu-id="5faf7-123">-   The file is not a portable executable (PE) file.</span></span> <span data-ttu-id="5faf7-124">**Uwaga:**  Te warunki są zależne od implementacji środowiska CLR i mogą być osłabione w przyszłych wersjach środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="5faf7-124">**Note:**  These conditions depend on the CLR implementation, and are likely to be weakened in future versions of the CLR.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5faf7-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5faf7-125">Remarks</span></span>  
 <span data-ttu-id="5faf7-126">Pamięć, która `ppvData` wskazuje na, jest prawidłowa tylko tak długo, jak źródłowy zakres metadanych jest otwarty.</span><span class="sxs-lookup"><span data-stu-id="5faf7-126">The memory that `ppvData` points to is valid only as long as the underlying metadata scope is open.</span></span>  
  
 <span data-ttu-id="5faf7-127">Aby ta metoda działała, podczas mapowania metadanych pliku na dysk do pamięci przez wywołanie metody [IMetaDataDispenser:: OpenScope —](imetadatadispenser-openscope-method.md) należy określić `ofReadOnly` flagę i nie należy określać `ofWrite` `ofCopyMemory` flagi or.</span><span class="sxs-lookup"><span data-stu-id="5faf7-127">In order for this method to work, when you map the metadata of an on-disk file into memory by calling the [IMetaDataDispenser::OpenScope](imetadatadispenser-openscope-method.md) method, you must specify the `ofReadOnly` flag and you must not specify the `ofWrite` or `ofCopyMemory` flag.</span></span>  
  
 <span data-ttu-id="5faf7-128">Wybór typu mapowania plików dla każdego zakresu jest specyficzny dla danej implementacji środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="5faf7-128">The choice of file mapping type for each scope is specific to a given implementation of the CLR.</span></span> <span data-ttu-id="5faf7-129">Nie można go ustawić przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="5faf7-129">It cannot be set by the user.</span></span> <span data-ttu-id="5faf7-130">Bieżąca implementacja środowiska CLR zawsze zwraca wartość `fmFlat` w `pdwMappingType` , ale może to zmienić w przyszłych wersjach środowiska CLR lub w przyszłych wersjach usługi danej wersji.</span><span class="sxs-lookup"><span data-stu-id="5faf7-130">The current implementation of the CLR always returns `fmFlat` in `pdwMappingType`, but this can change in future versions of the CLR or in future service releases of a given version.</span></span> <span data-ttu-id="5faf7-131">Należy zawsze sprawdzać wartość zwracaną w `pdwMappingType` , ponieważ różne typy będą mieć różne układy i przesunięcia.</span><span class="sxs-lookup"><span data-stu-id="5faf7-131">You should always check the returned value in `pdwMappingType`, because different types will have different layouts and offsets.</span></span>  
  
 <span data-ttu-id="5faf7-132">Przekazywanie wartości NULL dla dowolnego z trzech parametrów nie jest obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="5faf7-132">Passing NULL for any of the three parameters is not supported.</span></span> <span data-ttu-id="5faf7-133">Metoda zwraca `E_INVALIDARG` , a żadne wyjście nie jest wypełnione.</span><span class="sxs-lookup"><span data-stu-id="5faf7-133">The method returns `E_INVALIDARG`, and none of the outputs are filled.</span></span> <span data-ttu-id="5faf7-134">Ignorowanie typu mapowania lub rozmiaru regionu może spowodować nietypowe zakończenie działania programu.</span><span class="sxs-lookup"><span data-stu-id="5faf7-134">Ignoring the mapping type or the size of the region can result in abnormal program termination.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5faf7-135">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5faf7-135">Requirements</span></span>  
 <span data-ttu-id="5faf7-136">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5faf7-136">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5faf7-137">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="5faf7-137">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5faf7-138">**Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="5faf7-138">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5faf7-139">**.NET Framework wersje:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5faf7-139">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5faf7-140">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5faf7-140">See also</span></span>

- [<span data-ttu-id="5faf7-141">IMetaDataInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="5faf7-141">IMetaDataInfo Interface</span></span>](imetadatainfo-interface.md)
- [<span data-ttu-id="5faf7-142">CorFileMapping, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="5faf7-142">CorFileMapping Enumeration</span></span>](corfilemapping-enumeration.md)
