---
title: Projekt struktury
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- class library design guidelines [.NET Framework], structures
- deallocating structures
- allocating structures
- value types, structures
- structure design
- type design guidelines, structures
- structures [.NET Framework], design guidelines
ms.assetid: 1f48b2d8-608c-4be6-9ba4-d8f203ed9f9f
author: KrzysztofCwalina
ms.openlocfilehash: cc5b8d7effda31b0236477b217bccf5cf2137f8c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61650144"
---
# <a name="struct-design"></a>Projekt struktury
Typ wartości ogólnego przeznaczenia najczęściej nazywa się struktury, jego słowo kluczowe języka C#. Ta sekcja zawiera wskazówki dotyczące projektowania struktury ogólne.  
  
 **X DO NOT** Podaj domyślnego konstruktora dla struktury.  
  
 Ta wytyczna następujące umożliwia tablic struktur, które ma zostać utworzony bez konieczności uruchamiania konstruktora dla każdego elementu tablicy. Należy zauważyć, że języka C# nie zezwala na struktur ma domyślnych konstruktorów.  
  
 **X DO NOT** Definiowanie typów modyfikowalne wartości.  
  
 Typy wartości modyfikowalne ma kilka problemów. Na przykład gdy pobierającą właściwość zwraca typ wartości, obiekt wywołujący otrzymuje kopię. Ponieważ kopia zostanie utworzona w sposób niejawny, deweloperzy może nie być pamiętać, że są mutacja kopii i nie oryginalną wartość. Ponadto niektóre języki (dynamiczna języków, w szczególności) występują problemy przy użyciu typów wartości modyfikowalne, ponieważ zmienne lokalne, nawet wtedy, gdy wyłuskany, spowodować kopię ma zostać wykonane.  
  
 **✓ DO** zapewnić, że stan, w którym wszystkie dane wystąpienia jest ustawiony na zero, wartość false lub wartość null (zgodnie z potrzebami) jest nieprawidłowa.  
  
 Zapobiega to przypadkowym tworzenia nieprawidłowe wystąpień, po utworzeniu tablicy struktur.  
  
 **✓ DO** zaimplementować <xref:System.IEquatable%601> w typach wartości.  
  
 <xref:System.Object.Equals%2A?displayProperty=nameWithType> Metody w typach wartości powoduje, że konwersja boxing i jego domyślna implementacja jest bardzo wydajny, ponieważ używa odbicia. <xref:System.IEquatable%601.Equals%2A> może być znacznie lepszej wydajności, a następnie można zaimplementować tak, aby nie spowoduje pakowania.  
  
 **X DO NOT** jawnie rozszerzyć <xref:System.ValueType>. W rzeczywistości większość języków temu zapobiec.  
  
 Ogólnie rzecz biorąc struktury mogą być bardzo przydatne, ale należy używać tylko małej, pojedynczej, niezmienne wartości, które nie zostać opakowany często.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*  
  
 *Przedrukowano za uprawnienie Pearson edukacji, Inc. z [wytyczne dotyczące projektowania Framework: Konwencje, Idiomy i wzorców dla wielokrotnego użytku, do bibliotek .NET, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Brad Abrams publikowane 22 Oct 2008 przez Addison Wesley Professional w ramach serii rozwoju Windows firmy Microsoft.*  
  
## <a name="see-also"></a>Zobacz także

- [Typy — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/type.md)
- [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)
- [Wybieranie między klasą i strukturą](../../../docs/standard/design-guidelines/choosing-between-class-and-struct.md)
