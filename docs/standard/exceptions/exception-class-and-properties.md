---
title: Właściwości i klasy wyjątków
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- exceptions, Exception class
- Exception class
ms.assetid: e2e1f8c4-e7b4-467d-9a66-13c90861221d
ms.openlocfilehash: df05150a5bdd5d24766be252f5cec9a436720d8c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "75708948"
---
# <a name="exception-class-and-properties"></a>Klasa wyjątku i właściwości

Klasa <xref:System.Exception> jest klasą podstawową, z której dziedziczą wyjątki. Na przykład <xref:System.InvalidCastException> hierarchia klas jest następująca:

<xref:System.Object>\
&nbsp;&nbsp;<xref:System.Exception>\
&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.SystemException>\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.InvalidCastException>

Klasa <xref:System.Exception> ma następujące właściwości, które ułatwiają zrozumienie wyjątku.

| Nazwa właściwości | Opis |
| ------------- | ----------- |
| <xref:System.Exception.Data> | A, <xref:System.Collections.IDictionary> który przechowuje dowolne dane w parach klucz wartość. |
| <xref:System.Exception.HelpLink> | Może przechowywać adres URL (lub URN) do pliku pomocy, który zawiera obszerne informacje o przyczynie wyjątku. |
| <xref:System.Exception.InnerException> | Ta właściwość może służyć do tworzenia i zachowywania szereg wyjątków podczas obsługi wyjątków. Można go użyć do utworzenia nowego wyjątku, który zawiera wcześniej przechwycone wyjątki. Oryginalny wyjątek mogą być przechwytywane <xref:System.Exception.InnerException> przez drugi wyjątek we właściwości, dzięki czemu kod, który obsługuje drugi wyjątek, aby zbadać dodatkowe informacje. Załóżmy na przykład, że masz metodę, która odbiera argument, który jest nieprawidłowo sformatowany.  Kod próbuje odczytać argument, ale wyjątek. Metoda przechwytuje wyjątek i <xref:System.FormatException>zgłasza . Aby zwiększyć zdolność obiektu wywołującego do określenia przyczyny wyjątek, czasami jest pożądane dla metody do połowu wyjątek zgłoszony przez pomocnika rutynowych, a następnie zgłosić wyjątek bardziej wskazuje na błąd, który wystąpił. Można utworzyć nowy i bardziej znaczący wyjątek, gdzie odwołanie do wyjątku wewnętrznego można ustawić na oryginalny wyjątek. Ten bardziej znaczący wyjątek może następnie zostać zgłoszony do obiektu wywołującego. Należy zauważyć, że z tej funkcji można utworzyć serię połączonych wyjątków, który kończy się wyjątkiem, który został zgłoszony jako pierwszy. |
| <xref:System.Exception.Message> | Zawiera szczegółowe informacje o przyczynie wyjątku.
| <xref:System.Exception.Source> | Pobiera lub ustawia nazwę aplikacji lub obiektu, który powoduje błąd. |
| <xref:System.Exception.StackTrace>| Zawiera ślad stosu, który może służyć do określenia, gdzie wystąpił błąd. Śledzenie stosu zawiera nazwę pliku źródłowego i numer wiersza programu, jeśli dostępne są informacje o debugowaniu. |

Większość klas, które <xref:System.Exception> dziedziczą z nie implementują dodatkowych elementów członkowskich lub zapewniają dodatkowe funkcje; po prostu <xref:System.Exception>dziedziczą z . W związku z tym najważniejsze informacje dotyczące wyjątku można znaleźć w hierarchii klas wyjątków, nazwa wyjątku i informacje zawarte w wyjątku.

Zaleca się, aby zgłaszać i łapania tylko obiekty, które pochodzą <xref:System.Exception> <xref:System.Object> z , ale można zgłosić dowolny obiekt, który pochodzi z klasy jako wyjątek. Należy zauważyć, że nie wszystkie języki obsługują rzucanie <xref:System.Exception>i przechwytywanie obiektów, które nie pochodzą z .
  
## <a name="see-also"></a>Zobacz też

- [Wyjątki](index.md)
