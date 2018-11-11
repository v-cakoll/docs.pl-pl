---
title: Używanie konstruktorów (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- constructors [C#], about constructors
ms.assetid: 464253b2-fd5d-469a-836d-df0fdf2a43f7
ms.openlocfilehash: d10b0de0a3811e615297b31d2d9c8934c9338078
ms.sourcegitcommit: 3b1cb8467bd73dee854b604e306c0e7e3882d91a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2018
ms.locfileid: "43529023"
---
# <a name="using-constructors-c-programming-guide"></a>Używanie konstruktorów (Przewodnik programowania w języku C#)
Gdy [klasy](../../../csharp/language-reference/keywords/class.md) lub [struktury](../../../csharp/language-reference/keywords/struct.md) jest utworzone, jego konstruktor jest wywoływany. Konstruktory mają taką samą nazwę jak klasy lub struktury, a zwykle inicjują członków danych nowego obiektu.  
  
 W poniższym przykładzie klasę o nazwie `Taxi` jest zdefiniowana za pomocą prostego konstruktora. Ta klasa jest następnie utworzone za pomocą [nowe](../../../csharp/language-reference/keywords/new.md) operatora. `Taxi` Konstruktor jest wywoływany przez `new` operator natychmiast po pamięci zarezerwowanej dla nowego obiektu.  
  
 [!code-csharp[csProgGuideObjects#53](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_1.cs)]  
  
 Wywoływany jest konstruktor, który nie przyjmuje żadnych parametrów *domyślnego konstruktora*. Konstruktory domyślne są wywoływane zawsze wtedy, gdy jest tworzone wystąpienie obiektu za pomocą `new` operatora i żadne argumenty, które zostały udostępnione firmie `new`. Aby uzyskać więcej informacji, zobacz [konstruktory wystąpień](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md).  
  
 Chyba, że klasa jest [statyczne](../../../csharp/language-reference/keywords/static.md), klasy bez konstruktory są podane publicznego konstruktora domyślnego przez kompilator języka C# w celu umożliwienia tworzenia wystąpienia klasy. Aby uzyskać więcej informacji, zobacz [klasy statyczne i statyczne elementy członkowskie klasy](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).  
  
 Klasę można zapobiec uruchamianiu przez Konstruktor prywatny, w następujący sposób:  
  
 [!code-csharp[csProgGuideObjects#11](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_2.cs)]  
  
 Aby uzyskać więcej informacji, zobacz [konstruktory prywatne](../../../csharp/programming-guide/classes-and-structs/private-constructors.md).  
  
 Konstruktory [struktury](../../../csharp/language-reference/keywords/struct.md) typy przypominają Konstruktory klasy, ale `structs` nie może zawierać jawne domyślnego konstruktora, ponieważ zostało ono określone automatycznie przez kompilator. Ten konstruktor inicjuje wszystkie pola w `struct` do wartości domyślnych. Aby uzyskać więcej informacji, zobacz [tabela wartości domyślnych](../../../csharp/language-reference/keywords/default-values-table.md). Jednak to domyślny konstruktor jest wywoływana tylko jeśli `struct` jest utworzone za pomocą `new`. Na przykład, ten kod używa domyślnego konstruktora dla <xref:System.Int32>, dzięki czemu są pewność, że liczba całkowita jest zainicjowany:  
  
```csharp  
int i = new int();  
Console.WriteLine(i);  
```  
  
 Poniższy kod, jednak powoduje błąd kompilatora, ponieważ nie używa `new`, a ponieważ próbuje użyć obiektu, który nie został zainicjowany:  
  
```  
int i;  
Console.WriteLine(i);  
```  
  
 Alternatywnie, na podstawie obiektów `structs` (w tym wbudowane typy liczbowe) mogą zostać zainicjowane lub przypisane i następnie jest używany jak w poniższym przykładzie:  
  
```  
int a = 44;  // Initialize the value type...  
int b;  
b = 33;      // Or assign it before using it.  
Console.WriteLine("{0}, {1}", a, b);  
```  
  
 Dlatego wywołanie domyślnego konstruktora dla typu wartości nie jest wymagana.  
  
 Obie klasy i `structs` mogą definiować konstruktorów, które przyjmują parametry. Konstruktory, które przyjmują parametry musi zostać wywołana przez `new` instrukcji lub [podstawowy](../../../csharp/language-reference/keywords/base.md) instrukcji. Klasy i `structs` można również zdefiniować wiele konstruktorów i nie jest wymagany do zdefiniowania domyślnego konstruktora. Na przykład:  
  
 [!code-csharp[csProgGuideObjects#54](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_3.cs)]  
  
 Ta klasa można utworzyć przy użyciu jednej z następujących instrukcji:  
  
 [!code-csharp[csProgGuideObjects#55](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_4.cs)]  
  
 Można użyć konstruktora `base` słowo kluczowe, aby wywołać konstruktora klasy bazowej. Na przykład:  
  
 [!code-csharp[csProgGuideObjects#56](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_5.cs)]  
  
 W tym przykładzie konstruktora dla klasy bazowej jest wywoływana przed wykonaniem bloku dla konstruktora. `base` — Słowo kluczowe może być używany z bez parametrów. Wszelkie parametry konstruktora może służyć jako parametry `base`, lub jako część wyrażenia. Aby uzyskać więcej informacji, zobacz [podstawowy](../../../csharp/language-reference/keywords/base.md).  
  
 W klasie pochodnej, jeśli Konstruktor klasy bazowej nie jest jawnie wywoływana przy użyciu `base` — słowo kluczowe, Konstruktor domyślny, jeśli istnieje, jest wywoływana niejawnie. Oznacza to, że następujące deklaracje Konstruktor jest praktycznie taki sam:  
  
 [!code-csharp[csProgGuideObjects#58](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_6.cs)]  
  
 [!code-csharp[csProgGuideObjects#57](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_7.cs)]  
  
 Jeśli klasa bazowa nie oferuje domyślnego konstruktora, klasy pochodnej musi utworzyć jawnym wywołaniem konstruktora bazowego przy użyciu `base`.  
  
 Konstruktor może wywołać innego konstruktora w ten sam obiekt przy użyciu [to](../../../csharp/language-reference/keywords/this.md) — słowo kluczowe. Podobnie jak `base`, `this` może być używany z lub bez parametrów i parametrów w Konstruktorze są dostępne jako parametry `this`, lub jako część wyrażenia. Na przykład, drugi Konstruktor w poprzednim przykładzie może zostać przepisany z użyciem `this`:  
  
 [!code-csharp[csProgGuideObjects#59](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_8.cs)]  
  
 Korzystanie z `this` — słowo kluczowe w poprzednim przykładzie powoduje, że ten konstruktor do wywołania:  
  
 [!code-csharp[csProgGuideObjects#60](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_9.cs)]  
  
 Konstruktory może być oznaczona jako [publicznych](../../../csharp/language-reference/keywords/public.md), [prywatnej](../../../csharp/language-reference/keywords/private.md), [chronione](../../../csharp/language-reference/keywords/protected.md), [wewnętrzny](../../../csharp/language-reference/keywords/internal.md), [chronionych wewnętrznych](../../../csharp/language-reference/keywords/protected-internal.md)lub [prywatny chroniony](../../../csharp/language-reference/keywords/private-protected.md). Następujące modyfikatory dostępu definiują, jak użytkownicy klasy można skonstruować klasy. Aby uzyskać więcej informacji, zobacz [Modyfikatory dostępu](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).   
  
 Konstruktor mogą być deklarowane statycznych przy użyciu [statyczne](../../../csharp/language-reference/keywords/static.md) — słowo kluczowe. Konstruktory statyczne są nazywane automatycznie, bezpośrednio przed wykonaniem dowolnego pola statyczne są dostępne i są zazwyczaj używane do zainicjowania statyczni członkowie klas. Aby uzyskać więcej informacji, zobacz [konstruktorów statycznych](../../../csharp/programming-guide/classes-and-structs/static-constructors.md).  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  

Aby uzyskać więcej informacji, zobacz [wystąpienia konstruktory](~/_csharplang/spec/classes.md#instance-constructors) i [konstruktorów statycznych](~/_csharplang/spec/classes.md#static-constructors) w [ C# specyfikacji języka](../../language-reference/language-specification/index.md). Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Klasy i struktury](../../../csharp/programming-guide/classes-and-structs/index.md)  
- [Konstruktory](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
- [Finalizatory](../../../csharp/programming-guide/classes-and-structs/destructors.md)
