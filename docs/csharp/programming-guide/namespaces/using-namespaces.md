---
title: Korzystanie z obszarów nazw — przewodnik po programowaniu języka C#
ms.date: 07/20/2015
f1_keywords:
- cs.names
helpviewer_keywords:
- fully qualified names [C#]
- namespaces [C#], how to use
ms.assetid: 1fe8bf39-addc-438a-bd9e-86410e32381d
ms.openlocfilehash: b4326be8c9e299a96477096ec21864ec69037abe
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2020
ms.locfileid: "81738241"
---
# <a name="using-namespaces-c-programming-guide"></a>Korzystanie z obszarów nazw (Przewodnik programowania języka C#)

Przestrzenie nazw są intensywnie używane w programach Języka C# na dwa sposoby. Po pierwsze klasy .NET Framework używają obszarów nazw do organizowania wielu klas. Po drugie, deklarowanie własnych obszarów nazw może pomóc kontrolować zakres nazw klas i metod w większych projektach programowania.  
  
## <a name="accessing-namespaces"></a>Uzyskiwanie dostępu do obszarów nazw

 Większość aplikacji Języka C# `using` rozpoczyna się od sekcji dyrektyw. W tej sekcji wymieniono obszary nazw, które aplikacja będzie często używać i zapisuje programistę z określania w pełni kwalifikowanej nazwy za każdym razem, gdy używana jest metoda, która jest zawarta w.  
  
 Na przykład, dołączając wiersz:  
  
 [!code-csharp[csProgGuide#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/using.cs#1)]  
  
 Na początku programu programista może użyć kodu:  
  
 [!code-csharp[csProgGuide#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#31)]  
  
 Zamiast:  
  
 [!code-csharp[csProgGuide#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#30)]  
  
## <a name="namespace-aliases"></a>Aliasy obszaru nazw

 Można również użyć [ `using` dyrektywy](../../language-reference/keywords/using-directive.md) do utworzenia aliasu dla obszaru nazw. Użyj [kwalifikatora `::` aliasu obszaru nazw,](../../language-reference/operators/namespace-alias-qualifier.md) aby uzyskać dostęp do członków aliasowanego obszaru nazw. W poniższym przykładzie pokazano, jak utworzyć i używać aliasu obszaru nazw:
  
[!code-csharp[csProgGuideNamespaces#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#5)]
  
## <a name="using-namespaces-to-control-scope"></a>Sterowanie zakresem za pomocą obszarów nazw

 Słowo `namespace` kluczowe służy do deklarowania zakresu. Możliwość tworzenia zakresów w projekcie pomaga organizować kod i umożliwia tworzenie typów unikatowych globalnie. W poniższym przykładzie klasa `SampleClass` zatytułowana jest zdefiniowana w dwóch obszarach nazw, jeden zagnieżdżony wewnątrz drugiego. [ `.` Token](../../language-reference/operators/member-access-operators.md#member-access-expression-) jest używany do rozróżniania, która metoda zostanie wywołana.  
  
 [!code-csharp[csProgGuideNamespaces#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#8)]  
  
## <a name="fully-qualified-names"></a>W pełni kwalifikowane nazwy

 Przestrzenie nazw i typy mają unikatowe tytuły opisane przez w pełni kwalifikowane nazwy, które wskazują hierarchię logiczną. Na przykład instrukcja `A.B` oznacza, że `A` jest nazwą obszaru nazw `B` lub typu i jest zagnieżdżona wewnątrz niego.  
  
 W poniższym przykładzie istnieją zagnieżdżone klasy i przestrzenie nazw. W pełni kwalifikowana nazwa jest wskazywana jako komentarz po każdej jednostce.  
  
 [!code-csharp[csProgGuideNamespaces#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#9)]  
  
 W poprzednim segmencie kodu:  
  
- Obszar `N1` nazw jest członkiem globalnej przestrzeni nazw. Jego w pełni `N1`kwalifikowana nazwa to .  
  
- Obszar `N2` nazw jest członkiem programu `N1`. Jego w pełni `N1.N2`kwalifikowana nazwa to .  
  
- Klasa `C1` jest członkiem `N1`. Jego w pełni `N1.C1`kwalifikowana nazwa to .  
  
- Nazwa `C2` klasy jest używana dwa razy w tym kodzie. Jednak w pełni kwalifikowane nazwy są unikatowe. Pierwsza instancja `C2` jest `C1`zadeklarowana wewnątrz ; w związku z tym jego `N1.C1.C2`w pełni kwalifikowana nazwa to: . Drugie wystąpienie `C2` jest zadeklarowane `N2`wewnątrz obszaru nazw; w związku z tym `N1.N2.C2`jego w pełni kwalifikowana nazwa jest .  
  
 Korzystając z poprzedniego segmentu kodu, można `C3`dodać nowy element `N1.N2` członkowski klasy do obszaru nazw w następujący sposób:  
  
 [!code-csharp[csProgGuideNamespaces#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#10)]  
  
 Ogólnie rzecz biorąc, należy użyć [kwalifikatora `::` aliasu obszaru nazw,](../../language-reference/operators/namespace-alias-qualifier.md) aby odwołać się do aliasu obszaru nazw lub `global::` odwołać się do globalnego obszaru nazw i `.` zakwalifikować typy lub elementy członkowskie.  
  
 Jest to błąd `::` do użycia z aliasem, który odwołuje się do typu zamiast obszaru nazw. Przykład:  
  
 [!code-csharp[csProgGuideNamespaces#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces2.cs#11)]  
  
 [!code-csharp[csProgGuideNamespaces#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces2.cs#12)]  
  
 Należy pamiętać, `global` że słowo nie jest wstępnie zdefiniowanym aliasem; w związku `global.X` z tym nie ma żadnego szczególnego znaczenia. Nabiera specjalnego znaczenia tylko wtedy, gdy `::`jest używany z .  
  
 Ostrzeżenie kompilatora CS0440 jest generowane, jeśli `global::` zdefiniowano alias o nazwie globalny, ponieważ zawsze odwołuje się do globalnej przestrzeni nazw, a nie aliasu. Na przykład następujący wiersz generuje ostrzeżenie:  
  
 [!code-csharp[csProgGuideNamespaces#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces2.cs#13)]  
  
 Używanie `::` z aliasami jest dobrym pomysłem i chroni przed nieoczekiwanym wprowadzeniem dodatkowych typów. Rozważmy na przykład:  
  
 [!code-csharp[csProgGuideNamespaces#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#14)]  
  
 [!code-csharp[csProgGuideNamespaces#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#15)]  
  
 To działa, ale jeśli `Alias` typ o nazwie `Alias.` zostały następnie wprowadzone, będzie powiązana z tego typu zamiast. Korzystanie `Alias::Exception` zapewnia, `Alias` że jest traktowany jako alias obszaru nazw i nie mylone z typem.  

## <a name="see-also"></a>Zobacz też

- [C# Przewodnik programowania](../index.md)
- [Namespaces](./index.md)
- [Wyrażenie dostępu do elementu członkowskiego](../../language-reference/operators/member-access-operators.md#member-access-expression-)
- [:: — Operator](../../language-reference/operators/namespace-alias-qualifier.md)
- [alias zewnętrzny](../../language-reference/keywords/extern-alias.md)
