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
ms.openlocfilehash: bdb691570a9a2bf7bd2bb21af500b06c10b0bc53
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448524"
---
# <a name="diagnostics-symbol-store-interfaces"></a>Interfejsy magazynu symboli diagnostycznych
W tym temacie opisano niezarządzane interfejsy, które umożliwiają kompilatorowi generowanie informacji o symbolach do użycia przez debuger.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [IBindingDisplay, interfejs](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md)  
 Dostarcza metody, które wyświetlają bieżące informacje o powiązaniu dla działającej aplikacji.  
  
 [IDebugAutoAttach, interfejs](../../../../docs/framework/unmanaged-api/diagnostics/idebugautoattach-interface.md)  
 Definiuje interfejs dla automatycznie dołączanego debugera dla serwera.  
  
 [INotifyConnection2, interfejs](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)  
 Deklaruje metody rejestrowania źródła powiadomień połączenia i wyrejestrowywania go.  
  
 [INotifySink2, interfejs](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)  
 Deklaruje metody powiadamiania o ujściach.  
  
 [INotifySource2, interfejs](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)  
 Deklaruje metodę ustawiania filtrów powiadomień.  
  
 [ISymENCUnmanagedMethod, interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)  
 Zawiera informacje dotyczące funkcji Edytuj i Kontynuuj.  
  
 [ISymUnmanagedAsyncMethod, interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)  
 Ten interfejs jest uzupełnieniem odczytu do [interfejsu ISymUnmanagedAsyncMethodPropertiesWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md).  
  
 [ISymUnmanagedAsyncMethodPropertiesWriter, interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)  
 Zezwala na definiowanie opcjonalnych informacji o metodzie asynchronicznej dla symbolu metody. Musi być używana z otwartą metodą (czyli między wywołaniami [metody OpenMethod —](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)i [CloseMethod —](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md)).  
  
 [ISymUnmanagedBinder, interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)  
 Reprezentuje spinacz symboliczny dla niezarządzanego kodu.  
  
 [ISymUnmanagedBinder2, interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)  
 Reprezentuje spinacz symboliczny dla kodu niezarządzanego i rozszerza interfejs `ISymUnmanagedBinder`.  
  
 [ISymUnmanagedBinder3, interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-interface.md)  
 Reprezentuje spinacz symboliczny dla kodu niezarządzanego i rozszerza interfejs `ISymUnmanagedBinder`.  
  
 [ISymUnmanagedConstant, interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-interface.md)  
 Zapewnia dostęp do stałych niezarządzanych.  
  
 [ISymUnmanagedDispose, interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddispose-interface.md)  
 Usuwa niezarządzane zasoby.  
  
 [ISymUnmanagedDocument, interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)  
 Reprezentuje dokument, do którego odwołuje się magazyn symboli.  
  
 [ISymUnmanagedDocumentWriter, interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocumentwriter-interface.md)  
 Zapewnia metody zapisu do dokumentu, do którego odwołuje się magazyn symboli.  
  
 [ISymUnmanagedENCUpdate, interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-interface.md)  
 Zapewnia metody funkcji Edytuj i Kontynuuj.  
  
 [ISymUnmanagedMethod, interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)  
 Reprezentuje metodę w magazynie symboli.  
  
 [ISymUnmanagedNamespace, interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md)  
 Reprezentuje przestrzeń nazw.  
  
 [ISymUnmanagedReader, interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)  
 Reprezentuje czytnik symboli, który zapewnia dostęp do dokumentów, metod i zmiennych w magazynie symboli.  
  
 [ISymUnmanagedReader2, interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-interface.md)  
 Pobiera metodę czytnika symboli, używając tokenu metody oraz numeru wersji Edit-and-Copy.  
  
 [ISymUnmanagedReaderSymbolSearchInfo, interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreadersymbolsearchinfo-interface.md)  
 Dostarcza metody, które pobierają informacje o wyszukiwaniu symboli.  
  
 [ISymUnmanagedScope, interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)  
 Reprezentuje zakres leksykalny w ramach metody.  
  
 [ISymUnmanagedScope2, interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-interface.md)  
 Reprezentuje zakres leksykalny w ramach metody i rozszerza interfejs `ISymUnmanagedScope` przy użyciu metod, które pobierają informacje o stałych zdefiniowanych w zakresie.  
  
 [ISymUnmanagedSourceServerModule, interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsourceservermodule-interface.md)  
 Zapewnia dane serwera źródłowego dla modułu.  
  
 [ISymUnmanagedSymbolSearchInfo, interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-interface.md)  
 Dostarcza metody, które pobierają informacje o ścieżce wyszukiwania.  
  
 [ISymUnmanagedVariable, interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)  
 Reprezentuje zmienną, taką jak parametr, zmienna lokalna lub pole.  
  
 [ISymUnmanagedWriter, interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 Reprezentuje moduł zapisujący symboli i zawiera metody definiowania dokumentów, punktów sekwencji, zakresów leksykalnych i zmiennych.  
  
 [ISymUnmanagedWriter2, interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-interface.md)  
 Reprezentuje moduł zapisujący symboli i zawiera metody definiowania dokumentów, punktów sekwencji, zakresów leksykalnych i zmiennych. Rozszerza interfejs `ISymUnmanagedWriter`.  
  
 [ISymUnmanagedWriter3, interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)  
 Reprezentuje moduł zapisujący symboli i zawiera metody definiowania dokumentów, punktów sekwencji, zakresów leksykalnych i zmiennych. Rozszerza interfejs `ISymUnmanagedWriter`.  
  
 [ISymUnmanagedWriter4, interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter4-interface.md)  
 Interfejs ISymUnmanagedWriter4.  
  
 [ISymUnmanagedWriter5, interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-interface.md)  
 Interfejs ISymUnmanagedWriter5.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Wyliczenia magazynu symboli diagnostycznych](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)  
  
 [Struktury magazynu symboli diagnostycznych](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)  
  
 [Debugowanie](../../../../docs/framework/unmanaged-api/debugging/index.md)
