---
title: Używanie przestrzeni nazw (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
f1_keywords:
- cs.names
helpviewer_keywords:
- fully qualified names [C#]
- namespaces [C#], how to use
ms.assetid: 1fe8bf39-addc-438a-bd9e-86410e32381d
ms.openlocfilehash: 81876d1818a6e82764e4aea0ae2b6f9e091f0ba3
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/04/2018
ms.locfileid: "48579111"
---
# <a name="using-namespaces-c-programming-guide"></a>Używanie przestrzeni nazw (Przewodnik programowania w języku C#)
Przestrzenie nazw są intensywnie używane w programach języka C# na dwa sposoby. Po pierwsze klas .NET Framework umożliwia organizowanie jego wiele klas przestrzenie nazw. Po drugie deklarowania własne przestrzenie nazw może kontrolować zakres klasy i metody nazwy w dużych projektach programowania.  
  
## <a name="accessing-namespaces"></a>Uzyskiwanie dostępu do przestrzeni nazw  
 Większość aplikacji C# zaczynają się od sekcji `using` dyrektywy. Ta sekcja zawiera przestrzenie nazw, aplikacja będzie najczęściej używana i zapisuje programistę z określania każdym użyciu metody, która jest zawarta w pełni kwalifikowana nazwa.  
  
 Na przykład, w tym wierszu:  
  
 [!code-csharp[csProgGuide#1](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/using-namespaces_1.cs)]  
  
 Na początku programu programisty należy użyć kodu:  
  
 [!code-csharp[csProgGuide#31](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/using-namespaces_2.cs)]  
  
 Zamiast:  
  
 [!code-csharp[csProgGuide#30](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/using-namespaces_3.cs)]  
  
## <a name="namespace-aliases"></a>Aliasy Namespace  
 [Użycie dyrektywy](../../../csharp/language-reference/keywords/using-directive.md) może również służyć do tworzenia aliasów [przestrzeni nazw](../../../csharp/language-reference/keywords/namespace.md). Na przykład jeśli używasz poprzednio wpisaną przestrzeni nazw, która zawiera zagnieżdżone przestrzenie nazw, możesz zechcieć do deklarowania aliasem, aby umożliwić odwoływanie się do jednego w szczególności, jak w poniższym przykładzie skrót:  
  
 [!code-csharp[csProgGuideNamespaces#7](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_4.cs)]  
  
## <a name="using-namespaces-to-control-scope"></a>Używanie przestrzeni nazw do zakresu kontroli  
 `namespace` Słowo kluczowe jest używane do deklarowania zakresu. Możliwość tworzenia zakresów w obrębie projektu ułatwia organizowanie kodu i pozwala na tworzenie typów globalnie unikatowa. W poniższym przykładzie klasę o nazwie `SampleClass` jest zdefiniowany w dwie przestrzenie nazw, jednej zagnieżdżone wewnątrz innych. [. Operator](../../../csharp/language-reference/operators/member-access-operator.md) jest używany do odróżnienia, która metoda jest wywoływana.  
  
 [!code-csharp[csProgGuideNamespaces#8](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_5.cs)]  
  
## <a name="fully-qualified-names"></a>W pełni kwalifikowane nazwy  
 Obszary nazw i typy mają unikatowe tytuły opisanego przez w pełni kwalifikowanych nazw, które wskazują logicznej hierarchii. Na przykład instrukcja `A.B` oznacza, że `A` jest nazwą przestrzeni nazw lub typu, i `B` zagnieździć go.  
  
 W poniższym przykładzie istnieją zagnieżdżonych klas i przestrzenie nazw. W pełni kwalifikowana nazwa jest wskazywane jako komentarz następujące każdej jednostki.  
  
 [!code-csharp[csProgGuideNamespaces#9](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_6.cs)]  
  
 W poprzednim segment kodu:  
  
-   Przestrzeń nazw `N1` jest elementem członkowskim globalnej przestrzeni nazw. Jego w pełni kwalifikowana nazwa to `N1`.  
  
-   Przestrzeń nazw `N2` jest elementem członkowskim `N1`. Jego w pełni kwalifikowana nazwa to `N1.N2`.  
  
-   Klasa `C1` jest elementem członkowskim `N1`. Jego w pełni kwalifikowana nazwa to `N1.C1`.  
  
-   Nazwa klasy `C2` jest używany na dwa razy, w tym kodzie. Jednak w pełni kwalifikowane nazwy są unikatowe. Pierwsze wystąpienie `C2` jest zadeklarowana wewnątrz `C1`; w związku z tym, jego w pełni kwalifikowana nazwa to: `N1.C1.C2`. Drugie wystąpienie `C2` jest zadeklarowany wewnątrz przestrzeni nazw `N2`; w związku z tym, jego w pełni kwalifikowana nazwa to `N1.N2.C2`.  
  
 Korzystając z poprzedniego segmentu kodu, można dodać nowy element członkowski klasy `C3`, do przestrzeni nazw `N1.N2` w następujący sposób:  
  
 [!code-csharp[csProgGuideNamespaces#10](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_7.cs)]  
  
 Ogólnie rzecz biorąc, użyj `::` można odwoływać się do aliasu przestrzeni nazw lub `global::` można odwoływać się do globalnej przestrzeni nazw i `.` kwalifikowania typów ani elementów członkowskich.  
  
 Jest to błąd, aby użyć `::` z aliasem, który odwołuje się do typu, a nie przestrzeń nazw. Na przykład:  
  
 [!code-csharp[csProgGuideNamespaces#11](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_8.cs)]  
  
 [!code-csharp[csProgGuideNamespaces#12](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_9.cs)]  
  
 Należy pamiętać, że wyraz `global` nie jest wstępnie zdefiniowanej w alias; w związku z tym, `global.X` nie ma żadnego specjalnego znaczenia. Uzyskuje, specjalne, co oznacza tylko wtedy, gdy jest używana z `::`.  
  
 Kompilator ostrzeżenie CS0440 jest generowany, jeśli zdefiniujesz aliasu o nazwie global ponieważ `global::` zawsze odwołuje się do globalnej przestrzeni nazw, a nie do aliasu. Na przykład następujące polecenie generuje ostrzeżenie:  
  
 [!code-csharp[csProgGuideNamespaces#13](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_10.cs)]  
  
 Za pomocą `::` dobrym pomysłem jest z użyciem aliasów i chroni przed nieoczekiwanego wprowadzenia dodatkowych typów. Na przykład rozważmy następujący przykład:  
  
 [!code-csharp[csProgGuideNamespaces#14](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_11.cs)]  
  
 [!code-csharp[csProgGuideNamespaces#15](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_12.cs)]  
  
 To działa, ale jeśli typu o nazwie `Alias` zostały następnie zostać wprowadzony `Alias.` czy zamiast tego powiązania do tego typu. Za pomocą `Alias::Exception` ubezpieczycielom, `Alias` jest traktowana jako alias przestrzeni nazw, a nie mylone z typem.  
  
 Zobacz temat [instrukcje: użycie globalnych aliasów Namespace](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md) Aby uzyskać więcej informacji dotyczących `global` alias.  
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Przestrzenie nazw](../../../csharp/programming-guide/namespaces/index.md)  
- [Słowa kluczowe przestrzeni nazw](../../../csharp/language-reference/keywords/namespace-keywords.md)  
- [. operator](../../../csharp/language-reference/operators/member-access-operator.md)  
- [::, operator](../../../csharp/language-reference/operators/namespace-alias-qualifer.md)  
- [extern](../../../csharp/language-reference/keywords/extern.md)
