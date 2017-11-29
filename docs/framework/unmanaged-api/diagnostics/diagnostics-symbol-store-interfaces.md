---
title: Interfejsy magazynu symboli diagnostycznych
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], debugging
- diagnostics symbol store interfaces [.NET Framework]
- interfaces [.NET Framework], diagnostics symbol store
- unmanaged interfaces [.NET Framework], diagnostics symbol store
- debugging interfaces [.NET Framework]
- interfaces [.NET Framework debugging]
ms.assetid: f96987d5-e6a5-478b-ac5e-302e16545cce
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 50ef54c90609bf8ef1e3a943664daef95f50d926
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="diagnostics-symbol-store-interfaces"></a>Interfejsy magazynu symboli diagnostycznych
W tym temacie opisano niezarządzane interfejsy, umożliwiające kompilatora wygenerować informacje symbol do użycia przez debuger.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [IBindingDisplay — interfejs](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md)  
 Udostępnia metody, które są wyświetlane bieżące informacje o powiązaniu o działającej aplikacji.  
  
 [IDebugAutoAttach — interfejs](../../../../docs/framework/unmanaged-api/diagnostics/idebugautoattach-interface.md)  
 Definiuje interfejs dla dołączania automatycznie wywoływane serwera debugera.  
  
 [INotifyConnection2 — interfejs](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)  
 Deklaruje metody rejestrowanie i wyrejestrowywanie źródła powiadomień połączenia.  
  
 [INotifySink2 — interfejs](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)  
 Deklaruje metody do odbioru powiadomienia.  
  
 [INotifySource2 — interfejs](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)  
 Deklaruje metody filtry powiadomień.  
  
 [ISymENCUnmanagedMethod — interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)  
 Informacje dotyczące funkcji Edytuj i Kontynuuj.  
  
 [Isymunmanagedasyncmethod — interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)  
 Ten interfejs jest uzupełnienie odczytu [isymunmanagedasyncmethodpropertieswriter — interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md).  
  
 [Isymunmanagedasyncmethodpropertieswriter — interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)  
 Pozwala na określenie informacji o metodzie async opcjonalne na symbol — metoda. Należy użyć z metodą otwarty (to znaczy między wywołań [OpenMethod — metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)i [CloseMethod — metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md)).  
  
 [ISymUnmanagedBinder — interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)  
 Reprezentuje integrator symbol dla kodu niezarządzanego.  
  
 [ISymUnmanagedBinder2 — interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)  
 Reprezentuje integrator symbol dla niezarządzanego kodu i rozszerza `ISymUnmanagedBinder` interfejsu.  
  
 [ISymUnmanagedBinder3 — interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-interface.md)  
 Reprezentuje integrator symbol dla niezarządzanego kodu i rozszerza `ISymUnmanagedBinder` interfejsu.  
  
 [ISymUnmanagedConstant — interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-interface.md)  
 Zapewnia dostęp do niezarządzanego stałe.  
  
 [ISymUnmanagedDispose — interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddispose-interface.md)  
 Usuwa zasoby niezarządzane.  
  
 [ISymUnmanagedDocument — interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)  
 Reprezentuje dokument odwołuje się magazynu symboli.  
  
 [ISymUnmanagedDocumentWriter — interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocumentwriter-interface.md)  
 Udostępnia metody do zapisywania dokumentu odwołuje się magazynu symboli.  
  
 [ISymUnmanagedENCUpdate — interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-interface.md)  
 Udostępnia metody dla funkcji Edytuj i Kontynuuj.  
  
 [ISymUnmanagedMethod — interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)  
 Reprezentuje metodę w magazynie symboli.  
  
 [ISymUnmanagedNamespace — interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md)  
 Reprezentuje przestrzeni nazw.  
  
 [ISymUnmanagedReader — interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)  
 Reprezentuje czytnika symboli, która zapewnia dostęp do dokumentów, metod i zmiennych w magazynie symboli.  
  
 [ISymUnmanagedReader2 — interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-interface.md)  
 Pobiera metodę czytnika symboli podany token metody i numer wersji edycji i kopii.  
  
 [ISymUnmanagedReaderSymbolSearchInfo — interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreadersymbolsearchinfo-interface.md)  
 Udostępnia metody, które zawierają informacje o wyszukiwaniu symboli.  
  
 [ISymUnmanagedScope — interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)  
 Reprezentuje leksykalne zakresu w metodzie.  
  
 [ISymUnmanagedScope2 — interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-interface.md)  
 Reprezentuje leksykalne zakresu w metodzie i rozszerza `ISymUnmanagedScope` interfejs za pomocą metody pobierające informacje o stałych zdefiniowana w zakresie.  
  
 [ISymUnmanagedSourceServerModule — interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsourceservermodule-interface.md)  
 Udostępnia dane z serwera źródłowego dla modułu.  
  
 [ISymUnmanagedSymbolSearchInfo — interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-interface.md)  
 Udostępnia metody, które zawierają informacje o ścieżce wyszukiwania.  
  
 [ISymUnmanagedVariable — interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)  
 Reprezentuje zmienną, np. parametr, lokalnej zmiennej lub pola.  
  
 [ISymUnmanagedWriter — interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 Reprezentuje edytor symboli i udostępnia metody, aby zdefiniować dokumenty, punkty sekwencji leksykalne zakresy i zmienne.  
  
 [ISymUnmanagedWriter2 — interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-interface.md)  
 Reprezentuje edytor symboli i udostępnia metody, aby zdefiniować dokumenty, punkty sekwencji leksykalne zakresy i zmienne. Rozszerza `ISymUnmanagedWriter` interfejsu.  
  
 [ISymUnmanagedWriter3 — interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)  
 Reprezentuje edytor symboli i udostępnia metody, aby zdefiniować dokumenty, punkty sekwencji leksykalne zakresy i zmienne. Rozszerza `ISymUnmanagedWriter` interfejsu.  
  
 [Isymunmanagedwriter4 — interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter4-interface.md)  
 Isymunmanagedwriter4 — interfejs.  
  
 [Isymunmanagedwriter5 — interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-interface.md)  
 Isymunmanagedwriter5 — interfejs.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Wyliczenia magazynu symboli diagnostycznych](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)  
  
 [Struktury magazynu symboli diagnostycznych](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)  
  
 [Debugowanie](../../../../docs/framework/unmanaged-api/debugging/index.md)
