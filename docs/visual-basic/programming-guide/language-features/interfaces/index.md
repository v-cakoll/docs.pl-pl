---
title: Interfejsy (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
  - 'Visual Basic code, interfaces'
  - 'interfaces [Visual Basic], Visual Basic'
  - interfaces
  - 'interfaces [Visual Basic]'
ms.assetid: 61b06674-12c9-430b-be68-cc67ecee1f5b
---
# <a name="interfaces-visual-basic"></a>Interfejsy (Visual Basic)
*Interfejsy* zdefiniować właściwości, metody i zdarzenia, które można zaimplementować klasy. Interfejsy umożliwiają definiowanie funkcji jako mniejszym grupom ściśle powiązanych właściwości, metod i zdarzeń; Zmniejsza to problemów ze zgodnością, ponieważ możesz tworzyć rozszerzone implementacji interfejsów sieci bez narażenia istniejącego kodu. Opracowując implementacji i dodatkowe interfejsy, można dodać nowe funkcje w dowolnym momencie.  
  
 Istnieje kilka innych powodów dlaczego warto używać interfejsów zamiast dziedziczenia klasy:  
  
-   Interfejsy są bardziej odpowiednie do sytuacji, w których aplikacje wymagają, że wiele prawdopodobnie niezwiązanych ze sobą typy obiektów, które umożliwiają korzystanie z niektórych funkcji.  
  
-   Interfejsy są bardziej elastyczne niż klas bazowych, ponieważ możesz zdefiniować pojedynczej implementacji, które można zaimplementować wiele interfejsów.  
  
-   Interfejsy są lepsze w sytuacjach, w których nie trzeba dziedziczyć implementacji klasy podstawowej.  
  
-   Interfejsy są przydatne, gdy nie można użyć dziedziczenia klas. Na przykład struktury nie może dziedziczyć z klasy, ale mogące implementować interfejsy.  
  
## <a name="declaring-interfaces"></a>Deklarowanie interfejsów  
 Definicje interfejsu są ujęte w `Interface` i `End Interface` instrukcji. Następujące `Interface` instrukcji, można dodać opcjonalny `Inherits` instrukcję, która zawiera jeden lub więcej dziedziczonych interfejsów. `Inherits` Instrukcji musi poprzedzać wszystkie inne instrukcje w deklaracji z wyjątkiem komentarzy. Pozostałe instrukcje w definicji interfejsu powinny być `Event`, `Sub`, `Function`, `Property`, `Interface`, `Class`, `Structure`, i `Enum` instrukcji. Interfejsy nie mogą zawierać kod implementacji ani instrukcje związane z kodu realizacji, takie jak `End Sub` lub `End Property`.  
  
 W przypadku przestrzeni nazw interfejsu są `Friend` domyślnie, ale one mogą być także jawnie zadeklarowane jako `Public` lub `Friend`. Interfejsy zdefiniowane w obrębie klasy, moduły, interfejsy i struktury są `Public` domyślnie, ale one mogą być także jawnie zadeklarowane jako `Public`, `Friend`, `Protected`, lub `Private`.  
  
> [!NOTE]
>  `Shadows` — Słowo kluczowe mogą być stosowane do wszystkich składowych interfejsu. `Overloads` — Słowo kluczowe, które można zastosować do `Sub`, `Function`, i `Property` instrukcji zadeklarowanej w definicji interfejsu. Ponadto `Property` instrukcji może mieć `Default`, `ReadOnly`, lub `WriteOnly` modyfikatorów. Brak innych modyfikatorów —`Public`, `Private`, `Friend`, `Protected`, `Shared`, `Overrides`, `MustOverride`, lub `Overridable`— są dozwolone. Aby uzyskać więcej informacji, zobacz [Kontekst deklaracji i domyślne poziomy dostępu](../../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Na przykład poniższy kod definiuje interfejs za pomocą jednej funkcji, jednej właściwości i jedno zdarzenie.  
  
 [!code-vb[VbVbalrOOP#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#17)]  
  
## <a name="implementing-interfaces"></a>Implementowanie interfejsów.  
 Visual Basic słowa zarezerwowanego `Implements` jest używany na dwa sposoby. `Implements` Instrukcji oznacza, że klasa lub struktura implementuje interfejs. `Implements` — Słowo kluczowe oznacza, że składowej klasy lub element członkowski struktury implementuje składową określonego interfejsu.  
  
### <a name="implements-statement"></a>Implements — Instrukcja  
 Jeśli klasa lub struktura implementuje co najmniej jeden interfejs, musi on zawierać `Implements` instrukcji natychmiast po `Class` lub `Structure` instrukcji. `Implements` Instrukcja wymaga rozdzielaną przecinkami listę interfejsów, które powinny być implementowane przez klasy. Klasa lub struktura musi implementować wszyscy członkowie interfejsu przy użyciu `Implements` — słowo kluczowe.  
  
### <a name="implements-keyword"></a>Implements — słowo kluczowe  
 `Implements` — Słowo kluczowe wymaga rozdzielaną przecinkami listę elementów członkowskich interfejs do zaimplementowania. Ogólnie rzecz biorąc tylko członek jeden interfejs jest określony, ale można określić wiele elementów członkowskich. Specyfikacja elementu członkowskiego interfejsu, który składa się z nazwy interfejsu, która musi być określona w instrukcji implementuje w obrębie klasy; w okresie; i nazwa funkcji składowej, właściwość lub zdarzenie, które mają zostać wdrożone. Nazwa elementu członkowskiego, który implementuje składową interfejsu można użyć dowolnego dozwolonym identyfikatorem, a nie jest ograniczona do `InterfaceName_MethodName` Konwencji stosowane we wcześniejszych wersjach programu Visual Basic.  
  
 Na przykład, poniższy kod pokazuje sposób deklarowania procedurę o nazwie `Sub1` który implementuje metodę interfejsu:  
  
 [!code-vb[VbVbalrOOP#69](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#69)]  
  
 Typy parametrów i zwracane typy implementujące elementu członkowskiego musi być zgodna deklaracja właściwości lub elementu członkowskiego interfejsu w interfejsie. Najczęstszym sposobem wdrożenia elementu interfejsu jest z elementem członkowskim, który ma taką samą nazwę jak interfejs, jak pokazano w poprzednim przykładzie.  
  
 Aby zadeklarować implementację metody interfejsu, należy użyć wszelkie atrybuty, które są dopuszczalne w deklaracjach metody wystąpienia, w tym `Overloads`, `Overrides`, `Overridable`, `Public`, `Private`, `Protected`, `Friend`, `Protected Friend`, `MustOverride`, `Default`, i `Static`. `Shared` Atrybutu jest niedozwolona, ponieważ definiuje klasę zamiast metodą wystąpienia.  
  
 Za pomocą `Implements`, można także napisać pojedynczą metodę, która implementuje wiele metod zdefiniowane w interfejsie, jak w poniższym przykładzie:  
  
 [!code-vb[VbVbalrOOP#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#70)]  
  
 Aby implementować składowej interfejsu, można użyć od prywatnej składowej. Od prywatnej składowej implementuje składową interfejsu, ten element staje się dostępna za pomocą interfejsu mimo że nie jest dostępne bezpośrednio na zmienne obiektów w klasie.  
  
### <a name="interface-implementation-examples"></a>Przykłady implementacji interfejsu  
 Klasy, które implementują interfejs musi implementować jego właściwości, metody i zdarzenia.  
  
 W poniższym przykładzie zdefiniowano dwa interfejsy. Drugi interfejs `Interface2`, dziedziczy `Interface1` i definiuje dodatkowe właściwości i metody.  
  
 [!code-vb[VbVbalrOOP#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#39)]  
  
 Następny przykład implementuje `Interface1`, interfejs zdefiniowane w poprzednim przykładzie:  
  
 [!code-vb[VbVbalrOOP#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#40)]  
  
 Implementuje w ostatnim przykładzie `Interface2`, włącznie z metodą odziedziczone `Interface1`:  
  
 [!code-vb[VbVbalrOOP#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#41)]  
  
 Można zaimplementować właściwości tylko do odczytu z właściwością odczytu i zapisu (oznacza to, że nie masz do deklarowania go tylko do odczytu w klasy implementującej).  Implementowanie interfejsu zobowiązuje się do implementacji co najmniej elementów członkowskich, które deklaruje interfejs, ale może oferować więcej funkcji, takich jak co Twoja własność można było zapisywać.  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Przewodnik: tworzenie i implementowanie interfejsów](../../../../visual-basic/programming-guide/language-features/interfaces/walkthrough-creating-and-implementing-interfaces.md)|Zawiera szczegółowe procedury, która przeprowadzi Cię przez proces definiowania i wdrażania własnego interfejsu.|  
|[Wariancje w interfejsach ogólnych](../../concepts/covariance-contravariance/variance-in-generic-interfaces.md)|W tym artykule omówiono Kowariancja i kontrawariancja w interfejsach ogólnych i zawiera listę interfejsów ogólnych typu variant w programie .NET Framework.|
