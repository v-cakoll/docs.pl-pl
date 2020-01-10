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
ms.openlocfilehash: 8841a30f1dd0420b2ea45740b1e33bde5199c3f9
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709052"
---
# <a name="struct-design"></a>Projekt struktury
Typ wartości ogólnego przeznaczenia jest najczęściej określany jako struktura, jego C# słowo kluczowe. Ta sekcja zawiera wskazówki dotyczące ogólnego projektowania struktury.  
  
 **X nie** dostarcza konstruktora bez parametrów dla struktury.  
  
 Poniższe wytyczne umożliwiają tworzenie tablic struktur bez konieczności uruchamiania konstruktora dla każdego elementu tablicy. Zwróć uwagę C# , że struktury nie umożliwiają konstruktorom bez parametrów.  
  
 **X DO NOT** Definiowanie typów modyfikowalne wartości.  
  
 Modyfikowalne typy wartości mają kilka problemów. Na przykład, gdy metoda pobierająca Właściwość zwraca typ wartości, wywołujący otrzymuje kopię. Ponieważ kopia jest tworzona niejawnie, deweloperzy mogą nie wiedzieć, że są one mutacją, a nie pierwotną wartością. Ponadto w niektórych językach (w szczególności Języki dynamiczne) występują problemy z użyciem modyfikowalnych typów wartości, ponieważ nawet zmienne lokalne, gdy jest używana, powoduje, że kopia zostanie wykonana.  
  
 **✓ DO** zapewnić, że stan, w którym wszystkie dane wystąpienia jest ustawiony na zero, wartość false lub wartość null (zgodnie z potrzebami) jest nieprawidłowa.  
  
 Zapobiega to przypadkowemu tworzeniu nieprawidłowych wystąpień podczas tworzenia tablicy struktur.  
  
 **✓ DO** zaimplementować <xref:System.IEquatable%601> w typach wartości.  
  
 Metoda <xref:System.Object.Equals%2A?displayProperty=nameWithType> w typach wartości powoduje opakowanie, a jej domyślna implementacja nie jest bardzo wydajna, ponieważ używa odbicia. <xref:System.IEquatable%601.Equals%2A> może mieć znacznie lepszą wydajność i można ją zaimplementować, aby nie powodowały pakowania.  
  
 **X DO NOT** jawnie rozszerzyć <xref:System.ValueType>. W rzeczywistości większość języków zapobiega tym.  
  
 Ogólnie rzecz biorąc, struktury mogą być bardzo przydatne, ale powinny być używane tylko w przypadku małych, pojedynczych, niezmiennych wartości, które nie będą często opakowane.  
  
 *Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*  
  
 *Ponownie Wydrukowano przez uprawnienie Pearson Education, Inc. z [wytycznych dotyczących projektowania platformy: konwencje, idiomy i wzorce dla bibliotek .NET do wielokrotnego użytku, 2. wydanie](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) przez Krzysztof Cwalina i Brad Abrams, opublikowane 22, 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development.*  
  
## <a name="see-also"></a>Zobacz także

- [Typy — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/type.md)
- [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)
- [Wybieranie między klasą i strukturą](../../../docs/standard/design-guidelines/choosing-between-class-and-struct.md)
