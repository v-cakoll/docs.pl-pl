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
ms.openlocfilehash: 0f5bdf97132c05e765cd6fa423a19bb996105d28
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175268"
---
# <a name="imetadatainfogetfilemapping-method"></a><span data-ttu-id="f6beb-102">IMetaDataInfo::GetFileMapping — Metoda</span><span class="sxs-lookup"><span data-stu-id="f6beb-102">IMetaDataInfo::GetFileMapping Method</span></span>
<span data-ttu-id="f6beb-103">Pobiera obszar pamięci zamapowany plik i typ mapowania.</span><span class="sxs-lookup"><span data-stu-id="f6beb-103">Gets the memory region of the mapped file, and the type of mapping.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6beb-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f6beb-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFileMapping (  
    [out] const void           **ppvData,
    [out] ULONGLONG            *pcbData,
    [out] DWORD                *pdwMappingType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f6beb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f6beb-105">Parameters</span></span>  
 `ppvData`  
 <span data-ttu-id="f6beb-106">[na zewnątrz] Wskaźnik do początku zamapowany plik.</span><span class="sxs-lookup"><span data-stu-id="f6beb-106">[out] A pointer to the start of the mapped file.</span></span>  
  
 `pcbData`  
 <span data-ttu-id="f6beb-107">[na zewnątrz] Rozmiar zamapowanych regionów.</span><span class="sxs-lookup"><span data-stu-id="f6beb-107">[out] The size of the mapped region.</span></span> <span data-ttu-id="f6beb-108">Jeśli `pdwMappingType` `fmFlat`tak , jest to rozmiar pliku.</span><span class="sxs-lookup"><span data-stu-id="f6beb-108">If `pdwMappingType` is `fmFlat`, this is the size of the file.</span></span>  
  
 `pdwMappingType`  
 <span data-ttu-id="f6beb-109">[na zewnątrz] Wartość [CorFileMapping,](../../../../docs/framework/unmanaged-api/metadata/corfilemapping-enumeration.md) która wskazuje typ mapowania.</span><span class="sxs-lookup"><span data-stu-id="f6beb-109">[out] A [CorFileMapping](../../../../docs/framework/unmanaged-api/metadata/corfilemapping-enumeration.md) value that indicates the type of mapping.</span></span> <span data-ttu-id="f6beb-110">Bieżąca implementacja środowiska wykonawczego języka wspólnego (CLR) zawsze zwraca `fmFlat`.</span><span class="sxs-lookup"><span data-stu-id="f6beb-110">The current implementation of the common language runtime (CLR) always returns `fmFlat`.</span></span> <span data-ttu-id="f6beb-111">Inne wartości są zarezerwowane do wykorzystania w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="f6beb-111">Other values are reserved for future use.</span></span> <span data-ttu-id="f6beb-112">Jednak zawsze należy sprawdzić zwracaną wartość, ponieważ inne wartości mogą być włączone w przyszłych wersjach lub wersjach usługi.</span><span class="sxs-lookup"><span data-stu-id="f6beb-112">However, you should always verify the returned value, because other values may be enabled in future versions or service releases.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f6beb-113">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="f6beb-113">Return Value</span></span>  
  
|<span data-ttu-id="f6beb-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f6beb-114">HRESULT</span></span>|<span data-ttu-id="f6beb-115">Opis</span><span class="sxs-lookup"><span data-stu-id="f6beb-115">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="f6beb-116">Wszystkie wyjścia są wypełnione.</span><span class="sxs-lookup"><span data-stu-id="f6beb-116">All outputs are filled.</span></span>|  
|`E_INVALIDARG`|<span data-ttu-id="f6beb-117">Wartość NULL została przekazana jako wartość argumentu.</span><span class="sxs-lookup"><span data-stu-id="f6beb-117">NULL was passed as an argument value.</span></span>|  
|`COR_E_NOTSUPPORTED`|<span data-ttu-id="f6beb-118">Implementacja CLR nie może dostarczyć informacji o regionie pamięci.</span><span class="sxs-lookup"><span data-stu-id="f6beb-118">The CLR implementation cannot provide information about the memory region.</span></span> <span data-ttu-id="f6beb-119">Może się to zdarzyć z następujących powodów:</span><span class="sxs-lookup"><span data-stu-id="f6beb-119">This can happen for the following reasons:</span></span><br /><br /> <span data-ttu-id="f6beb-120">- Zakres metadanych został `ofWrite` `ofCopyMemory` otwarty z lub flagi.</span><span class="sxs-lookup"><span data-stu-id="f6beb-120">-   The metadata scope was opened with the `ofWrite` or `ofCopyMemory` flag.</span></span><br /><span data-ttu-id="f6beb-121">- Zakres metadanych został `ofReadOnly` otwarty bez flagi.</span><span class="sxs-lookup"><span data-stu-id="f6beb-121">-   The metadata scope was opened without the `ofReadOnly` flag.</span></span><br /><span data-ttu-id="f6beb-122">- Metoda [IMetaDataDispenser::OpenScopeOnMemory](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md) została użyta do otwarcia tylko części metadanych pliku.</span><span class="sxs-lookup"><span data-stu-id="f6beb-122">-   The [IMetaDataDispenser::OpenScopeOnMemory](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md) method was used to open only the metadata portion of the file.</span></span><br /><span data-ttu-id="f6beb-123">- Plik nie jest przenośnym plikiem wykonywalnym (PE).</span><span class="sxs-lookup"><span data-stu-id="f6beb-123">-   The file is not a portable executable (PE) file.</span></span> <span data-ttu-id="f6beb-124">**Uwaga:**  Warunki te zależą od implementacji CLR i mogą być osłabione w przyszłych wersjach CLR.</span><span class="sxs-lookup"><span data-stu-id="f6beb-124">**Note:**  These conditions depend on the CLR implementation, and are likely to be weakened in future versions of the CLR.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f6beb-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f6beb-125">Remarks</span></span>  
 <span data-ttu-id="f6beb-126">Pamięć, `ppvData` która wskazuje jest prawidłowa tylko tak długo, jak zakres podstawowych metadanych jest otwarty.</span><span class="sxs-lookup"><span data-stu-id="f6beb-126">The memory that `ppvData` points to is valid only as long as the underlying metadata scope is open.</span></span>  
  
 <span data-ttu-id="f6beb-127">Aby ta metoda działała, podczas mapowania metadanych pliku na dysku do pamięci przez [wywołanie IMetaDataDispenser::OpenScope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md) metody, należy określić `ofReadOnly` flagę i nie należy określić `ofWrite` lub `ofCopyMemory` flagi.</span><span class="sxs-lookup"><span data-stu-id="f6beb-127">In order for this method to work, when you map the metadata of an on-disk file into memory by calling the [IMetaDataDispenser::OpenScope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md) method, you must specify the `ofReadOnly` flag and you must not specify the `ofWrite` or `ofCopyMemory` flag.</span></span>  
  
 <span data-ttu-id="f6beb-128">Wybór typu mapowania plików dla każdego zakresu jest specyficzny dla danej implementacji CLR.</span><span class="sxs-lookup"><span data-stu-id="f6beb-128">The choice of file mapping type for each scope is specific to a given implementation of the CLR.</span></span> <span data-ttu-id="f6beb-129">Nie można go ustawić przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="f6beb-129">It cannot be set by the user.</span></span> <span data-ttu-id="f6beb-130">Bieżąca implementacja CLR `fmFlat` zawsze `pdwMappingType`zwraca w , ale może się to zmienić w przyszłych wersjach CLR lub w przyszłych wersjach usługi danej wersji.</span><span class="sxs-lookup"><span data-stu-id="f6beb-130">The current implementation of the CLR always returns `fmFlat` in `pdwMappingType`, but this can change in future versions of the CLR or in future service releases of a given version.</span></span> <span data-ttu-id="f6beb-131">Zawsze należy sprawdzić zwróconą `pdwMappingType`wartość w , ponieważ różne typy będą miały różne układy i przesunięcia.</span><span class="sxs-lookup"><span data-stu-id="f6beb-131">You should always check the returned value in `pdwMappingType`, because different types will have different layouts and offsets.</span></span>  
  
 <span data-ttu-id="f6beb-132">Przekazywanie null dla dowolnego z trzech parametrów nie jest obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="f6beb-132">Passing NULL for any of the three parameters is not supported.</span></span> <span data-ttu-id="f6beb-133">Metoda zwraca `E_INVALIDARG`, a żadne z wyjść nie są wypełnione.</span><span class="sxs-lookup"><span data-stu-id="f6beb-133">The method returns `E_INVALIDARG`, and none of the outputs are filled.</span></span> <span data-ttu-id="f6beb-134">Ignorowanie typu mapowania lub rozmiaru regionu może spowodować nieprawidłowe zakończenie programu.</span><span class="sxs-lookup"><span data-stu-id="f6beb-134">Ignoring the mapping type or the size of the region can result in abnormal program termination.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f6beb-135">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f6beb-135">Requirements</span></span>  
 <span data-ttu-id="f6beb-136">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f6beb-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f6beb-137">**Nagłówek:** Okręg wyborczy Cor.h</span><span class="sxs-lookup"><span data-stu-id="f6beb-137">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f6beb-138">**Biblioteka:** Używany jako zasób w pliku MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f6beb-138">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f6beb-139">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f6beb-139">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6beb-140">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f6beb-140">See also</span></span>

- [<span data-ttu-id="f6beb-141">IMetaDataInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="f6beb-141">IMetaDataInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-interface.md)
- [<span data-ttu-id="f6beb-142">CorFileMapping, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="f6beb-142">CorFileMapping Enumeration</span></span>](../../../../docs/framework/unmanaged-api/metadata/corfilemapping-enumeration.md)
