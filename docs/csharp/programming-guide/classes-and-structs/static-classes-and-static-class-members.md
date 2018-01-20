---
title: "Klasy statyczne i statyczni członkowie klas (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- C# language, static members
- static members [C#]
- static classes [C#]
- C# language, static classes
- static class members [C#]
ms.assetid: 235614b5-1371-4dbd-9abd-b406a8b0298b
caps.latest.revision: "49"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b1e7366d8d82ca99a8d779dda1e194dcc8c2ab6e
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="static-classes-and-static-class-members-c-programming-guide"></a>Klasy statyczne i statyczni członkowie klas (Przewodnik programowania w języku C#)
A [statycznej](../../../csharp/language-reference/keywords/static.md) klasy jest zasadniczo taki sam, jak Klasa statyczna, ale ma różnicy jednego: nie można utworzyć wystąpienia klasy statycznej. Innymi słowy, nie można użyć [nowe](../../../csharp/language-reference/keywords/new.md) — słowo kluczowe, aby utworzyć zmienną typu klasy. Ponieważ nie ma żadnych zmienna wystąpienia, możesz uzyskać dostęp z członkami klasy statycznej przy użyciu Nazwa klasy. Na przykład, jeśli statycznego klasy, która jest nazywane `UtilityClass` mający publiczną metodę o nazwie `MethodA`, należy wywołać metodę, jak pokazano w poniższym przykładzie:  
  
```csharp  
UtilityClass.MethodA();  
```  
  
 Klasa statyczna może służyć jako kontener wygodny dla zestawów metody, które właśnie działać na parametry wejściowe i nie mają do pobierania lub ustawiania wszystkie pola wystąpienia wewnętrznego. Na przykład w bibliotece w klas programu .NET Framework, statycznych <xref:System.Math?displayProperty=nameWithType> klasa zawiera metody, które wykonują operacje matematyczne, bez konieczności przechowywania i pobierania danych, która jest unikatowa dla konkretnego wystąpienia <xref:System.Math> klasy. Oznacza to należy zastosować elementów członkowskich klasy, określając nazwę klasy i nazwę metody, jak pokazano w poniższym przykładzie.  
  
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
  
 Podobnie jak w przypadku wszystkich typów klasy, informacje o typie dla klasy statycznej jest ładowany przez [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] środowisko uruchomieniowe języka wspólnego (CLR) po załadowaniu program, który odwołuje się do klasy. Program nie można określić dokładnie po załadowaniu klasy. Jednak gwarantowane do załadowania i jego pola zainicjowane i jego Konstruktor statyczny wywoływana przed po raz pierwszy w programie odwołuje się do klasy. Konstruktor statyczny wywołana tylko raz, a Klasa statyczna pozostaje w pamięci przez czas ich istnienia domeny aplikacji, w której znajduje się program.  
  
> [!NOTE]
>  Aby utworzyć niestatyczna klasę, która umożliwia tylko jednego wystąpienia samej siebie, należy utworzyć, zobacz [implementacja Singleton w języku C#](https://msdn.microsoft.com/library/ms998558.aspx).  
  
 Poniżej przedstawiono główne elementy klasy statycznej:  
  
-   Zawiera tylko statyczne elementy członkowskie.  
  
-   Nie można utworzyć wystąpienia.  
  
-   Jest zapieczętowany.  
  
-   Nie może zawierać [konstruktorów wystąpienia](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md).  
  
 Tworzenie statycznej klasy jest w związku z tym zasadniczo taki sam jak podczas tworzenia klasy, która zawiera tylko statyczne elementy członkowskie i Konstruktor prywatny. Konstruktor prywatny uniemożliwia utworzenia wystąpienia klasy. Zaletą używania Klasa statyczna jest kompilator można sprawdzić upewnij się, że przypadkowo dodania żadnych członków wystąpienia. Kompilator gwarantuje, że nie można utworzyć wystąpienia tej klasy.  
  
 Klasy statyczne są zapieczętowane i nie może być dziedziczona. Nie można dziedziczyć dowolnej klasy, z wyjątkiem <xref:System.Object>. Klasy statyczne nie mogą zawierać konstruktora wystąpienia; może jednak zawierać Konstruktor statyczny. Niestatyczne klasy powinny również definiować Konstruktor statyczny, jeśli klasa zawiera statycznych elementów członkowskich, które wymagają nieuproszczony inicjowania. Aby uzyskać więcej informacji, zobacz [konstruktory statyczne](../../../csharp/programming-guide/classes-and-structs/static-constructors.md).  
  
## <a name="example"></a>Przykład  
 Oto przykład statycznej klasy, która zawiera dwie metody, których przekonwertować temperatury z c do f i f do c:  
  
 [!code-csharp[csProgGuideObjects#31](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/static-classes-and-static-class-members_1.cs)]  
  
## <a name="static-members"></a>Statyczne elementy członkowskie  
 Klasy statyczne nie może zawierać metod statycznych, pola, właściwości lub zdarzeń. Statyczny element członkowski jest można wywołać w klasie, nawet wtedy, gdy utworzono żadne wystąpienie klasy. Statyczny element członkowski jest zawsze dostęp do nazwy klasy, a nie nazwę wystąpienia. Istnieje tylko jedna kopia statycznego elementu członkowskiego, niezależnie od tego, jak wiele wystąpień klasy są tworzone. Właściwości i metod statycznych nie można uzyskać dostępu niestatycznego pola i zdarzeń w ich typ zawierający, a nie może uzyskać dostępu do zmiennej wystąpienia dowolnego obiektu, chyba że jawnie przekazany parametr metody.  
  
 Jest bardziej typowego do zadeklarowania klasy niestatycznego z niektórych statycznych elementów członkowskich, niż Aby zadeklarować całej klasy jako statyczny. Najczęstsze zastosowania dwóch pól statycznych są zachowanie liczbę liczbę obiektów, które zostały utworzone, lub do przechowywania wartości, które muszą być współużytkowane przez wszystkie wystąpienia.  
  
 Metody statyczne mogą być przeciążone, ale nie została zastąpiona, ponieważ należą do klasy, a nie do dowolnego wystąpienia klasy.  
  
 Mimo że pola nie może być zadeklarowany jako `static const`, [const](../../../csharp/language-reference/keywords/const.md) pole jest zasadniczo statyczne w jego zachowania. Należy do tego typu, a nie do wystąpień typu. W związku z tym const pola są dostępne za pomocą takie same `ClassName.MemberName` notation używanym dla pola statyczne. Żadne wystąpienie obiektu jest wymagana.  
  
 C# nie obsługuje statycznych zmiennych lokalnych (zmienne, które są zadeklarowane w zakresie metody).  
  
 Deklarowanie klas statycznych elementów członkowskich za pomocą `static` — słowo kluczowe przed zwracanym typem elementu członkowskiego, jak pokazano w poniższym przykładzie:  
  
 [!code-csharp[csProgGuideObjects#29](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/static-classes-and-static-class-members_2.cs)]  
  
 Statyczne elementy członkowskie są inicjowane przed statyczny element członkowski jest dostępny po raz pierwszy, a przed statycznego konstruktora, jeśli istnieje, jest wywoływana. Aby uzyskać dostęp do elementu członkowskiego klasy statycznej, użyj nazwy klasy zamiast nazwy zmiennej do określenia lokalizacji elementu członkowskiego, jak pokazano w poniższym przykładzie:  
  
 [!code-csharp[csProgGuideObjects#30](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/static-classes-and-static-class-members_3.cs)]  
  
 Jeśli klasa zawiera pola statyczne, podaj statycznego konstruktora, który inicjuje je po załadowaniu klasy.  
  
 Wywołanie metody statycznej generuje instrukcję wywołanie w języku pośrednim firmy Microsoft (MSIL), natomiast generuje wywołanie do metody wystąpienia `callvirt` instrukcji, która sprawdza również dla obiekt zerowy odwołuje się do. Jednak w większości przypadków różnicy wydajności między tymi dwoma nie ma znaczenia.  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [static](../../../csharp/language-reference/keywords/static.md)  
 [Klasy](../../../csharp/programming-guide/classes-and-structs/classes.md)  
 [class](../../../csharp/language-reference/keywords/class.md)  
 [Konstruktory statyczne](../../../csharp/programming-guide/classes-and-structs/static-constructors.md)  
 [Konstruktory wystąpień](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md)
