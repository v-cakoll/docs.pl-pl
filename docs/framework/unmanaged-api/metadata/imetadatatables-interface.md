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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2b2298e2d67e8a50e11d53d864f0e78f3b549e45
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59131420"
---
# <a name="imetadatatables-interface"></a><span data-ttu-id="d71f6-102">IMetaDataTables — Interfejs</span><span class="sxs-lookup"><span data-stu-id="d71f6-102">IMetaDataTables Interface</span></span>
<span data-ttu-id="d71f6-103">Zawiera metody służące do przechowywania i pobierania informacji o metadanych w tabelach.</span><span class="sxs-lookup"><span data-stu-id="d71f6-103">Provides methods for the storage and retrieval of metadata information in tables.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d71f6-104">Metody</span><span class="sxs-lookup"><span data-stu-id="d71f6-104">Methods</span></span>  
  
|<span data-ttu-id="d71f6-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="d71f6-105">Method</span></span>|<span data-ttu-id="d71f6-106">Opis</span><span class="sxs-lookup"><span data-stu-id="d71f6-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d71f6-107">GetBlob, metoda</span><span class="sxs-lookup"><span data-stu-id="d71f6-107">GetBlob Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getblob-method.md)|<span data-ttu-id="d71f6-108">Pobiera wskaźnik do dużego obiektu binarnego (BLOB) pod indeksem określonej kolumny.</span><span class="sxs-lookup"><span data-stu-id="d71f6-108">Gets a pointer to the binary large object (BLOB) at the specified column index.</span></span>|  
|[<span data-ttu-id="d71f6-109">GetBlobHeapSize, metoda</span><span class="sxs-lookup"><span data-stu-id="d71f6-109">GetBlobHeapSize Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getblobheapsize-method.md)|<span data-ttu-id="d71f6-110">Pobiera rozmiar w bajtach stosu obiektów BLOB.</span><span class="sxs-lookup"><span data-stu-id="d71f6-110">Gets the size, in bytes, of the BLOB heap.</span></span>|  
|[<span data-ttu-id="d71f6-111">GetCodedTokenInfo, metoda</span><span class="sxs-lookup"><span data-stu-id="d71f6-111">GetCodedTokenInfo Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getcodedtokeninfo-method.md)|<span data-ttu-id="d71f6-112">Pobiera wskaźnik do tablicy tokenów skojarzone z indeksem określony wiersz.</span><span class="sxs-lookup"><span data-stu-id="d71f6-112">Gets a pointer to an array of tokens associated with the specified row index.</span></span>|  
|[<span data-ttu-id="d71f6-113">GetColumn, metoda</span><span class="sxs-lookup"><span data-stu-id="d71f6-113">GetColumn Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getcolumn-method.md)|<span data-ttu-id="d71f6-114">Pobiera wskaźnik do wartości znajdujących się w kolumnie pod indeksem określonej kolumny w tabeli pod indeksem określonej tabeli.</span><span class="sxs-lookup"><span data-stu-id="d71f6-114">Gets a pointer to the values contained in the column at the specified column index, in the table at the specified table index.</span></span>|  
|[<span data-ttu-id="d71f6-115">GetColumnInfo, metoda</span><span class="sxs-lookup"><span data-stu-id="d71f6-115">GetColumnInfo Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getcolumninfo-method.md)|<span data-ttu-id="d71f6-116">Pobiera dane o określonej kolumny w określonej tabeli.</span><span class="sxs-lookup"><span data-stu-id="d71f6-116">Gets data about the specified column in the specified table.</span></span>|  
|[<span data-ttu-id="d71f6-117">GetGuid, metoda</span><span class="sxs-lookup"><span data-stu-id="d71f6-117">GetGuid Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getguid-method.md)|<span data-ttu-id="d71f6-118">Pobiera identyfikator GUID z wiersz pod określonym indeksem.</span><span class="sxs-lookup"><span data-stu-id="d71f6-118">Gets a GUID from the row at the specified index.</span></span>|  
|[<span data-ttu-id="d71f6-119">GetGuidHeapSize, metoda</span><span class="sxs-lookup"><span data-stu-id="d71f6-119">GetGuidHeapSize Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getguidheapsize-method.md)|<span data-ttu-id="d71f6-120">Pobiera rozmiar w bajtach sterty identyfikatora GUID.</span><span class="sxs-lookup"><span data-stu-id="d71f6-120">Gets the size, in bytes, of the GUID heap.</span></span>|  
|[<span data-ttu-id="d71f6-121">GetNextBlob, metoda</span><span class="sxs-lookup"><span data-stu-id="d71f6-121">GetNextBlob Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnextblob-method.md)|<span data-ttu-id="d71f6-122">Pobiera indeks następnego obiektu blob w tabeli.</span><span class="sxs-lookup"><span data-stu-id="d71f6-122">Gets the index of the next BLOB in the table.</span></span>|  
|[<span data-ttu-id="d71f6-123">GetNextGuid, metoda</span><span class="sxs-lookup"><span data-stu-id="d71f6-123">GetNextGuid Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnextguid-method.md)|<span data-ttu-id="d71f6-124">Pobiera indeks następnego wartość identyfikatora GUID w bieżącej kolumnie tabeli.</span><span class="sxs-lookup"><span data-stu-id="d71f6-124">Gets the index of the next GUID value in the current table column.</span></span>|  
|[<span data-ttu-id="d71f6-125">GetNextString, metoda</span><span class="sxs-lookup"><span data-stu-id="d71f6-125">GetNextString Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnextstring-method.md)|<span data-ttu-id="d71f6-126">Pobiera indeks następnego ciągu w bieżącej kolumnie tabeli.</span><span class="sxs-lookup"><span data-stu-id="d71f6-126">Gets the index of the next string in the current table column.</span></span>|  
|[<span data-ttu-id="d71f6-127">GetNextUserString, metoda</span><span class="sxs-lookup"><span data-stu-id="d71f6-127">GetNextUserString Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnextuserstring-method.md)|<span data-ttu-id="d71f6-128">Pobiera indeks wiersza, który zawiera następnego ciągu ustalonych w bieżącej kolumnie tabeli.</span><span class="sxs-lookup"><span data-stu-id="d71f6-128">Gets the index of the row that contains the next hard-coded string in the current table column.</span></span>|  
|[<span data-ttu-id="d71f6-129">GetNumTables, metoda</span><span class="sxs-lookup"><span data-stu-id="d71f6-129">GetNumTables Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnumtables-method.md)|<span data-ttu-id="d71f6-130">Pobiera liczbę tabel w zakresie bieżącego `IMetaDataTables` wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="d71f6-130">Gets the number of tables in the scope of the current `IMetaDataTables` instance.</span></span>|  
|[<span data-ttu-id="d71f6-131">GetRow, metoda</span><span class="sxs-lookup"><span data-stu-id="d71f6-131">GetRow Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getrow-method.md)|<span data-ttu-id="d71f6-132">Pobiera wiersz indeksu określony wiersz w tabeli pod indeksem określonej tabeli.</span><span class="sxs-lookup"><span data-stu-id="d71f6-132">Gets the row at the specified row index, in the table at the specified table index.</span></span>|  
|[<span data-ttu-id="d71f6-133">GetString, metoda</span><span class="sxs-lookup"><span data-stu-id="d71f6-133">GetString Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getstring-method.md)|<span data-ttu-id="d71f6-134">Pobiera parametry dla podanego indeksu z kolumną tabeli w bieżącym zakresie odwołania.</span><span class="sxs-lookup"><span data-stu-id="d71f6-134">Gets the string at the specified index from the table column in the current reference scope.</span></span>|  
|[<span data-ttu-id="d71f6-135">GetStringHeapSize, metoda</span><span class="sxs-lookup"><span data-stu-id="d71f6-135">GetStringHeapSize Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getstringheapsize-method.md)|<span data-ttu-id="d71f6-136">Pobiera rozmiar w bajtach stercie będącej ciągiem tekstowym.</span><span class="sxs-lookup"><span data-stu-id="d71f6-136">Gets the size, in bytes, of the string heap.</span></span>|  
|[<span data-ttu-id="d71f6-137">GetTableIndex, metoda</span><span class="sxs-lookup"><span data-stu-id="d71f6-137">GetTableIndex Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-gettableindex-method.md)|<span data-ttu-id="d71f6-138">Pobiera indeks dla tabeli przywoływanej przez określony token.</span><span class="sxs-lookup"><span data-stu-id="d71f6-138">Gets the index for the table referenced by the specified token.</span></span>|  
|[<span data-ttu-id="d71f6-139">GetTableInfo, metoda</span><span class="sxs-lookup"><span data-stu-id="d71f6-139">GetTableInfo Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-gettableinfo-method.md)|<span data-ttu-id="d71f6-140">Pobiera nazwę, rozmiar wiersza, liczba wierszy, liczba kolumn, a kolumny klucza indeksu tabeli dla indeksu określonej tabeli.</span><span class="sxs-lookup"><span data-stu-id="d71f6-140">Gets the name, row size, number of rows, number of columns, and key column index of the table at the specified table index.</span></span>|  
|[<span data-ttu-id="d71f6-141">GetUserString, metoda</span><span class="sxs-lookup"><span data-stu-id="d71f6-141">GetUserString Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getuserstring-method.md)|<span data-ttu-id="d71f6-142">Pobiera ciąg ustaloną dla podanego indeksu w kolumnie ciągu w bieżącym zakresie.</span><span class="sxs-lookup"><span data-stu-id="d71f6-142">Gets the hard-coded string at the specified index in the string column in the current scope.</span></span>|  
|[<span data-ttu-id="d71f6-143">GetUserStringHeapSize, metoda</span><span class="sxs-lookup"><span data-stu-id="d71f6-143">GetUserStringHeapSize Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getuserstringheapsize-method.md)|<span data-ttu-id="d71f6-144">Pobiera rozmiar w bajtach sterty ciągu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="d71f6-144">Gets the size, in bytes, of the user string heap.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d71f6-145">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d71f6-145">Requirements</span></span>  
 <span data-ttu-id="d71f6-146">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d71f6-146">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d71f6-147">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="d71f6-147">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d71f6-148">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d71f6-148">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="d71f6-149">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="d71f6-149">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d71f6-150">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d71f6-150">See also</span></span>

- [<span data-ttu-id="d71f6-151">Interfejsy metadanych</span><span class="sxs-lookup"><span data-stu-id="d71f6-151">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [<span data-ttu-id="d71f6-152">IMetaDataTables2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="d71f6-152">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
