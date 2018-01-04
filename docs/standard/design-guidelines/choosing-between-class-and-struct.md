---
title: "Wybór między klasy i struktury"
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
- class library design guidelines [.NET Framework], classes
- structures [.NET Framework], vs. classes
- classes [.NET Framework], design guidelines
- type design guidelines, structures
- structures [.NET Framework], design guidelines
- classes [.NET Framework], vs. structures
- type design guidelines, classes
ms.assetid: f8b8ec9b-0ba7-4dea-aadf-a93395cd804f
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 68a3d2c7335ff15706925f9a7986164e6d9c0c36
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="choosing-between-class-and-struct"></a>Wybór między klasy i struktury
Jednym z podstawowych decyzji projektowych który skierowany framework designer na co jest czy zaprojektować typu jako klasy (Typ referencyjny) lub struct (typ wartości). Dobrą znajomością różnice w zachowaniu typy wartości i typy referencyjne odgrywa kluczową rolę w podejmowaniu ten wybór.  
  
 Pierwszy różnica między typy referencyjne i typów wartości, które firma Microsoft będzie uwzględniać typy referencyjne są przydzielone na stercie i odzyskiwanie zbierane typów wartości są przydzielane na stosie lub tekście zawierający typów, a kiedy alokację stosu cofa lub po ich typ zawierający pobiera alokację. W związku z tym alokacji i dezalokacji typów wartości są zwykle tańsze niż alokacji i dezalokacji typy referencyjne.  
  
 Następnie tablice odwołania, których typy są przydzielone poza zewnętrznych, co oznacza tablicy, która elementy są tylko odwołania do wystąpienia typu referencyjnego znajdującej się na stosie. Tablice typu wartości są przydzielane wbudowane, co oznacza, że elementy tablicy są bieżące wystąpienia typu wartości. W związku z tym alokacji i dezalokacji tablic typu wartości są znacznie tańszy niż alokacji i dezalokacji tablic typu odwołania. Ponadto w większości przypadków tablic typu wartości wykazują znacznie lepszą miejscowości odwołania.  
  
 Różnica dalej jest powiązany z użycia pamięci. Typy wartości get opakowany po Rzutowanie na typ referencyjny lub jednego z interfejsów, które wdrażają. Następnie otrzymują oni rozpakowany podczas rzutowania do typu wartości. Ponieważ pola są obiekty, które są przydzielone na stercie i są zbierane w pamięci, zbyt dużo konwersja boxing i Rozpakowywanie może mieć negatywny wpływ na stercie modułu zbierającego elementy bezużyteczne i ostatecznie wydajność aplikacji.  Z kolei nie takie opakowanie występuje jako typów referencyjnych są rzutowania.  
  
 Następnie przypisania typu odwołanie skopiuj odwołanie, natomiast wartość typu przypisania skopiować całą wartość. W związku z tym przypisania typów dużych odwołania są tańsze niż przypisania duża wartość.  
  
 Na koniec typy referencyjne są przekazywane przez odwołanie, podczas gdy typy wartości są przekazywane przez wartość. Zmiany do wystąpienia typu referencyjnego wpływają na wszystkie odwołania wskazujące wystąpienie. Wystąpienia typu wartości są kopiowane, gdy są one przekazywane przez wartość. Po zmianie wystąpienia typu wartości on oczywiście nie wpływa na jej kopii. Ponieważ kopie nie są jawnie tworzone przez użytkownika, ale niejawnie są tworzone, gdy argumenty są przekazywane lub zwracać wartości są zwracane typy wartości, które można zmienić może być trudne dla wielu użytkowników. W związku z tym typów wartości powinno być niezmienialne.  
  
 Zasadą większość typów w ramach powinny być klasy. Istnieje jednak kilka sytuacji, w których typ wartości właściwości stał się bardziej odpowiednie do użycia w strukturach.  
  
 **ROZWAŻ ✓** definiowania struktury zamiast klasy, jeśli wystąpienia typu małych i często krótkim okresie lub często są osadzone w innych obiektach.  
  
 **X należy UNIKAĆ** definiowania struktury, chyba że typ ma wszystkie następujące właściwości:  
  
-   Logicznie reprezentuje pojedynczą wartość, podobnie jak typy pierwotne (`int`, `double`itp.).  
  
-   Ma rozmiar wystąpienia w obszarze 16 bajtów.  
  
-   Jest niezmienialny.  
  
-   Nie będzie miał zostać opakowany często.  
  
 We wszystkich innych przypadkach należy zdefiniować typy użytkownika jako klasy.  
  
 *Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*  
  
 *Drukowane uprawnieniami wariancji x edukacji, Inc. z [Framework zaleceń dotyczących projektowania: konwencje, Idioms i wzorce dla bibliotek .NET wielokrotnego użytku, wydanie 2](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Abrams Brada opublikowane 22 Oct 2008 przez Professional Addison-Wesley jako część serii rozwoju systemu Windows firmy Microsoft.*  
  
## <a name="see-also"></a>Zobacz też  
 [Typy — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/type.md)  
 [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)
