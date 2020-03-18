---
title: Klasy statyczne i elementy członkowskie klasy statycznej — przewodnik programowania języka C#
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, static members
- static members [C#]
- static classes [C#]
- C# language, static classes
- static class members [C#]
ms.assetid: 235614b5-1371-4dbd-9abd-b406a8b0298b
ms.openlocfilehash: 7add512b262afbabe996f752c083566a2c394dfd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705434"
---
# <a name="static-classes-and-static-class-members-c-programming-guide"></a>Klasy statyczne i statyczni członkowie klas (Przewodnik programowania w języku C#)

Klasa [statyczna](../../language-reference/keywords/static.md) jest w zasadzie taka sama jak klasa niestatyczna, ale istnieje jedna różnica: nie można utworzyć utworzenia klasy statycznej. Innymi słowy nie można użyć [nowego](../../language-reference/operators/new-operator.md) operatora, aby utworzyć zmienną typu klasy. Ponieważ nie ma zmiennej instancji, można uzyskać dostęp do elementów członkowskich klasy statycznej przy użyciu samej nazwy klasy. Na przykład jeśli masz klasę statyczną, `UtilityClass` która ma `MethodA`publiczną metodę statyczną o nazwie, należy wywołać metodę, jak pokazano w poniższym przykładzie:  
  
```csharp  
UtilityClass.MethodA();  
```  
  
 Klasa statyczna może służyć jako wygodny kontener dla zestawów metod, które po prostu działają na parametry wejściowe i nie trzeba uzyskać lub ustawić żadnych pól wystąpienia wewnętrznego. Na przykład w bibliotece klas programu <xref:System.Math?displayProperty=nameWithType> .NET Framework klasa statyczna zawiera metody, które wykonują operacje matematyczne, <xref:System.Math> bez konieczności przechowywania lub pobierania danych, które są unikatowe dla określonego wystąpienia klasy. Oznacza to, że można zastosować członków klasy, określając nazwę klasy i nazwę metody, jak pokazano w poniższym przykładzie.  
  
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
  
 Podobnie jak w przypadku wszystkich typów klas, informacje o typie klasy statycznej są ładowane przez program clr wspólnego języka .NET Framework po załadowaniu programu odwołującego się do klasy. Program nie może dokładnie określić, kiedy klasa jest ładowana. Jednak jest gwarantowana do załadowania i mieć jego pola zainicjowane i jego konstruktor statyczne wywoływane przed klasy odwołuje się po raz pierwszy w programie. Konstruktor statyczny jest nazywany tylko jeden raz, a klasa statyczna pozostaje w pamięci przez cały okres istnienia domeny aplikacji, w którym znajduje się program.  
  
> [!NOTE]
> Aby utworzyć klasę niestatyczną, która umożliwia utworzenie tylko jednego wystąpienia samego siebie, zobacz [Implementowanie Singletona w języku C#.](https://docs.microsoft.com/previous-versions/msp-n-p/ff650316%28v=pandp.10%29)  
  
 Poniższa lista zawiera główne cechy klasy statycznej:  
  
- Zawiera tylko elementy statyczny.  
  
- Nie można utworzyć wystąpienia.  
  
- Jest zapieczętowany.  
  
- Nie może zawierać [konstruktorów wystąpień](./instance-constructors.md).  
  
 Tworzenie klasy statycznej jest zatem w zasadzie taki sam jak tworzenie klasy, która zawiera tylko statycznych elementów członkowskich i konstruktora prywatnego. Prywatny konstruktor zapobiega tworzeniu się klasy. Zaletą przy użyciu klasy statycznej jest to, że kompilator można sprawdzić, aby upewnić się, że żadne elementy członkowskie wystąpienia są przypadkowo dodawane. Kompilator zagwarantuje, że nie można utworzyć wystąpień tej klasy.  
  
 Klasy statyczne są zapieczętowane i dlatego nie mogą być dziedziczone. Nie mogą dziedziczyć z żadnej klasy z wyjątkiem <xref:System.Object>. Klasy statyczne nie mogą zawierać konstruktora wystąpienia; jednak mogą one zawierać konstruktora statycznego. Klasy niestatyczne należy również zdefiniować konstruktora statycznego, jeśli klasa zawiera statycznych elementów członkowskich, które wymagają nietrywialne inicjowania. Aby uzyskać więcej informacji, zobacz [Konstruktora statyczne](./static-constructors.md).  
  
## <a name="example"></a>Przykład  
 Oto przykład klasy statycznej, która zawiera dwie metody, które przekształcają temperaturę z Celsjusza na Fahrenheita i z Fahrenheita do Celsjusza:  
  
 [!code-csharp[csProgGuideObjects#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#31)]  
  
## <a name="static-members"></a>Statyczne elementy członkowskie  
 Klasa niestatyczna może zawierać metody statyczne, pola, właściwości lub zdarzenia. Statyczny element członkowski jest wywoływany na klasie, nawet wtedy, gdy nie utworzono żadnego wystąpienia klasy. Statyczny element członkowski jest zawsze dostępny przez nazwę klasy, a nie nazwę wystąpienia. Istnieje tylko jedna kopia statycznego elementu członkowskiego, niezależnie od tego, ile wystąpień klasy są tworzone. Statyczne metody i właściwości nie mogą uzyskać dostępu do niestatycznych pól i zdarzeń w ich typie zawierającym i nie mogą uzyskać dostępu do zmiennej instancji dowolnego obiektu, chyba że jest jawnie przekazywana w parametrze metody.  
  
 Jest bardziej typowe zadeklarować klasę niestatyczną z niektórych elementów statycznych, niż zadeklarować całą klasę jako statyczne. Dwa typowe zastosowania pól statycznych są do utrzymania liczby obiektów, które zostały uprzedzione lub do przechowywania wartości, które muszą być współużytkowane przez wszystkie wystąpienia.  
  
 Metody statyczne mogą być przeciążone, ale nie zastąpione, ponieważ należą do klasy, a nie do dowolnego wystąpienia klasy.  
  
 Chociaż pole nie może `static const`być zadeklarowane jako , pole [const](../../language-reference/keywords/const.md) jest zasadniczo statyczne w jego zachowaniu. Należy do typu, a nie do wystąpień typu. W związku z tym pola const `ClassName.MemberName` są dostępne przy użyciu tej samej notacji, która jest używana dla pól statycznych. Nie jest wymagane wystąpienie obiektu.  
  
 C# nie obsługuje statycznych zmiennych lokalnych (zmienne, które są zadeklarowane w zakresie metody).  
  
 Deklarujesz elementy członkowskie `static` klasy statycznej za pomocą słowa kluczowego przed typem zwracanego elementu członkowskiego, jak pokazano w poniższym przykładzie:  
  
 [!code-csharp[csProgGuideObjects#29](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#29)]  
  
 Elementy statyczne są inicjowane przed statyczny element członkowski jest dostępny po raz pierwszy i przed konstruktora statycznego, jeśli istnieje, jest wywoływana. Aby uzyskać dostęp do elementu członkowskiego klasy statycznej, użyj nazwy klasy zamiast nazwy zmiennej, aby określić lokalizację elementu członkowskiego, jak pokazano w poniższym przykładzie:  
  
 [!code-csharp[csProgGuideObjects#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#30)]  
  
 Jeśli klasa zawiera pola statyczne, należy podać konstruktora statycznego, który inicjuje je po załadowaniu klasy.  
  
 Wywołanie metody statycznej generuje instrukcję wywołania w języku pośrednim firmy Microsoft (MSIL), podczas gdy wywołanie metody wystąpienia generuje instrukcję, `callvirt` która również sprawdza odwołania do obiektu null. Jednak w większości czasu różnica w wydajności między nimi nie jest znacząca.  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  

Aby uzyskać więcej informacji, zobacz [Klasy statyczne](~/_csharplang/spec/classes.md#static-classes) i elementy członkowskie statyczne [i wystąpienia](~/_csharplang/spec/classes.md#static-and-instance-members) w [specyfikacji języka Języka C#.](/dotnet/csharp/language-reference/language-specification/introduction) Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania języka C#](../index.md)
- [Statyczne](../../language-reference/keywords/static.md)
- [Klasy](./classes.md)
- [Klasa](../../language-reference/keywords/class.md)
- [Konstruktory statyczne](./static-constructors.md)
- [Konstruktory wystąpień](./instance-constructors.md)
