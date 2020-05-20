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
ms.openlocfilehash: b372021fcda39d9973d96a9c39e93e38617887a6
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615465"
---
# <a name="isymunmanagedreader-interface"></a>ISymUnmanagedReader — Interfejs
Reprezentuje czytnik symboli, który zapewnia dostęp do dokumentów, metod i zmiennych w magazynie symboli.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetDocument, metoda](isymunmanagedreader-getdocument-method.md)|Znajduje dokument.|  
|[GetDocuments, metoda](isymunmanagedreader-getdocuments-method.md)|Zwraca tablicę wszystkich dokumentów zdefiniowanych w magazynie symboli.|  
|[GetDocumentVersion, metoda](isymunmanagedreader-getdocumentversion-method.md)|Pobiera określoną wersję określonego dokumentu.|  
|[GetGlobalVariables, metoda](isymunmanagedreader-getglobalvariables-method.md)|Zwraca wszystkie zmienne globalne.|  
|[GetMethod, metoda](isymunmanagedreader-getmethod-method.md)|Pobiera metodę czytnika symboli, używając tokenu metody.|  
|[GetMethodByVersion, metoda](isymunmanagedreader-getmethodbyversion-method.md)|Pobiera metodę czytnika symboli, uwzględniając token metody i numer wersji do edycji i kopiowania.|  
|[GetMethodFromDocumentPosition, metoda](isymunmanagedreader-getmethodfromdocumentposition-method.md)|Zwraca metodę, która zawiera punkt przerwania w podanym miejscu w dokumencie.|  
|[GetMethodsFromDocumentPosition, metoda](isymunmanagedreader-getmethodsfromdocumentposition-method.md)|Zwraca tablicę metod, z których każdy zawiera punkt przerwania w podanym miejscu w dokumencie.|  
|[GetMethodVersion, metoda](isymunmanagedreader-getmethodversion-method.md)|Pobiera wersję metody.|  
|[GetNamespaces, metoda](isymunmanagedreader-getnamespaces-method.md)|Pobiera przestrzenie nazw zdefiniowane w globalnym zakresie w ramach tego magazynu symboli.|  
|[GetSymAttribute, metoda](isymunmanagedreader-getsymattribute-method.md)|Pobiera atrybut niestandardowy na podstawie jego nazwy.|  
|[GetSymbolStoreFileName, metoda](isymunmanagedreader-getsymbolstorefilename-method.md)|Udostępnia nazwę pliku na dysku magazynu symboli.|  
|[GetUserEntryPoint, metoda](isymunmanagedreader-getuserentrypoint-method.md)|Zwraca metodę, która została określona jako punkt wejścia użytkownika dla modułu, jeśli istnieje.|  
|[GetVariables, metoda](isymunmanagedreader-getvariables-method.md)|Zwróć zmienną nielokalną, używając jej elementu nadrzędnego i nazwy.|  
|[Initialize — Metoda](isymunmanagedreader-initialize-method.md)|Inicjuje czytnik symboli z interfejsem importera metadanych, z którym zostanie skojarzony ten czytnik, wraz z nazwą pliku modułu.|  
|[ReplaceSymbolStore, metoda](isymunmanagedreader-replacesymbolstore-method.md)|Zamienia istniejący magazyn symboli na magazyn symboli różnicowych.|  
|[UpdateSymbolStore, metoda](isymunmanagedreader-updatesymbolstore-method.md)|Aktualizuje istniejący magazyn symboli przy użyciu magazynu symboli różnicowych.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Zobacz także

- [Interfejsy magazynu symboli diagnostycznych](diagnostics-symbol-store-interfaces.md)
- [ISymUnmanagedReader2 — Interfejs](isymunmanagedreader2-interface.md)
