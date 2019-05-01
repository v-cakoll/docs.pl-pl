---
title: Dane struktury usługi
ms.date: 03/30/2017
ms.assetid: 2a2c8ddc-4e82-4e7f-a79f-97085c469517
ms.openlocfilehash: 5c65e9d473b5fe3f2b1c29824dcc1151abb0c3f6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61780812"
---
# <a name="service-framework-data"></a>Dane struktury usługi
Ten temat zawiera listę wszystkich wyjątków generowanych przez dane struktury usługi.  
  
## <a name="exception-list"></a>Lista wyjątków  
  
|Kod zasobu|Ciąg zasobu|  
|-------------------|---------------------|  
|AddressingExtensionInBadNS|Określony element w określonej przestrzeni nazw nie jest prawidłowy. Oznacza to, że określony element jest zduplikowany element lub że nie jest niedozwolonym rozszerzeniem ponieważ elementów rozszerzenia nie może znajdować się w przestrzeni nazw adresowania.|  
|BinaryEncoderSessionInvalid|Sesja kodera binarnego jest nieprawidłowa, ponieważ wystąpił błąd podczas dekodowania poprzedniego komunikatu.|  
|CannotDetectAddressingVersion|Nie można wykryć wersji WS-Addressing. EndpointAddress nie rozpoczyna się od elementu.|  
|CouldNotFindNamespaceForPrefix|Określony prefiks jest Brak powiązania przestrzeni nazw w zakresie.|  
|EncoderBadContentType|Nie można przetworzyć do contentType.|  
|EncoderEnvelopeVersionMismatch|Wersja schematu envelope określonego komunikatu przychodzącego jest niezgodny z określonym kodera. Upewnij się, że powiązanie jest skonfigurowane przy użyciu tej samej wersji co oczekiwane komunikaty.|  
|EncoderMessageVersionMismatch|Wersja komunikatu określonego komunikatu wychodzącego jest niezgodny z określonym kodera. Upewnij się, że powiązanie jest skonfigurowane przy użyciu tej samej wersji co komunikat.|  
|ExtraContentIsPresentInFaultDetail|Dodatkowa zawartość Extensible Markup Language znajduje się w błędnym elemencie szczegółowym. Dozwolone jest tylko jeden element.|  
|FilterBadTableType|Obiekt IMessageFilterTable utworzony dla filtru nie może być obiektem lub pochodzić od MessageFilterTable.|  
|FilterTableInvalidForLookup|MessageFilterTable jest uszkodzony. Nie można przeprowadzić żądanego wyszukiwania.|  
|MandatoryHeaderNotUnderstood|Co najmniej wymagana prostego obiektu dostępu protokołu nagłówka bloki była niezrozumiała.|  
|MessageBodyIsStream|Treść komunikatu jest strumień.|  
|MessageBodyIsUnknown|Format treści komunikatu jest nieznany.|  
|MessageBodyReaderInvalidReadState|Określony ReadState czytnika treść komunikatu nie mogą być używane.|  
|MessageTextEncodingNotSupported|Kodowanie określony tekst, który jest używany w formacie wiadomości tekstowej nie jest obsługiwane.|  
|MissingMessageID|Żądanie wiadomości Brak nagłówka MessageID. Nagłówka MessageID jest wymagany do dopasowania odpowiedzi.|  
|MultipleMessageHeaders|Znaleziono więcej niż jeden nagłówek o określonej nazwie i przestrzeni nazw.|  
|MultipleMessageHeadersWithActor|Znaleziono więcej niż jeden nagłówek o określonej nazwie, przestrzeni nazw i ról.|  
|MultipleRelatesToHeaders|Znaleziono więcej niż jeden nagłówka RelatesTo z określonej relacji. Dla każdej relacji jest dozwolony tylko jeden.|  
|QueryFunctionTypeNotSupported|Określony zwrotu typu dla IXsltContextFunction nie jest obsługiwana.|  
|QueryIteratorOutOfScope|Klasa XPathNodeIterator zostały unieważnione. Elementy, które są przekazywane jako argumenty do elementów IXsltContextFunctions XPathNodeIterators są prawidłowe tylko w obrębie funkcji. Nie może być pamięci podręcznej do późniejszego użycia lub zwrócona przez funkcję.|  
|QueryVariableNull|Metody IXsltContextVariable nie może zwracać wartość null.|  
|QueryVariableTypeNotSupported|Określony IXsltContextVariable, typu pochodnego nie jest obsługiwana.|  
|ReceiveShutdownReturnedMessage|Kanał odebrał nieoczekiwany komunikat wejściowy o określonej akcji podczas zamykania. Zamknij kanał, gdy żadne komunikaty wejściowe nie są oczekiwane.|  
|XmlBufferInInvalidState|Wystąpił błąd wewnętrzny. Nie można wykonać operacji ze względu na stan buforu XML.|  
|XmlBufferQuotaExceeded|Rozmiar wymagany do buforowania zawartości Extensible Markup Language przekroczył limit przydziału buforu.|
