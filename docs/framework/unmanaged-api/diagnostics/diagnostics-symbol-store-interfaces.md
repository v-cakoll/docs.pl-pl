---
title: Interfejsy magazynu symboli diagnostycznych
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], debugging
- diagnostics symbol store interfaces [.NET Framework]
- interfaces [.NET Framework], diagnostics symbol store
- unmanaged interfaces [.NET Framework], diagnostics symbol store
- debugging interfaces [.NET Framework]
- interfaces [.NET Framework debugging]
ms.assetid: f96987d5-e6a5-478b-ac5e-302e16545cce
ms.openlocfilehash: 044ed5e08a85442c5a73c123cf51529d2fd3f1fc
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/16/2020
ms.locfileid: "83442179"
---
# <a name="diagnostics-symbol-store-interfaces"></a>Interfejsy magazynu symboli diagnostycznych
W tym temacie opisano niezarządzane interfejsy, które umożliwiają kompilatorowi generowanie informacji o symbolach do użycia przez debuger.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [IBindingDisplay — Interfejs](ibindingdisplay-interface.md)  
 Dostarcza metody, które wyświetlają bieżące informacje o powiązaniu dla działającej aplikacji.  
  
 [IDebugAutoAttach — Interfejs](idebugautoattach-interface.md)  
 Definiuje interfejs dla automatycznie dołączanego debugera dla serwera.  
  
 [INotifyConnection2 — Interfejs](inotifyconnection2-interface.md)  
 Deklaruje metody rejestrowania źródła powiadomień połączenia i wyrejestrowywania go.  
  
 [INotifySink2 — Interfejs](inotifysink2-interface.md)  
 Deklaruje metody powiadamiania o ujściach.  
  
 [INotifySource2 — Interfejs](inotifysource2-interface.md)  
 Deklaruje metodę ustawiania filtrów powiadomień.  
  
 [ISymENCUnmanagedMethod — Interfejs](isymencunmanagedmethod-interface.md)  
 Zawiera informacje dotyczące funkcji Edytuj i Kontynuuj.  
  
 [ISymUnmanagedAsyncMethod — Interfejs](isymunmanagedasyncmethod-interface.md)  
 Ten interfejs jest uzupełnieniem odczytu do [interfejsu ISymUnmanagedAsyncMethodPropertiesWriter](isymunmanagedasyncmethodpropertieswriter-interface.md).  
  
 [ISymUnmanagedAsyncMethodPropertiesWriter — Interfejs](isymunmanagedasyncmethodpropertieswriter-interface.md)  
 Zezwala na definiowanie opcjonalnych informacji o metodzie asynchronicznej dla symbolu metody. Musi być używana z otwartą metodą (czyli między wywołaniami [metody OpenMethod —](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)i [CloseMethod —](isymunmanagedwriter-closemethod-method.md)).  
  
 [ISymUnmanagedBinder — Interfejs](isymunmanagedbinder-interface.md)  
 Reprezentuje spinacz symboliczny dla niezarządzanego kodu.  
  
 [ISymUnmanagedBinder2, interfejs](isymunmanagedbinder2-interface.md)  
 Reprezentuje segregator symboliczny dla kodu niezarządzanego i rozszerza `ISymUnmanagedBinder` interfejs.  
  
 [ISymUnmanagedBinder3 — Interfejs](isymunmanagedbinder3-interface.md)  
 Reprezentuje segregator symboliczny dla kodu niezarządzanego i rozszerza `ISymUnmanagedBinder` interfejs.  
  
 [ISymUnmanagedConstant — Interfejs](isymunmanagedconstant-interface.md)  
 Zapewnia dostęp do stałych niezarządzanych.  
  
 [ISymUnmanagedDispose — Interfejs](isymunmanageddispose-interface.md)  
 Usuwa niezarządzane zasoby.  
  
 [ISymUnmanagedDocument, interfejs](isymunmanageddocument-interface.md)  
 Reprezentuje dokument, do którego odwołuje się magazyn symboli.  
  
 [ISymUnmanagedDocumentWriter, interfejs](isymunmanageddocumentwriter-interface.md)  
 Zapewnia metody zapisu do dokumentu, do którego odwołuje się magazyn symboli.  
  
 [ISymUnmanagedENCUpdate, interfejs](isymunmanagedencupdate-interface.md)  
 Zapewnia metody funkcji Edytuj i Kontynuuj.  
  
 [ISymUnmanagedMethod — Interfejs](isymunmanagedmethod-interface.md)  
 Reprezentuje metodę w magazynie symboli.  
  
 [ISymUnmanagedNamespace, interfejs](isymunmanagednamespace-interface.md)  
 Reprezentuje przestrzeń nazw.  
  
 [ISymUnmanagedReader — Interfejs](isymunmanagedreader-interface.md)  
 Reprezentuje czytnik symboli, który zapewnia dostęp do dokumentów, metod i zmiennych w magazynie symboli.  
  
 [ISymUnmanagedReader2 — Interfejs](isymunmanagedreader2-interface.md)  
 Pobiera metodę czytnika symboli, używając tokenu metody oraz numeru wersji Edit-and-Copy.  
  
 [ISymUnmanagedReaderSymbolSearchInfo — Interfejs](isymunmanagedreadersymbolsearchinfo-interface.md)  
 Dostarcza metody, które pobierają informacje o wyszukiwaniu symboli.  
  
 [ISymUnmanagedScope — Interfejs](isymunmanagedscope-interface.md)  
 Reprezentuje zakres leksykalny w ramach metody.  
  
 [ISymUnmanagedScope2, interfejs](isymunmanagedscope2-interface.md)  
 Reprezentuje zakres leksykalny w ramach metody i rozszerza `ISymUnmanagedScope` interfejs przy użyciu metod, które pobierają informacje o stałych zdefiniowanych w zakresie.  
  
 [ISymUnmanagedSourceServerModule — Interfejs](isymunmanagedsourceservermodule-interface.md)  
 Zapewnia dane serwera źródłowego dla modułu.  
  
 [ISymUnmanagedSymbolSearchInfo, interfejs](isymunmanagedsymbolsearchinfo-interface.md)  
 Dostarcza metody, które pobierają informacje o ścieżce wyszukiwania.  
  
 [ISymUnmanagedVariable, interfejs](isymunmanagedvariable-interface.md)  
 Reprezentuje zmienną, taką jak parametr, zmienna lokalna lub pole.  
  
 [ISymUnmanagedWriter — Interfejs](isymunmanagedwriter-interface.md)  
 Reprezentuje moduł zapisujący symboli i zawiera metody definiowania dokumentów, punktów sekwencji, zakresów leksykalnych i zmiennych.  
  
 [ISymUnmanagedWriter2 — Interfejs](isymunmanagedwriter2-interface.md)  
 Reprezentuje moduł zapisujący symboli i zawiera metody definiowania dokumentów, punktów sekwencji, zakresów leksykalnych i zmiennych. Rozszerza `ISymUnmanagedWriter` interfejs.  
  
 [ISymUnmanagedWriter3 — Interfejs](isymunmanagedwriter3-interface.md)  
 Reprezentuje moduł zapisujący symboli i zawiera metody definiowania dokumentów, punktów sekwencji, zakresów leksykalnych i zmiennych. Rozszerza `ISymUnmanagedWriter` interfejs.  
  
 [ISymUnmanagedWriter4 — Interfejs](isymunmanagedwriter4-interface.md)  
 Interfejs ISymUnmanagedWriter4.  
  
 [ISymUnmanagedWriter5 — Interfejs](isymunmanagedwriter5-interface.md)  
 Interfejs ISymUnmanagedWriter5.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Wyliczenia magazynu symboli diagnostycznych](diagnostics-symbol-store-enumerations.md)  
  
 [Struktury magazynu symboli diagnostycznych](diagnostics-symbol-store-structures.md)  
  
 [Debugowanie](../debugging/index.md)
