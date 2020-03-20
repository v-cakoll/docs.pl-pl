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
ms.openlocfilehash: cc8aac32149fed952737d928e16a8f6efc448c79
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177123"
---
# <a name="imetadatatablesgetcolumninfo-method"></a><span data-ttu-id="dcc6b-102">IMetaDataTables::GetColumnInfo — Metoda</span><span class="sxs-lookup"><span data-stu-id="dcc6b-102">IMetaDataTables::GetColumnInfo Method</span></span>
<span data-ttu-id="dcc6b-103">Pobiera dane dotyczące określonej kolumny w określonej tabeli.</span><span class="sxs-lookup"><span data-stu-id="dcc6b-103">Gets data about the specified column in the specified table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dcc6b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="dcc6b-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="dcc6b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="dcc6b-105">Parameters</span></span>
=======

 `ixTbl`  
 <span data-ttu-id="dcc6b-106">[w] Indeks żądanej tabeli.</span><span class="sxs-lookup"><span data-stu-id="dcc6b-106">[in] The index of the desired table.</span></span>  
  
 `ixCol`  
 <span data-ttu-id="dcc6b-107">[w] Indeks żądanej kolumny.</span><span class="sxs-lookup"><span data-stu-id="dcc6b-107">[in] The index of the desired column.</span></span>  
  
 `poCol`  
 <span data-ttu-id="dcc6b-108">[na zewnątrz] Wskaźnik do odsunięcia kolumny w wierszu.</span><span class="sxs-lookup"><span data-stu-id="dcc6b-108">[out] A pointer to the offset of the column in the row.</span></span>  
  
 `pcbCol`  
 <span data-ttu-id="dcc6b-109">[na zewnątrz] Wskaźnik do rozmiaru w bajtach kolumny.</span><span class="sxs-lookup"><span data-stu-id="dcc6b-109">[out] A pointer to the size, in bytes, of the column.</span></span>  
  
 `pType`  
 <span data-ttu-id="dcc6b-110">[na zewnątrz] Wskaźnik do typu wartości w kolumnie.</span><span class="sxs-lookup"><span data-stu-id="dcc6b-110">[out] A pointer to the type of the values in the column.</span></span>  
  
 `ppName`  
 <span data-ttu-id="dcc6b-111">[na zewnątrz] Wskaźnik do wskaźnika do nazwy kolumny.</span><span class="sxs-lookup"><span data-stu-id="dcc6b-111">[out] A pointer to a pointer to the column name.</span></span>  

## <a name="remarks"></a><span data-ttu-id="dcc6b-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="dcc6b-112">Remarks</span></span>

<span data-ttu-id="dcc6b-113">Zwracany typ kolumny mieści się w zakresie wartości:</span><span class="sxs-lookup"><span data-stu-id="dcc6b-113">The returned column type falls within a range of values:</span></span>

| <span data-ttu-id="dcc6b-114">pTyp</span><span class="sxs-lookup"><span data-stu-id="dcc6b-114">pType</span></span>                    | <span data-ttu-id="dcc6b-115">Opis</span><span class="sxs-lookup"><span data-stu-id="dcc6b-115">Description</span></span>   | <span data-ttu-id="dcc6b-116">Funkcja pomocnika</span><span class="sxs-lookup"><span data-stu-id="dcc6b-116">Helper function</span></span>                   |
|--------------------------|---------------|-----------------------------------|
| <span data-ttu-id="dcc6b-117">`0`..`iRidMax`</span><span class="sxs-lookup"><span data-stu-id="dcc6b-117">`0`..`iRidMax`</span></span><br><span data-ttu-id="dcc6b-118">(0..63)</span><span class="sxs-lookup"><span data-stu-id="dcc6b-118">(0..63)</span></span>   | <span data-ttu-id="dcc6b-119">Rid</span><span class="sxs-lookup"><span data-stu-id="dcc6b-119">Rid</span></span>           | <span data-ttu-id="dcc6b-120">**Typ IsRid**</span><span class="sxs-lookup"><span data-stu-id="dcc6b-120">**IsRidType**</span></span><br><span data-ttu-id="dcc6b-121">**IsRidOrToken (IsRidOrToken)**</span><span class="sxs-lookup"><span data-stu-id="dcc6b-121">**IsRidOrToken**</span></span> |
| <span data-ttu-id="dcc6b-122">`iCodedToken`..`iCodedTokenMax`</span><span class="sxs-lookup"><span data-stu-id="dcc6b-122">`iCodedToken`..`iCodedTokenMax`</span></span><br><span data-ttu-id="dcc6b-123">(64..95)</span><span class="sxs-lookup"><span data-stu-id="dcc6b-123">(64..95)</span></span> | <span data-ttu-id="dcc6b-124">Token kodowany</span><span class="sxs-lookup"><span data-stu-id="dcc6b-124">Coded token</span></span> | <span data-ttu-id="dcc6b-125">**Typ IsCodedToken**</span><span class="sxs-lookup"><span data-stu-id="dcc6b-125">**IsCodedTokenType**</span></span> <br><span data-ttu-id="dcc6b-126">**IsRidOrToken (IsRidOrToken)**</span><span class="sxs-lookup"><span data-stu-id="dcc6b-126">**IsRidOrToken**</span></span> |
| <span data-ttu-id="dcc6b-127">`iSHORT`(96)</span><span class="sxs-lookup"><span data-stu-id="dcc6b-127">`iSHORT` (96)</span></span>            | <span data-ttu-id="dcc6b-128">Int16</span><span class="sxs-lookup"><span data-stu-id="dcc6b-128">Int16</span></span>         | <span data-ttu-id="dcc6b-129">**IsFixedType (Typ isfixedtype)**</span><span class="sxs-lookup"><span data-stu-id="dcc6b-129">**IsFixedType**</span></span>                   |
| <span data-ttu-id="dcc6b-130">`iUSHORT`(97)</span><span class="sxs-lookup"><span data-stu-id="dcc6b-130">`iUSHORT` (97)</span></span>           | <span data-ttu-id="dcc6b-131">UInt16</span><span class="sxs-lookup"><span data-stu-id="dcc6b-131">UInt16</span></span>        | <span data-ttu-id="dcc6b-132">**IsFixedType (Typ isfixedtype)**</span><span class="sxs-lookup"><span data-stu-id="dcc6b-132">**IsFixedType**</span></span>                   |
| <span data-ttu-id="dcc6b-133">`iLONG`(98)</span><span class="sxs-lookup"><span data-stu-id="dcc6b-133">`iLONG` (98)</span></span>             | <span data-ttu-id="dcc6b-134">Int32</span><span class="sxs-lookup"><span data-stu-id="dcc6b-134">Int32</span></span>         | <span data-ttu-id="dcc6b-135">**IsFixedType (Typ isfixedtype)**</span><span class="sxs-lookup"><span data-stu-id="dcc6b-135">**IsFixedType**</span></span>                   |
| <span data-ttu-id="dcc6b-136">`iULONG`(99)</span><span class="sxs-lookup"><span data-stu-id="dcc6b-136">`iULONG` (99)</span></span>            | <span data-ttu-id="dcc6b-137">UInt32</span><span class="sxs-lookup"><span data-stu-id="dcc6b-137">UInt32</span></span>        | <span data-ttu-id="dcc6b-138">**IsFixedType (Typ isfixedtype)**</span><span class="sxs-lookup"><span data-stu-id="dcc6b-138">**IsFixedType**</span></span>                   |
| <span data-ttu-id="dcc6b-139">`iBYTE`(100)</span><span class="sxs-lookup"><span data-stu-id="dcc6b-139">`iBYTE` (100)</span></span>            | <span data-ttu-id="dcc6b-140">Byte</span><span class="sxs-lookup"><span data-stu-id="dcc6b-140">Byte</span></span>          | <span data-ttu-id="dcc6b-141">**IsFixedType (Typ isfixedtype)**</span><span class="sxs-lookup"><span data-stu-id="dcc6b-141">**IsFixedType**</span></span>                   |
| <span data-ttu-id="dcc6b-142">`iSTRING`(101)</span><span class="sxs-lookup"><span data-stu-id="dcc6b-142">`iSTRING` (101)</span></span>          | <span data-ttu-id="dcc6b-143">Ciąg</span><span class="sxs-lookup"><span data-stu-id="dcc6b-143">String</span></span>        | <span data-ttu-id="dcc6b-144">**Typ IsHeapType**</span><span class="sxs-lookup"><span data-stu-id="dcc6b-144">**IsHeapType**</span></span>                    |
| <span data-ttu-id="dcc6b-145">`iGUID`(102)</span><span class="sxs-lookup"><span data-stu-id="dcc6b-145">`iGUID` (102)</span></span>            | <span data-ttu-id="dcc6b-146">Guid (identyfikator GUID)</span><span class="sxs-lookup"><span data-stu-id="dcc6b-146">Guid</span></span>          | <span data-ttu-id="dcc6b-147">**Typ IsHeapType**</span><span class="sxs-lookup"><span data-stu-id="dcc6b-147">**IsHeapType**</span></span>                    |
| <span data-ttu-id="dcc6b-148">`iBLOB`(103)</span><span class="sxs-lookup"><span data-stu-id="dcc6b-148">`iBLOB` (103)</span></span>            | <span data-ttu-id="dcc6b-149">Obiekt blob</span><span class="sxs-lookup"><span data-stu-id="dcc6b-149">Blob</span></span>          | <span data-ttu-id="dcc6b-150">**Typ IsHeapType**</span><span class="sxs-lookup"><span data-stu-id="dcc6b-150">**IsHeapType**</span></span>                    |

<span data-ttu-id="dcc6b-151">Wartości, które są przechowywane w *stercie* `IsHeapType == true`(czyli) można odczytać za pomocą:</span><span class="sxs-lookup"><span data-stu-id="dcc6b-151">Values that are stored in the *heap* (that is, `IsHeapType == true`) can be read using:</span></span>

- <span data-ttu-id="dcc6b-152">`iSTRING`: **IMetadataTables.GetString**</span><span class="sxs-lookup"><span data-stu-id="dcc6b-152">`iSTRING`: **IMetadataTables.GetString**</span></span>
- <span data-ttu-id="dcc6b-153">`iGUID`: **IMetadataTables.GetGUID**</span><span class="sxs-lookup"><span data-stu-id="dcc6b-153">`iGUID`: **IMetadataTables.GetGUID**</span></span>
- <span data-ttu-id="dcc6b-154">`iBLOB`: **IMetadataTables.GetBlob**</span><span class="sxs-lookup"><span data-stu-id="dcc6b-154">`iBLOB`: **IMetadataTables.GetBlob**</span></span>

> [!IMPORTANT]
> <span data-ttu-id="dcc6b-155">Aby użyć stałych zdefiniowanych w powyższej `#define _DEFINE_META_DATA_META_CONSTANTS` tabeli, należy dołączyć dyrektywę dostarczoną przez plik nagłówka *cor.h.*</span><span class="sxs-lookup"><span data-stu-id="dcc6b-155">To use the constants defined in the table above, include the directive `#define _DEFINE_META_DATA_META_CONSTANTS` provided by the *cor.h* header file.</span></span>

## <a name="requirements"></a><span data-ttu-id="dcc6b-156">Wymagania</span><span class="sxs-lookup"><span data-stu-id="dcc6b-156">Requirements</span></span>  
 <span data-ttu-id="dcc6b-157">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dcc6b-157">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dcc6b-158">**Nagłówek:** Okręg wyborczy Cor.h</span><span class="sxs-lookup"><span data-stu-id="dcc6b-158">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="dcc6b-159">**Biblioteka:** Używany jako zasób w pliku MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="dcc6b-159">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="dcc6b-160">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dcc6b-160">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dcc6b-161">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="dcc6b-161">See also</span></span>

- [<span data-ttu-id="dcc6b-162">IMetaDataTables, interfejs</span><span class="sxs-lookup"><span data-stu-id="dcc6b-162">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="dcc6b-163">IMetaDataTables2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="dcc6b-163">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
