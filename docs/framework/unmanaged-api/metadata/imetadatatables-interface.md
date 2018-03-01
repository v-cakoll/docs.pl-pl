---
title: "IMetaDataTables — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: ff70e99a963c929792a73cefd6e8feaefa8b252e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="imetadatatables-interface"></a>IMetaDataTables — Interfejs
Udostępnia metody przechowywania i pobierania informacji o metadanych w tabelach.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetBlob, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getblob-method.md)|Pobiera wskaźnik do dużego obiektu binarnego (BLOB) pod indeksem określonej kolumny.|  
|[GetBlobHeapSize, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getblobheapsize-method.md)|Pobiera rozmiar w bajtach sterty obiektu BLOB.|  
|[GetCodedTokenInfo, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getcodedtokeninfo-method.md)|Pobiera wskaźnik do tablicy tokenów skojarzone z indeks określonego wiersza.|  
|[GetColumn, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getcolumn-method.md)|Pobiera wskaźnik do wartości zawarte w kolumnie pod indeksem określonej kolumny w tabeli w indeksie określonej tabeli.|  
|[GetColumnInfo, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getcolumninfo-method.md)|Pobiera dane o określonej kolumny w określonej tabeli.|  
|[GetGuid, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getguid-method.md)|Pobiera identyfikator GUID z wiersza pod określonym indeksem.|  
|[GetGuidHeapSize, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getguidheapsize-method.md)|Pobiera rozmiar w bajtach sterty identyfikatora GUID.|  
|[GetNextBlob, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnextblob-method.md)|Pobiera indeks następnego obiektu blob w tabeli.|  
|[GetNextGuid, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnextguid-method.md)|Pobiera indeks następnego wartości identyfikatora GUID w bieżącej kolumny tabeli.|  
|[GetNextString, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnextstring-method.md)|Pobiera indeks następnego ciągu w bieżącej kolumny tabeli.|  
|[GetNextUserString, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnextuserstring-method.md)|Pobiera indeks wiersza, który zawiera dalej ustalony ciąg w bieżącej kolumny tabeli.|  
|[GetNumTables, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnumtables-method.md)|Pobiera liczbę tabel w zakresie bieżącego `IMetaDataTables` wystąpienia.|  
|[GetRow, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getrow-method.md)|Pobiera wiersz w indeksie określony wiersz, w tabeli w indeksie określonej tabeli.|  
|[GetString, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getstring-method.md)|Pobiera ciąg pod określonym indeksem z kolumną tabeli w bieżącym zakresie odwołania.|  
|[GetStringHeapSize, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getstringheapsize-method.md)|Pobiera rozmiar w bajtach sterty ciągu.|  
|[GetTableIndex, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-gettableindex-method.md)|Pobiera indeks tabeli odwołuje się określony token.|  
|[GetTableInfo, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-gettableinfo-method.md)|Pobiera nazwę, rozmiar wiersza, liczbę wierszy, liczby kolumn oraz indeks kolumny klucza tabeli w indeksie określonej tabeli.|  
|[GetUserString, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getuserstring-method.md)|Pobiera ciąg ustalony pod określonym indeksem w kolumnie ciągu w bieżącym zakresie.|  
|[GetUserStringHeapSize, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getuserstringheapsize-method.md)|Pobiera rozmiar w bajtach sterty ciągu użytkownika.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor.h  
  
 **Biblioteka:** używany jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
 [IMetaDataTables2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
