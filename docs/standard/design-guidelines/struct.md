---
title: Projektowanie struktury
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- class library design guidelines [.NET Framework], structures
- deallocating structures
- allocating structures
- value types, structures
- structure design
- type design guidelines, structures
- structures [.NET Framework], design guidelines
ms.assetid: 1f48b2d8-608c-4be6-9ba4-d8f203ed9f9f
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d1566d2b67e1dda5b0b221a2c10affb6bdaea888
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="struct-design"></a>Projektowanie struktury
Typ wartości ogólnego przeznaczenia najczęściej nazywa się struktury, jego słowo kluczowe języka C#. Ta sekcja zawiera wskazówki dotyczące projektowania struktury ogólne.  
  
 **X nie** Podaj domyślnego konstruktora dla struktury.  
  
 Niniejsze wytyczne po umożliwia tablice struktur ma zostać utworzony bez konieczności uruchamiania Konstruktora na każdy element tablicy. Zwróć uwagę, że C# nie zezwala na struktury ma domyślnych konstruktorów.  
  
 **X nie** Definiowanie typów modyfikowalne wartości.  
  
 Typy wartości modyfikowalne ma kilka problemów. Na przykład gdy metody pobierającej właściwość zwraca typ wartości, wywołujący wysyłana kopia. Ponieważ kopia zostanie utworzona niejawnie, deweloperzy mogą nie być pamiętać, że są mutacja kopia i nie oryginalnej wartości. Ponadto w przypadku niektórych języków (dynamiczny języki, w szczególności) występują problemy przy użyciu typów wartości modyfikowalne, ponieważ nawet zmiennych lokalnych, gdy wyłuskiwany, spowodować kopii ma zostać wykonane.  
  
 **CZY ✓** zapewnić, że stan, w którym wszystkie dane wystąpienia jest ustawiony na zero, wartość false lub wartość null (zgodnie z potrzebami) jest nieprawidłowa.  
  
 Zapobiega przypadkowemu tworzenia wystąpień nieprawidłowy, po utworzeniu tablicę struktury.  
  
 **CZY ✓** zaimplementować <xref:System.IEquatable%601> w typach wartości.  
  
 <xref:System.Object.Equals%2A?displayProperty=nameWithType> Metody w typach wartości powoduje, że opakowywanie i jego domyślna implementacja nie jest bardzo wydajny, ponieważ używa odbicia. <xref:System.IEquatable%601.Equals%2A>może być znacznie lepszą wydajność i można zaimplementować tak, aby nie spowoduje boxing.  
  
 **X nie** jawnie rozszerzyć <xref:System.ValueType>. W rzeczywistości większość języków temu zapobiec.  
  
 Ogólnie rzecz biorąc struktury może być bardzo przydatne, ale należy używać tylko w małych, jednego, modyfikować wartości, które nie można spakować często.  
  
 *Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*  
  
 *Drukowane uprawnieniami wariancji x edukacji, Inc. z [Framework zaleceń dotyczących projektowania: konwencje, Idioms i wzorce dla bibliotek .NET wielokrotnego użytku, wydanie 2](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Abrams Brada opublikowane 22 Oct 2008 przez Professional Addison-Wesley jako część serii rozwoju systemu Windows firmy Microsoft.*  
  
## <a name="see-also"></a>Zobacz też  
 [Wytyczne dotyczące projektowania typu](../../../docs/standard/design-guidelines/type.md)  
 [Wytyczne dotyczące projektowania Framework](../../../docs/standard/design-guidelines/index.md)  
 [Wybór między klasy i struktury](../../../docs/standard/design-guidelines/choosing-between-class-and-struct.md)
