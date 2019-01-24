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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 84d53bd5bb9c0eca83b39fc9d1c83d93440e336b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54645473"
---
# <a name="imetadatainfogetfilemapping-method"></a><span data-ttu-id="40966-102">IMetaDataInfo::GetFileMapping — Metoda</span><span class="sxs-lookup"><span data-stu-id="40966-102">IMetaDataInfo::GetFileMapping Method</span></span>
<span data-ttu-id="40966-103">Pobiera region pamięci zamapowanego pliku, a Typ mapowania.</span><span class="sxs-lookup"><span data-stu-id="40966-103">Gets the memory region of the mapped file, and the type of mapping.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40966-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="40966-104">Syntax</span></span>  
  
```  
HRESULT GetFileMapping (  
    [out] const void           **ppvData,   
    [out] ULONGLONG            *pcbData,   
    [out] DWORD                *pdwMappingType  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="40966-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="40966-105">Parameters</span></span>  
 `ppvData`  
 <span data-ttu-id="40966-106">[out] Wskaźnik do początku zamapowanego pliku.</span><span class="sxs-lookup"><span data-stu-id="40966-106">[out] A pointer to the start of the mapped file.</span></span>  
  
 `pcbData`  
 <span data-ttu-id="40966-107">[out] Rozmiar mapowanego obszaru.</span><span class="sxs-lookup"><span data-stu-id="40966-107">[out] The size of the mapped region.</span></span> <span data-ttu-id="40966-108">Jeśli `pdwMappingType` jest `fmFlat`, jest to rozmiar pliku.</span><span class="sxs-lookup"><span data-stu-id="40966-108">If `pdwMappingType` is `fmFlat`, this is the size of the file.</span></span>  
  
 `pdwMappingType`  
 <span data-ttu-id="40966-109">[out] A [corfilemapping —](../../../../docs/framework/unmanaged-api/metadata/corfilemapping-enumeration.md) wartość, która wskazuje typ mapowania.</span><span class="sxs-lookup"><span data-stu-id="40966-109">[out] A [CorFileMapping](../../../../docs/framework/unmanaged-api/metadata/corfilemapping-enumeration.md) value that indicates the type of mapping.</span></span> <span data-ttu-id="40966-110">Bieżąca implementacja środowisko uruchomieniowe języka wspólnego (CLR) zawsze zwraca `fmFlat`.</span><span class="sxs-lookup"><span data-stu-id="40966-110">The current implementation of the common language runtime (CLR) always returns `fmFlat`.</span></span> <span data-ttu-id="40966-111">Inne wartości są zarezerwowane do użytku w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="40966-111">Other values are reserved for future use.</span></span> <span data-ttu-id="40966-112">Jednak musisz zawsze sprawdzić, zwrócona wartość, ponieważ inne wartości może być włączone w przyszłych wersjach lub usług wydań.</span><span class="sxs-lookup"><span data-stu-id="40966-112">However, you should always verify the returned value, because other values may be enabled in future versions or service releases.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="40966-113">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="40966-113">Return Value</span></span>  
  
|<span data-ttu-id="40966-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="40966-114">HRESULT</span></span>|<span data-ttu-id="40966-115">Opis</span><span class="sxs-lookup"><span data-stu-id="40966-115">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="40966-116">Wszystkie dane wyjściowe są wypełnione.</span><span class="sxs-lookup"><span data-stu-id="40966-116">All outputs are filled.</span></span>|  
|`E_INVALIDARG`|<span data-ttu-id="40966-117">Wartość NULL została przekazana jako wartość argumentu.</span><span class="sxs-lookup"><span data-stu-id="40966-117">NULL was passed as an argument value.</span></span>|  
|`COR_E_NOTSUPPORTED`|<span data-ttu-id="40966-118">Implementacji środowiska CLR nie może dostarczyć informacji na temat regionu pamięci.</span><span class="sxs-lookup"><span data-stu-id="40966-118">The CLR implementation cannot provide information about the memory region.</span></span> <span data-ttu-id="40966-119">Może się to zdarzyć z następujących powodów:</span><span class="sxs-lookup"><span data-stu-id="40966-119">This can happen for the following reasons:</span></span><br /><br /> <span data-ttu-id="40966-120">Zakres metadanych zostało otwarte z `ofWrite` lub `ofCopyMemory` flagi.</span><span class="sxs-lookup"><span data-stu-id="40966-120">-   The metadata scope was opened with the `ofWrite` or `ofCopyMemory` flag.</span></span><br /><span data-ttu-id="40966-121">Zakres metadanych został otwarty bez `ofReadOnly` flagi.</span><span class="sxs-lookup"><span data-stu-id="40966-121">-   The metadata scope was opened without the `ofReadOnly` flag.</span></span><br /><span data-ttu-id="40966-122">[IMetaDataDispenser::OpenScopeOnMemory](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md) metoda użyty do otwarcia tylko część metadanych pliku.</span><span class="sxs-lookup"><span data-stu-id="40966-122">-   The [IMetaDataDispenser::OpenScopeOnMemory](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md) method was used to open only the metadata portion of the file.</span></span><br /><span data-ttu-id="40966-123">-Plik nie jest plikiem przenośny plik wykonywalny (PE).</span><span class="sxs-lookup"><span data-stu-id="40966-123">-   The file is not a portable executable (PE) file.</span></span> <span data-ttu-id="40966-124">**Uwaga:**  Te warunki są zależne od implementacji środowiska CLR i prawdopodobnie należy obniżyć poziom w przyszłych wersjach środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="40966-124">**Note:**  These conditions depend on the CLR implementation, and are likely to be weakened in future versions of the CLR.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="40966-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="40966-125">Remarks</span></span>  
 <span data-ttu-id="40966-126">Pamięć, `ppvData` wskazuje jest prawidłowy tylko tak długo, jak podstawowy zakres metadanych jest otwarty.</span><span class="sxs-lookup"><span data-stu-id="40966-126">The memory that `ppvData` points to is valid only as long as the underlying metadata scope is open.</span></span>  
  
 <span data-ttu-id="40966-127">W kolejności dla tej metody do pracy, kiedy mapujesz metadanych pliku na dysku do pamięci poprzez wywołanie [IMetaDataDispenser::OpenScope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md) metody, należy określić `ofReadOnly` flagę i nie mogą określać `ofWrite` lub `ofCopyMemory` flagi.</span><span class="sxs-lookup"><span data-stu-id="40966-127">In order for this method to work, when you map the metadata of an on-disk file into memory by calling the [IMetaDataDispenser::OpenScope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md) method, you must specify the `ofReadOnly` flag and you must not specify the `ofWrite` or `ofCopyMemory` flag.</span></span>  
  
 <span data-ttu-id="40966-128">Wybór typu mapowanie pliku dla każdego zakresu jest specyficzne dla danego wdrożenia środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="40966-128">The choice of file mapping type for each scope is specific to a given implementation of the CLR.</span></span> <span data-ttu-id="40966-129">Nie można ustawić przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="40966-129">It cannot be set by the user.</span></span> <span data-ttu-id="40966-130">Bieżąca implementacja CLR zawsze zwraca `fmFlat` w `pdwMappingType`, ale mogą one zmienić w przyszłych wersji środowiska CLR, lub w przyszłych wydaniach usługa danej wersji.</span><span class="sxs-lookup"><span data-stu-id="40966-130">The current implementation of the CLR always returns `fmFlat` in `pdwMappingType`, but this can change in future versions of the CLR or in future service releases of a given version.</span></span> <span data-ttu-id="40966-131">Należy zawsze sprawdzić zwracanej wartości `pdwMappingType`, ponieważ różne typy mają różne układy i przesunięcia.</span><span class="sxs-lookup"><span data-stu-id="40966-131">You should always check the returned value in `pdwMappingType`, because different types will have different layouts and offsets.</span></span>  
  
 <span data-ttu-id="40966-132">Przekazanie wartości NULL dla każdego z trzech parametrów nie jest obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="40966-132">Passing NULL for any of the three parameters is not supported.</span></span> <span data-ttu-id="40966-133">Metoda ta zwraca `E_INVALIDARG`, a żadne dane wyjściowe są wypełniane.</span><span class="sxs-lookup"><span data-stu-id="40966-133">The method returns `E_INVALIDARG`, and none of the outputs are filled.</span></span> <span data-ttu-id="40966-134">Ignorowanie typu mapowania lub rozmiar obszaru może spowodować Nienormalne zakończenie programu.</span><span class="sxs-lookup"><span data-stu-id="40966-134">Ignoring the mapping type or the size of the region can result in abnormal program termination.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="40966-135">Wymagania</span><span class="sxs-lookup"><span data-stu-id="40966-135">Requirements</span></span>  
 <span data-ttu-id="40966-136">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="40966-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="40966-137">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="40966-137">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="40966-138">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="40966-138">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="40966-139">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="40966-139">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40966-140">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="40966-140">See also</span></span>
- [<span data-ttu-id="40966-141">IMetaDataInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="40966-141">IMetaDataInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-interface.md)
- [<span data-ttu-id="40966-142">CorFileMapping, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="40966-142">CorFileMapping Enumeration</span></span>](../../../../docs/framework/unmanaged-api/metadata/corfilemapping-enumeration.md)
