---
title: Korzystanie z przestrzeni nazw — Przewodnik programowania w języku C#
ms.date: 07/20/2015
f1_keywords:
- cs.names
helpviewer_keywords:
- fully qualified names [C#]
- namespaces [C#], how to use
ms.assetid: 1fe8bf39-addc-438a-bd9e-86410e32381d
ms.openlocfilehash: 71d97f7c1c0c3ece0cdce3de4318d8a9d65baed3
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2020
ms.locfileid: "84241932"
---
# <a name="using-namespaces-c-programming-guide"></a>Używanie przestrzeni nazw (Przewodnik programowania w języku C#)

Przestrzenie nazw są intensywnie używane w programach C# na dwa sposoby. Po pierwsze klasy .NET używają przestrzeni nazw do organizowania wielu klas. Po drugie, zadeklarowanie własnych przestrzeni nazw może pomóc w kontroli zakresu nazw klas i metod w większych projektach programistycznych.  
  
## <a name="accessing-namespaces"></a>Uzyskiwanie dostępu do przestrzeni nazw

 Większość aplikacji C# zaczyna się od sekcji `using` dyrektywy. Ta sekcja zawiera listę przestrzeni nazw, których aplikacja będzie często używać, i zapisuje programistę w celu określenia w pełni kwalifikowanej nazwy za każdym razem, gdy używana jest metoda, która jest zawarta w.  
  
 Na przykład, dołączając wiersz:  
  
 [!code-csharp[csProgGuide#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/using.cs#1)]  
  
 Na początku programu programista może użyć kodu:  
  
 [!code-csharp[csProgGuide#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#31)]  
  
 Zamiast:  
  
 [!code-csharp[csProgGuide#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#30)]  
  
## <a name="namespace-aliases"></a>Aliasy przestrzeni nazw

 Możesz również użyć [ `using` dyrektywy](../../language-reference/keywords/using-directive.md) , aby utworzyć alias dla przestrzeni nazw. Użyj [kwalifikatora `::` aliasu przestrzeni nazw](../../language-reference/operators/namespace-alias-qualifier.md) , aby uzyskać dostęp do elementów członkowskich aliasu przestrzeni nazw. Poniższy przykład przedstawia sposób tworzenia i używania aliasu przestrzeni nazw:
  
[!code-csharp[csProgGuideNamespaces#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#5)]
  
## <a name="using-namespaces-to-control-scope"></a>Używanie przestrzeni nazw do sterowania zakresem

 `namespace`Słowo kluczowe jest używane do deklarowania zakresu. Możliwość tworzenia zakresów w projekcie pomaga organizować kod i umożliwia tworzenie typów unikatowych globalnie. W poniższym przykładzie Klasa zatytułowana `SampleClass` jest zdefiniowana w dwóch przestrzeniach nazw, jedna zagnieżdżona w drugim. [ `.` Token](../../language-reference/operators/member-access-operators.md#member-access-expression-) jest używany do odróżnienia metody wywoływanej.  
  
 [!code-csharp[csProgGuideNamespaces#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#8)]  
  
## <a name="fully-qualified-names"></a>W pełni kwalifikowane nazwy

 Przestrzenie nazw i typy mają unikatowe tytuły opisane przez w pełni kwalifikowane nazwy wskazujące hierarchię logiczną. Na przykład instrukcja oznacza, `A.B` że `A` jest nazwą przestrzeni nazw lub typem, i `B` jest zagnieżdżona wewnątrz niej.  
  
 W poniższym przykładzie istnieją zagnieżdżone klasy i przestrzenie nazw. W pełni kwalifikowana nazwa jest wskazywana jako komentarz po każdej jednostce.  
  
 [!code-csharp[csProgGuideNamespaces#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#9)]  
  
 W poprzednim segmencie kodu:  
  
- Przestrzeń nazw `N1` jest członkiem globalnej przestrzeni nazw. Jego w pełni kwalifikowana nazwa jest `N1` .  
  
- Przestrzeń nazw `N2` jest członkiem `N1` . Jego w pełni kwalifikowana nazwa jest `N1.N2` .  
  
- Klasa `C1` jest członkiem `N1` . Jego w pełni kwalifikowana nazwa jest `N1.C1` .  
  
- Nazwa klasy `C2` jest używana dwa razy w tym kodzie. Jednak w pełni kwalifikowane nazwy są unikatowe. Pierwsze wystąpienie `C2` jest zadeklarowane wewnątrz `C1` ; w związku z tym jego w pełni kwalifikowana nazwa to: `N1.C1.C2` . Drugie wystąpienie `C2` jest zadeklarowane wewnątrz przestrzeni nazw `N2` ; w związku z tym jego w pełni kwalifikowana nazwa jest `N1.N2.C2` .  
  
 Korzystając z poprzedniego segmentu kodu, można dodać nowy element członkowski klasy, `C3` , do przestrzeni nazw `N1.N2` w następujący sposób:  
  
 [!code-csharp[csProgGuideNamespaces#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#10)]  
  
 Ogólnie rzecz biorąc, użyj [kwalifikatora `::` aliasu przestrzeni nazw](../../language-reference/operators/namespace-alias-qualifier.md) , aby odwołać się do aliasu przestrzeni nazw lub `global::` odwoływać się do globalnej przestrzeni nazw oraz `.` do kwalifikowania typów lub członków.  
  
 Jest to błąd używany `::` z aliasem, który odwołuje się do typu zamiast przestrzeni nazw. Przykład:  
  
 [!code-csharp[csProgGuideNamespaces#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces2.cs#11)]  
  
 [!code-csharp[csProgGuideNamespaces#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces2.cs#12)]  
  
 Należy pamiętać, że słowo `global` nie jest wstępnie zdefiniowanym aliasem; w związku z tym nie `global.X` ma żadnych specjalnych znaczenia. Uzyskuje specjalne znaczenie tylko wtedy, gdy jest używany z `::` .  
  
 Ostrzeżenie kompilatora CS0440 jest generowany, jeśli zdefiniujesz alias o nazwie Global, ponieważ `global::` zawsze odwołuje się do globalnej przestrzeni nazw, a nie do aliasu. Na przykład poniższy wiersz generuje ostrzeżenie:  
  
 [!code-csharp[csProgGuideNamespaces#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces2.cs#13)]  
  
 Korzystanie `::` z aliasów jest dobrym pomysłem i chroni przed nieoczekiwanym wprowadzeniem dodatkowych typów. Rozważmy na przykład ten przykład:  
  
 [!code-csharp[csProgGuideNamespaces#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#14)]  
  
 [!code-csharp[csProgGuideNamespaces#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#15)]  
  
 To działa, ale jeśli typ nazwany `Alias` miał zostać później wprowadzony, `Alias.` zostałby powiązać z tym typem. Użycie `Alias::Exception` gwarantuje, że `Alias` jest traktowany jako alias przestrzeni nazw i nie zostanie pomylony z typem.  

## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania w języku C#](../index.md)
- [Przestrzenie nazw](./index.md)
- [Wyrażenie dostępu do składowej](../../language-reference/operators/member-access-operators.md#member-access-expression-)
- [:: — Operator](../../language-reference/operators/namespace-alias-qualifier.md)
- [alias zewnętrzny](../../language-reference/keywords/extern-alias.md)
