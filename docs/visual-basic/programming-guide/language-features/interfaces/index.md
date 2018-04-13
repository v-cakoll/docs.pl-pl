---
title: Interfejsy (Visual Studio)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Visual Basic code, interfaces
- interfaces [Visual Basic], Visual Basic
- interfaces
- interfaces [Visual Basic]
ms.assetid: 61b06674-12c9-430b-be68-cc67ecee1f5b
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c26bb7322064d0b8cdf733e74f8b37e81b1e620c
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="interfaces-visual-basic"></a>Interfejsy (Visual Studio)
*Interfejsy* Definiowanie właściwości, metod i zdarzeń, które można zaimplementować klasy. Interfejsy umożliwiają definiowanie funkcji jako małych grup ściśle powiązane właściwości, metod i zdarzeń; Zmniejsza to problemy ze zgodnością, ponieważ możesz utworzyć rozszerzoną implementacje interfejsów sieci bez narażenia istniejącego kodu. Możesz dodać nowe funkcje w dowolnym momencie przez tworzenie implementacji i dodatkowe interfejsy.  
  
 Istnieje kilka innych przyczyn, dlaczego warto używać interfejsów zamiast dziedziczenia klas:  
  
-   Interfejsy są bardziej odpowiednie do sytuacji, w których aplikacje wymagają się, że prawdopodobnie wielu niepowiązanych typów obiektów, które umożliwiają korzystanie z niektórych funkcji.  
  
-   Interfejsy są bardziej elastyczne niż klasy podstawowej, ponieważ można określić pojedynczej implementacji, które można zaimplementować wiele interfejsów.  
  
-   Interfejsy są lepsze w sytuacjach, w których nie masz dziedziczenia z klasy podstawowej implementacji.  
  
-   Interfejsy są przydatne, gdy nie można użyć dziedziczenia klas. Na przykład struktury nie może dziedziczyć z klasy, ale miały zaimplementowane interfejsy.  
  
## <a name="declaring-interfaces"></a>Deklarowanie interfejsów  
 Definicje interfejsu są ujęte w `Interface` i `End Interface` instrukcje. Po `Interface` instrukcji, można dodać opcjonalne `Inherits` instrukcji, która zawiera jeden lub więcej dziedziczonych interfejsach. `Inherits` Instrukcje musi poprzedzać wszystkie inne instrukcje w deklaracji z wyjątkiem komentarze. Pozostałe instrukcje w definicji interfejsu powinny być `Event`, `Sub`, `Function`, `Property`, `Interface`, `Class`, `Structure`, i `Enum` instrukcje. Interfejsy nie mogą zawierać kod implementacji ani instrukcji skojarzony z kodem wdrożenia, takich jak `End Sub` lub `End Property`.  
  
 W przypadku przestrzeni nazw są instrukcje interfejsu `Friend` domyślnie, ale one mogą również być jawnie deklarowane jako `Public` lub `Friend`. Interfejsy zdefiniowane w obrębie klasy, modułów, interfejsów i struktury są `Public` domyślnie, ale one mogą również być jawnie deklarowane jako `Public`, `Friend`, `Protected`, lub `Private`.  
  
> [!NOTE]
>  `Shadows` — Słowo kluczowe może odnosić się do wszystkich członków interfejsu. `Overloads` — Słowo kluczowe może odnosić się do `Sub`, `Function`, i `Property` instrukcje zadeklarowany w definicji interfejsu. Ponadto `Property` instrukcje mogą mieć `Default`, `ReadOnly`, lub `WriteOnly` modyfikatorów. Brak innych modyfikatorów —`Public`, `Private`, `Friend`, `Protected`, `Shared`, `Overrides`, `MustOverride`, lub `Overridable`— są dozwolone. Aby uzyskać więcej informacji, zobacz [kontekst deklaracji i domyślne poziomy dostępu](../../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Na przykład poniższy kod definiuje interfejs z jednej funkcji, jednej właściwości i jedno zdarzenie.  
  
 [!code-vb[VbVbalrOOP#17](../../../../visual-basic/misc/codesnippet/VisualBasic/index_1.vb)]  
  
## <a name="implementing-interfaces"></a>Implementowanie interfejsów  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] Słowa zarezerwowanego `Implements` jest używany na dwa sposoby. `Implements` Instrukcji oznacza, że klasy lub struktury implementuje interfejs. `Implements` — Słowo kluczowe oznacza, że element członkowski klasy lub struktury element członkowski implementuje członkiem określonego interfejsu.  
  
### <a name="implements-statement"></a>Implements — Instrukcja  
 Jeśli klasy lub struktury implementuje jeden lub więcej interfejsów, musi on zawierać `Implements` instrukcji natychmiast po `Class` lub `Structure` instrukcji. `Implements` Instrukcja wymaga rozdzielana przecinkami lista interfejsy do zaimplementowania przez klasę. Klasy lub struktury musi implementować wszystkie elementy członkowskie interfejsu za pomocą `Implements` — słowo kluczowe.  
  
### <a name="implements-keyword"></a>Implements — słowo kluczowe  
 `Implements` — Słowo kluczowe wymaga rozdzielana przecinkami lista członków interfejsu do zaimplementowania. Ogólnie rzecz biorąc tylko członek jeden interfejs jest określony, ale można określić wiele elementów członkowskich. Specyfikacja elementu członkowskiego interfejsu, który składa się z nazwy interfejsu, która musi zostać określona w instrukcji implementuje w obrębie klasy; okres; i nazwa funkcji członkowskiej, właściwość lub zdarzenie, które mają zostać wdrożone. Nazwa elementu członkowskiego, który implementuje element członkowski można użyć dowolnego poprawnego identyfikatora i nie jest ograniczona do `InterfaceName_MethodName` Konwencji używany w starszych wersjach [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].  
  
 Na przykład poniższy kod przedstawia sposób Zadeklaruj procedury o nazwie `Sub1` implementującej metody interfejsu:  
  
 [!code-vb[VbVbalrOOP#69](../../../../visual-basic/misc/codesnippet/VisualBasic/index_2.vb)]  
  
 Typy parametrów i zwracanych typów implementujący element członkowski musi być zgodna deklaracja właściwości lub elementu członkowskiego interfejsu w interfejsie. Najbardziej typowe sposób implementowania elementem interfejsu jest z elementu członkowskiego, który ma taką samą nazwę jak interfejs, jak pokazano w poprzednim przykładzie.  
  
 Aby zadeklarować implementacja metody interfejsu, można użyć wszelkie atrybuty, które są prawnych w deklaracjach metody wystąpienia, w tym `Overloads`, `Overrides`, `Overridable`, `Public`, `Private`, `Protected`, `Friend`, `Protected Friend`, `MustOverride`, `Default`, i `Static`. `Shared` Atrybutu jest niedozwolona, ponieważ definiuje klasę zamiast metody wystąpienia.  
  
 Przy użyciu `Implements`, można także zapisywać pojedynczej metody, która implementuje wiele metod zdefiniowane w interfejsie, jak w poniższym przykładzie:  
  
 [!code-vb[VbVbalrOOP#70](../../../../visual-basic/misc/codesnippet/VisualBasic/index_3.vb)]  
  
 Prywatnego elementu członkowskiego służy do implementowania elementem interfejsu. Członek prywatny implementuje elementu członkowskiego interfejsu, ten element członkowski staje się dostępna na interfejsie mimo że nie jest dostępny bezpośrednio na zmienne obiektów w klasie.  
  
### <a name="interface-implementation-examples"></a>Przykłady implementacji interfejsu  
 Klasy, które implementują interfejs musi implementować jego właściwości, metod i zdarzeń.  
  
 W poniższym przykładzie zdefiniowano dwa interfejsy. Drugi interfejs `Interface2`, dziedziczy `Interface1` i definiuje dodatkowe właściwości i metody.  
  
 [!code-vb[VbVbalrOOP#39](../../../../visual-basic/misc/codesnippet/VisualBasic/index_4.vb)]  
  
 Implementuje w następnym przykładzie `Interface1`, interface, określone w poprzednim przykładzie:  
  
 [!code-vb[VbVbalrOOP#40](../../../../visual-basic/misc/codesnippet/VisualBasic/index_5.vb)]  
  
 Implementuje końcowy przykład `Interface2`, łącznie z metody dziedziczone z `Interface1`:  
  
 [!code-vb[VbVbalrOOP#41](../../../../visual-basic/misc/codesnippet/VisualBasic/index_6.vb)]  
  
 Można zaimplementować właściwość tylko do odczytu z właściwością readwrite (oznacza to, że nie masz zadeklarować on tylko do odczytu w klasie wykonawczych).  Implementowanie interfejsu zobowiązuje się do wdrożenia co najmniej elementów członkowskich, które deklaruje interfejsu, ale mogą oferować więcej możliwości, takie jak stosowanie równą możliwa do zapisu.  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Wskazówki: Tworzenie i wdrażanie interfejsów](../../../../visual-basic/programming-guide/language-features/interfaces/walkthrough-creating-and-implementing-interfaces.md)|Zawiera szczegółowe procedury, która przeprowadza użytkownika przez proces definiowanie i wdrażanie własnego interfejsu.|  
|[Wariancje w interfejsach](../../concepts/covariance-contravariance/variance-in-generic-interfaces.md)|Zawiera omówienie Kowariancja i kontrawariancja w interfejsach, a także listę interfejsów ogólnych typu variant w programie .NET Framework.|
