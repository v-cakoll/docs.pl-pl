---
title: Korzystanie z konstruktorów — przewodnik programowania C#
ms.date: 07/20/2015
helpviewer_keywords:
- constructors [C#], about constructors
ms.assetid: 464253b2-fd5d-469a-836d-df0fdf2a43f7
ms.openlocfilehash: 7c227b61c6d5b4ead00fced0dba046b90683fde1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77626415"
---
# <a name="using-constructors-c-programming-guide"></a>Używanie konstruktorów (Przewodnik programowania w języku C#)

Po utworzeniu [klasy](../../language-reference/keywords/class.md) lub [struktury,](../../language-reference/builtin-types/struct.md) jego konstruktor jest wywoływana. Konstruktorzy mają taką samą nazwę jak klasy lub struktury i zwykle inicjowania członków danych nowego obiektu.  
  
 W poniższym przykładzie klasa `Taxi` o nazwie jest zdefiniowana przy użyciu prostego konstruktora. Ta klasa jest następnie tworzone z [nowym](../../language-reference/operators/new-operator.md) operatorem. Konstruktor `Taxi` jest wywoływany przez `new` operatora natychmiast po przydzielonym pamięci dla nowego obiektu.  
  
 [!code-csharp[csProgGuideObjects#53](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#53)]  
  
 Konstruktor, który nie przyjmuje żadnych parametrów jest nazywany *konstruktorem bezparametrów*. Konstruktory bezparametrów są wywoływane za każdym razem, `new` gdy obiekt jest tworzony `new`przy użyciu operatora i nie podano żadnych argumentów . Aby uzyskać więcej informacji, zobacz [Konstruktora wystąpień](./instance-constructors.md).  
  
 Chyba że klasa jest [statyczna](../../language-reference/keywords/static.md), klasy bez konstruktorów są podane konstruktora public parameterless przez kompilator C#, aby umożliwić wystąpienia klasy. Aby uzyskać więcej informacji, zobacz [Klasy statyczne i elementy członkowskie klasy statycznej](./static-classes-and-static-class-members.md).  
  
 Można zapobiec klasy z wystąpienia przez co konstruktora prywatnych, w następujący sposób:  
  
 [!code-csharp[csProgGuideObjects#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#11)]  
  
 Aby uzyskać więcej informacji, zobacz [Konstruktory prywatne](./private-constructors.md).  
  
 Konstruktory dla typów [struktur](../../language-reference/builtin-types/struct.md) przypominają konstruktory klas, ale `structs` nie może zawierać jawny konstruktor bezparametrów, ponieważ jeden jest dostarczany automatycznie przez kompilator. Ten konstruktor inicjuje `struct` każde pole w [wartości domyślnej.](../../language-reference/builtin-types/default-values.md) Jednak ten konstruktor bez parametrów `struct` jest wywoływany tylko `new`wtedy, gdy jest tworzony za pomocą . Na przykład ten kod używa konstruktora bezparametrów dla <xref:System.Int32>, dzięki czemu masz pewność, że liczba całkowita jest inicjowana:  
  
```csharp  
int i = new int();  
Console.WriteLine(i);  
```  
  
 Poniższy kod powoduje jednak błąd kompilatora, `new`ponieważ nie używa , a ponieważ próbuje użyć obiektu, który nie został zainicjowany:  
  
```csharp  
int i;  
Console.WriteLine(i);  
```  
  
 Alternatywnie obiekty oparte `structs` na (w tym wszystkie wbudowane typy liczbowe) mogą być inicjowane lub przypisywane, a następnie używane w poniższym przykładzie:  
  
```csharp  
int a = 44;  // Initialize the value type...  
int b;  
b = 33;      // Or assign it before using it.  
Console.WriteLine("{0}, {1}", a, b);  
```  
  
 Tak więc wywołanie konstruktora bez parametrów dla typu wartości nie jest wymagane.  
  
 Obie klasy `structs` i można zdefiniować konstruktory, które przyjmują parametry. Konstruktory, które przyjmują parametry `new` muszą być wywoływane za pośrednictwem instrukcji lub [instrukcji podstawowej.](../../language-reference/keywords/base.md) Klasy `structs` i można również zdefiniować wiele konstruktorów i nie jest wymagane do definiowania konstruktora bezparametrów. Przykład:  
  
 [!code-csharp[csProgGuideObjects#54](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#54)]  
  
 Tę klasę można utworzyć przy użyciu jednej z następujących instrukcji:  
  
 [!code-csharp[csProgGuideObjects#55](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#55)]  
  
 Konstruktor można `base` użyć słowa kluczowego do wywołania konstruktora klasy podstawowej. Przykład:  
  
 [!code-csharp[csProgGuideObjects#56](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#56)]  
  
 W tym przykładzie konstruktora dla klasy podstawowej jest wywoływana przed blok dla konstruktora jest wykonywana. Słowa `base` kluczowego można używać z parametrami lub bez. Wszystkie parametry do konstruktora mogą być `base`używane jako parametry do , lub jako część wyrażenia. Aby uzyskać więcej informacji, zobacz [podstawa](../../language-reference/keywords/base.md).  
  
 W klasie pochodnej, jeśli konstruktor klasy podstawowej nie `base` jest wywoływany jawnie przy użyciu słowa kluczowego, konstruktor bezparametrów, jeśli istnieje, jest wywoływany niejawnie. Oznacza to, że następujące deklaracje konstruktorów są skutecznie takie same:  
  
 [!code-csharp[csProgGuideObjects#58](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#58)]  
  
 [!code-csharp[csProgGuideObjects#57](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#57)]  
  
 Jeśli klasa podstawowa nie oferuje konstruktora bezparametrów, klasa pochodna musi jawne `base`wywołanie konstruktora podstawowego przy użyciu .  
  
 Konstruktor może wywołać innego konstruktora w tym samym obiekcie przy użyciu [tego](../../language-reference/keywords/this.md) słowa kluczowego. Podobnie `base` `this` jak , może być używany z parametrami lub bez, a wszystkie `this`parametry w konstruktorze są dostępne jako parametry do , lub jako część wyrażenia. Na przykład drugi konstruktor w poprzednim przykładzie `this`można przepisać przy użyciu:  
  
 [!code-csharp[csProgGuideObjects#59](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#59)]  
  
 Użycie `this` słowa kluczowego w poprzednim przykładzie powoduje, że ten konstruktor ma być wywoływany:  
  
 [!code-csharp[csProgGuideObjects#60](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#60)]  
  
 Konstruktorzy mogą być oznaczani jako [publiczni,](../../language-reference/keywords/public.md) [prywatni, chronieni,](../../language-reference/keywords/protected.md) [private](../../language-reference/keywords/private.md) [wewnętrzni,](../../language-reference/keywords/internal.md) [chronieni wewnętrznie](../../language-reference/keywords/protected-internal.md) lub [prywatnie.](../../language-reference/keywords/private-protected.md) Te modyfikatory dostępu definiują sposób, w jaki użytkownicy klasy mogą konstruować klasę. Aby uzyskać więcej informacji, zobacz [Modyfikatory dostępu](./access-modifiers.md).  
  
 Konstruktora można zadeklarować statyczne przy użyciu [statycznego](../../language-reference/keywords/static.md) słowa kluczowego. Konstruktory statyczne są wywoływane automatycznie, bezpośrednio przed dostępem do jakichkolwiek pól statycznych i są zwykle używane do inicjowania statycznych elementów członkowskich klasy. Aby uzyskać więcej informacji, zobacz [Konstruktora statyczne](./static-constructors.md).  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  

Aby uzyskać więcej informacji, zobacz [Konstruktory wystąpienia](~/_csharplang/spec/classes.md#instance-constructors) i [konstruktory statyczne](~/_csharplang/spec/classes.md#static-constructors) w [specyfikacji języka Języka C#.](/dotnet/csharp/language-reference/language-specification/introduction) Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania języka C#](../index.md)
- [Klasy i struktury](./index.md)
- [Konstruktory](./constructors.md)
- [Finalizatory](./destructors.md)
