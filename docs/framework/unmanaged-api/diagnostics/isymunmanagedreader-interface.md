---
title: "ISymUnmanagedReader — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedReader
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedReader
helpviewer_keywords: ISymUnmanagedReader interface [.NET Framework debugging]
ms.assetid: aa3cc15d-058e-4e6f-b03e-39569646ba47
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9e8daea11292cb37deb8e956e6a666c14579fbfa
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedreader-interface"></a>ISymUnmanagedReader — Interfejs
Reprezentuje czytnika symboli, która zapewnia dostęp do dokumentów, metod i zmiennych w magazynie symboli.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetDocument, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getdocument-method.md)|Umożliwia znalezienie dokumentu.|  
|[GetDocuments, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getdocuments-method.md)|Zwraca tablicę wszystkich dokumentów, które są zdefiniowane w magazynie symboli.|  
|[GetDocumentVersion, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getdocumentversion-method.md)|Pobiera określoną wersję określonego dokumentu.|  
|[GetGlobalVariables, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getglobalvariables-method.md)|Zwraca wszystkie zmienne globalne.|  
|[GetMethod, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethod-method.md)|Pobiera metodę czytnika symboli podany token metody.|  
|[GetMethodByVersion, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethodbyversion-method.md)|Pobiera metodę czytnika symboli podany token metody i numer wersji edycji i kopii.|  
|[GetMethodFromDocumentPosition, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethodfromdocumentposition-method.md)|Zwraca metodę, która zawiera punkt przerwania w danej pozycji w dokumencie.|  
|[GetMethodsFromDocumentPosition, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethodsfromdocumentposition-method.md)|Zwraca tablicę z metod, z których każdy zawiera punkt przerwania w danej pozycji w dokumencie.|  
|[GetMethodVersion, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethodversion-method.md)|Pobiera wersję metody.|  
|[GetNamespaces, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getnamespaces-method.md)|Pobiera przestrzenie nazw zdefiniowane w zakresie globalnym, w tym magazynie symboli.|  
|[GetSymAttribute, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getsymattribute-method.md)|Pobiera atrybut niestandardowy ustalane na podstawie jego nazwy.|  
|[GetSymbolStoreFileName, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getsymbolstorefilename-method.md)|Zawiera nazwę pliku na dysku magazynu symboli.|  
|[GetUserEntryPoint, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getuserentrypoint-method.md)|Zwraca metodę, która została określona jako punktu wejścia użytkownika dla modułu, jeśli istnieje.|  
|[GetVariables, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getvariables-method.md)|Zwracają zmienną innego niż lokalne jego nadrzędny i nazwę.|  
|[Initialize, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-initialize-method.md)|Inicjuje czytnika symboli z interfejsem importer metadanych, który tego czytnika zostanie skojarzona z, wraz z nazwą modułu.|  
|[ReplaceSymbolStore, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-replacesymbolstore-method.md)|Zamienia istniejący magazyn symbol magazynu symboli delta.|  
|[UpdateSymbolStore, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md)|Aktualizuje istniejący magazyn symbol magazynu symboli delta.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy magazynu symboli diagnostycznych](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [ISymUnmanagedReader2, interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-interface.md)
