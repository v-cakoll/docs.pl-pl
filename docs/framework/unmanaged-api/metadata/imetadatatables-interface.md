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
# <a name="imetadatatables-interface"></a>IMetaDataTables — Interfejs
Zawiera metody służące do przechowywania i pobierania informacji o metadanych w tabelach.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetBlob, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getblob-method.md)|Pobiera wskaźnik do dużego obiektu binarnego (BLOB) pod indeksem określonej kolumny.|  
|[GetBlobHeapSize, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getblobheapsize-method.md)|Pobiera rozmiar w bajtach stosu obiektów BLOB.|  
|[GetCodedTokenInfo, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getcodedtokeninfo-method.md)|Pobiera wskaźnik do tablicy tokenów skojarzone z indeksem określony wiersz.|  
|[GetColumn, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getcolumn-method.md)|Pobiera wskaźnik do wartości znajdujących się w kolumnie pod indeksem określonej kolumny w tabeli pod indeksem określonej tabeli.|  
|[GetColumnInfo, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getcolumninfo-method.md)|Pobiera dane o określonej kolumny w określonej tabeli.|  
|[GetGuid, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getguid-method.md)|Pobiera identyfikator GUID z wiersz pod określonym indeksem.|  
|[GetGuidHeapSize, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getguidheapsize-method.md)|Pobiera rozmiar w bajtach sterty identyfikatora GUID.|  
|[GetNextBlob, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnextblob-method.md)|Pobiera indeks następnego obiektu blob w tabeli.|  
|[GetNextGuid, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnextguid-method.md)|Pobiera indeks następnego wartość identyfikatora GUID w bieżącej kolumnie tabeli.|  
|[GetNextString, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnextstring-method.md)|Pobiera indeks następnego ciągu w bieżącej kolumnie tabeli.|  
|[GetNextUserString, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnextuserstring-method.md)|Pobiera indeks wiersza, który zawiera następnego ciągu ustalonych w bieżącej kolumnie tabeli.|  
|[GetNumTables, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnumtables-method.md)|Pobiera liczbę tabel w zakresie bieżącego `IMetaDataTables` wystąpienia.|  
|[GetRow, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getrow-method.md)|Pobiera wiersz indeksu określony wiersz w tabeli pod indeksem określonej tabeli.|  
|[GetString, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getstring-method.md)|Pobiera parametry dla podanego indeksu z kolumną tabeli w bieżącym zakresie odwołania.|  
|[GetStringHeapSize, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getstringheapsize-method.md)|Pobiera rozmiar w bajtach stercie będącej ciągiem tekstowym.|  
|[GetTableIndex, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-gettableindex-method.md)|Pobiera indeks dla tabeli przywoływanej przez określony token.|  
|[GetTableInfo, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-gettableinfo-method.md)|Pobiera nazwę, rozmiar wiersza, liczba wierszy, liczba kolumn, a kolumny klucza indeksu tabeli dla indeksu określonej tabeli.|  
|[GetUserString, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getuserstring-method.md)|Pobiera ciąg ustaloną dla podanego indeksu w kolumnie ciągu w bieżącym zakresie.|  
|[GetUserStringHeapSize, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getuserstringheapsize-method.md)|Pobiera rozmiar w bajtach sterty ciągu użytkownika.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** COR.h  
  
 **Biblioteka:** Używany jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Interfejsy metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [IMetaDataTables2 — Interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
