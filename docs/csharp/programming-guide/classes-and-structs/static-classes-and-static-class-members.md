---
title: Klasy statyczne i statyczne elementy członkowskie klasy — Przewodnik programowania w języku C#
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, static members
- static members [C#]
- static classes [C#]
- C# language, static classes
- static class members [C#]
ms.assetid: 235614b5-1371-4dbd-9abd-b406a8b0298b
ms.openlocfilehash: 71cbf8278b3a8092e93a8ae3d8be291540f16cc3
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990096"
---
# <a name="static-classes-and-static-class-members-c-programming-guide"></a>Klasy statyczne i statyczni członkowie klas (Przewodnik programowania w języku C#)

Klasa [statyczna](../../language-reference/keywords/static.md) jest zasadniczo taka sama jak Klasa niestatyczna, ale istnieje jedna różnica: nie można utworzyć wystąpienia klasy statycznej. Innymi słowy, nie można użyć operatora [New](../../language-reference/operators/new-operator.md) , aby utworzyć zmienną typu klasy. Ponieważ nie istnieje zmienna wystąpienia, dostęp do elementów członkowskich klasy statycznej można uzyskać przy użyciu samej nazwy klasy. Na przykład jeśli masz klasę statyczną o nazwie, `UtilityClass` która ma publiczną metodę statyczną o nazwie `MethodA` , wywoływana jest metoda, jak pokazano w następującym przykładzie:  
  
```csharp  
UtilityClass.MethodA();  
```  
  
 Klasa statyczna może być używana jako wygodny kontener dla zestawów metod, które po prostu działają w parametrach wejściowych i nie muszą pobierać ani ustawiać żadnych pól wystąpienia wewnętrznego. Na przykład w bibliotece klas .NET Klasa statyczna <xref:System.Math?displayProperty=nameWithType> zawiera metody, które wykonują operacje matematyczne, bez konieczności przechowywania lub pobierania danych, które są unikatowe dla określonego wystąpienia <xref:System.Math> klasy. Oznacza to, że należy zastosować elementy członkowskie klasy, określając nazwę klasy i nazwę metody, jak pokazano w poniższym przykładzie.  
  
```csharp  
double dub = -3.14;  
Console.WriteLine(Math.Abs(dub));  
Console.WriteLine(Math.Floor(dub));  
Console.WriteLine(Math.Round(Math.Abs(dub)));  
  
// Output:  
// 3.14  
// -4  
// 3  
```  
  
 Podobnie jak w przypadku wszystkich typów klas, informacje o typie klasy statycznej są ładowane przez środowisko uruchomieniowe platformy .NET, gdy zostanie załadowany program, który odwołuje się do klasy. Program nie może określić dokładnie, gdy Klasa jest załadowana. Jednak zagwarantowane jest załadowanie i zainicjowanie jego pól oraz jego konstruktora statycznego wywołanego przed odwołaniem do klasy po raz pierwszy w programie. Konstruktor statyczny jest wywoływany tylko jednokrotnie, a Klasa statyczna pozostaje w pamięci przez okres istnienia domeny aplikacji, w której znajduje się program.  
  
> [!NOTE]
> Aby utworzyć niestatyczną klasę, która umożliwia utworzenie tylko jednego wystąpienia, zobacz [implementowanie pojedynczych w języku C#](https://docs.microsoft.com/previous-versions/msp-n-p/ff650316%28v=pandp.10%29).  
  
 Poniższa lista zawiera główne funkcje klasy statycznej:  
  
- Zawiera tylko statyczne elementy członkowskie.  
  
- Nie można utworzyć wystąpienia.  
  
- Jest zapieczętowany.  
  
- Nie może zawierać [konstruktorów wystąpień](./instance-constructors.md).  
  
 Tworzenie klasy statycznej jest tak samo samo jak w przypadku tworzenia klasy, która zawiera tylko statyczne elementy członkowskie i Konstruktor prywatny. Konstruktor prywatny uniemożliwia utworzenie wystąpienia klasy. Zaletą używania klasy statycznej jest to, że kompilator może sprawdzić, czy żaden element członkowski wystąpienia nie został przypadkowo dodany. Kompilator gwarantuje, że wystąpienia tej klasy nie mogą zostać utworzone.  
  
 Klasy statyczne są zapieczętowane i w związku z tym nie można ich dziedziczyć. Nie mogą dziedziczyć z żadnej klasy z wyjątkiem <xref:System.Object> . Klasy statyczne nie mogą zawierać konstruktora wystąpień. Jednak mogą zawierać statyczny Konstruktor. Klasy niestatyczne powinny także definiować Konstruktor statyczny, jeśli Klasa zawiera statyczne składowe, które wymagają inicjalizacji nieuproszczonej. Aby uzyskać więcej informacji, zobacz [statyczne konstruktory](./static-constructors.md).  
  
## <a name="example"></a>Przykład  
 Oto przykład klasy statycznej zawierającej dwie metody, które konwertują temperaturę z Celsjusza na Fahrenheita i od Fahrenheita do c:  
  
 [!code-csharp[csProgGuideObjects#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#31)]  
  
## <a name="static-members"></a>Statyczne elementy członkowskie  
 Klasa niestatyczna może zawierać statyczne metody, pola, właściwości lub zdarzenia. Statyczny element członkowski jest wywoływany na klasie nawet wtedy, gdy nie utworzono żadnego wystąpienia klasy. Statyczny element członkowski jest zawsze używany przez nazwę klasy, a nie nazwę wystąpienia. Istnieje tylko jedna kopia statycznej składowej, niezależnie od tego, ile wystąpień klasy zostały utworzone. Metody i właściwości statyczne nie mogą uzyskać dostępu do niestatycznych pól i zdarzeń w ich typie zawierającym i nie mogą uzyskać dostępu do zmiennej wystąpienia dowolnego obiektu, chyba że jest on jawnie przekazywać w parametrze metody.  
  
 Bardziej typowym jest zadeklarowanie niestatycznej klasy z pewnymi statycznymi składowymi, niż w celu deklarowania całej klasy jako statycznej. Dwa typowe zastosowania pól statycznych mają na celu zachowanie liczby obiektów, które zostały utworzone, lub do przechowywania wartości, które muszą być współużytkowane przez wszystkie wystąpienia.  
  
 Metody statyczne mogą być przeciążone, ale nie przesłaniane, ponieważ należą do klasy, a nie do żadnego wystąpienia klasy.  
  
 Chociaż nie można zadeklarować pola jako `static const` , pole [const](../../language-reference/keywords/const.md) jest zasadniczo statyczne w zachowaniu. Należy do typu, nie do wystąpienia typu. W związku z tym `const` pola są dostępne za pomocą tej samej `ClassName.MemberName` notacji, która jest używana dla pól statycznych. Nie jest wymagane żadne wystąpienie obiektu.  
  
 Język C# nie obsługuje statycznych zmiennych lokalnych (czyli zmiennych, które są zadeklarowane w zakresie metody).  
  
 Elementy członkowskie klasy statycznej deklaruje się za pomocą `static` słowa kluczowego przed typem zwracanym elementu członkowskiego, jak pokazano w następującym przykładzie:  
  
 [!code-csharp[csProgGuideObjects#29](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#29)]  
  
 Statyczne składowe są inicjowane przed uzyskaniem dostępu do statycznego elementu członkowskiego po raz pierwszy i przed konstruktorem statycznym, jeśli istnieje. Aby uzyskać dostęp do statycznej składowej klasy, użyj nazwy klasy zamiast nazwy zmiennej, aby określić lokalizację elementu członkowskiego, jak pokazano w następującym przykładzie:  
  
 [!code-csharp[csProgGuideObjects#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#30)]  
  
 Jeśli Klasa zawiera pola statyczne, podaj statyczny Konstruktor, który inicjuje je podczas ładowania klasy.  
  
 Wywołanie metody statycznej generuje instrukcję wywołania w języku pośrednim firmy Microsoft (MSIL), podczas gdy wywołanie metody instancji generuje `callvirt` instrukcję, która również sprawdza odwołania do obiektów o wartości null. Jednak większość czasu różnica między wydajnością nie jest istotna.  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  

Aby uzyskać więcej informacji, zobacz [klasy statyczne](~/_csharplang/spec/classes.md#static-classes) i [elementy członkowskie statyczne i wystąpienia](~/_csharplang/spec/classes.md#static-and-instance-members) w [specyfikacji języka C#](/dotnet/csharp/language-reference/language-specification/introduction). Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania w języku C#](../index.md)
- [static](../../language-reference/keywords/static.md)
- [Klasy](./classes.md)
- [określonej](../../language-reference/keywords/class.md)
- [Konstruktory statyczne](./static-constructors.md)
- [Konstruktory wystąpień](./instance-constructors.md)
