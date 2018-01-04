---
title: "IMetaDataTables — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataTables
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataTables
helpviewer_keywords: IMetaDataTables interface [.NET Framework metadata]
ms.assetid: 31272cce-506a-4f18-bcbf-01ee45e36356
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ff70e99a963c929792a73cefd6e8feaefa8b252e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="imetadatatables-interface"></a><span data-ttu-id="592af-102">IMetaDataTables — Interfejs</span><span class="sxs-lookup"><span data-stu-id="592af-102">IMetaDataTables Interface</span></span>
<span data-ttu-id="592af-103">Udostępnia metody przechowywania i pobierania informacji o metadanych w tabelach.</span><span class="sxs-lookup"><span data-stu-id="592af-103">Provides methods for the storage and retrieval of metadata information in tables.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="592af-104">Metody</span><span class="sxs-lookup"><span data-stu-id="592af-104">Methods</span></span>  
  
|<span data-ttu-id="592af-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="592af-105">Method</span></span>|<span data-ttu-id="592af-106">Opis</span><span class="sxs-lookup"><span data-stu-id="592af-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="592af-107">GetBlob, metoda</span><span class="sxs-lookup"><span data-stu-id="592af-107">GetBlob Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getblob-method.md)|<span data-ttu-id="592af-108">Pobiera wskaźnik do dużego obiektu binarnego (BLOB) pod indeksem określonej kolumny.</span><span class="sxs-lookup"><span data-stu-id="592af-108">Gets a pointer to the binary large object (BLOB) at the specified column index.</span></span>|  
|[<span data-ttu-id="592af-109">GetBlobHeapSize, metoda</span><span class="sxs-lookup"><span data-stu-id="592af-109">GetBlobHeapSize Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getblobheapsize-method.md)|<span data-ttu-id="592af-110">Pobiera rozmiar w bajtach sterty obiektu BLOB.</span><span class="sxs-lookup"><span data-stu-id="592af-110">Gets the size, in bytes, of the BLOB heap.</span></span>|  
|[<span data-ttu-id="592af-111">GetCodedTokenInfo, metoda</span><span class="sxs-lookup"><span data-stu-id="592af-111">GetCodedTokenInfo Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getcodedtokeninfo-method.md)|<span data-ttu-id="592af-112">Pobiera wskaźnik do tablicy tokenów skojarzone z indeks określonego wiersza.</span><span class="sxs-lookup"><span data-stu-id="592af-112">Gets a pointer to an array of tokens associated with the specified row index.</span></span>|  
|[<span data-ttu-id="592af-113">GetColumn, metoda</span><span class="sxs-lookup"><span data-stu-id="592af-113">GetColumn Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getcolumn-method.md)|<span data-ttu-id="592af-114">Pobiera wskaźnik do wartości zawarte w kolumnie pod indeksem określonej kolumny w tabeli w indeksie określonej tabeli.</span><span class="sxs-lookup"><span data-stu-id="592af-114">Gets a pointer to the values contained in the column at the specified column index, in the table at the specified table index.</span></span>|  
|[<span data-ttu-id="592af-115">GetColumnInfo, metoda</span><span class="sxs-lookup"><span data-stu-id="592af-115">GetColumnInfo Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getcolumninfo-method.md)|<span data-ttu-id="592af-116">Pobiera dane o określonej kolumny w określonej tabeli.</span><span class="sxs-lookup"><span data-stu-id="592af-116">Gets data about the specified column in the specified table.</span></span>|  
|[<span data-ttu-id="592af-117">GetGuid, metoda</span><span class="sxs-lookup"><span data-stu-id="592af-117">GetGuid Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getguid-method.md)|<span data-ttu-id="592af-118">Pobiera identyfikator GUID z wiersza pod określonym indeksem.</span><span class="sxs-lookup"><span data-stu-id="592af-118">Gets a GUID from the row at the specified index.</span></span>|  
|[<span data-ttu-id="592af-119">GetGuidHeapSize, metoda</span><span class="sxs-lookup"><span data-stu-id="592af-119">GetGuidHeapSize Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getguidheapsize-method.md)|<span data-ttu-id="592af-120">Pobiera rozmiar w bajtach sterty identyfikatora GUID.</span><span class="sxs-lookup"><span data-stu-id="592af-120">Gets the size, in bytes, of the GUID heap.</span></span>|  
|[<span data-ttu-id="592af-121">GetNextBlob, metoda</span><span class="sxs-lookup"><span data-stu-id="592af-121">GetNextBlob Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnextblob-method.md)|<span data-ttu-id="592af-122">Pobiera indeks następnego obiektu blob w tabeli.</span><span class="sxs-lookup"><span data-stu-id="592af-122">Gets the index of the next BLOB in the table.</span></span>|  
|[<span data-ttu-id="592af-123">GetNextGuid, metoda</span><span class="sxs-lookup"><span data-stu-id="592af-123">GetNextGuid Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnextguid-method.md)|<span data-ttu-id="592af-124">Pobiera indeks następnego wartości identyfikatora GUID w bieżącej kolumny tabeli.</span><span class="sxs-lookup"><span data-stu-id="592af-124">Gets the index of the next GUID value in the current table column.</span></span>|  
|[<span data-ttu-id="592af-125">GetNextString, metoda</span><span class="sxs-lookup"><span data-stu-id="592af-125">GetNextString Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnextstring-method.md)|<span data-ttu-id="592af-126">Pobiera indeks następnego ciągu w bieżącej kolumny tabeli.</span><span class="sxs-lookup"><span data-stu-id="592af-126">Gets the index of the next string in the current table column.</span></span>|  
|[<span data-ttu-id="592af-127">GetNextUserString, metoda</span><span class="sxs-lookup"><span data-stu-id="592af-127">GetNextUserString Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnextuserstring-method.md)|<span data-ttu-id="592af-128">Pobiera indeks wiersza, który zawiera dalej ustalony ciąg w bieżącej kolumny tabeli.</span><span class="sxs-lookup"><span data-stu-id="592af-128">Gets the index of the row that contains the next hard-coded string in the current table column.</span></span>|  
|[<span data-ttu-id="592af-129">GetNumTables, metoda</span><span class="sxs-lookup"><span data-stu-id="592af-129">GetNumTables Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnumtables-method.md)|<span data-ttu-id="592af-130">Pobiera liczbę tabel w zakresie bieżącego `IMetaDataTables` wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="592af-130">Gets the number of tables in the scope of the current `IMetaDataTables` instance.</span></span>|  
|[<span data-ttu-id="592af-131">GetRow, metoda</span><span class="sxs-lookup"><span data-stu-id="592af-131">GetRow Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getrow-method.md)|<span data-ttu-id="592af-132">Pobiera wiersz w indeksie określony wiersz, w tabeli w indeksie określonej tabeli.</span><span class="sxs-lookup"><span data-stu-id="592af-132">Gets the row at the specified row index, in the table at the specified table index.</span></span>|  
|[<span data-ttu-id="592af-133">GetString, metoda</span><span class="sxs-lookup"><span data-stu-id="592af-133">GetString Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getstring-method.md)|<span data-ttu-id="592af-134">Pobiera ciąg pod określonym indeksem z kolumną tabeli w bieżącym zakresie odwołania.</span><span class="sxs-lookup"><span data-stu-id="592af-134">Gets the string at the specified index from the table column in the current reference scope.</span></span>|  
|[<span data-ttu-id="592af-135">GetStringHeapSize, metoda</span><span class="sxs-lookup"><span data-stu-id="592af-135">GetStringHeapSize Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getstringheapsize-method.md)|<span data-ttu-id="592af-136">Pobiera rozmiar w bajtach sterty ciągu.</span><span class="sxs-lookup"><span data-stu-id="592af-136">Gets the size, in bytes, of the string heap.</span></span>|  
|[<span data-ttu-id="592af-137">GetTableIndex, metoda</span><span class="sxs-lookup"><span data-stu-id="592af-137">GetTableIndex Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-gettableindex-method.md)|<span data-ttu-id="592af-138">Pobiera indeks tabeli odwołuje się określony token.</span><span class="sxs-lookup"><span data-stu-id="592af-138">Gets the index for the table referenced by the specified token.</span></span>|  
|[<span data-ttu-id="592af-139">GetTableInfo, metoda</span><span class="sxs-lookup"><span data-stu-id="592af-139">GetTableInfo Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-gettableinfo-method.md)|<span data-ttu-id="592af-140">Pobiera nazwę, rozmiar wiersza, liczbę wierszy, liczby kolumn oraz indeks kolumny klucza tabeli w indeksie określonej tabeli.</span><span class="sxs-lookup"><span data-stu-id="592af-140">Gets the name, row size, number of rows, number of columns, and key column index of the table at the specified table index.</span></span>|  
|[<span data-ttu-id="592af-141">GetUserString, metoda</span><span class="sxs-lookup"><span data-stu-id="592af-141">GetUserString Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getuserstring-method.md)|<span data-ttu-id="592af-142">Pobiera ciąg ustalony pod określonym indeksem w kolumnie ciągu w bieżącym zakresie.</span><span class="sxs-lookup"><span data-stu-id="592af-142">Gets the hard-coded string at the specified index in the string column in the current scope.</span></span>|  
|[<span data-ttu-id="592af-143">GetUserStringHeapSize, metoda</span><span class="sxs-lookup"><span data-stu-id="592af-143">GetUserStringHeapSize Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getuserstringheapsize-method.md)|<span data-ttu-id="592af-144">Pobiera rozmiar w bajtach sterty ciągu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="592af-144">Gets the size, in bytes, of the user string heap.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="592af-145">Wymagania</span><span class="sxs-lookup"><span data-stu-id="592af-145">Requirements</span></span>  
 <span data-ttu-id="592af-146">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="592af-146">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="592af-147">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="592af-147">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="592af-148">**Biblioteka:** używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="592af-148">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="592af-149">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="592af-149">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="592af-150">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="592af-150">See Also</span></span>  
 [<span data-ttu-id="592af-151">Interfejsy metadanych</span><span class="sxs-lookup"><span data-stu-id="592af-151">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
 [<span data-ttu-id="592af-152">IMetaDataTables2, interfejs</span><span class="sxs-lookup"><span data-stu-id="592af-152">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
