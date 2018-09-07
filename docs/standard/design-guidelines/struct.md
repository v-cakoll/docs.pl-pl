---
title: Projekt struktury
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3879dc3f0270a56132b44882a74c50d05914ff89
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44067454"
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
  
 *Przedrukowano przez uprawnienie Pearson edukacji, Inc. z [wytyczne dotyczące projektowania Framework: konwencje Idiomy i wzorce wielokrotnego użytku, do bibliotek .NET, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Brad Abrams opublikowane 22 Oct 2008 przez Professional Addison Wesley jako część serii rozwoju Windows firmy Microsoft.*  
  
## <a name="see-also"></a>Zobacz także

- [Typy — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/type.md)  
- [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)  
- [Wybieranie między klasą i strukturą](../../../docs/standard/design-guidelines/choosing-between-class-and-struct.md)
