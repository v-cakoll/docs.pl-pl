---
title: IMetaDataTables::GetColumnInfo — Metoda
ms.date: 10/10/2019
api_name:
- IMetaDataTables.GetColumnInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetColumnInfo
helpviewer_keywords:
- IMetaDataTables::GetColumnInfo method [.NET Framework metadata]
- GetColumnInfo method [.NET Framework metadata]
ms.assetid: 68c160ea-ae7d-4750-985d-a038b2c8e7d9
topic_type:
- apiref
ms.openlocfilehash: 854d3ad28cc00c03e903b9e1d2ce3863e3ceef17
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436096"
---
# <a name="imetadatatablesgetcolumninfo-method"></a><span data-ttu-id="71b03-102">IMetaDataTables::GetColumnInfo — Metoda</span><span class="sxs-lookup"><span data-stu-id="71b03-102">IMetaDataTables::GetColumnInfo Method</span></span>
<span data-ttu-id="71b03-103">Pobiera dane dotyczące określonej kolumny w określonej tabeli.</span><span class="sxs-lookup"><span data-stu-id="71b03-103">Gets data about the specified column in the specified table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71b03-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="71b03-104">Syntax</span></span>  
  
```cpp  
HRESULT GetColumnInfo (   
    [in]  ULONG        ixTbl,  
    [in]  ULONG        ixCol,  
    [out] ULONG        *poCol,  
    [out] ULONG        *pcbCol,  
    [out] ULONG        *pType,  
    [out] const char   **ppName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="71b03-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="71b03-105">Parameters</span></span>
=======

 `ixTbl`  
 <span data-ttu-id="71b03-106">podczas Indeks żądanej tabeli.</span><span class="sxs-lookup"><span data-stu-id="71b03-106">[in] The index of the desired table.</span></span>  
  
 `ixCol`  
 <span data-ttu-id="71b03-107">podczas Indeks żądanej kolumny.</span><span class="sxs-lookup"><span data-stu-id="71b03-107">[in] The index of the desired column.</span></span>  
  
 `poCol`  
 <span data-ttu-id="71b03-108">określoną Wskaźnik do przesunięcia kolumny w wierszu.</span><span class="sxs-lookup"><span data-stu-id="71b03-108">[out] A pointer to the offset of the column in the row.</span></span>  
  
 `pcbCol`  
 <span data-ttu-id="71b03-109">określoną Wskaźnik do rozmiaru, w bajtach, kolumny.</span><span class="sxs-lookup"><span data-stu-id="71b03-109">[out] A pointer to the size, in bytes, of the column.</span></span>  
  
 `pType`  
 <span data-ttu-id="71b03-110">określoną Wskaźnik do typu wartości w kolumnie.</span><span class="sxs-lookup"><span data-stu-id="71b03-110">[out] A pointer to the type of the values in the column.</span></span>  
  
 `ppName`  
 <span data-ttu-id="71b03-111">określoną Wskaźnik do wskaźnika do nazwy kolumny.</span><span class="sxs-lookup"><span data-stu-id="71b03-111">[out] A pointer to a pointer to the column name.</span></span>  
 
## <a name="remarks"></a><span data-ttu-id="71b03-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="71b03-112">Remarks</span></span>

<span data-ttu-id="71b03-113">Zwracany typ kolumny znajduje się w zakresie wartości:</span><span class="sxs-lookup"><span data-stu-id="71b03-113">The returned column type falls within a range of values:</span></span>

| <span data-ttu-id="71b03-114">pType</span><span class="sxs-lookup"><span data-stu-id="71b03-114">pType</span></span>                    | <span data-ttu-id="71b03-115">Opis</span><span class="sxs-lookup"><span data-stu-id="71b03-115">Description</span></span>   | <span data-ttu-id="71b03-116">Funkcja pomocnika</span><span class="sxs-lookup"><span data-stu-id="71b03-116">Helper function</span></span>                   |
|--------------------------|---------------|-----------------------------------|
| <span data-ttu-id="71b03-117">`0`..`iRidMax`</span><span class="sxs-lookup"><span data-stu-id="71b03-117">`0`..`iRidMax`</span></span><br><span data-ttu-id="71b03-118">(0.. 63)</span><span class="sxs-lookup"><span data-stu-id="71b03-118">(0..63)</span></span>   | <span data-ttu-id="71b03-119">Objęte</span><span class="sxs-lookup"><span data-stu-id="71b03-119">Rid</span></span>           | <span data-ttu-id="71b03-120">**IsRidType**</span><span class="sxs-lookup"><span data-stu-id="71b03-120">**IsRidType**</span></span><br><span data-ttu-id="71b03-121">**IsRidOrToken**</span><span class="sxs-lookup"><span data-stu-id="71b03-121">**IsRidOrToken**</span></span> |
| <span data-ttu-id="71b03-122">`iCodedToken`..`iCodedTokenMax`</span><span class="sxs-lookup"><span data-stu-id="71b03-122">`iCodedToken`..`iCodedTokenMax`</span></span><br><span data-ttu-id="71b03-123">(64.. 95)</span><span class="sxs-lookup"><span data-stu-id="71b03-123">(64..95)</span></span> | <span data-ttu-id="71b03-124">Zakodowany token</span><span class="sxs-lookup"><span data-stu-id="71b03-124">Coded token</span></span> | <span data-ttu-id="71b03-125">**IsCodedTokenType**</span><span class="sxs-lookup"><span data-stu-id="71b03-125">**IsCodedTokenType**</span></span> <br><span data-ttu-id="71b03-126">**IsRidOrToken**</span><span class="sxs-lookup"><span data-stu-id="71b03-126">**IsRidOrToken**</span></span> |
| <span data-ttu-id="71b03-127">`iSHORT` (96)</span><span class="sxs-lookup"><span data-stu-id="71b03-127">`iSHORT` (96)</span></span>            | <span data-ttu-id="71b03-128">Int16</span><span class="sxs-lookup"><span data-stu-id="71b03-128">Int16</span></span>         | <span data-ttu-id="71b03-129">**Isfixedtype**</span><span class="sxs-lookup"><span data-stu-id="71b03-129">**IsFixedType**</span></span>                   |
| <span data-ttu-id="71b03-130">`iUSHORT` (97)</span><span class="sxs-lookup"><span data-stu-id="71b03-130">`iUSHORT` (97)</span></span>           | <span data-ttu-id="71b03-131">UInt16</span><span class="sxs-lookup"><span data-stu-id="71b03-131">UInt16</span></span>        | <span data-ttu-id="71b03-132">**Isfixedtype**</span><span class="sxs-lookup"><span data-stu-id="71b03-132">**IsFixedType**</span></span>                   |
| <span data-ttu-id="71b03-133">`iLONG` (98)</span><span class="sxs-lookup"><span data-stu-id="71b03-133">`iLONG` (98)</span></span>             | <span data-ttu-id="71b03-134">Int32</span><span class="sxs-lookup"><span data-stu-id="71b03-134">Int32</span></span>         | <span data-ttu-id="71b03-135">**Isfixedtype**</span><span class="sxs-lookup"><span data-stu-id="71b03-135">**IsFixedType**</span></span>                   |
| <span data-ttu-id="71b03-136">`iULONG` (99)</span><span class="sxs-lookup"><span data-stu-id="71b03-136">`iULONG` (99)</span></span>            | <span data-ttu-id="71b03-137">UInt32</span><span class="sxs-lookup"><span data-stu-id="71b03-137">UInt32</span></span>        | <span data-ttu-id="71b03-138">**Isfixedtype**</span><span class="sxs-lookup"><span data-stu-id="71b03-138">**IsFixedType**</span></span>                   |
| <span data-ttu-id="71b03-139">`iBYTE` (100)</span><span class="sxs-lookup"><span data-stu-id="71b03-139">`iBYTE` (100)</span></span>            | <span data-ttu-id="71b03-140">Byte</span><span class="sxs-lookup"><span data-stu-id="71b03-140">Byte</span></span>          | <span data-ttu-id="71b03-141">**Isfixedtype**</span><span class="sxs-lookup"><span data-stu-id="71b03-141">**IsFixedType**</span></span>                   |
| <span data-ttu-id="71b03-142">`iSTRING` (101)</span><span class="sxs-lookup"><span data-stu-id="71b03-142">`iSTRING` (101)</span></span>          | <span data-ttu-id="71b03-143">String</span><span class="sxs-lookup"><span data-stu-id="71b03-143">String</span></span>        | <span data-ttu-id="71b03-144">**Issterta**</span><span class="sxs-lookup"><span data-stu-id="71b03-144">**IsHeapType**</span></span>                    |
| <span data-ttu-id="71b03-145">`iGUID` (102)</span><span class="sxs-lookup"><span data-stu-id="71b03-145">`iGUID` (102)</span></span>            | <span data-ttu-id="71b03-146">Identyfikator GUID</span><span class="sxs-lookup"><span data-stu-id="71b03-146">Guid</span></span>          | <span data-ttu-id="71b03-147">**Issterta**</span><span class="sxs-lookup"><span data-stu-id="71b03-147">**IsHeapType**</span></span>                    |
| <span data-ttu-id="71b03-148">`iBLOB` (103)</span><span class="sxs-lookup"><span data-stu-id="71b03-148">`iBLOB` (103)</span></span>            | <span data-ttu-id="71b03-149">Blob</span><span class="sxs-lookup"><span data-stu-id="71b03-149">Blob</span></span>          | <span data-ttu-id="71b03-150">**Issterta**</span><span class="sxs-lookup"><span data-stu-id="71b03-150">**IsHeapType**</span></span>                    |

<span data-ttu-id="71b03-151">Wartości, które są przechowywane w *stercie* (`IsHeapType == true`) można odczytać przy użyciu:</span><span class="sxs-lookup"><span data-stu-id="71b03-151">Values that are stored in the *heap* (that is, `IsHeapType == true`) can be read using:</span></span>

- <span data-ttu-id="71b03-152">`iSTRING`: **IMetadataTables. GetString**</span><span class="sxs-lookup"><span data-stu-id="71b03-152">`iSTRING`: **IMetadataTables.GetString**</span></span>
- <span data-ttu-id="71b03-153">`iGUID`: **IMetadataTables. GETguid**</span><span class="sxs-lookup"><span data-stu-id="71b03-153">`iGUID`: **IMetadataTables.GetGUID**</span></span>
- <span data-ttu-id="71b03-154">`iBLOB`: **IMetadataTables. GetBlob**</span><span class="sxs-lookup"><span data-stu-id="71b03-154">`iBLOB`: **IMetadataTables.GetBlob**</span></span>

> [!IMPORTANT]
> <span data-ttu-id="71b03-155">Aby użyć stałych zdefiniowanych w powyższej tabeli, należy uwzględnić dyrektywę `#define _DEFINE_META_DATA_META_CONSTANTS` dostarczoną przez plik nagłówkowy *cor. h* .</span><span class="sxs-lookup"><span data-stu-id="71b03-155">To use the constants defined in the table above, include the directive `#define _DEFINE_META_DATA_META_CONSTANTS` provided by the *cor.h* header file.</span></span>

## <a name="requirements"></a><span data-ttu-id="71b03-156">Wymagania</span><span class="sxs-lookup"><span data-stu-id="71b03-156">Requirements</span></span>  
 <span data-ttu-id="71b03-157">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="71b03-157">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="71b03-158">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="71b03-158">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="71b03-159">**Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="71b03-159">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="71b03-160">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="71b03-160">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71b03-161">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="71b03-161">See also</span></span>

- [<span data-ttu-id="71b03-162">IMetaDataTables, interfejs</span><span class="sxs-lookup"><span data-stu-id="71b03-162">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="71b03-163">IMetaDataTables2, interfejs</span><span class="sxs-lookup"><span data-stu-id="71b03-163">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
