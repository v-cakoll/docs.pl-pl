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
ms.openlocfilehash: 17305f2c088dd6f479da4c823d3db0fd50c0b3d7
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74443218"
---
# <a name="imetadatatables-interface"></a>IMetaDataTables — Interfejs
Zapewnia metody przechowywania i pobierania informacji o metadanych w tabelach.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetBlob, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getblob-method.md)|Pobiera wskaźnik do dużego obiektu binarnego (BLOB) w określonym indeksie kolumny.|  
|[GetBlobHeapSize, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getblobheapsize-method.md)|Pobiera rozmiar (w bajtach) sterty obiektu BLOB.|  
|[GetCodedTokenInfo, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getcodedtokeninfo-method.md)|Pobiera wskaźnik do tablicy tokenów skojarzonych z określonym indeksem wiersza.|  
|[GetColumn, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getcolumn-method.md)|Pobiera wskaźnik do wartości zawartych w kolumnie w określonym indeksie kolumny w tabeli w określonym indeksie tabeli.|  
|[GetColumnInfo, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getcolumninfo-method.md)|Pobiera dane dotyczące określonej kolumny w określonej tabeli.|  
|[GetGuid, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getguid-method.md)|Pobiera identyfikator GUID z wiersza o określonym indeksie.|  
|[GetGuidHeapSize, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getguidheapsize-method.md)|Pobiera rozmiar sterty identyfikatora GUID w bajtach.|  
|[GetNextBlob, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnextblob-method.md)|Pobiera indeks następnego obiektu BLOB w tabeli.|  
|[GetNextGuid, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnextguid-method.md)|Pobiera indeks następnej wartości identyfikatora GUID z bieżącej kolumny tabeli.|  
|[GetNextString, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnextstring-method.md)|Pobiera indeks następnego ciągu w bieżącej kolumnie tabeli.|  
|[GetNextUserString, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnextuserstring-method.md)|Pobiera indeks wiersza, który zawiera następny zakodowany ciąg w bieżącej kolumnie tabeli.|  
|[GetNumTables, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnumtables-method.md)|Pobiera liczbę tabel w zakresie bieżącego wystąpienia `IMetaDataTables`.|  
|[GetRow, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getrow-method.md)|Pobiera wiersz o określonym indeksie wiersza w tabeli w określonym indeksie tabeli.|  
|[GetString, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getstring-method.md)|Pobiera ciąg o określonym indeksie z kolumny tabeli w bieżącym zakresie odwołania.|  
|[GetStringHeapSize, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getstringheapsize-method.md)|Pobiera rozmiar sterty ciągu w bajtach.|  
|[GetTableIndex, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-gettableindex-method.md)|Pobiera indeks tabeli, do której odwołuje się określony token.|  
|[GetTableInfo, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-gettableinfo-method.md)|Pobiera nazwę, rozmiar wiersza, liczbę wierszy, liczbę kolumn i indeks kolumny klucza tabeli w określonym indeksie tabeli.|  
|[GetUserString, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getuserstring-method.md)|Pobiera zakodowany ciąg o określonym indeksie w kolumnie ciąg w bieżącym zakresie.|  
|[GetUserStringHeapSize, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getuserstringheapsize-method.md)|Pobiera rozmiar sterty ciągu użytkownika w bajtach.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor. h  
  
 **Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Interfejsy metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [IMetaDataTables2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
