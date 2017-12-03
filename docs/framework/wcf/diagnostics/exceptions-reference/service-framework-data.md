---
title: "Dane struktury usługi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2a2c8ddc-4e82-4e7f-a79f-97085c469517
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a7c20da9f4eafa615ff23bad4d78e669a8417464
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="service-framework-data"></a>Dane struktury usługi
W tym temacie wymieniono wszystkie wyjątki generowane przez dane struktury usługi.  
  
## <a name="exception-list"></a>Listy wyjątków  
  
|Kod zasobu|Ciąg zasobu|  
|-------------------|---------------------|  
|AddressingExtensionInBadNS|Określony element w określonej przestrzeni nazw jest nieprawidłowy. Oznacza to, że określony element jest zduplikowany element lub że nie jest nielegalnym rozszerzeniem ponieważ elementów rozszerzeń nie może być w przestrzeni nazw adresowania.|  
|BinaryEncoderSessionInvalid|Sesja kodera binarnego jest nieprawidłowa, ponieważ wystąpił błąd podczas dekodowania poprzedniego komunikatu.|  
|CannotDetectAddressingVersion|Nie można wykryć wersji WS-Addressing. EndpointAddress nie rozpoczyna się od elementu.|  
|CouldNotFindNamespaceForPrefix|Określony prefiks nie zawiera żadnego wiązania przestrzeni nazw w zakresie.|  
|EncoderBadContentType|Nie można przetworzyć do contentType.|  
|EncoderEnvelopeVersionMismatch|Wersja schematu envelope określony komunikat przychodzący nie jest zgodna wskazanego kodera. Upewnij się, że powiązanie jest skonfigurowane przy użyciu tej samej wersji, co oczekiwane komunikaty.|  
|EncoderMessageVersionMismatch|Wersja określonego komunikatu wychodzącego jest niezgodny z określonym kodera. Upewnij się, że powiązanie jest skonfigurowane z tej samej wersji, co komunikat.|  
|ExtraContentIsPresentInFaultDetail|Dodatkowa zawartość Extensible Markup Language znajduje się w błędnym elemencie szczegółowym. Dozwolone jest tylko jeden element.|  
|FilterBadTableType|Obiekt IMessageFilterTable utworzony dla elementu Filter nie może być obiektem lub typ pochodzący od obiektu MessageFilterTable.|  
|FilterTableInvalidForLookup|Obiekt MessageFilterTable jest uszkodzony. Nie można wykonać żądanego wyszukiwania.|  
|MandatoryHeaderNotUnderstood|Co najmniej jednego wymaganego są niezrozumiałe bloków nagłówków protokołu dostępu prostego obiektu.|  
|MessageBodyIsStream|Treść komunikatu jest typu stream.|  
|MessageBodyIsUnknown|Format treści wiadomości jest nieznany.|  
|MessageBodyReaderInvalidReadState|Określony ReadState czytnika treść wiadomości nie mogą być używane.|  
|MessageTextEncodingNotSupported|Kodowanie określony tekst, który jest używany w formacie wiadomości tekstowej nie jest obsługiwane.|  
|MissingMessageID|Żądanie wiadomości Brak nagłówka MessageID. Nagłówka MessageID jest wymagany do dopasowania odpowiedzi.|  
|MultipleMessageHeaders|Znaleziono więcej niż jeden nagłówek o określonej nazwie i przestrzeni nazw.|  
|MultipleMessageHeadersWithActor|Znaleziono więcej niż jeden nagłówek o określonej nazwie, przestrzeni nazw i roli.|  
|MultipleRelatesToHeaders|Znaleziono więcej niż jeden nagłówka RelatesTo z określonej relacji. Dla każdej relacji jest dozwolony tylko jeden.|  
|QueryFunctionTypeNotSupported|Określony zwracany typ funkcji IXsltContextFunction nie jest obsługiwane.|  
|QueryIteratorOutOfScope|Element XPathNodeIterator został unieważniony. Elementy XPathNodeIterators przekazywane jako argumenty do elementów IXsltContextFunctions są prawidłowe tylko w funkcji. Nie może być w pamięci podręcznej do późniejszego użycia ani zwracane przez funkcję.|  
|QueryVariableNull|Metody IXsltContextVariable nie może zwracać wartości null.|  
|QueryVariableTypeNotSupported|Określony IXsltContextVariable, typu pochodnego nie jest obsługiwana.|  
|ReceiveShutdownReturnedMessage|Kanał odebrał nieoczekiwany komunikat wejściowy o określonej akcji podczas zamykania. Zamknij kanał, gdy żadne komunikaty wejściowe nie są oczekiwane.|  
|XmlBufferInInvalidState|Wystąpił błąd wewnętrzny. Nie można wykonać operacji z powodu stan buforu XML.|  
|XmlBufferQuotaExceeded|Rozmiar wymagany do buforowania zawartości Extensible Markup Language przekracza limit przydziału buforu.|
