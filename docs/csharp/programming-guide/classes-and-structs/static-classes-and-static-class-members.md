---
title: Klasy statyczne i statyczni członkowie klas (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, static members
- static members [C#]
- static classes [C#]
- C# language, static classes
- static class members [C#]
ms.assetid: 235614b5-1371-4dbd-9abd-b406a8b0298b
ms.openlocfilehash: 60a75946d30b1555aea01507d846e790dd00f767
ms.sourcegitcommit: 15d99019aea4a5c3c91ddc9ba23692284a7f61f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2018
ms.locfileid: "49122726"
---
# <a name="static-classes-and-static-class-members-c-programming-guide"></a>Klasy statyczne i statyczni członkowie klas (Przewodnik programowania w języku C#)
A [statyczne](../../../csharp/language-reference/keywords/static.md) klasy jest zasadniczo taki sam jak niestatycznych klas, ale ma jedną różnicą: nie można utworzyć wystąpienia klasy statycznej. Innymi słowy, nie można użyć [nowe](../../../csharp/language-reference/keywords/new.md) — słowo kluczowe, aby utworzyć zmienną typu klasy. Ponieważ nie ma żadnej zmiennej wystąpienia, uzyskujesz dostęp do członków klasy statycznej za pomocą sama nazwa klasy. Na przykład jeśli masz statyczna klasy, która jest o nazwie `UtilityClass` który posiada publiczną metodę o nazwie `MethodA`, należy wywołać metodę, jak pokazano w poniższym przykładzie:  
  
```csharp  
UtilityClass.MethodA();  
```  
  
 Klasa statyczna może służyć jako wygodny kontenera dla zestawów metod, które po prostu działają na parametry wejściowe i nie trzeba pobrać lub ustawić wszystkie pola wystąpienia wewnętrznego. Na przykład w bibliotece w klas programu .NET Framework, statycznej <xref:System.Math?displayProperty=nameWithType> klasa zawiera metody, które wykonują operacje matematyczne, bez konieczności zapisanie lub pobranie danych, który jest unikatowy dla konkretnego wystąpienia <xref:System.Math> klasy. Oznacza to należy zastosować składowych klasy, określając nazwę klasy i nazwę metody, jak pokazano w poniższym przykładzie.  
  
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
  
 Podobnie jak w przypadku wszystkich typów klasy, informacje o typie dla klasy statycznej jest ładowany przez [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] środowisko uruchomieniowe języka wspólnego (CLR), gdy jest ładowany przez program, który odwołuje się do klasy. Program nie można określić dokładnie, gdy klasa jest ładowany. Jednak jest gwarantowane do załadowania i jego pola zainicjowane i jego statyczny Konstruktor wywołuje się, zanim po raz pierwszy w programie odwołuje się do klasy. Statyczny Konstruktor jest wywoływany tylko jeden raz, a Klasa statyczna pozostaje w pamięci dla okresu istnienia domeny aplikacji, w której znajduje się program.  
  
> [!NOTE]
>  Aby utworzyć klasę niestatyczna, która zezwala na tylko jedno wystąpienie sam ma zostać utworzony, zobacz [wdrażanie pojedynczego wystąpienia w języku C#](https://msdn.microsoft.com/library/ms998558.aspx).  
  
 Poniższa lista zawiera główne funkcje klasy statycznej:  
  
-   Zawiera tylko statyczne elementy członkowskie.  
  
-   Nie można utworzyć wystąpienia.  
  
-   Jest zapieczętowany.  
  
-   Nie może zawierać [konstruktory wystąpień](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md).  
  
 Tworzenie klasy statycznej jest więc zasadniczo takie same, jak podczas tworzenia klasy, która zawiera tylko statyczne elementy członkowskie i Konstruktor prywatny. Konstruktor prywatny zapobiega uruchamianiu klasy. Zaletą używania klasy statycznej jest, że kompilator można sprawdzić, aby upewnić się, że nie składowych wystąpienia przypadkowo są dodawane. Kompilator gwarantuje, że nie można utworzyć wystąpienia tej klasy.  
  
 Klasy statyczne są zapieczętowane i nie może być dziedziczona. Nie można dziedziczyć wszystkie klasy, z wyjątkiem <xref:System.Object>. Klasy statyczne nie mogą zawierać konstruktora wystąpień; może jednak zawierać Konstruktor statyczny. Jeśli klasa zawiera statyczne elementy członkowskie, które wymagają inicjalizacji nietrywialnymi niestatycznych klas także zdefiniować Konstruktor statyczny. Aby uzyskać więcej informacji, zobacz [konstruktorów statycznych](../../../csharp/programming-guide/classes-and-structs/static-constructors.md).  
  
## <a name="example"></a>Przykład  
 Oto przykład klasy statycznej, która zawiera dwie metody, które konwertują temperaturę w stopniach Celsjusza do f i Fahrenheita do c:  
  
 [!code-csharp[csProgGuideObjects#31](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/static-classes-and-static-class-members_1.cs)]  
  
## <a name="static-members"></a>Statyczne elementy członkowskie  
 Klasy statyczne nie może zawierać metody statyczne, pola, właściwości lub zdarzenia. Statyczny element członkowski jest wywoływane w klasie, nawet wtedy, gdy utworzono żadnego wystąpienia klasy. Statyczny element członkowski zawsze odbywa się przy użyciu nazwy klasy, a nie nazwę wystąpienia. Istnieje tylko jedna kopia statyczny element członkowski, niezależnie od tego, jak wiele wystąpień klasy są tworzone. Statyczne metody i właściwości nie można uzyskać dostępu niestatycznego pola i zdarzenia w ich typem zawierającym i nie można uzyskać dostępu do zmiennej wystąpienia dowolnego obiektu, chyba że jawnie przekazany parametr metody.  
  
 Jest bardziej typowego do deklarowania niestatycznych klas z niektórych statycznych elementów członkowskich, niż zadeklarowanie całej klasy jako statyczny. Najczęstsze zastosowania dwóch pól statycznych są zapewnienie liczbę obiektów, które zostały utworzone lub do przechowywania wartości, które muszą być współużytkowane przez wszystkie wystąpienia.  
  
 Metody statyczne mogą być przeciążone, ale nie ich nadpisano, ponieważ należą do klasy, a nie do dowolnego wystąpienia klasy.  
  
 Mimo że pole nie może być zadeklarowana jako `static const`, [const](../../../csharp/language-reference/keywords/const.md) pole jest zasadniczo statyczne w jego zachowanie. Należy do typu, a nie do wystąpienia typu. W związku z tym, const pola są dostępne, korzystając z tych samych `ClassName.MemberName` notacji, który służy do pola statyczne. Żadne wystąpienie obiektu jest wymagana.  
  
 C# nie obsługuje statyczne zmienne lokalne (zmienne, które są zadeklarowane w zakresie metody).  
  
 Deklarowanie statyczni członkowie klas za pomocą `static` — słowo kluczowe przed zwracanym typem elementu członkowskiego, jak pokazano w poniższym przykładzie:  
  
 [!code-csharp[csProgGuideObjects#29](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/static-classes-and-static-class-members_2.cs)]  
  
 Statyczne elementy członkowskie są inicjowane przed statyczny element członkowski jest dostępny po raz pierwszy, a także przed statyczny Konstruktor, jeśli istnieje, zostanie wywołana. Aby uzyskać dostęp do składowej klasy statycznej, użyj nazwy klasy zamiast nazwy zmiennej do określenia lokalizacji elementu członkowskiego, jak pokazano w poniższym przykładzie:  
  
 [!code-csharp[csProgGuideObjects#30](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/static-classes-and-static-class-members_3.cs)]  
  
 Jeśli klasa zawiera pola statyczne, należy podać statyczny Konstruktor, który inicjuje je, gdy klasa jest ładowany.  
  
 Wywołanie metody statycznej generuje instrukcją call w języka Microsoft intermediate language (MSIL), natomiast generuje wywołanie metody wystąpienia `callvirt` instrukcji, co sprawdza również dla odwołuje się obiekt z wartością null. Jednak w większości przypadków różnicy wydajności między tymi dwoma nie ma znaczenia.  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [static](../../../csharp/language-reference/keywords/static.md)  
- [Klasy](../../../csharp/programming-guide/classes-and-structs/classes.md)  
- [class](../../../csharp/language-reference/keywords/class.md)  
- [Konstruktory statyczne](../../../csharp/programming-guide/classes-and-structs/static-constructors.md)  
- [Konstruktory wystąpień](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md)
