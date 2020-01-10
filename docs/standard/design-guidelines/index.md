---
title: Framework — zalecenia dotyczące projektowania
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- libraries, .NET Framework class library
- class library design guidelines [.NET Framework], about
- class library design guidelines [.NET Framework]
ms.assetid: 5fbcaf4f-ea2a-4d20-b0d6-e61dee202b4b
ms.openlocfilehash: 623391de63891c1695a63482a424bb76a861deba
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709312"
---
# <a name="framework-design-guidelines"></a>Framework — zalecenia dotyczące projektowania
Ta sekcja zawiera wskazówki dotyczące projektowania bibliotek, które zwiększają i współpracują z .NET Framework. Celem jest ułatwienie projektantom biblioteki zapewnienia spójności interfejsu API i prostoty użycia przez zapewnienie ujednoliconego modelu programowania, który jest niezależny od języka programowania używanego do programowania. Zalecamy przestrzeganie tych wytycznych dotyczących projektowania podczas tworzenia klas i składników, które zwiększają .NET Framework. Niespójny projekt biblioteki niekorzystnie wpływa na produktywność deweloperów i odradza wdrażanie.  
  
 Wytyczne są zorganizowane jako proste zalecenia poprzedzone postanowieniami `Do`, `Consider`, `Avoid`i `Do not`. Te wytyczne mają na celu ułatwienie projektantom biblioteki klas zrozumienia zalet różnych rozwiązań. Mogą wystąpić sytuacje, w których dobry projekt biblioteki wymaga naruszenia tych wytycznych projektowych. Takie przypadki powinny być rzadkie i ważne jest, aby użytkownik miał jasno i atrakcyjny powód podjęcia decyzji.  
  
 Wytyczne te są przedstawione na podstawie *wytycznych dotyczących projektowania struktury książki: konwencje, idiomy i wzorce dla bibliotek .NET do wielokrotnego użytku, wydanie 2*, Krzysztof Cwalina i Brad Abrams.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Wskazówki dotyczące nazewnictwa](../../../docs/standard/design-guidelines/naming-guidelines.md)  
 Zawiera wskazówki dotyczące nazewnictwa zestawów, przestrzeni nazw, typów i elementów członkowskich w bibliotekach klas.  
  
 [Typy — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/type.md)  
 Zawiera wytyczne dotyczące używania klas statycznych i abstrakcyjnych, interfejsów, wyliczeń, struktur i innych typów.  
  
 [Element członkowski — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/member.md)  
 Zawiera wytyczne dotyczące projektowania i używania właściwości, metod, konstruktorów, pól, zdarzeń, operatorów i parametrów.  
  
 [Projektowanie pod kątem rozszerzalności](../../../docs/standard/design-guidelines/designing-for-extensibility.md)  
 Omawia mechanizmy rozszerzalności, takie jak podklasa, korzystanie z zdarzeń, wirtualne elementy członkowskie i wywołania zwrotne, oraz wyjaśnia, jak wybrać mechanizmy najlepiej spełniające wymagania platformy.  
  
 [Wyjątki — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/exceptions.md)  
 Zawiera opis wytycznych dotyczących projektowania, zgłaszania i przechwytywania wyjątków.  
  
 [Zalecenia dotyczące użytkowania](../../../docs/standard/design-guidelines/usage-guidelines.md)  
 Opisuje wskazówki dotyczące używania typów wspólnych, takich jak tablice, atrybuty i kolekcje, Obsługa serializacji i przeciążanie operatorów równości.  
  
 [Często używane wzorce projektowe](../../../docs/standard/design-guidelines/common-design-patterns.md)  
 Zawiera wskazówki dotyczące wybierania i implementowania właściwości zależności.  
  
 *Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*  
  
 *Ponownie Wydrukowano przez uprawnienie Pearson Education, Inc. z [wytycznych dotyczących projektowania platformy: konwencje, idiomy i wzorce dla bibliotek .NET do wielokrotnego użytku, 2. wydanie](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) przez Krzysztof Cwalina i Brad Abrams, opublikowane 22, 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development.*  
  
## <a name="see-also"></a>Zobacz także

- [Omówienie](../../../docs/framework/get-started/overview.md)
- [Podręcznik programowania](../../../docs/framework/development-guide.md)
