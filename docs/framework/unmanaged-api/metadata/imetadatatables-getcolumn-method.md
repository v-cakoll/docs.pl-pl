---
title: IMetaDataTables::GetColumn — Metoda
ms.date: 02/25/2019
api_name:
- IMetaDataTables.GetColumn
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetColumn
helpviewer_keywords:
- IMetaDataTables::GetColumn method [.NET Framework metadata]
- GetColumn method [.NET Framework metadata]
ms.assetid: 1032055b-cabb-45c5-a50e-7e853201b175
topic_type:
- apiref
ms.openlocfilehash: f43d4d1547cbe92f325950e1697dada83b42c4f3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177138"
---
# <a name="imetadatatablesgetcolumn-method"></a><span data-ttu-id="ddbc1-102">IMetaDataTables::GetColumn — Metoda</span><span class="sxs-lookup"><span data-stu-id="ddbc1-102">IMetaDataTables::GetColumn Method</span></span>
<span data-ttu-id="ddbc1-103">Pobiera wskaźnik do wartości zawartej w komórce określonej kolumny i wiersza w danej tabeli.</span><span class="sxs-lookup"><span data-stu-id="ddbc1-103">Gets a pointer to the value contained in the cell of the specified column and row in the given table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ddbc1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ddbc1-104">Syntax</span></span>  
  
```cpp  
HRESULT GetColumn (
    [in]  ULONG   ixTbl,  
    [in]  ULONG   ixCol,  
    [in]  ULONG   rid,  
    [out] ULONG   *pVal  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ddbc1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ddbc1-105">Parameters</span></span>

 `ixTbl`  
 <span data-ttu-id="ddbc1-106">[w] Indeks tabeli.</span><span class="sxs-lookup"><span data-stu-id="ddbc1-106">[in] The index of the table.</span></span>  
  
 `ixCol`  
 <span data-ttu-id="ddbc1-107">[w] Indeks kolumny w tabeli.</span><span class="sxs-lookup"><span data-stu-id="ddbc1-107">[in] The index of the column in the table.</span></span>  
  
 `rid`  
 <span data-ttu-id="ddbc1-108">[w] Indeks wiersza w tabeli.</span><span class="sxs-lookup"><span data-stu-id="ddbc1-108">[in] The index of the row in the table.</span></span>  
  
 `pVal`  
 <span data-ttu-id="ddbc1-109">[na zewnątrz] Wskaźnik do wartości w komórce.</span><span class="sxs-lookup"><span data-stu-id="ddbc1-109">[out] A pointer to the value in the cell.</span></span>  

## <a name="remarks"></a><span data-ttu-id="ddbc1-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ddbc1-110">Remarks</span></span>

<span data-ttu-id="ddbc1-111">Interpretacja wartości zwracanej `pVal` za pośrednictwem zależy od typu kolumny.</span><span class="sxs-lookup"><span data-stu-id="ddbc1-111">The interpretion of the value returned through `pVal` depends on the column's type.</span></span> <span data-ttu-id="ddbc1-112">Typ kolumny można określić, wywołując [IMetaDataTables.GetColumnInfo](imetadatatables-getcolumninfo-method.md).</span><span class="sxs-lookup"><span data-stu-id="ddbc1-112">The column type can be determined by calling [IMetaDataTables.GetColumnInfo](imetadatatables-getcolumninfo-method.md).</span></span>

- <span data-ttu-id="ddbc1-113">**Metoda GetColumn** automatycznie konwertuje kolumny typu **Rid** lub **CodedToken** na `mdToken` pełne wartości 32-bitowe.</span><span class="sxs-lookup"><span data-stu-id="ddbc1-113">The **GetColumn** method automatically converts columns of type **Rid** or **CodedToken** to full 32-bit `mdToken` values.</span></span>
- <span data-ttu-id="ddbc1-114">Automatycznie konwertuje również wartości 8-bitowe lub 16-bitowe na pełne wartości 32-bitowe.</span><span class="sxs-lookup"><span data-stu-id="ddbc1-114">It also automatically converts 8-bit or 16-bit values to full 32-bit values.</span></span>
- <span data-ttu-id="ddbc1-115">Dla kolumn typu *sterty* zwrócony *pVal* będzie indeksem do odpowiedniego stosu.</span><span class="sxs-lookup"><span data-stu-id="ddbc1-115">For *heap* type columns, the returned *pVal* will be an index into the corresponding heap.</span></span>

| <span data-ttu-id="ddbc1-116">Typ kolumny</span><span class="sxs-lookup"><span data-stu-id="ddbc1-116">Column type</span></span>              | <span data-ttu-id="ddbc1-117">pVal zawiera</span><span class="sxs-lookup"><span data-stu-id="ddbc1-117">pVal contains</span></span> | <span data-ttu-id="ddbc1-118">Komentarz</span><span class="sxs-lookup"><span data-stu-id="ddbc1-118">Comment</span></span>                          |
|--------------------------|---------------|-----------------------------------|
| <span data-ttu-id="ddbc1-119">`0`..`iRidMax`</span><span class="sxs-lookup"><span data-stu-id="ddbc1-119">`0`..`iRidMax`</span></span><br><span data-ttu-id="ddbc1-120">(0..63)</span><span class="sxs-lookup"><span data-stu-id="ddbc1-120">(0..63)</span></span>  | <span data-ttu-id="ddbc1-121">mdToken (mdToken)</span><span class="sxs-lookup"><span data-stu-id="ddbc1-121">mdToken</span></span>     | <span data-ttu-id="ddbc1-122">*pVal* będzie zawierać pełny token.</span><span class="sxs-lookup"><span data-stu-id="ddbc1-122">*pVal* will contain a full Token.</span></span> <span data-ttu-id="ddbc1-123">Funkcja automatycznie konwertuje Rid do pełnego tokenu.</span><span class="sxs-lookup"><span data-stu-id="ddbc1-123">The function automatically converts the Rid into a full token.</span></span> |
| <span data-ttu-id="ddbc1-124">`iCodedToken`..`iCodedTokenMax`</span><span class="sxs-lookup"><span data-stu-id="ddbc1-124">`iCodedToken`..`iCodedTokenMax`</span></span><br><span data-ttu-id="ddbc1-125">(64..95)</span><span class="sxs-lookup"><span data-stu-id="ddbc1-125">(64..95)</span></span> | <span data-ttu-id="ddbc1-126">mdToken (mdToken)</span><span class="sxs-lookup"><span data-stu-id="ddbc1-126">mdToken</span></span> | <span data-ttu-id="ddbc1-127">Po zwrocie *pVal* będzie zawierał pełny Token.</span><span class="sxs-lookup"><span data-stu-id="ddbc1-127">Upon return, *pVal* will contain a full Token.</span></span> <span data-ttu-id="ddbc1-128">Funkcja automatycznie dekompresuje CodedToken do pełnego tokenu.</span><span class="sxs-lookup"><span data-stu-id="ddbc1-128">The function automatically decompresses the CodedToken into a full token.</span></span> |
| <span data-ttu-id="ddbc1-129">`iSHORT`(96)</span><span class="sxs-lookup"><span data-stu-id="ddbc1-129">`iSHORT` (96)</span></span>            | <span data-ttu-id="ddbc1-130">Int16</span><span class="sxs-lookup"><span data-stu-id="ddbc1-130">Int16</span></span>         | <span data-ttu-id="ddbc1-131">Automatycznie podpisuj rozszerzony do 32-bitowego.</span><span class="sxs-lookup"><span data-stu-id="ddbc1-131">Automatically sign-extended to 32-bit.</span></span>  |
| <span data-ttu-id="ddbc1-132">`iUSHORT`(97)</span><span class="sxs-lookup"><span data-stu-id="ddbc1-132">`iUSHORT` (97)</span></span>           | <span data-ttu-id="ddbc1-133">UInt16</span><span class="sxs-lookup"><span data-stu-id="ddbc1-133">UInt16</span></span>        | <span data-ttu-id="ddbc1-134">Automatycznie podpisuj rozszerzony do 32-bitowego.</span><span class="sxs-lookup"><span data-stu-id="ddbc1-134">Automatically sign-extended to 32-bit.</span></span>  |
| <span data-ttu-id="ddbc1-135">`iLONG`(98)</span><span class="sxs-lookup"><span data-stu-id="ddbc1-135">`iLONG` (98)</span></span>             | <span data-ttu-id="ddbc1-136">Int32</span><span class="sxs-lookup"><span data-stu-id="ddbc1-136">Int32</span></span>         |                                        |
| <span data-ttu-id="ddbc1-137">`iULONG`(99)</span><span class="sxs-lookup"><span data-stu-id="ddbc1-137">`iULONG` (99)</span></span>            | <span data-ttu-id="ddbc1-138">UInt32</span><span class="sxs-lookup"><span data-stu-id="ddbc1-138">UInt32</span></span>        |                                        |
| <span data-ttu-id="ddbc1-139">`iBYTE`(100)</span><span class="sxs-lookup"><span data-stu-id="ddbc1-139">`iBYTE` (100)</span></span>            | <span data-ttu-id="ddbc1-140">Byte</span><span class="sxs-lookup"><span data-stu-id="ddbc1-140">Byte</span></span>          | <span data-ttu-id="ddbc1-141">Automatycznie podpisuj rozszerzony do 32-bitowego.</span><span class="sxs-lookup"><span data-stu-id="ddbc1-141">Automatically sign-extended to 32-bit.</span></span>  |
| <span data-ttu-id="ddbc1-142">`iSTRING`(101)</span><span class="sxs-lookup"><span data-stu-id="ddbc1-142">`iSTRING` (101)</span></span>          | <span data-ttu-id="ddbc1-143">Indeks sterty ciągów</span><span class="sxs-lookup"><span data-stu-id="ddbc1-143">String heap index</span></span> | <span data-ttu-id="ddbc1-144">*pVal* jest indeksem do stosu String.</span><span class="sxs-lookup"><span data-stu-id="ddbc1-144">*pVal* is an index into the String heap.</span></span> <span data-ttu-id="ddbc1-145">Użyj [IMetadataTables::GetString,](imetadatatables-getstring-method.md) aby uzyskać rzeczywistą wartość ciągu kolumny.</span><span class="sxs-lookup"><span data-stu-id="ddbc1-145">Use [IMetadataTables::GetString](imetadatatables-getstring-method.md) to get the actual column String value.</span></span> |
| <span data-ttu-id="ddbc1-146">`iGUID`(102)</span><span class="sxs-lookup"><span data-stu-id="ddbc1-146">`iGUID` (102)</span></span>            | <span data-ttu-id="ddbc1-147">Wskaźnik sterty guid</span><span class="sxs-lookup"><span data-stu-id="ddbc1-147">Guid heap index</span></span> | <span data-ttu-id="ddbc1-148">*pVal* jest indeksem do sterty Guid.</span><span class="sxs-lookup"><span data-stu-id="ddbc1-148">*pVal* is an index into the Guid heap.</span></span> <span data-ttu-id="ddbc1-149">Użyj [IMetadataTables::GetGuid,](imetadatatables-getguid-method.md) aby uzyskać rzeczywistą wartość Guid kolumny.</span><span class="sxs-lookup"><span data-stu-id="ddbc1-149">Use [IMetadataTables::GetGuid](imetadatatables-getguid-method.md) to get the actual column Guid value.</span></span> |
| <span data-ttu-id="ddbc1-150">`iBLOB`(103)</span><span class="sxs-lookup"><span data-stu-id="ddbc1-150">`iBLOB` (103)</span></span>            | <span data-ttu-id="ddbc1-151">Indeks sterty obiektów blob</span><span class="sxs-lookup"><span data-stu-id="ddbc1-151">Blob heap index</span></span> | <span data-ttu-id="ddbc1-152">*pVal* jest indeksem do sterty obiektów Blob.</span><span class="sxs-lookup"><span data-stu-id="ddbc1-152">*pVal* is an index into the Blob heap.</span></span> <span data-ttu-id="ddbc1-153">Użyj [IMetadataTables::GetBlob,](imetadatatables-getblob-method.md) aby uzyskać rzeczywistą wartość obiektu blob kolumny.</span><span class="sxs-lookup"><span data-stu-id="ddbc1-153">Use [IMetadataTables::GetBlob](imetadatatables-getblob-method.md) to get the actual column Blob value.</span></span> |
  
## <a name="requirements"></a><span data-ttu-id="ddbc1-154">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ddbc1-154">Requirements</span></span>  
 <span data-ttu-id="ddbc1-155">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ddbc1-155">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ddbc1-156">**Nagłówek:** Okręg wyborczy Cor.h</span><span class="sxs-lookup"><span data-stu-id="ddbc1-156">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ddbc1-157">**Biblioteka:** Używany jako zasób w pliku MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ddbc1-157">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ddbc1-158">**Wersje programu .NET Framework**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ddbc1-158">**.NET Framework Versions** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ddbc1-159">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ddbc1-159">See also</span></span>

- [<span data-ttu-id="ddbc1-160">IMetaDataTables, interfejs</span><span class="sxs-lookup"><span data-stu-id="ddbc1-160">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="ddbc1-161">IMetaDataTables2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="ddbc1-161">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
