---
title: Korzystanie z konstruktorów — C# Przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- constructors [C#], about constructors
ms.assetid: 464253b2-fd5d-469a-836d-df0fdf2a43f7
ms.openlocfilehash: 018710f753df261fce28e2e1cae1272b36923a05
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/20/2019
ms.locfileid: "68363005"
---
# <a name="using-constructors-c-programming-guide"></a>Używanie konstruktorów (Przewodnik programowania w języku C#)

Gdy tworzona jest [Klasa](../../../csharp/language-reference/keywords/class.md) lub [Struktura](../../../csharp/language-reference/keywords/struct.md) , jego Konstruktor jest wywoływany. Konstruktory mają taką samą nazwę jak Klasa lub struktura i zazwyczaj inicjują elementy członkowskie danych nowego obiektu.  
  
 W poniższym przykładzie Klasa o nazwie `Taxi` jest definiowana przy użyciu prostego konstruktora. Ta klasa jest następnie tworzona przy użyciu operatora [New](../../../csharp/language-reference/operators/new-operator.md) . Konstruktor jest wywoływany `new` przez operatora natychmiast po przydzieleniu pamięci dla nowego obiektu. `Taxi`  
  
 [!code-csharp[csProgGuideObjects#53](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#53)]  
  
 Konstruktor, który nie pobiera parametrów, jest nazywany *konstruktorem bez parametrów*. Konstruktory bez parametrów są wywoływane za każdym razem, gdy obiekt jest skonkretyzowany `new` przy użyciu operatora i nie ma żadnych `new`argumentów. Aby uzyskać więcej informacji, zobacz [konstruktory wystąpień](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md).  
  
 O ile Klasa nie [](../../../csharp/language-reference/keywords/static.md)jest statyczna, klasy bez konstruktorów uzyskują publiczny Konstruktor bezparametrowy przez C# kompilator w celu włączenia tworzenia wystąpienia klasy. Aby uzyskać więcej informacji, zobacz [klasy statyczne i statyczne elementy członkowskie klas](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).  
  
 Można zapobiec tworzeniu wystąpienia klasy przez uczynienie konstruktora prywatnym w następujący sposób:  
  
 [!code-csharp[csProgGuideObjects#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#11)]  
  
 Aby uzyskać więcej informacji, zobacz [prywatne konstruktory](../../../csharp/programming-guide/classes-and-structs/private-constructors.md).  
  
 Konstruktory dla typów [struktur](../../../csharp/language-reference/keywords/struct.md) przypominają konstruktory klas `structs` , ale nie mogą zawierać jawnego konstruktora bez parametrów, ponieważ jeden jest dostarczany automatycznie przez kompilator. Ten konstruktor inicjuje każde pole w `struct` wartości domyślnych. Aby uzyskać więcej informacji, zobacz [tabela wartości domyślnych](../../../csharp/language-reference/keywords/default-values-table.md). Jednak ten konstruktor bez parametrów jest wywoływany tylko wtedy, `struct` gdy jest tworzone wystąpienie `new`z. Na przykład, ten kod używa konstruktora bez parametrów dla <xref:System.Int32>, aby mieć pewność, że liczba całkowita została zainicjowana:  
  
```csharp  
int i = new int();  
Console.WriteLine(i);  
```  
  
 Poniższy kod powoduje jednak błąd kompilatora, ponieważ nie używa `new`i ponieważ próbuje użyć obiektu, który nie został zainicjowany:  
  
```  
int i;  
Console.WriteLine(i);  
```  
  
 Alternatywnie obiekty oparte na ( `structs` w tym wszystkie wbudowane typy liczbowe) mogą być inicjowane lub przypisane, a następnie używane jak w poniższym przykładzie:  
  
```  
int a = 44;  // Initialize the value type...  
int b;  
b = 33;      // Or assign it before using it.  
Console.WriteLine("{0}, {1}", a, b);  
```  
  
 Wywołanie konstruktora bez parametrów dla typu wartości nie jest wymagane.  
  
 Obie klasy i `structs` mogą definiować konstruktory, które pobierają parametry. Konstruktory, które pobierają parametry, muszą `new` być wywoływane za pomocą instrukcji lub [podstawowej](../../../csharp/language-reference/keywords/base.md) instrukcji. Klasy i `structs` mogą także definiować wiele konstruktorów, a żaden z nich nie jest wymagany do definiowania konstruktora bez parametrów. Na przykład:  
  
 [!code-csharp[csProgGuideObjects#54](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#54)]  
  
 Tę klasę można utworzyć przy użyciu jednej z następujących instrukcji:  
  
 [!code-csharp[csProgGuideObjects#55](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#55)]  
  
 Konstruktor może użyć `base` słowa kluczowego do wywołania konstruktora klasy bazowej. Na przykład:  
  
 [!code-csharp[csProgGuideObjects#56](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#56)]  
  
 W tym przykładzie Konstruktor klasy bazowej jest wywoływany przed wykonaniem bloku dla konstruktora. `base` Słowo kluczowe może być używane z parametrami lub bez nich. Wszystkie parametry konstruktora mogą służyć jako parametry do `base`, lub jako część wyrażenia. Aby uzyskać więcej informacji, zobacz temat [Base](../../../csharp/language-reference/keywords/base.md).  
  
 W klasie pochodnej, jeśli Konstruktor klasy bazowej nie jest jawnie wywoływany za pomocą `base` słowa kluczowego, Konstruktor bez parametrów, jeśli istnieje, jest wywoływana niejawnie. Oznacza to, że następujące deklaracje konstruktora są efektywnie takie same:  
  
 [!code-csharp[csProgGuideObjects#58](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#58)]  
  
 [!code-csharp[csProgGuideObjects#57](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#57)]  
  
 Jeśli klasa bazowa nie oferuje konstruktora bez parametrów, Klasa pochodna musi jawnie wywołać konstruktora podstawowego przy użyciu `base`.  
  
 Konstruktor może wywołać innego konstruktora w tym samym obiekcie za pomocą słowa kluczowego [this](../../../csharp/language-reference/keywords/this.md) . Na przykład `this`,może być używany z parametrami lub bez nich, a wszystkie parametry w Konstruktorze są dostępne `this`jako parametry do, lub jako część wyrażenia. `base` Na przykład Drugi Konstruktor w poprzednim przykładzie można napisać ponownie przy użyciu `this`:  
  
 [!code-csharp[csProgGuideObjects#59](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#59)]  
  
 Użycie `this` słowa kluczowego w poprzednim przykładzie powoduje, że ten konstruktor jest wywoływany:  
  
 [!code-csharp[csProgGuideObjects#60](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#60)]  
  
 Konstruktory mogą być oznaczone jako [publiczne](../../../csharp/language-reference/keywords/public.md), [prywatne](../../../csharp/language-reference/keywords/private.md), [chronione](../../../csharp/language-reference/keywords/protected.md), [wewnętrzne](../../../csharp/language-reference/keywords/internal.md), [chronione wewnętrznie](../../../csharp/language-reference/keywords/protected-internal.md) lub [chronione prywatnie](../../../csharp/language-reference/keywords/private-protected.md). Te Modyfikatory dostępu definiują sposób, w jaki użytkownicy klasy mogą tworzyć klasy. Aby uzyskać więcej informacji, zobacz [Modyfikatory dostępu](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).  
  
 Konstruktor może być zadeklarowany jako statyczny za pomocą słowa kluczowego [static](../../../csharp/language-reference/keywords/static.md) . Konstruktory statyczne są wywoływane automatycznie, bezpośrednio przed uzyskaniem dostępu do dowolnych pól statycznych i są zwykle używane do inicjowania statycznych elementów członkowskich klas. Aby uzyskać więcej informacji, zobacz [statyczne konstruktory](../../../csharp/programming-guide/classes-and-structs/static-constructors.md).  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  

Aby uzyskać więcej informacji, zobacz [konstruktory wystąpień](~/_csharplang/spec/classes.md#instance-constructors) i [konstruktory statyczne](~/_csharplang/spec/classes.md#static-constructors) w [ C# specyfikacji języka](../../language-reference/language-specification/index.md). Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
- [Klasy i struktury](../../../csharp/programming-guide/classes-and-structs/index.md)
- [Konstruktory](../../../csharp/programming-guide/classes-and-structs/constructors.md)
- [Finalizatory](../../../csharp/programming-guide/classes-and-structs/destructors.md)
