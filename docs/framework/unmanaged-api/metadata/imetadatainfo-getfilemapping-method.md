---
title: "IMetaDataInfo::GetFileMapping — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataInfo.GetFileMapping
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataInfo::GetFileMapping
helpviewer_keywords:
- IMetaDataInfo::GetFileMapping method [.NET Framework metadata]
- GetFileMapping method [.NET Framework metadata]
ms.assetid: 2868dfec-c992-4606-88bb-a8e0b6b18271
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f974230dc5ddf2a663f05fc06850f49f1de6e773
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="imetadatainfogetfilemapping-method"></a><span data-ttu-id="7e395-102">IMetaDataInfo::GetFileMapping — Metoda</span><span class="sxs-lookup"><span data-stu-id="7e395-102">IMetaDataInfo::GetFileMapping Method</span></span>
<span data-ttu-id="7e395-103">Pobiera regionu pamięci zamapowanego pliku, a Typ mapowania.</span><span class="sxs-lookup"><span data-stu-id="7e395-103">Gets the memory region of the mapped file, and the type of mapping.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e395-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7e395-104">Syntax</span></span>  
  
```  
HRESULT GetFileMapping (  
    [out] const void           **ppvData,   
    [out] ULONGLONG            *pcbData,   
    [out] DWORD                *pdwMappingType  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7e395-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7e395-105">Parameters</span></span>  
 `ppvData`  
 <span data-ttu-id="7e395-106">[out] Wskaźnik do początku zamapowanego pliku.</span><span class="sxs-lookup"><span data-stu-id="7e395-106">[out] A pointer to the start of the mapped file.</span></span>  
  
 `pcbData`  
 <span data-ttu-id="7e395-107">[out] Rozmiar mapowanego regionu.</span><span class="sxs-lookup"><span data-stu-id="7e395-107">[out] The size of the mapped region.</span></span> <span data-ttu-id="7e395-108">Jeśli `pdwMappingType` jest `fmFlat`, rozmiar pliku.</span><span class="sxs-lookup"><span data-stu-id="7e395-108">If `pdwMappingType` is `fmFlat`, this is the size of the file.</span></span>  
  
 `pdwMappingType`  
 <span data-ttu-id="7e395-109">[out] A [CorFileMapping](../../../../docs/framework/unmanaged-api/metadata/corfilemapping-enumeration.md) wartość, która wskazuje typ mapowania.</span><span class="sxs-lookup"><span data-stu-id="7e395-109">[out] A [CorFileMapping](../../../../docs/framework/unmanaged-api/metadata/corfilemapping-enumeration.md) value that indicates the type of mapping.</span></span> <span data-ttu-id="7e395-110">Bieżąca implementacja środowisko uruchomieniowe języka wspólnego (CLR) zawsze zwraca `fmFlat`.</span><span class="sxs-lookup"><span data-stu-id="7e395-110">The current implementation of the common language runtime (CLR) always returns `fmFlat`.</span></span> <span data-ttu-id="7e395-111">Inne wartości są zarezerwowane do użytku w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="7e395-111">Other values are reserved for future use.</span></span> <span data-ttu-id="7e395-112">Jednak należy zawsze sprawdzić zwrócona wartość ponieważ inne wartości może być włączone w przyszłych wersjach lub wersje usługi.</span><span class="sxs-lookup"><span data-stu-id="7e395-112">However, you should always verify the returned value, because other values may be enabled in future versions or service releases.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7e395-113">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="7e395-113">Return Value</span></span>  
  
|<span data-ttu-id="7e395-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7e395-114">HRESULT</span></span>|<span data-ttu-id="7e395-115">Opis</span><span class="sxs-lookup"><span data-stu-id="7e395-115">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="7e395-116">Wszystkie dane wyjściowe są wypełnione.</span><span class="sxs-lookup"><span data-stu-id="7e395-116">All outputs are filled.</span></span>|  
|`E_INVALIDARG`|<span data-ttu-id="7e395-117">Wartości NULL został przekazany jako wartość argumentu.</span><span class="sxs-lookup"><span data-stu-id="7e395-117">NULL was passed as an argument value.</span></span>|  
|`COR_E_NOTSUPPORTED`|<span data-ttu-id="7e395-118">Implementacji środowiska CLR nie może dostarczyć informacji o regionie pamięci.</span><span class="sxs-lookup"><span data-stu-id="7e395-118">The CLR implementation cannot provide information about the memory region.</span></span> <span data-ttu-id="7e395-119">Może się to zdarzyć w następujących sytuacjach:</span><span class="sxs-lookup"><span data-stu-id="7e395-119">This can happen for the following reasons:</span></span><br /><br /> <span data-ttu-id="7e395-120">-Zakres metadanych została otwarta z `ofWrite` lub `ofCopyMemory` flagi.</span><span class="sxs-lookup"><span data-stu-id="7e395-120">-   The metadata scope was opened with the `ofWrite` or `ofCopyMemory` flag.</span></span><br /><span data-ttu-id="7e395-121">-Zakres metadanych został otwarty bez `ofReadOnly` flagi.</span><span class="sxs-lookup"><span data-stu-id="7e395-121">-   The metadata scope was opened without the `ofReadOnly` flag.</span></span><br /><span data-ttu-id="7e395-122">- [IMetaDataDispenser::OpenScopeOnMemory](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md) użyto metody można otworzyć tylko część metadane pliku.</span><span class="sxs-lookup"><span data-stu-id="7e395-122">-   The [IMetaDataDispenser::OpenScopeOnMemory](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md) method was used to open only the metadata portion of the file.</span></span><br /><span data-ttu-id="7e395-123">-Plik nie jest plikiem przenośny plik wykonywalny (PE).</span><span class="sxs-lookup"><span data-stu-id="7e395-123">-   The file is not a portable executable (PE) file.</span></span> <span data-ttu-id="7e395-124">**Uwaga:** te warunki są zależne od implementacji środowiska CLR i są prawdopodobnie obniżony w przyszłych wersjach środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="7e395-124">**Note:**  These conditions depend on the CLR implementation, and are likely to be weakened in future versions of the CLR.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7e395-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7e395-125">Remarks</span></span>  
 <span data-ttu-id="7e395-126">Pamięć który `ppvData` punktów jest prawidłowy tylko tak długo, jak podstawowej zakres metadanych jest otwarty.</span><span class="sxs-lookup"><span data-stu-id="7e395-126">The memory that `ppvData` points to is valid only as long as the underlying metadata scope is open.</span></span>  
  
 <span data-ttu-id="7e395-127">Aby tę metodę, aby pracować, podczas mapowania metadanych pliku na dysku w pamięci, wywołując [IMetaDataDispenser::OpenScope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md) metody, należy określić `ofReadOnly` flagi, a nie mogą określać `ofWrite` lub `ofCopyMemory` flagi.</span><span class="sxs-lookup"><span data-stu-id="7e395-127">In order for this method to work, when you map the metadata of an on-disk file into memory by calling the [IMetaDataDispenser::OpenScope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md) method, you must specify the `ofReadOnly` flag and you must not specify the `ofWrite` or `ofCopyMemory` flag.</span></span>  
  
 <span data-ttu-id="7e395-128">Wybór typu mapowania pliku dla każdego zakresu jest specyficzne dla danego wdrożenia środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="7e395-128">The choice of file mapping type for each scope is specific to a given implementation of the CLR.</span></span> <span data-ttu-id="7e395-129">Nie można ustawić przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="7e395-129">It cannot be set by the user.</span></span> <span data-ttu-id="7e395-130">Bieżąca implementacja CLR zawsze zwraca `fmFlat` w `pdwMappingType`, ale ten może ulec zmianie w przyszłych wersji środowiska CLR lub w przyszłych wersjach usługi danej wersji.</span><span class="sxs-lookup"><span data-stu-id="7e395-130">The current implementation of the CLR always returns `fmFlat` in `pdwMappingType`, but this can change in future versions of the CLR or in future service releases of a given version.</span></span> <span data-ttu-id="7e395-131">Zwrócone wartości należy zawsze sprawdzić `pdwMappingType`, ponieważ mają różne typy układów i przesunięcia.</span><span class="sxs-lookup"><span data-stu-id="7e395-131">You should always check the returned value in `pdwMappingType`, because different types will have different layouts and offsets.</span></span>  
  
 <span data-ttu-id="7e395-132">Przekazywanie wartości NULL dla każdego z trzech parametrów nie jest obsługiwana.</span><span class="sxs-lookup"><span data-stu-id="7e395-132">Passing NULL for any of the three parameters is not supported.</span></span> <span data-ttu-id="7e395-133">Metoda zwraca `E_INVALIDARG`, a żadne dane wyjściowe są wypełniane.</span><span class="sxs-lookup"><span data-stu-id="7e395-133">The method returns `E_INVALIDARG`, and none of the outputs are filled.</span></span> <span data-ttu-id="7e395-134">Ignorowanie Typ mapowania lub rozmiar regionu może spowodować zakończenie nietypowe programu.</span><span class="sxs-lookup"><span data-stu-id="7e395-134">Ignoring the mapping type or the size of the region can result in abnormal program termination.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7e395-135">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7e395-135">Requirements</span></span>  
 <span data-ttu-id="7e395-136">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7e395-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7e395-137">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="7e395-137">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7e395-138">**Biblioteka:** używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7e395-138">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7e395-139">**Wersje programu .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7e395-139">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e395-140">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7e395-140">See Also</span></span>  
 [<span data-ttu-id="7e395-141">IMetaDataInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="7e395-141">IMetaDataInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-interface.md)  
 [<span data-ttu-id="7e395-142">CorFileMapping, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="7e395-142">CorFileMapping Enumeration</span></span>](../../../../docs/framework/unmanaged-api/metadata/corfilemapping-enumeration.md)
