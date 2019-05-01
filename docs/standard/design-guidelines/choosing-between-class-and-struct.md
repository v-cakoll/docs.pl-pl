---
title: Wybieranie między klasą i strukturą
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- class library design guidelines [.NET Framework], structures
- class library design guidelines [.NET Framework], classes
- structures [.NET Framework], vs. classes
- classes [.NET Framework], design guidelines
- type design guidelines, structures
- structures [.NET Framework], design guidelines
- classes [.NET Framework], vs. structures
- type design guidelines, classes
ms.assetid: f8b8ec9b-0ba7-4dea-aadf-a93395cd804f
author: KrzysztofCwalina
ms.openlocfilehash: a47e43b2387362500d46c8e531f16d004d823c4c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61778784"
---
# <a name="choosing-between-class-and-struct"></a>Wybieranie między klasą i strukturą
Jednym z decyzji projektowych podstawowe twarzy każdego Projektant framework jest czy zaprojektować typu jako klasę (typ odwołania) lub struct (typu wartości). Dobre zrozumienie różnic w zachowaniu typy odwołań i typy wartości jest sprawą kluczową podczas wprowadzania tego wyboru.  
  
 Pierwszy różnica między typami odwołań i typy wartości, które firma Microsoft będzie należy wziąć pod uwagę typów referencyjnych są przydzielone na stercie i jesdnostką zbierającą śmieci, natomiast typy wartości są przydzielane na stosie, lub bezpośrednio w zawierających typy i cofnięta kiedy stos rozwija lub po ich typem zawierającym cofnięcie jej przydziału. W związku z tym alokacji i liczbą typów wartości są ogólnie rzecz biorąc tańsze niż alokacji i liczbą typów odwołań.  
  
 Następnie tablice, odwołania, które typy są przydzielane poza wierszem, co oznacza tablicy, które elementy są tylko odwołania do wystąpienia typu referencyjnego znajdującej się na stosie. Tablicami typu wartości są przydzielane w tekście, co oznacza, że elementy tablicy są bieżące wystąpienia typu wartości. W związku z tym alokacji i liczbą tablicami typu wartości są znacznie tańsze niż alokacji i liczbą tablicami typu odwołania. Ponadto w większości przypadków tablicami typu wartości następującej liczby etapów stwierdzono znacznie lepiej miejscowość odwołania.  
  
 Następna różnica dotyczy użycia pamięci. Typy wartości Pobierz zapakowany, jeśli zrzutować na typ referencyjny lub jeden z interfejsów, które implementują. Otrzymają one rozpakowany Jeśli zrzutować do typu wartości. Ponieważ pola są obiekty, które są przydzielane na stosie i zebranych elementów bezużytecznych, zbyt dużo pakowania, jak i rozpakowania może mieć negatywny wpływ na stercie modułu odśmiecania pamięci i ostatecznie wydajność aplikacji.  Z kolei nie takich pakowania wypada rzutowania są typami odwołań. (Aby uzyskać więcej informacji, zobacz [opakowywanie i rozpakowywanie](../../csharp/programming-guide/types/boxing-and-unboxing.md)).
  
 Następnie przypisania typu odwołania wykonywać kopiowanie odwołania, natomiast wartość typu przypisania skopiować całą wartość. Dlatego przypisania typów referencyjnych dużych są tańsze niż przypisania duża wartość.  
  
 Na koniec typów referencyjnych są przekazywane przez odwołanie, natomiast typy wartości są przekazywane przez wartość. Zmiany do wystąpienia typu referencyjnego wpływają na wszystkie odwołania, które wskazuje na wystąpienie. Wystąpienia typu wartości są kopiowane, gdy są przekazywane przez wartość. Po zmianie wystąpienie typu wartości jego oczywiście nie wpływa na jego kopii. Ponieważ kopie nie są jawnie tworzone przez użytkownika, ale są tworzone niejawnie, gdy argumenty są przekazywane lub zwracanych wartości są zwracane typy wartości, które mogą być zmieniane może być mylące dla wielu użytkowników. W związku z tym typy wartości powinno być niezmienialne.  
  
 Jako ogólną regułę można przyjąć większość typów w ramach powinna być klasy. Istnieją jednak sytuacje, w których właściwości typu wartości stał się bardziej odpowiednie użycie struktury.  
  
 **✓ CONSIDER** definiowania struktury zamiast klasy, jeśli wystąpienia typu małych i często krótkim okresie lub często są osadzone w innych obiektach.  
  
 **X AVOID** definiowania struktury, chyba że typ ma wszystkie następujące właściwości:  
  
- Logicznie reprezentuje pojedynczą wartość, podobnie jak typy pierwotne (`int`, `double`itp.).  
  
- Ma rozmiar wystąpienia w obszarze 16 bajtów.  
  
- Jest on niezmienny.  
  
- Nie będzie można go opakować często.  
  
 We wszystkich innych przypadkach należy zdefiniować typów jako klasy.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*  
  
 *Przedrukowano za uprawnienie Pearson edukacji, Inc. z [wytyczne dotyczące projektowania Framework: Konwencje, Idiomy i wzorców dla wielokrotnego użytku, do bibliotek .NET, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Brad Abrams publikowane 22 Oct 2008 przez Addison Wesley Professional w ramach serii rozwoju Windows firmy Microsoft.*  
  
## <a name="see-also"></a>Zobacz także

- [Typy — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/type.md)
- [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)
