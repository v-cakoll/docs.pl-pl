---
title: Używanie konstruktorów - C# przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- constructors [C#], about constructors
ms.assetid: 464253b2-fd5d-469a-836d-df0fdf2a43f7
ms.openlocfilehash: 1f47459fc5002118d94cc8d389f35c18fa2c611a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61703286"
---
# <a name="using-constructors-c-programming-guide"></a>Używanie konstruktorów (Przewodnik programowania w języku C#)
Gdy [klasy](../../../csharp/language-reference/keywords/class.md) lub [struktury](../../../csharp/language-reference/keywords/struct.md) jest utworzone, jego konstruktor jest wywoływany. Konstruktory mają taką samą nazwę jak klasy lub struktury, a zwykle inicjują członków danych nowego obiektu.  
  
 W poniższym przykładzie klasę o nazwie `Taxi` jest zdefiniowana za pomocą prostego konstruktora. Ta klasa jest następnie utworzone za pomocą [nowe](../../../csharp/language-reference/keywords/new.md) operatora. `Taxi` Konstruktor jest wywoływany przez `new` operator natychmiast po pamięci zarezerwowanej dla nowego obiektu.  
  
 [!code-csharp[csProgGuideObjects#53](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#53)]  
  
 Wywoływany jest konstruktor, który nie przyjmuje żadnych parametrów *konstruktora bez parametrów*. Konstruktory domyślne są wywoływane zawsze wtedy, gdy jest tworzone wystąpienie obiektu za pomocą `new` operatora i żadne argumenty, które zostały udostępnione firmie `new`. Aby uzyskać więcej informacji, zobacz [konstruktory wystąpień](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md).  
  
 Chyba, że klasa jest [statyczne](../../../csharp/language-reference/keywords/static.md), klasy bez konstruktory są podane publicznego konstruktora bez parametrów, C# kompilatora w celu umożliwienia tworzenia wystąpienia klasy. Aby uzyskać więcej informacji, zobacz [klasy statyczne i statyczne elementy członkowskie klasy](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).  
  
 Klasę można zapobiec uruchamianiu przez Konstruktor prywatny, w następujący sposób:  
  
 [!code-csharp[csProgGuideObjects#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#11)]  
  
 Aby uzyskać więcej informacji, zobacz [konstruktory prywatne](../../../csharp/programming-guide/classes-and-structs/private-constructors.md).  
  
 Konstruktory [struktury](../../../csharp/language-reference/keywords/struct.md) typy przypominają Konstruktory klasy, ale `structs` nie może zawierać jawny konstruktor bez parametrów, ponieważ zostało ono określone automatycznie przez kompilator. Ten konstruktor inicjuje wszystkie pola w `struct` do wartości domyślnych. Aby uzyskać więcej informacji, zobacz [tabela wartości domyślnych](../../../csharp/language-reference/keywords/default-values-table.md). Jednak ten konstruktor bez parametrów jest wywoływana tylko jeśli `struct` jest utworzone za pomocą `new`. Na przykład, ten kod używa konstruktora bez parametrów dla <xref:System.Int32>, dzięki czemu są pewność, że liczba całkowita jest zainicjowany:  
  
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
  
 Dlatego wywołanie konstruktora bez parametrów dla typu wartości nie jest wymagana.  
  
 Obie klasy i `structs` mogą definiować konstruktorów, które przyjmują parametry. Konstruktory, które przyjmują parametry musi zostać wywołana przez `new` instrukcji lub [podstawowy](../../../csharp/language-reference/keywords/base.md) instrukcji. Klasy i `structs` można również zdefiniować wiele konstruktorów i nie jest wymagany do zdefiniowania konstruktora bez parametrów. Na przykład:  
  
 [!code-csharp[csProgGuideObjects#54](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#54)]  
  
 Ta klasa można utworzyć przy użyciu jednej z następujących instrukcji:  
  
 [!code-csharp[csProgGuideObjects#55](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#55)]  
  
 Można użyć konstruktora `base` słowo kluczowe, aby wywołać konstruktora klasy bazowej. Na przykład:  
  
 [!code-csharp[csProgGuideObjects#56](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#56)]  
  
 W tym przykładzie konstruktora dla klasy bazowej jest wywoływana przed wykonaniem bloku dla konstruktora. `base` — Słowo kluczowe może być używany z bez parametrów. Wszelkie parametry konstruktora może służyć jako parametry `base`, lub jako część wyrażenia. Aby uzyskać więcej informacji, zobacz [podstawowy](../../../csharp/language-reference/keywords/base.md).  
  
 W klasie pochodnej, jeśli Konstruktor klasy bazowej nie jest jawnie wywoływana przy użyciu `base` — słowo kluczowe, konstruktor bez parametrów, jeśli istnieje, jest wywoływana niejawnie. Oznacza to, że następujące deklaracje Konstruktor jest praktycznie taki sam:  
  
 [!code-csharp[csProgGuideObjects#58](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#58)]  
  
 [!code-csharp[csProgGuideObjects#57](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#57)]  
  
 Jeśli klasa bazowa nie oferuje konstruktora bez parametrów, klasy pochodnej musi utworzyć jawnym wywołaniem konstruktora bazowego przy użyciu `base`.  
  
 Konstruktor może wywołać innego konstruktora w ten sam obiekt przy użyciu [to](../../../csharp/language-reference/keywords/this.md) — słowo kluczowe. Podobnie jak `base`, `this` może być używany z lub bez parametrów i parametrów w Konstruktorze są dostępne jako parametry `this`, lub jako część wyrażenia. Na przykład, drugi Konstruktor w poprzednim przykładzie może zostać przepisany z użyciem `this`:  
  
 [!code-csharp[csProgGuideObjects#59](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#59)]  
  
 Korzystanie z `this` — słowo kluczowe w poprzednim przykładzie powoduje, że ten konstruktor do wywołania:  
  
 [!code-csharp[csProgGuideObjects#60](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#60)]  
  
 Konstruktory może być oznaczona jako [publicznych](../../../csharp/language-reference/keywords/public.md), [prywatnej](../../../csharp/language-reference/keywords/private.md), [chronione](../../../csharp/language-reference/keywords/protected.md), [wewnętrzny](../../../csharp/language-reference/keywords/internal.md), [chronionych wewnętrznych](../../../csharp/language-reference/keywords/protected-internal.md)lub [prywatny chroniony](../../../csharp/language-reference/keywords/private-protected.md). Następujące modyfikatory dostępu definiują, jak użytkownicy klasy można skonstruować klasy. Aby uzyskać więcej informacji, zobacz [Modyfikatory dostępu](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).   
  
 Konstruktor mogą być deklarowane statycznych przy użyciu [statyczne](../../../csharp/language-reference/keywords/static.md) — słowo kluczowe. Konstruktory statyczne są nazywane automatycznie, bezpośrednio przed wykonaniem dowolnego pola statyczne są dostępne i są zazwyczaj używane do zainicjowania statyczni członkowie klas. Aby uzyskać więcej informacji, zobacz [konstruktorów statycznych](../../../csharp/programming-guide/classes-and-structs/static-constructors.md).  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  

Aby uzyskać więcej informacji, zobacz [wystąpienia konstruktory](~/_csharplang/spec/classes.md#instance-constructors) i [konstruktorów statycznych](~/_csharplang/spec/classes.md#static-constructors) w [ C# specyfikacji języka](../../language-reference/language-specification/index.md). Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
- [Klasy i struktury](../../../csharp/programming-guide/classes-and-structs/index.md)
- [Konstruktory](../../../csharp/programming-guide/classes-and-structs/constructors.md)
- [Finalizatory](../../../csharp/programming-guide/classes-and-structs/destructors.md)
