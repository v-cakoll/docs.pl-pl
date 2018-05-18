---
title: Używanie konstruktorów (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- constructors [C#], about constructors
ms.assetid: 464253b2-fd5d-469a-836d-df0fdf2a43f7
ms.openlocfilehash: 5fe6f10e3842c0c0aac4b2669f8ca367fa8c3be2
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2018
---
# <a name="using-constructors-c-programming-guide"></a>Używanie konstruktorów (Przewodnik programowania w języku C#)
Gdy [klasy](../../../csharp/language-reference/keywords/class.md) lub [struktury](../../../csharp/language-reference/keywords/struct.md) jest utworzona, jest nazywany jego konstruktora. Konstruktory ma taką samą nazwę jak klasy lub struktury i zwykle inicjowania elementów członkowskich danych nowego obiektu.  
  
 W poniższym przykładzie klasa o nazwie `Taxi` jest definiowana za pomocą prostego konstruktora. Ta klasa jest następnie utworzono wystąpienie [nowe](../../../csharp/language-reference/keywords/new.md) operatora. `Taxi` Konstruktor jest wywoływany przez `new` operator natychmiast po pamięci zarezerwowanej dla nowego obiektu.  
  
 [!code-csharp[csProgGuideObjects#53](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_1.cs)]  
  
 Konstruktor, który nie przyjmuje żadnych parametrów jest nazywany *domyślnego konstruktora*. Konstruktory domyślne są wywoływane zawsze, gdy obiekt zostanie uruchomiony przy użyciu `new` operatora i argumenty nie są dostarczane do `new`. Aby uzyskać więcej informacji, zobacz [konstruktorów wystąpienia](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md).  
  
 Jeśli klasa jest [statycznych](../../../csharp/language-reference/keywords/static.md), klasy bez konstruktorów podano publicznego konstruktora domyślnego za pomocą kompilatora C# umożliwiające tworzenie wystąpienia klasy. Aby uzyskać więcej informacji, zobacz [klasy statyczne i statycznych elementów członkowskich klasy](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).  
  
 Klasę można zapobiec uruchamianiu przez Konstruktor prywatny, w następujący sposób:  
  
 [!code-csharp[csProgGuideObjects#11](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_2.cs)]  
  
 Aby uzyskać więcej informacji, zobacz [konstruktory prywatne](../../../csharp/programming-guide/classes-and-structs/private-constructors.md).  
  
 Konstruktory [struktury](../../../csharp/language-reference/keywords/struct.md) typy przypominać konstruktorów klasy, ale `structs` nie mogą zawierać jawny Konstruktor domyślny, ponieważ zostało ono określone automatycznie przez kompilator. Ten konstruktor inicjuje wszystkie pola w `struct` do wartości domyślnych. Aby uzyskać więcej informacji, zobacz [tabela wartości domyślnych](../../../csharp/language-reference/keywords/default-values-table.md). Jednak ten konstruktor domyślny jest wywoływana tylko jeśli `struct` zostanie uruchomiony z `new`. Na przykład ten kod używa domyślnego konstruktora dla <xref:System.Int32>, dzięki czemu zapewni zainicjowanej liczbę całkowitą:  
  
```csharp  
int i = new int();  
Console.WriteLine(i);  
```  
  
 Następujący kod, jednak powoduje błąd kompilatora, ponieważ nie używa `new`, ponieważ klient próbuje użyć obiektu, który nie został zainicjowany:  
  
```  
int i;  
Console.WriteLine(i);  
```  
  
 Możesz też na podstawie obiektów `structs` (w tym wszystkie wbudowane typy liczbowe) można zainicjować lub przypisać i następnie używany jak w poniższym przykładzie:  
  
```  
int a = 44;  // Initialize the value type...  
int b;  
b = 33;      // Or assign it before using it.  
Console.WriteLine("{0}, {1}", a, b);  
```  
  
 Dlatego wywołanie domyślnego konstruktora dla typu wartości nie jest wymagane.  
  
 Obie klasy i `structs` można definiować konstruktorów przyjmujących parametrów. Konstruktorów przyjmujących parametrów musi zostać wywołana za pomocą `new` instrukcji lub [podstawowej](../../../csharp/language-reference/keywords/base.md) instrukcji. Klasy i `structs` można również zdefiniować wiele konstruktorów i nie będzie konieczne zdefiniowanie konstruktora domyślnego. Na przykład:  
  
 [!code-csharp[csProgGuideObjects#54](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_3.cs)]  
  
 Ta klasa można utworzyć przy użyciu jednej z następujących instrukcji:  
  
 [!code-csharp[csProgGuideObjects#55](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_4.cs)]  
  
 Można użyć konstruktora `base` — słowo kluczowe można wywołać konstruktora klasy podstawowej. Na przykład:  
  
 [!code-csharp[csProgGuideObjects#56](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_5.cs)]  
  
 W tym przykładzie konstruktora dla klasy podstawowej jest wywoływana przed wykonaniem dla konstruktora bloku. `base` z lub bez parametrów można używać słowa kluczowego. Wszystkie parametry konstruktora mogą być używane jako parametry `base`, lub jako część wyrażenia. Aby uzyskać więcej informacji, zobacz [podstawowej](../../../csharp/language-reference/keywords/base.md).  
  
 W klasie pochodnej, jeśli konstruktora klasy podstawowej nie jest jawnie wywołać przy użyciu `base` — słowo kluczowe, Konstruktor domyślny, jeśli istnieje, jest nazywany niejawnie. Oznacza to, że następujące deklaracje konstruktora skutecznie są takie same:  
  
 [!code-csharp[csProgGuideObjects#58](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_6.cs)]  
  
 [!code-csharp[csProgGuideObjects#57](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_7.cs)]  
  
 Jeśli klasą podstawową nie oferuje konstruktora domyślnego, klasy pochodnej wprowadzić jawnego wywołania konstruktora podstawowego przy użyciu `base`.  
  
 Konstruktor może wywołać innego konstruktora w tym samym obiekcie za pomocą [to](../../../csharp/language-reference/keywords/this.md) — słowo kluczowe. Podobnie jak `base`, `this` mogą być używane z lub bez parametrów i wszelkie parametry w Konstruktorze są dostępne jako parametry `this`, lub jako część wyrażenia. Na przykład drugi Konstruktor w poprzednim przykładzie można ponownego napisania przy użyciu `this`:  
  
 [!code-csharp[csProgGuideObjects#59](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_8.cs)]  
  
 Korzystanie z `this` — słowo kluczowe w poprzednim przykładzie powoduje, że ten konstruktor do wywołania:  
  
 [!code-csharp[csProgGuideObjects#60](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_9.cs)]  
  
 Konstruktory może być oznaczony jako [publicznego](../../../csharp/language-reference/keywords/public.md), [prywatnej](../../../csharp/language-reference/keywords/private.md), [chronione](../../../csharp/language-reference/keywords/protected.md), [wewnętrzny](../../../csharp/language-reference/keywords/internal.md), [chronionych wewnętrznych](../../../csharp/language-reference/keywords/protected-internal.md)lub [prywatne chronione](../../../csharp/language-reference/keywords/private-protected.md). Te modyfikatorów dostępu zdefiniuj, jak użytkownicy klasy można utworzyć klasy. Aby uzyskać więcej informacji, zobacz [modyfikatory dostępu](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).  
  
 Konstruktor może być zadeklarowany jako statyczny przy użyciu [statycznych](../../../csharp/language-reference/keywords/static.md) — słowo kluczowe. Konstruktory statyczne są nazywane automatycznie, bezpośrednio przed wszystkie pola statyczne są dostępne i są zazwyczaj używane do zainicjowania statyczni członkowie klas. Aby uzyskać więcej informacji, zobacz [konstruktory statyczne](../../../csharp/programming-guide/classes-and-structs/static-constructors.md).  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Klasy i struktury](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [Konstruktory](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
 [Finalizatory](../../../csharp/programming-guide/classes-and-structs/destructors.md)
