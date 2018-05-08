---
title: Właściwości i klasy wyjątków
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- exceptions, Exception class
- Exception class
ms.assetid: e2e1f8c4-e7b4-467d-9a66-13c90861221d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9cdc464234871fc07feeeb8dd02635ebdd151d76
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="exception-class-and-properties"></a>Właściwości i klasy wyjątków

<xref:System.Exception> Klasa jest klasy podstawowej, z której dziedziczy wyjątków. Na przykład <xref:System.InvalidCastException> hierarchii klas jest następujący:

```
Object
  Exception
    SystemException
       InvalidCastException
```

<xref:System.Exception> Klasa ma następujące właściwości ułatwiających opis wyjątku łatwiejsze.

| Nazwa właściwości | Opis |
| ------------- | ----------- |
| <xref:System.Exception.Data> | <xref:System.Collections.IDictionary> Przechowuje dowolne dane w pary klucz wartość. |
| <xref:System.Exception.HelpLink> | Może zawierać adres URL (lub URN) do pliku pomocy, który udostępnia szeroką gamę informacje dotyczące przyczyny wyjątku. |
| <xref:System.Exception.InnerException> | Ta właściwość umożliwia tworzenie i przechowywanie szereg wyjątków podczas obsługi wyjątków. Aby utworzyć nowy wyjątek, który zawiera wcześniej zgłoszony wyjątków, można użyć go. Pierwotny wyjątek mogą być przechwytywane przez drugi wyjątek w <xref:System.Exception.InnerException> właściwości, dzięki czemu kod obsługujący drugi wyjątek, aby sprawdzić dodatkowe informacje. Na przykład załóżmy, że ma metodę, która odbiera argument, który jest nieprawidłowo sformatowana.  Kod próbuje odczytać argument, ale jest zgłaszany wyjątek. Metoda przechwytuje wyjątek i zgłasza <xref:System.FormatException>. Aby zwiększyć możliwości wywołującego ustalenie przyczyny, dla której jest zgłaszany wyjątek, czasami jest pożądane dla metody catch wyjątku zgłoszonego przez procedury pomocnika i następnie zgłosić wyjątek więcej świadczy o wystąpieniu tego błędu. Można utworzyć wyjątek nowych i bardziej zrozumiałe, gdzie pierwotny wyjątek można ustawić odwołania wyjątek wewnętrzny. Ten wyjątek bardziej zrozumiałej następnie może zostać zgłoszony do obiektu wywołującego. Należy pamiętać, że dzięki tej funkcji, można utworzyć serii połączonego wyjątków, która kończy się najpierw zgłoszony wyjątek. |
| <xref:System.Exception.Message> | Zawiera szczegółowe informacje o przyczynie Wystąpił wyjątek.
| <xref:System.Exception.Source> | Pobiera lub ustawia nazwę aplikacji lub obiekt, który powoduje błąd. |
| <xref:System.Exception.StackTrace>| Zawiera ślad stosu, który może służyć do określenia, w którym wystąpił błąd. Ślad stosu obejmuje plik nazwy i program numer wiersza źródła Jeśli informacje o debugowaniu jest dostępna. |

Większość klas, które dziedziczą z <xref:System.Exception> nie implementuje dodatkowych członków lub oferowanie dodatkowych funkcji; dziedziczą po prostu z <xref:System.Exception>. W związku z tym najważniejsze informacje dla wyjątku znajdują się w hierarchii klasy wyjątków, nazwa wyjątku i informacje zawarte w wyjątek.

Zalecamy throw i catch tylko te obiekty, które pochodzą z <xref:System.Exception>, ale może zgłosić dowolnego obiektu, która jest pochodną <xref:System.Object> klasy jako wyjątek. Należy pamiętać, że nie obsługuje wszystkich języków zgłaszanie i przechwytywanie obiektów, które nie pochodzą z <xref:System.Exception>.
  
## <a name="see-also"></a>Zobacz też  
[Wyjątki](index.md)
