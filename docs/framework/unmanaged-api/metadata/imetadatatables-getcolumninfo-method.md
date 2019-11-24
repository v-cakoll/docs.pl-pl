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
# <a name="imetadatatablesgetcolumninfo-method"></a><span data-ttu-id="bd032-102">IMetaDataTables::GetColumnInfo — Metoda</span><span class="sxs-lookup"><span data-stu-id="bd032-102">IMetaDataTables::GetColumnInfo Method</span></span>
<span data-ttu-id="bd032-103">Gets data about the specified column in the specified table.</span><span class="sxs-lookup"><span data-stu-id="bd032-103">Gets data about the specified column in the specified table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd032-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="bd032-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="bd032-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bd032-105">Parameters</span></span>
=======

 `ixTbl`  
 <span data-ttu-id="bd032-106">[in] The index of the desired table.</span><span class="sxs-lookup"><span data-stu-id="bd032-106">[in] The index of the desired table.</span></span>  
  
 `ixCol`  
 <span data-ttu-id="bd032-107">[in] The index of the desired column.</span><span class="sxs-lookup"><span data-stu-id="bd032-107">[in] The index of the desired column.</span></span>  
  
 `poCol`  
 <span data-ttu-id="bd032-108">[out] A pointer to the offset of the column in the row.</span><span class="sxs-lookup"><span data-stu-id="bd032-108">[out] A pointer to the offset of the column in the row.</span></span>  
  
 `pcbCol`  
 <span data-ttu-id="bd032-109">[out] A pointer to the size, in bytes, of the column.</span><span class="sxs-lookup"><span data-stu-id="bd032-109">[out] A pointer to the size, in bytes, of the column.</span></span>  
  
 `pType`  
 <span data-ttu-id="bd032-110">[out] A pointer to the type of the values in the column.</span><span class="sxs-lookup"><span data-stu-id="bd032-110">[out] A pointer to the type of the values in the column.</span></span>  
  
 `ppName`  
 <span data-ttu-id="bd032-111">[out] A pointer to a pointer to the column name.</span><span class="sxs-lookup"><span data-stu-id="bd032-111">[out] A pointer to a pointer to the column name.</span></span>  
 
## <a name="remarks"></a><span data-ttu-id="bd032-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bd032-112">Remarks</span></span>

<span data-ttu-id="bd032-113">The returned column type falls within a range of values:</span><span class="sxs-lookup"><span data-stu-id="bd032-113">The returned column type falls within a range of values:</span></span>

| <span data-ttu-id="bd032-114">pType</span><span class="sxs-lookup"><span data-stu-id="bd032-114">pType</span></span>                    | <span data-ttu-id="bd032-115">Opis</span><span class="sxs-lookup"><span data-stu-id="bd032-115">Description</span></span>   | <span data-ttu-id="bd032-116">Helper function</span><span class="sxs-lookup"><span data-stu-id="bd032-116">Helper function</span></span>                   |
|--------------------------|---------------|-----------------------------------|
| <span data-ttu-id="bd032-117">`0`..`iRidMax`</span><span class="sxs-lookup"><span data-stu-id="bd032-117">`0`..`iRidMax`</span></span><br><span data-ttu-id="bd032-118">(0..63)</span><span class="sxs-lookup"><span data-stu-id="bd032-118">(0..63)</span></span>   | <span data-ttu-id="bd032-119">Rid</span><span class="sxs-lookup"><span data-stu-id="bd032-119">Rid</span></span>           | <span data-ttu-id="bd032-120">**IsRidType**</span><span class="sxs-lookup"><span data-stu-id="bd032-120">**IsRidType**</span></span><br><span data-ttu-id="bd032-121">**IsRidOrToken**</span><span class="sxs-lookup"><span data-stu-id="bd032-121">**IsRidOrToken**</span></span> |
| <span data-ttu-id="bd032-122">`iCodedToken`..`iCodedTokenMax`</span><span class="sxs-lookup"><span data-stu-id="bd032-122">`iCodedToken`..`iCodedTokenMax`</span></span><br><span data-ttu-id="bd032-123">(64..95)</span><span class="sxs-lookup"><span data-stu-id="bd032-123">(64..95)</span></span> | <span data-ttu-id="bd032-124">Coded token</span><span class="sxs-lookup"><span data-stu-id="bd032-124">Coded token</span></span> | <span data-ttu-id="bd032-125">**IsCodedTokenType**</span><span class="sxs-lookup"><span data-stu-id="bd032-125">**IsCodedTokenType**</span></span> <br><span data-ttu-id="bd032-126">**IsRidOrToken**</span><span class="sxs-lookup"><span data-stu-id="bd032-126">**IsRidOrToken**</span></span> |
| <span data-ttu-id="bd032-127">`iSHORT` (96)</span><span class="sxs-lookup"><span data-stu-id="bd032-127">`iSHORT` (96)</span></span>            | <span data-ttu-id="bd032-128">Int16</span><span class="sxs-lookup"><span data-stu-id="bd032-128">Int16</span></span>         | <span data-ttu-id="bd032-129">**IsFixedType**</span><span class="sxs-lookup"><span data-stu-id="bd032-129">**IsFixedType**</span></span>                   |
| <span data-ttu-id="bd032-130">`iUSHORT` (97)</span><span class="sxs-lookup"><span data-stu-id="bd032-130">`iUSHORT` (97)</span></span>           | <span data-ttu-id="bd032-131">UInt16</span><span class="sxs-lookup"><span data-stu-id="bd032-131">UInt16</span></span>        | <span data-ttu-id="bd032-132">**IsFixedType**</span><span class="sxs-lookup"><span data-stu-id="bd032-132">**IsFixedType**</span></span>                   |
| <span data-ttu-id="bd032-133">`iLONG` (98)</span><span class="sxs-lookup"><span data-stu-id="bd032-133">`iLONG` (98)</span></span>             | <span data-ttu-id="bd032-134">Int32</span><span class="sxs-lookup"><span data-stu-id="bd032-134">Int32</span></span>         | <span data-ttu-id="bd032-135">**IsFixedType**</span><span class="sxs-lookup"><span data-stu-id="bd032-135">**IsFixedType**</span></span>                   |
| <span data-ttu-id="bd032-136">`iULONG` (99)</span><span class="sxs-lookup"><span data-stu-id="bd032-136">`iULONG` (99)</span></span>            | <span data-ttu-id="bd032-137">UInt32</span><span class="sxs-lookup"><span data-stu-id="bd032-137">UInt32</span></span>        | <span data-ttu-id="bd032-138">**IsFixedType**</span><span class="sxs-lookup"><span data-stu-id="bd032-138">**IsFixedType**</span></span>                   |
| <span data-ttu-id="bd032-139">`iBYTE` (100)</span><span class="sxs-lookup"><span data-stu-id="bd032-139">`iBYTE` (100)</span></span>            | <span data-ttu-id="bd032-140">Byte</span><span class="sxs-lookup"><span data-stu-id="bd032-140">Byte</span></span>          | <span data-ttu-id="bd032-141">**IsFixedType**</span><span class="sxs-lookup"><span data-stu-id="bd032-141">**IsFixedType**</span></span>                   |
| <span data-ttu-id="bd032-142">`iSTRING` (101)</span><span class="sxs-lookup"><span data-stu-id="bd032-142">`iSTRING` (101)</span></span>          | <span data-ttu-id="bd032-143">String</span><span class="sxs-lookup"><span data-stu-id="bd032-143">String</span></span>        | <span data-ttu-id="bd032-144">**IsHeapType**</span><span class="sxs-lookup"><span data-stu-id="bd032-144">**IsHeapType**</span></span>                    |
| <span data-ttu-id="bd032-145">`iGUID` (102)</span><span class="sxs-lookup"><span data-stu-id="bd032-145">`iGUID` (102)</span></span>            | <span data-ttu-id="bd032-146">Guid</span><span class="sxs-lookup"><span data-stu-id="bd032-146">Guid</span></span>          | <span data-ttu-id="bd032-147">**IsHeapType**</span><span class="sxs-lookup"><span data-stu-id="bd032-147">**IsHeapType**</span></span>                    |
| <span data-ttu-id="bd032-148">`iBLOB` (103)</span><span class="sxs-lookup"><span data-stu-id="bd032-148">`iBLOB` (103)</span></span>            | <span data-ttu-id="bd032-149">Blob</span><span class="sxs-lookup"><span data-stu-id="bd032-149">Blob</span></span>          | <span data-ttu-id="bd032-150">**IsHeapType**</span><span class="sxs-lookup"><span data-stu-id="bd032-150">**IsHeapType**</span></span>                    |

<span data-ttu-id="bd032-151">Values that are stored in the *heap* (that is, `IsHeapType == true`) can be read using:</span><span class="sxs-lookup"><span data-stu-id="bd032-151">Values that are stored in the *heap* (that is, `IsHeapType == true`) can be read using:</span></span>

- <span data-ttu-id="bd032-152">`iSTRING`: **IMetadataTables.GetString**</span><span class="sxs-lookup"><span data-stu-id="bd032-152">`iSTRING`: **IMetadataTables.GetString**</span></span>
- <span data-ttu-id="bd032-153">`iGUID`: **IMetadataTables.GetGUID**</span><span class="sxs-lookup"><span data-stu-id="bd032-153">`iGUID`: **IMetadataTables.GetGUID**</span></span>
- <span data-ttu-id="bd032-154">`iBLOB`: **IMetadataTables.GetBlob**</span><span class="sxs-lookup"><span data-stu-id="bd032-154">`iBLOB`: **IMetadataTables.GetBlob**</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bd032-155">To use the constants defined in the table above, include the directive `#define _DEFINE_META_DATA_META_CONSTANTS` provided by the *cor.h* header file.</span><span class="sxs-lookup"><span data-stu-id="bd032-155">To use the constants defined in the table above, include the directive `#define _DEFINE_META_DATA_META_CONSTANTS` provided by the *cor.h* header file.</span></span>

## <a name="requirements"></a><span data-ttu-id="bd032-156">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bd032-156">Requirements</span></span>  
 <span data-ttu-id="bd032-157">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bd032-157">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bd032-158">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="bd032-158">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bd032-159">**Library:** Used as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="bd032-159">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="bd032-160">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bd032-160">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd032-161">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bd032-161">See also</span></span>

- [<span data-ttu-id="bd032-162">IMetaDataTables, interfejs</span><span class="sxs-lookup"><span data-stu-id="bd032-162">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="bd032-163">IMetaDataTables2, interfejs</span><span class="sxs-lookup"><span data-stu-id="bd032-163">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
