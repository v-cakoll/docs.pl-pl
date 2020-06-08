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
ms.openlocfilehash: 76d23fe9221ae5a07d79b8c5c1a7ad297922b003
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501251"
---
# <a name="imetadatatablesgetcolumn-method"></a><span data-ttu-id="e79c3-102">IMetaDataTables::GetColumn — Metoda</span><span class="sxs-lookup"><span data-stu-id="e79c3-102">IMetaDataTables::GetColumn Method</span></span>
<span data-ttu-id="e79c3-103">Pobiera wskaźnik do wartości zawartej w komórce określonej kolumny i wiersza w danej tabeli.</span><span class="sxs-lookup"><span data-stu-id="e79c3-103">Gets a pointer to the value contained in the cell of the specified column and row in the given table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e79c3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e79c3-104">Syntax</span></span>  
  
```cpp  
HRESULT GetColumn (
    [in]  ULONG   ixTbl,  
    [in]  ULONG   ixCol,  
    [in]  ULONG   rid,  
    [out] ULONG   *pVal  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e79c3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e79c3-105">Parameters</span></span>

 `ixTbl`  
 <span data-ttu-id="e79c3-106">podczas Indeks tabeli.</span><span class="sxs-lookup"><span data-stu-id="e79c3-106">[in] The index of the table.</span></span>  
  
 `ixCol`  
 <span data-ttu-id="e79c3-107">podczas Indeks kolumny w tabeli.</span><span class="sxs-lookup"><span data-stu-id="e79c3-107">[in] The index of the column in the table.</span></span>  
  
 `rid`  
 <span data-ttu-id="e79c3-108">podczas Indeks wiersza w tabeli.</span><span class="sxs-lookup"><span data-stu-id="e79c3-108">[in] The index of the row in the table.</span></span>  
  
 `pVal`  
 <span data-ttu-id="e79c3-109">określoną Wskaźnik do wartości w komórce.</span><span class="sxs-lookup"><span data-stu-id="e79c3-109">[out] A pointer to the value in the cell.</span></span>  

## <a name="remarks"></a><span data-ttu-id="e79c3-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e79c3-110">Remarks</span></span>

<span data-ttu-id="e79c3-111">Interpretacja wartości zwracanej przez jest `pVal` zależna od typu kolumny.</span><span class="sxs-lookup"><span data-stu-id="e79c3-111">The interpretion of the value returned through `pVal` depends on the column's type.</span></span> <span data-ttu-id="e79c3-112">Typ kolumny można określić przez wywołanie metody [IMetaDataTables. GetColumnInfo](imetadatatables-getcolumninfo-method.md).</span><span class="sxs-lookup"><span data-stu-id="e79c3-112">The column type can be determined by calling [IMetaDataTables.GetColumnInfo](imetadatatables-getcolumninfo-method.md).</span></span>

- <span data-ttu-id="e79c3-113">Metoda **GetColumn** automatycznie konwertuje kolumny typu **RID** lub **CodedToken** na pełne wartości 32-bitowe `mdToken` .</span><span class="sxs-lookup"><span data-stu-id="e79c3-113">The **GetColumn** method automatically converts columns of type **Rid** or **CodedToken** to full 32-bit `mdToken` values.</span></span>
- <span data-ttu-id="e79c3-114">Automatycznie konwertuje wartości 8-bitowe lub 16-bitowe na pełne wartości 32-bitowe.</span><span class="sxs-lookup"><span data-stu-id="e79c3-114">It also automatically converts 8-bit or 16-bit values to full 32-bit values.</span></span>
- <span data-ttu-id="e79c3-115">W przypadku kolumn typu *sterty* zwracany *Pval* będzie indeksem do odpowiedniej sterty.</span><span class="sxs-lookup"><span data-stu-id="e79c3-115">For *heap* type columns, the returned *pVal* will be an index into the corresponding heap.</span></span>

| <span data-ttu-id="e79c3-116">Typ kolumny</span><span class="sxs-lookup"><span data-stu-id="e79c3-116">Column type</span></span>              | <span data-ttu-id="e79c3-117">pVal zawiera</span><span class="sxs-lookup"><span data-stu-id="e79c3-117">pVal contains</span></span> | <span data-ttu-id="e79c3-118">Komentarz</span><span class="sxs-lookup"><span data-stu-id="e79c3-118">Comment</span></span>                          |
|--------------------------|---------------|-----------------------------------|
| <span data-ttu-id="e79c3-119">`0`..`iRidMax`</span><span class="sxs-lookup"><span data-stu-id="e79c3-119">`0`..`iRidMax`</span></span><br><span data-ttu-id="e79c3-120">(0.. 63)</span><span class="sxs-lookup"><span data-stu-id="e79c3-120">(0..63)</span></span>  | <span data-ttu-id="e79c3-121">mdToken</span><span class="sxs-lookup"><span data-stu-id="e79c3-121">mdToken</span></span>     | <span data-ttu-id="e79c3-122">*Pval* będzie zawierać pełny token.</span><span class="sxs-lookup"><span data-stu-id="e79c3-122">*pVal* will contain a full Token.</span></span> <span data-ttu-id="e79c3-123">Funkcja automatycznie konwertuje identyfikator RID na pełny token.</span><span class="sxs-lookup"><span data-stu-id="e79c3-123">The function automatically converts the Rid into a full token.</span></span> |
| <span data-ttu-id="e79c3-124">`iCodedToken`..`iCodedTokenMax`</span><span class="sxs-lookup"><span data-stu-id="e79c3-124">`iCodedToken`..`iCodedTokenMax`</span></span><br><span data-ttu-id="e79c3-125">(64.. 95)</span><span class="sxs-lookup"><span data-stu-id="e79c3-125">(64..95)</span></span> | <span data-ttu-id="e79c3-126">mdToken</span><span class="sxs-lookup"><span data-stu-id="e79c3-126">mdToken</span></span> | <span data-ttu-id="e79c3-127">Po powrocie *Pval* będzie zawierać pełny token.</span><span class="sxs-lookup"><span data-stu-id="e79c3-127">Upon return, *pVal* will contain a full Token.</span></span> <span data-ttu-id="e79c3-128">Funkcja automatycznie dekompresuje CodedToken do pełnego tokenu.</span><span class="sxs-lookup"><span data-stu-id="e79c3-128">The function automatically decompresses the CodedToken into a full token.</span></span> |
| <span data-ttu-id="e79c3-129">`iSHORT`(96)</span><span class="sxs-lookup"><span data-stu-id="e79c3-129">`iSHORT` (96)</span></span>            | <span data-ttu-id="e79c3-130">Int16</span><span class="sxs-lookup"><span data-stu-id="e79c3-130">Int16</span></span>         | <span data-ttu-id="e79c3-131">Automatycznie Podpisz do 32-bitowego.</span><span class="sxs-lookup"><span data-stu-id="e79c3-131">Automatically sign-extended to 32-bit.</span></span>  |
| <span data-ttu-id="e79c3-132">`iUSHORT`(97)</span><span class="sxs-lookup"><span data-stu-id="e79c3-132">`iUSHORT` (97)</span></span>           | <span data-ttu-id="e79c3-133">UInt16</span><span class="sxs-lookup"><span data-stu-id="e79c3-133">UInt16</span></span>        | <span data-ttu-id="e79c3-134">Automatycznie Podpisz do 32-bitowego.</span><span class="sxs-lookup"><span data-stu-id="e79c3-134">Automatically sign-extended to 32-bit.</span></span>  |
| <span data-ttu-id="e79c3-135">`iLONG`(98)</span><span class="sxs-lookup"><span data-stu-id="e79c3-135">`iLONG` (98)</span></span>             | <span data-ttu-id="e79c3-136">Int32</span><span class="sxs-lookup"><span data-stu-id="e79c3-136">Int32</span></span>         |                                        |
| <span data-ttu-id="e79c3-137">`iULONG`(99)</span><span class="sxs-lookup"><span data-stu-id="e79c3-137">`iULONG` (99)</span></span>            | <span data-ttu-id="e79c3-138">UInt32</span><span class="sxs-lookup"><span data-stu-id="e79c3-138">UInt32</span></span>        |                                        |
| <span data-ttu-id="e79c3-139">`iBYTE`(100)</span><span class="sxs-lookup"><span data-stu-id="e79c3-139">`iBYTE` (100)</span></span>            | <span data-ttu-id="e79c3-140">Byte</span><span class="sxs-lookup"><span data-stu-id="e79c3-140">Byte</span></span>          | <span data-ttu-id="e79c3-141">Automatycznie Podpisz do 32-bitowego.</span><span class="sxs-lookup"><span data-stu-id="e79c3-141">Automatically sign-extended to 32-bit.</span></span>  |
| <span data-ttu-id="e79c3-142">`iSTRING`(101)</span><span class="sxs-lookup"><span data-stu-id="e79c3-142">`iSTRING` (101)</span></span>          | <span data-ttu-id="e79c3-143">Indeks sterty ciągu</span><span class="sxs-lookup"><span data-stu-id="e79c3-143">String heap index</span></span> | <span data-ttu-id="e79c3-144">*Pval* jest indeksem do sterty ciągu.</span><span class="sxs-lookup"><span data-stu-id="e79c3-144">*pVal* is an index into the String heap.</span></span> <span data-ttu-id="e79c3-145">Użyj [IMetadataTables:: GetString](imetadatatables-getstring-method.md) , aby uzyskać rzeczywistą wartość ciągu kolumny.</span><span class="sxs-lookup"><span data-stu-id="e79c3-145">Use [IMetadataTables::GetString](imetadatatables-getstring-method.md) to get the actual column String value.</span></span> |
| <span data-ttu-id="e79c3-146">`iGUID`(102)</span><span class="sxs-lookup"><span data-stu-id="e79c3-146">`iGUID` (102)</span></span>            | <span data-ttu-id="e79c3-147">Indeks sterty identyfikatora GUID</span><span class="sxs-lookup"><span data-stu-id="e79c3-147">Guid heap index</span></span> | <span data-ttu-id="e79c3-148">*Pval* jest indeksem do sterty identyfikatora GUID.</span><span class="sxs-lookup"><span data-stu-id="e79c3-148">*pVal* is an index into the Guid heap.</span></span> <span data-ttu-id="e79c3-149">Użyj [IMetadataTables:: GetGuid](imetadatatables-getguid-method.md) , aby uzyskać rzeczywistą wartość identyfikatora GUID kolumny.</span><span class="sxs-lookup"><span data-stu-id="e79c3-149">Use [IMetadataTables::GetGuid](imetadatatables-getguid-method.md) to get the actual column Guid value.</span></span> |
| <span data-ttu-id="e79c3-150">`iBLOB`(103)</span><span class="sxs-lookup"><span data-stu-id="e79c3-150">`iBLOB` (103)</span></span>            | <span data-ttu-id="e79c3-151">Indeks sterty obiektu BLOB</span><span class="sxs-lookup"><span data-stu-id="e79c3-151">Blob heap index</span></span> | <span data-ttu-id="e79c3-152">*Pval* jest indeksem do sterty obiektu BLOB.</span><span class="sxs-lookup"><span data-stu-id="e79c3-152">*pVal* is an index into the Blob heap.</span></span> <span data-ttu-id="e79c3-153">Użyj [IMetadataTables:: GetBlob](imetadatatables-getblob-method.md) , aby uzyskać rzeczywistą wartość obiektu BLOB kolumny.</span><span class="sxs-lookup"><span data-stu-id="e79c3-153">Use [IMetadataTables::GetBlob](imetadatatables-getblob-method.md) to get the actual column Blob value.</span></span> |
  
## <a name="requirements"></a><span data-ttu-id="e79c3-154">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e79c3-154">Requirements</span></span>  
 <span data-ttu-id="e79c3-155">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e79c3-155">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e79c3-156">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="e79c3-156">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e79c3-157">**Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="e79c3-157">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e79c3-158">**Wersje .NET Framework**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e79c3-158">**.NET Framework Versions** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e79c3-159">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e79c3-159">See also</span></span>

- [<span data-ttu-id="e79c3-160">IMetaDataTables, interfejs</span><span class="sxs-lookup"><span data-stu-id="e79c3-160">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="e79c3-161">IMetaDataTables2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="e79c3-161">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
