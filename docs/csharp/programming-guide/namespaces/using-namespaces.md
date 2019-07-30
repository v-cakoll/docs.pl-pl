---
title: Korzystanie z przestrzeni C# nazw — Przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- cs.names
helpviewer_keywords:
- fully qualified names [C#]
- namespaces [C#], how to use
ms.assetid: 1fe8bf39-addc-438a-bd9e-86410e32381d
ms.openlocfilehash: bf194e207262ecea0511a0b67bbafeadd8d5d31d
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68629492"
---
# <a name="using-namespaces-c-programming-guide"></a>Używanie przestrzeni nazw (Przewodnik programowania w języku C#)
Przestrzenie nazw są intensywnie używane w C# programach na dwa sposoby. Po pierwsze klasy .NET Framework używają przestrzeni nazw do organizowania wielu klas. Po drugie, zadeklarowanie własnych przestrzeni nazw może pomóc w kontroli zakresu nazw klas i metod w większych projektach programistycznych.  
  
## <a name="accessing-namespaces"></a>Uzyskiwanie dostępu do przestrzeni nazw  
 Większość C# aplikacji rozpoczyna się od sekcji `using` dyrektywy. Ta sekcja zawiera listę przestrzeni nazw, których aplikacja będzie często używać, i zapisuje programistę w celu określenia w pełni kwalifikowanej nazwy za każdym razem, gdy używana jest metoda, która jest zawarta w.  
  
 Na przykład, dołączając wiersz:  
  
 [!code-csharp[csProgGuide#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/using.cs#1)]  
  
 Na początku programu programista może użyć kodu:  
  
 [!code-csharp[csProgGuide#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#31)]  
  
 Zamiast:  
  
 [!code-csharp[csProgGuide#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#30)]  
  
## <a name="namespace-aliases"></a>Aliasy przestrzeni nazw  
 [Dyrektywy using](../../../csharp/language-reference/keywords/using-directive.md) można także użyć do utworzenia aliasu dla [przestrzeni nazw](../../../csharp/language-reference/keywords/namespace.md). Na przykład jeśli używasz wcześniej zapisywanej przestrzeni nazw, która zawiera zagnieżdżone przestrzenie nazw, możesz chcieć zadeklarować alias w celu zapewnienia skróconego sposobu odwoływania się do jednego w szczególności, jak w poniższym przykładzie:  
  
 [!code-csharp[csProgGuideNamespaces#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces2.cs#7)]  
  
## <a name="using-namespaces-to-control-scope"></a>Używanie przestrzeni nazw do sterowania zakresem  
 `namespace` Słowo kluczowe jest używane do deklarowania zakresu. Możliwość tworzenia zakresów w projekcie pomaga organizować kod i umożliwia tworzenie typów unikatowych globalnie. W poniższym przykładzie Klasa zatytułowana `SampleClass` jest zdefiniowana w dwóch przestrzeniach nazw, jedna zagnieżdżona w drugim. [Operator `.` dostępu do elementów członkowskich](../../language-reference/operators/member-access-operators.md#member-access-operator-) jest używany do odróżnienia metody wywoływanej.  
  
 [!code-csharp[csProgGuideNamespaces#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#8)]  
  
## <a name="fully-qualified-names"></a>W pełni kwalifikowane nazwy  
 Przestrzenie nazw i typy mają unikatowe tytuły opisane przez w pełni kwalifikowane nazwy wskazujące hierarchię logiczną. Na przykład instrukcja `A.B` oznacza, że `A` jest nazwą przestrzeni nazw lub typem, i `B` jest zagnieżdżona wewnątrz niej.  
  
 W poniższym przykładzie istnieją zagnieżdżone klasy i przestrzenie nazw. W pełni kwalifikowana nazwa jest wskazywana jako komentarz po każdej jednostce.  
  
 [!code-csharp[csProgGuideNamespaces#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#9)]  
  
 W poprzednim segmencie kodu:  
  
- Przestrzeń nazw `N1` jest członkiem globalnej przestrzeni nazw. Jego w pełni kwalifikowana nazwa `N1`jest.  
  
- Przestrzeń nazw `N2` jest `N1`członkiem. Jego w pełni kwalifikowana nazwa `N1.N2`jest.  
  
- Klasa `C1` jest`N1`członkiem. Jego w pełni kwalifikowana nazwa `N1.C1`jest.  
  
- Nazwa `C2` klasy jest używana dwa razy w tym kodzie. Jednak w pełni kwalifikowane nazwy są unikatowe. Pierwsze wystąpienie `C2` jest zadeklarowane wewnątrz `C1`; w związku z tym jego w pełni kwalifikowana nazwa `N1.C1.C2`to:. Drugie wystąpienie `C2` jest zadeklarowane wewnątrz przestrzeni nazw `N2`; w związku z tym jego w pełni kwalifikowana `N1.N2.C2`nazwa jest.  
  
 Korzystając z poprzedniego segmentu kodu, można dodać nowy element członkowski `C3`klasy,, do przestrzeni nazw `N1.N2` w następujący sposób:  
  
 [!code-csharp[csProgGuideNamespaces#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#10)]  
  
 Ogólnie rzecz biorąc służy `::` do odwoływania się do aliasu przestrzeni nazw lub `global::` odwoływania `.` się do globalnej przestrzeni nazw oraz do kwalifikowania typów lub członków.  
  
 Jest to błąd używany `::` z aliasem, który odwołuje się do typu zamiast przestrzeni nazw. Przykład:  
  
 [!code-csharp[csProgGuideNamespaces#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces2.cs#11)]  
  
 [!code-csharp[csProgGuideNamespaces#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces2.cs#12)]  
  
 Należy pamiętać, że `global` słowo nie jest wstępnie zdefiniowanym aliasem `global.X` ; w związku z tym nie ma żadnych specjalnych znaczenia. Uzyskuje specjalne znaczenie tylko wtedy, gdy jest używany z `::`.  
  
 Ostrzeżenie kompilatora CS0440 jest generowany, jeśli zdefiniujesz alias o nazwie Global `global::` , ponieważ zawsze odwołuje się do globalnej przestrzeni nazw, a nie do aliasu. Na przykład poniższy wiersz generuje ostrzeżenie:  
  
 [!code-csharp[csProgGuideNamespaces#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces2.cs#13)]  
  
 Korzystanie `::` z aliasów jest dobrym pomysłem i chroni przed nieoczekiwanym wprowadzeniem dodatkowych typów. Rozważmy na przykład ten przykład:  
  
 [!code-csharp[csProgGuideNamespaces#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#14)]  
  
 [!code-csharp[csProgGuideNamespaces#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#15)]  
  
 To działa, ale jeśli typ nazwany `Alias` miał zostać później wprowadzony, `Alias.` zostałby powiązać z tym typem. Użycie `Alias::Exception` gwarantuje, `Alias` że jest traktowany jako alias przestrzeni nazw i nie zostanie pomylony z typem.  
  
 Zapoznaj się [z tematem How to: Aby uzyskać więcej informacji na](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md) `global` temat aliasu, Użyj globalnego aliasu przestrzeni nazw.  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
- [Przestrzenie nazw](../../../csharp/programming-guide/namespaces/index.md)
- [. operator](../../../csharp/language-reference/operators/member-access-operators.md#member-access-operator-)
- [:: operator](../../../csharp/language-reference/operators/namespace-alias-qualifier.md)
- [extern alias](../../../csharp/language-reference/keywords/extern-alias.md)
