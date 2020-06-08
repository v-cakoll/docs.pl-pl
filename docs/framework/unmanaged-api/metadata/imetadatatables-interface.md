---
title: IMetaDataTables — Interfejs
ms.date: 03/30/2017
api_name:
- IMetaDataTables
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables
helpviewer_keywords:
- IMetaDataTables interface [.NET Framework metadata]
ms.assetid: 31272cce-506a-4f18-bcbf-01ee45e36356
topic_type:
- apiref
ms.openlocfilehash: 2105033e684ec172e24adfb14bcab7668b388af3
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501124"
---
# <a name="imetadatatables-interface"></a><span data-ttu-id="561bc-102">IMetaDataTables — Interfejs</span><span class="sxs-lookup"><span data-stu-id="561bc-102">IMetaDataTables Interface</span></span>
<span data-ttu-id="561bc-103">Zapewnia metody przechowywania i pobierania informacji o metadanych w tabelach.</span><span class="sxs-lookup"><span data-stu-id="561bc-103">Provides methods for the storage and retrieval of metadata information in tables.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="561bc-104">Metody</span><span class="sxs-lookup"><span data-stu-id="561bc-104">Methods</span></span>  
  
|<span data-ttu-id="561bc-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="561bc-105">Method</span></span>|<span data-ttu-id="561bc-106">Opis</span><span class="sxs-lookup"><span data-stu-id="561bc-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="561bc-107">GetBlob — Metoda</span><span class="sxs-lookup"><span data-stu-id="561bc-107">GetBlob Method</span></span>](imetadatatables-getblob-method.md)|<span data-ttu-id="561bc-108">Pobiera wskaźnik do dużego obiektu binarnego (BLOB) w określonym indeksie kolumny.</span><span class="sxs-lookup"><span data-stu-id="561bc-108">Gets a pointer to the binary large object (BLOB) at the specified column index.</span></span>|  
|[<span data-ttu-id="561bc-109">GetBlobHeapSize — Metoda</span><span class="sxs-lookup"><span data-stu-id="561bc-109">GetBlobHeapSize Method</span></span>](imetadatatables-getblobheapsize-method.md)|<span data-ttu-id="561bc-110">Pobiera rozmiar (w bajtach) sterty obiektu BLOB.</span><span class="sxs-lookup"><span data-stu-id="561bc-110">Gets the size, in bytes, of the BLOB heap.</span></span>|  
|[<span data-ttu-id="561bc-111">GetCodedTokenInfo — Metoda</span><span class="sxs-lookup"><span data-stu-id="561bc-111">GetCodedTokenInfo Method</span></span>](imetadatatables-getcodedtokeninfo-method.md)|<span data-ttu-id="561bc-112">Pobiera wskaźnik do tablicy tokenów skojarzonych z określonym indeksem wiersza.</span><span class="sxs-lookup"><span data-stu-id="561bc-112">Gets a pointer to an array of tokens associated with the specified row index.</span></span>|  
|[<span data-ttu-id="561bc-113">GetColumn — Metoda</span><span class="sxs-lookup"><span data-stu-id="561bc-113">GetColumn Method</span></span>](imetadatatables-getcolumn-method.md)|<span data-ttu-id="561bc-114">Pobiera wskaźnik do wartości zawartych w kolumnie w określonym indeksie kolumny w tabeli w określonym indeksie tabeli.</span><span class="sxs-lookup"><span data-stu-id="561bc-114">Gets a pointer to the values contained in the column at the specified column index, in the table at the specified table index.</span></span>|  
|[<span data-ttu-id="561bc-115">GetColumnInfo — Metoda</span><span class="sxs-lookup"><span data-stu-id="561bc-115">GetColumnInfo Method</span></span>](imetadatatables-getcolumninfo-method.md)|<span data-ttu-id="561bc-116">Pobiera dane dotyczące określonej kolumny w określonej tabeli.</span><span class="sxs-lookup"><span data-stu-id="561bc-116">Gets data about the specified column in the specified table.</span></span>|  
|[<span data-ttu-id="561bc-117">GetGuid — Metoda</span><span class="sxs-lookup"><span data-stu-id="561bc-117">GetGuid Method</span></span>](imetadatatables-getguid-method.md)|<span data-ttu-id="561bc-118">Pobiera identyfikator GUID z wiersza o określonym indeksie.</span><span class="sxs-lookup"><span data-stu-id="561bc-118">Gets a GUID from the row at the specified index.</span></span>|  
|[<span data-ttu-id="561bc-119">GetGuidHeapSize — Metoda</span><span class="sxs-lookup"><span data-stu-id="561bc-119">GetGuidHeapSize Method</span></span>](imetadatatables-getguidheapsize-method.md)|<span data-ttu-id="561bc-120">Pobiera rozmiar sterty identyfikatora GUID w bajtach.</span><span class="sxs-lookup"><span data-stu-id="561bc-120">Gets the size, in bytes, of the GUID heap.</span></span>|  
|[<span data-ttu-id="561bc-121">GetNextBlob — Metoda</span><span class="sxs-lookup"><span data-stu-id="561bc-121">GetNextBlob Method</span></span>](imetadatatables-getnextblob-method.md)|<span data-ttu-id="561bc-122">Pobiera indeks następnego obiektu BLOB w tabeli.</span><span class="sxs-lookup"><span data-stu-id="561bc-122">Gets the index of the next BLOB in the table.</span></span>|  
|[<span data-ttu-id="561bc-123">GetNextGuid — Metoda</span><span class="sxs-lookup"><span data-stu-id="561bc-123">GetNextGuid Method</span></span>](imetadatatables-getnextguid-method.md)|<span data-ttu-id="561bc-124">Pobiera indeks następnej wartości identyfikatora GUID z bieżącej kolumny tabeli.</span><span class="sxs-lookup"><span data-stu-id="561bc-124">Gets the index of the next GUID value in the current table column.</span></span>|  
|[<span data-ttu-id="561bc-125">GetNextString — Metoda</span><span class="sxs-lookup"><span data-stu-id="561bc-125">GetNextString Method</span></span>](imetadatatables-getnextstring-method.md)|<span data-ttu-id="561bc-126">Pobiera indeks następnego ciągu w bieżącej kolumnie tabeli.</span><span class="sxs-lookup"><span data-stu-id="561bc-126">Gets the index of the next string in the current table column.</span></span>|  
|[<span data-ttu-id="561bc-127">GetNextUserString — Metoda</span><span class="sxs-lookup"><span data-stu-id="561bc-127">GetNextUserString Method</span></span>](imetadatatables-getnextuserstring-method.md)|<span data-ttu-id="561bc-128">Pobiera indeks wiersza, który zawiera następny zakodowany ciąg w bieżącej kolumnie tabeli.</span><span class="sxs-lookup"><span data-stu-id="561bc-128">Gets the index of the row that contains the next hard-coded string in the current table column.</span></span>|  
|[<span data-ttu-id="561bc-129">GetNumTables — Metoda</span><span class="sxs-lookup"><span data-stu-id="561bc-129">GetNumTables Method</span></span>](imetadatatables-getnumtables-method.md)|<span data-ttu-id="561bc-130">Pobiera liczbę tabel w zakresie bieżącego `IMetaDataTables` wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="561bc-130">Gets the number of tables in the scope of the current `IMetaDataTables` instance.</span></span>|  
|[<span data-ttu-id="561bc-131">GetRow — Metoda</span><span class="sxs-lookup"><span data-stu-id="561bc-131">GetRow Method</span></span>](imetadatatables-getrow-method.md)|<span data-ttu-id="561bc-132">Pobiera wiersz o określonym indeksie wiersza w tabeli w określonym indeksie tabeli.</span><span class="sxs-lookup"><span data-stu-id="561bc-132">Gets the row at the specified row index, in the table at the specified table index.</span></span>|  
|[<span data-ttu-id="561bc-133">GetString — Metoda</span><span class="sxs-lookup"><span data-stu-id="561bc-133">GetString Method</span></span>](imetadatatables-getstring-method.md)|<span data-ttu-id="561bc-134">Pobiera ciąg o określonym indeksie z kolumny tabeli w bieżącym zakresie odwołania.</span><span class="sxs-lookup"><span data-stu-id="561bc-134">Gets the string at the specified index from the table column in the current reference scope.</span></span>|  
|[<span data-ttu-id="561bc-135">GetStringHeapSize — Metoda</span><span class="sxs-lookup"><span data-stu-id="561bc-135">GetStringHeapSize Method</span></span>](imetadatatables-getstringheapsize-method.md)|<span data-ttu-id="561bc-136">Pobiera rozmiar sterty ciągu w bajtach.</span><span class="sxs-lookup"><span data-stu-id="561bc-136">Gets the size, in bytes, of the string heap.</span></span>|  
|[<span data-ttu-id="561bc-137">GetTableIndex — Metoda</span><span class="sxs-lookup"><span data-stu-id="561bc-137">GetTableIndex Method</span></span>](imetadatatables-gettableindex-method.md)|<span data-ttu-id="561bc-138">Pobiera indeks tabeli, do której odwołuje się określony token.</span><span class="sxs-lookup"><span data-stu-id="561bc-138">Gets the index for the table referenced by the specified token.</span></span>|  
|[<span data-ttu-id="561bc-139">GetTableInfo — Metoda</span><span class="sxs-lookup"><span data-stu-id="561bc-139">GetTableInfo Method</span></span>](imetadatatables-gettableinfo-method.md)|<span data-ttu-id="561bc-140">Pobiera nazwę, rozmiar wiersza, liczbę wierszy, liczbę kolumn i indeks kolumny klucza tabeli w określonym indeksie tabeli.</span><span class="sxs-lookup"><span data-stu-id="561bc-140">Gets the name, row size, number of rows, number of columns, and key column index of the table at the specified table index.</span></span>|  
|[<span data-ttu-id="561bc-141">GetUserString — Metoda</span><span class="sxs-lookup"><span data-stu-id="561bc-141">GetUserString Method</span></span>](imetadatatables-getuserstring-method.md)|<span data-ttu-id="561bc-142">Pobiera zakodowany ciąg o określonym indeksie w kolumnie ciąg w bieżącym zakresie.</span><span class="sxs-lookup"><span data-stu-id="561bc-142">Gets the hard-coded string at the specified index in the string column in the current scope.</span></span>|  
|[<span data-ttu-id="561bc-143">GetUserStringHeapSize — Metoda</span><span class="sxs-lookup"><span data-stu-id="561bc-143">GetUserStringHeapSize Method</span></span>](imetadatatables-getuserstringheapsize-method.md)|<span data-ttu-id="561bc-144">Pobiera rozmiar sterty ciągu użytkownika w bajtach.</span><span class="sxs-lookup"><span data-stu-id="561bc-144">Gets the size, in bytes, of the user string heap.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="561bc-145">Wymagania</span><span class="sxs-lookup"><span data-stu-id="561bc-145">Requirements</span></span>  
 <span data-ttu-id="561bc-146">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="561bc-146">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="561bc-147">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="561bc-147">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="561bc-148">**Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="561bc-148">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="561bc-149">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="561bc-149">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="561bc-150">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="561bc-150">See also</span></span>

- [<span data-ttu-id="561bc-151">Interfejsy metadanych</span><span class="sxs-lookup"><span data-stu-id="561bc-151">Metadata Interfaces</span></span>](metadata-interfaces.md)
- [<span data-ttu-id="561bc-152">IMetaDataTables2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="561bc-152">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
