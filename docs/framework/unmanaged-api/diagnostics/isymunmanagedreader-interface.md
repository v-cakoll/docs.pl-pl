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
ms.openlocfilehash: 7ae978f5d2c9f7e90f4549c15a3935b441eabf04
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74434009"
---
# <a name="isymunmanagedreader-interface"></a>ISymUnmanagedReader — Interfejs
Reprezentuje czytnik symboli, który zapewnia dostęp do dokumentów, metod i zmiennych w magazynie symboli.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetDocument, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getdocument-method.md)|Znajduje dokument.|  
|[GetDocuments, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getdocuments-method.md)|Zwraca tablicę wszystkich dokumentów zdefiniowanych w magazynie symboli.|  
|[GetDocumentVersion, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getdocumentversion-method.md)|Pobiera określoną wersję określonego dokumentu.|  
|[GetGlobalVariables, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getglobalvariables-method.md)|Zwraca wszystkie zmienne globalne.|  
|[GetMethod, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethod-method.md)|Pobiera metodę czytnika symboli, używając tokenu metody.|  
|[GetMethodByVersion, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethodbyversion-method.md)|Pobiera metodę czytnika symboli, uwzględniając token metody i numer wersji do edycji i kopiowania.|  
|[GetMethodFromDocumentPosition, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethodfromdocumentposition-method.md)|Zwraca metodę, która zawiera punkt przerwania w podanym miejscu w dokumencie.|  
|[GetMethodsFromDocumentPosition, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethodsfromdocumentposition-method.md)|Zwraca tablicę metod, z których każdy zawiera punkt przerwania w podanym miejscu w dokumencie.|  
|[GetMethodVersion, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethodversion-method.md)|Pobiera wersję metody.|  
|[GetNamespaces, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getnamespaces-method.md)|Pobiera przestrzenie nazw zdefiniowane w globalnym zakresie w ramach tego magazynu symboli.|  
|[GetSymAttribute, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getsymattribute-method.md)|Pobiera atrybut niestandardowy na podstawie jego nazwy.|  
|[GetSymbolStoreFileName, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getsymbolstorefilename-method.md)|Udostępnia nazwę pliku na dysku magazynu symboli.|  
|[GetUserEntryPoint, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getuserentrypoint-method.md)|Zwraca metodę, która została określona jako punkt wejścia użytkownika dla modułu, jeśli istnieje.|  
|[GetVariables, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getvariables-method.md)|Zwróć zmienną nielokalną, używając jej elementu nadrzędnego i nazwy.|  
|[Initialize, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-initialize-method.md)|Inicjuje czytnik symboli z interfejsem importera metadanych, z którym zostanie skojarzony ten czytnik, wraz z nazwą pliku modułu.|  
|[ReplaceSymbolStore, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-replacesymbolstore-method.md)|Zamienia istniejący magazyn symboli na magazyn symboli różnicowych.|  
|[UpdateSymbolStore, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md)|Aktualizuje istniejący magazyn symboli przy użyciu magazynu symboli różnicowych.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Zobacz także

- [Interfejsy magazynu symboli diagnostycznych](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [ISymUnmanagedReader2, interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-interface.md)
