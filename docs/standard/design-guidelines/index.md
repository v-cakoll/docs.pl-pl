---
title: Framework — zalecenia dotyczące projektowania
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- libraries, .NET Framework class library
- class library design guidelines [.NET Framework], about
- class library design guidelines [.NET Framework]
ms.assetid: 5fbcaf4f-ea2a-4d20-b0d6-e61dee202b4b
author: KrzysztofCwalina
ms.openlocfilehash: c20430f9cdcd71cc2e178d38aeed48f9fa4e75c5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62026383"
---
# <a name="framework-design-guidelines"></a>Framework — zalecenia dotyczące projektowania
Ta sekcja zawiera wskazówki dotyczące projektowania bibliotek, które rozszerzają i wchodzić w interakcje z programu .NET Framework. Celem jest pomoc projektantów Biblioteka zapewnia spójność interfejsu API i łatwość użycia, udostępniając ujednolicony model programowania, który jest niezależny od języka programowania, używany do tworzenia aplikacji. Zaleca się przestrzegać następujących wytycznych projektowania, podczas tworzenia klas i składników, które rozszerzają programu .NET Framework. Biblioteka niespójne projektu niekorzystnie wpływa na wydajność pracy deweloperskiej i zniechęca do przyjęcia.  
  
 Wytyczne są uporządkowane jako prosty zalecenia prefiksem warunki `Do`, `Consider`, `Avoid`, i `Do not`. Te wytyczne są celem projektantów biblioteki klasy zrozumieć wad i zalet różnych rozwiązań. Może to być sytuacje, w których projekt biblioteki w dobrej wymaga, że naruszają te wytyczne dotyczące projektowania. Takiej sytuacji należy rzadkich i jest ważne, czy masz czytelne i atrakcyjne przyczynę swojej decyzji.  
  
 Te wytyczne pochodzą z książki *wytyczne dotyczące projektowania Framework: Konwencje, Idiomy i wzorców dla bibliotek .NET wielokrotnego użytku, wydanie 2*, Krzysztof Cwalina i Brad Abrams.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Wskazówki dotyczące nazewnictwa](../../../docs/standard/design-guidelines/naming-guidelines.md)  
 Zawiera wskazówki dotyczące nazewnictwa zestawów, przestrzeni nazw, typów i członków w bibliotekach klas.  
  
 [Typy — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/type.md)  
 Wskazówki dotyczące używania klas statycznych i abstrakcyjny, interfejsy, wyliczenia, struktur i innych typów.  
  
 [Element członkowski — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/member.md)  
 Wskazówki dotyczące projektowania i używania właściwości, metody, konstruktory, pola, zdarzenia, operatorów i parametry.  
  
 [Projektowanie pod kątem rozszerzalności](../../../docs/standard/design-guidelines/designing-for-extensibility.md)  
 W tym artykule omówiono rozszerzalności mechanizmów, takich jak podklasy, za pomocą zdarzeń, wirtualne elementy członkowskie i wywołania zwrotne i wyjaśnia, jak wybrać mechanizmów, które najlepiej spełniają wymagania preferowanej struktury.  
  
 [Wyjątki — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/exceptions.md)  
 W tym artykule opisano wytyczne dotyczące projektowania dla projektowania, zgłaszanie i połowowe wyjątków.  
  
 [Zalecenia dotyczące użytkowania](../../../docs/standard/design-guidelines/usage-guidelines.md)  
 W tym artykule opisano wskazówki dotyczące przy użyciu popularnych typów, takich jak tablice, atrybuty i kolekcje, obsługa serializacji i przeciążanie operatorów równości.  
  
 [Często używane wzorce projektowe](../../../docs/standard/design-guidelines/common-design-patterns.md)  
 Zawiera wskazówki dotyczące wybierania i implementowanie właściwości zależności.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*  
  
 *Przedrukowano za uprawnienie Pearson edukacji, Inc. z [wytyczne dotyczące projektowania Framework: Konwencje, Idiomy i wzorców dla wielokrotnego użytku, do bibliotek .NET, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Brad Abrams publikowane 22 Oct 2008 przez Addison Wesley Professional w ramach serii rozwoju Windows firmy Microsoft.*  
  
## <a name="see-also"></a>Zobacz także

- [Omówienie](../../../docs/framework/get-started/overview.md)
- [Podręcznik programowania](../../../docs/framework/development-guide.md)
