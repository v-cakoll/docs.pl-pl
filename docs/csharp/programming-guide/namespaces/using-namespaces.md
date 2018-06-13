---
title: Używanie przestrzeni nazw (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
f1_keywords:
- cs.names
helpviewer_keywords:
- fully qualified names [C#]
- namespaces [C#], how to use
ms.assetid: 1fe8bf39-addc-438a-bd9e-86410e32381d
ms.openlocfilehash: 773add221317a2154ac620acf766607ec22c629d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33329550"
---
# <a name="using-namespaces-c-programming-guide"></a>Używanie przestrzeni nazw (Przewodnik programowania w języku C#)
Przestrzenie nazw silnie są używane w ramach programów C# na dwa sposoby. Po pierwsze klas .NET Framework umożliwia organizowanie jego wiele klas przestrzeni nazw. Po drugie deklarowanie własnych przestrzeni nazw można kontrolować zakres klasy i metody nazwy w większych projektów programowania.  
  
## <a name="accessing-namespaces"></a>Uzyskiwanie dostępu do przestrzeni nazw  
 Większość aplikacji C# zaczynać sekcję `using` dyrektywy. Ta sekcja zawiera listę nazw często można za pomocą aplikacji i zapisuje programisty z określania każdym użyciu metody, która jest zawarta w pełni kwalifikowanej nazwy.  
  
 Na przykład umieszczając w niej wiersz:  
  
 [!code-csharp[csProgGuide#1](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/using-namespaces_1.cs)]  
  
 Na początku programu programistę można użyć kodu:  
  
 [!code-csharp[csProgGuide#31](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/using-namespaces_2.cs)]  
  
 Zamiast:  
  
 [!code-csharp[csProgGuide#30](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/using-namespaces_3.cs)]  
  
## <a name="namespace-aliases"></a>Aliasy Namespace  
 [Dyrektywa using](../../../csharp/language-reference/keywords/using-directive.md) może również służyć do tworzenia aliasu dla [przestrzeni nazw](../../../csharp/language-reference/keywords/namespace.md). Na przykład jeśli używasz wcześniej zapisany przestrzeni nazw, która zawiera zagnieżdżone przestrzeni nazw można deklarować aliasu, aby zapewnić sposób skrócona odwołujące się do jednego w szczególności, jak w poniższym przykładzie:  
  
 [!code-csharp[csProgGuideNamespaces#7](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_4.cs)]  
  
## <a name="using-namespaces-to-control-scope"></a>Używanie przestrzeni nazw do zakresu kontroli  
 `namespace` — Słowo kluczowe służy do deklarowania zakresu. Możliwość tworzenia zakresów w ramach projektu ułatwia organizowanie kodu i umożliwia utworzenie typów globalnie unikatowe. W poniższym przykładzie klasa zatytułowany `SampleClass` jest zdefiniowany w dwóch obszarach nazw jedną zagnieżdżone w innych. [. Operator](../../../csharp/language-reference/operators/member-access-operator.md) służy do rozróżnienia, która metoda jest wywoływana.  
  
 [!code-csharp[csProgGuideNamespaces#8](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_5.cs)]  
  
## <a name="fully-qualified-names"></a>W pełni kwalifikowane nazwy  
 Obszary nazw i typy mają unikatowe tytułów opisanego przez w pełni kwalifikowane nazwy wskazujące logicznej hierarchii. Na przykład instrukcja `A.B` oznacza, że `A` jest nazwą przestrzeni nazw lub typu, i `B` jest zagnieżdżony w nim.  
  
 W poniższym przykładzie są zagnieżdżone klasy i przestrzenie nazw. W pełni kwalifikowana nazwa jest oznaczony jako komentarz po każdej jednostki.  
  
 [!code-csharp[csProgGuideNamespaces#9](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_6.cs)]  
  
 W poprzednich segment kodu:  
  
-   Przestrzeń nazw `N1` jest członkiem grupy globalnej przestrzeni nazw. Jest w pełni kwalifikowanej nazwy `N1`.  
  
-   Przestrzeń nazw `N2` jest elementem członkowskim `N1`. Jest w pełni kwalifikowanej nazwy `N1.N2`.  
  
-   Klasa `C1` jest elementem członkowskim `N1`. Jest w pełni kwalifikowanej nazwy `N1.C1`.  
  
-   Nazwa klasy `C2` służy dwa razy w tym kodzie. Jednak w pełni kwalifikowane nazwy są unikatowe. Pierwsze wystąpienie `C2` jest zadeklarowana wewnątrz `C1`; w związku z tym jest w pełni kwalifikowanej nazwy: `N1.C1.C2`. Drugie wystąpienie parametru `C2` jest zadeklarowany wewnątrz przestrzeni nazw `N2`; w związku z tym jest w pełni kwalifikowanej nazwy `N1.N2.C2`.  
  
 Używając poprzedniego segmentu kodu, można dodać nowy element członkowski klasy `C3`, do przestrzeni nazw `N1.N2` w następujący sposób:  
  
 [!code-csharp[csProgGuideNamespaces#10](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_7.cs)]  
  
 Ogólnie rzecz biorąc, użyj `::` do odwołania aliasu przestrzeni nazw lub `global::` do odwołania globalnej przestrzeni nazw i `.` na kwalifikować się do typów albo elementów członkowskich.  
  
 Jest błędem `::` z aliasem odwołuje się do typu zamiast przestrzeni nazw. Na przykład:  
  
 [!code-csharp[csProgGuideNamespaces#11](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_8.cs)]  
  
 [!code-csharp[csProgGuideNamespaces#12](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_9.cs)]  
  
 Należy pamiętać, że wyraz `global` nie jest wstępnie zdefiniowanej alias; w związku z tym `global.X` nie ma żadnego specjalnego znaczenia. Uzyskuje, specjalne, co oznacza tylko wtedy, gdy jest używany z `::`.  
  
 Kompilator ostrzeżenie CS0440 jest generowany w przypadku definiowania aliasu o nazwie global ponieważ `global::` zawsze odwołuje się do globalnej przestrzeni nazw, a nie do aliasu. Na przykład poniższy wiersz generuje ostrzeżenie:  
  
 [!code-csharp[csProgGuideNamespaces#13](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_10.cs)]  
  
 Przy użyciu `::` z aliasami dobrym pomysłem jest i chroni przed wprowadzeniem nieoczekiwany dodatkowe typy. Rozważmy na przykład w tym przykładzie:  
  
 [!code-csharp[csProgGuideNamespaces#14](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_11.cs)]  
  
 [!code-csharp[csProgGuideNamespaces#15](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_12.cs)]  
  
 To działa, ale jeśli typu o nazwie `Alias` były następnie zostać wprowadzony, `Alias.` czy zamiast tego powiązania dla tego typu. Przy użyciu `Alias::Exception` temu, że `Alias` jest traktowane jako alias przestrzeni nazw i nie pomylone typu.  
  
 Zobacz temat [porady: użycie globalnych aliasów Namespace](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md) Aby uzyskać więcej informacji dotyczących `global` alias.  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Przestrzenie nazw](../../../csharp/programming-guide/namespaces/index.md)  
 [Słowa kluczowe przestrzeni nazw](../../../csharp/language-reference/keywords/namespace-keywords.md)  
 [. operator](../../../csharp/language-reference/operators/member-access-operator.md)  
 [::, operator](../../../csharp/language-reference/operators/namespace-alias-qualifer.md)  
 [extern](../../../csharp/language-reference/keywords/extern.md)
