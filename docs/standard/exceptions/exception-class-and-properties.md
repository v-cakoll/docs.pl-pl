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
ms.openlocfilehash: 283b3b1aa0d56b50b6f9e67b66de3e0b68ae2331
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "44036349"
---
# <a name="exception-class-and-properties"></a>Właściwości i klasy wyjątków

<xref:System.Exception> Klasa to klasa bazowa, z którego dziedziczą wyjątków. Na przykład <xref:System.InvalidCastException> hierarchii klas jest następująca:

```
Object
  Exception
    SystemException
       InvalidCastException
```

<xref:System.Exception> Klasa ma następujące właściwości, które tworzą wyjątek ułatwia zrozumienie.

| Nazwa właściwości | Opis |
| ------------- | ----------- |
| <xref:System.Exception.Data> | <xref:System.Collections.IDictionary> Przechowuje dowolne dane w parach klucz wartość. |
| <xref:System.Exception.HelpLink> | Może zawierać adres URL (lub URN) do pliku pomocy, który zawiera wyczerpujące informacje o przyczynie wyjątku. |
| <xref:System.Exception.InnerException> | Ta właściwość może służyć do tworzenia i zachować szereg wyjątki podczas obsługi wyjątku. Można użyć go, aby utworzyć nowy wyjątek, który zawiera wcześniej przechwycone wyjątki. Oryginalny wyjątek mogą być przechwytywane przez drugi wyjątek w <xref:System.Exception.InnerException> właściwości, dzięki czemu kod, który obsługuje drugi wyjątek, aby sprawdzić dodatkowe informacje. Na przykład załóżmy, że ma metodę, która odbiera argument, który jest nieprawidłowo sformatowana.  Kod próbuje odczytać argument, ale jest zgłaszany wyjątek. Metoda przechwytuje wyjątek i zgłasza <xref:System.FormatException>. Aby poprawić wywołującego zdolność do określenia przyczyny, dla której zgłaszany jest wyjątek, czasami jest pożądane dla metody przechwycić wyjątek zgłoszony przez pomocnika procedury i następnie generują bardziej wskazujące na błąd, który wystąpił wyjątek. Można utworzyć wyjątek nowe i bardziej zrozumiały, gdzie można ustawić odwołanie do wewnętrznego wyjątku do oryginalnego wyjątku. Ten bardziej zrozumiały może następnie być wyjątek do obiektu wywołującego. Należy pamiętać, że dzięki tej funkcji, możesz utworzyć serii połączone wyjątki, kończące się wyjątek, który został zgłoszony jako pierwsze. |
| <xref:System.Exception.Message> | Zawiera szczegółowe informacje o przyczynie wyjątku.
| <xref:System.Exception.Source> | Pobiera lub ustawia nazwę aplikacji lub obiekt, który powoduje błąd. |
| <xref:System.Exception.StackTrace>| Zawiera ślad stosu, który może służyć do określenia, gdzie wystąpił błąd. Ślad stosu obejmuje źródła pliku nazwa i program numer wiersza, jeśli informacje o debugowaniu są dostępne. |

Większość klas, które dziedziczą z <xref:System.Exception> nie implementuje dodatkowe elementy Członkowskie lub udostępniają dodatkowe funkcje; po prostu dziedziczą z <xref:System.Exception>. W związku z tym najważniejsze informacje o wyjątku znajdują się w hierarchii klasy wyjątków, nazwa wyjątku i informacje zawarte w wyjątku.

Zalecamy throw i catch tylko te obiekty, które wynikają z <xref:System.Exception>, ale może zgłosić dowolnego obiektu, który pochodzi od klasy <xref:System.Object> klasy jako wyjątek. Należy pamiętać, że nie wszystkie języki obsługują zgłaszania i przechwytywania obiektów, które nie pochodzą z <xref:System.Exception>.
  
## <a name="see-also"></a>Zobacz także

- [Wyjątki](index.md)
