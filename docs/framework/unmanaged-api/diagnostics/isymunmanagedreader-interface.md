---
title: ISymUnmanagedReader — Interfejs
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader
helpviewer_keywords:
- ISymUnmanagedReader interface [.NET Framework debugging]
ms.assetid: aa3cc15d-058e-4e6f-b03e-39569646ba47
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0782533f773b69eeeb0b89175e5b22c61e822ed9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59147215"
---
# <a name="isymunmanagedreader-interface"></a>ISymUnmanagedReader — Interfejs
Reprezentuje czytnik symbolu, który zapewnia dostęp do dokumentów, metod i zmiennych w magazynie symboli.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetDocument, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getdocument-method.md)|Umożliwia znalezienie dokumentu.|  
|[GetDocuments, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getdocuments-method.md)|Zwraca tablicę wszystkich dokumentów, które są zdefiniowane w magazynie symboli.|  
|[GetDocumentVersion, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getdocumentversion-method.md)|Pobiera określoną wersję określonego dokumentu.|  
|[GetGlobalVariables, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getglobalvariables-method.md)|Zwraca wszystkie zmienne globalne.|  
|[GetMethod, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethod-method.md)|Pobiera metodę czytnika symboli podany token metody.|  
|[GetMethodByVersion, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethodbyversion-method.md)|Pobiera metodę czytnika symboli podany token metody i numeru wersji edycji i kopiowania.|  
|[GetMethodFromDocumentPosition, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethodfromdocumentposition-method.md)|Zwraca metodę, która zawiera punkt przerwania na pozycji w dokumencie.|  
|[GetMethodsFromDocumentPosition, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethodsfromdocumentposition-method.md)|Zwraca tablicę z metod, z których każdy zawiera punkt przerwania na pozycji w dokumencie.|  
|[GetMethodVersion, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethodversion-method.md)|Pobiera wersję metody.|  
|[GetNamespaces, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getnamespaces-method.md)|Pobiera przestrzenie nazw zdefiniowane w zakresie globalnym, w tym magazynie symboli.|  
|[GetSymAttribute, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getsymattribute-method.md)|Pobiera atrybut niestandardowy na podstawie jego nazwy.|  
|[GetSymbolStoreFileName, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getsymbolstorefilename-method.md)|Zawiera nazwę pliku na dysku w magazynie symboli.|  
|[GetUserEntryPoint, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getuserentrypoint-method.md)|Zwraca metodę, która została określona jako punkt wejścia użytkownika dla modułu, jeśli istnieje.|  
|[GetVariables, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getvariables-method.md)|Zwracają zmienną inną niż lokalna, biorąc pod uwagę jej nadrzędnej i nazwę.|  
|[Initialize, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-initialize-method.md)|Inicjuje czytnika symboli z interfejsem importera metadanych, które ten czytnik będzie skojarzona, wraz z nazwą pliku modułu.|  
|[ReplaceSymbolStore, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-replacesymbolstore-method.md)|Zamienia istniejący magazyn symboli w magazynie symboli delta.|  
|[UpdateSymbolStore, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md)|Aktualizuje istniejący magazyn symboli w magazynie symboli delta.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Zobacz także

- [Interfejsy magazynu symboli diagnostycznych](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [ISymUnmanagedReader2 — Interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-interface.md)
