---
title: Finalizatory — C# Przewodnik programowania
ms.custom: seodec18
ms.date: 10/08/2018
helpviewer_keywords:
- ~ [C#], in finalizers
- C# language, finalizers
- finalizers [C#]
ms.assetid: 1ae6e46d-a4b1-4a49-abe5-b97f53d9e049
ms.openlocfilehash: f7cb9bd05d08a33be53abad58b78b39e36c6dffe
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73419360"
---
# <a name="finalizers-c-programming-guide"></a>Finalizatory (C# Przewodnik programowania)
Finalizatory (nazywane również **destruktorami**) służą do wykonywania wszelkich niezbędnych ostatecznych oczyszczeniów, gdy wystąpienie klasy jest zbierane przez moduł wyrzucania elementów bezużytecznych.  
  
## <a name="remarks"></a>Uwagi  
  
- Finalizatory nie mogą być zdefiniowane w strukturach. Są one używane tylko z klasami.  
  
- Klasa może mieć tylko jeden finalizator.  
  
- Finalizatory nie mogą być dziedziczone ani przeciążone.  
  
- Nie można wywołać finalizatorów. Są one wywoływane automatycznie.  
  
- Finalizator nie przyjmuje modyfikatorów ani nie ma parametrów.  
  
 Na przykład poniżej znajduje się deklaracja finalizatora dla klasy `Car`.
  
 [!code-csharp[csProgGuideObjects#86](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#86)]  

Finalizator może być również zaimplementowany jako definicja treści wyrażenia, jak pokazano w poniższym przykładzie.

[!code-csharp[expression-bodied-finalizer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-destructor.cs#1)]  
  
 Finalizator niejawnie wywołuje <xref:System.Object.Finalize%2A> w klasie podstawowej obiektu. W związku z tym wywołanie finalizatora jest niejawnie tłumaczone na następujący kod:  
  
```csharp  
protected override void Finalize()  
{  
    try  
    {  
        // Cleanup statements...  
    }  
    finally  
    {  
        base.Finalize();  
    }  
}  
```  
  
 Oznacza to, że metoda `Finalize` jest wywoływana cyklicznie dla wszystkich wystąpień w łańcuchu dziedziczenia, od najbardziej pochodnego do najmniej pochodnego.  
  
> [!NOTE]
> Nie należy używać pustych finalizatorów. Gdy Klasa zawiera finalizator, w kolejce `Finalize` jest tworzony wpis. Gdy finalizator jest wywoływany, Moduł wyrzucania elementów bezużytecznych jest wywoływany w celu przetworzenia kolejki. Pusty finalizator powoduje jedynie niepotrzebną utratę wydajności.  
  
 Programista nie ma kontroli nad tym, gdy finalizator jest wywoływany, ponieważ jest określany przez moduł wyrzucania elementów bezużytecznych. Moduł wyrzucania elementów bezużytecznych sprawdza obiekty, które nie są już używane przez aplikację. Jeśli uzna, że obiekt kwalifikuje się do finalizacji, wywołuje finalizator (jeśli istnieje) i ponownie przejmuje pamięć używaną do przechowywania obiektu. 
 
 W aplikacjach .NET Framework (ale nie w aplikacjach .NET Core) finalizatory są również wywoływane po zakończeniu działania programu. 
  
 Istnieje możliwość wymuszenia wyrzucania elementów bezużytecznych przez wywołanie <xref:System.GC.Collect%2A>, ale większości czasu, należy to uniknąć, ponieważ może to spowodować problemy z wydajnością.  
  
## <a name="using-finalizers-to-release-resources"></a>Korzystanie z finalizatorów do zwolnienia zasobów  
 Ogólnie rzecz biorąc C# , nie wymaga tak dużo zarządzania pamięcią, ile jest potrzebne podczas tworzenia w języku, który nie jest przeznaczony dla środowiska uruchomieniowego z odzyskiwaniem pamięci. Dzieje się tak, ponieważ .NET Framework Moduł wyrzucania elementów bezużytecznych niejawnie zarządza alokacją i ilością pamięci dla obiektów. Jeśli jednak aplikacja hermetyzuje niezarządzane zasoby, takie jak Windows, pliki i połączenia sieciowe, należy używać finalizatorów do zwolnienia tych zasobów. Gdy obiekt kwalifikuje się do finalizacji, Moduł wyrzucania elementów bezużytecznych uruchamia metodę `Finalize` obiektu.  
  
## <a name="explicit-release-of-resources"></a>Jawne wydanie zasobów  
 Jeśli aplikacja korzysta z kosztownych zasobów zewnętrznych, zalecamy również zapewnienie jawnie zwolnienia zasobu, zanim moduł wyrzucania elementów bezużytecznych zwolni obiekt. W tym celu należy zaimplementować metodę `Dispose` z interfejsu <xref:System.IDisposable>, który wykonuje wymagane czyszczenie dla obiektu. Może to znacząco poprawić wydajność aplikacji. Nawet w przypadku tej jawnej kontroli nad zasobami finalizator jest środkiem do czyszczenia zasobów, jeśli wywołanie metody `Dispose` nie powiodło się.  
  
 Więcej informacji o czyszczeniu zasobów znajduje się w następujących tematach:  
  
- [Oczyszczanie zasobów niezarządzanych](../../../standard/garbage-collection/unmanaged.md)  
  
- [Implementacja metody Dispose](../../../standard/garbage-collection/implementing-dispose.md)  
  
- [using, instrukcja](../../language-reference/keywords/using-statement.md)  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy trzy klasy, które tworzą łańcuch dziedziczenia. Klasa `First` jest klasą bazową, `Second` pochodzi od `First`, a `Third` pochodzi od `Second`. Wszystkie trzy mają finalizatory. W `Main`jest tworzone wystąpienie klasy z największą pochodną. Po uruchomieniu programu należy zauważyć, że finalizatory dla trzech klas są wywoływane automatycznie i w kolejności, od najbardziej pochodnego do najmniej pochodnego.  
  
 [!code-csharp[csProgGuideObjects#85](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#85)]  
  
## <a name="c-language-specification"></a>specyfikacja języka C#  

Aby uzyskać więcej informacji, zobacz sekcję [destruktory](~/_csharplang/spec/classes.md#destructors) [ C# specyfikacji języka](/dotnet/csharp/language-reference/language-specification/introduction).
  
## <a name="see-also"></a>Zobacz także

- <xref:System.IDisposable>
- [Przewodnik programowania w języku C#](../index.md)
- [Konstruktory](./constructors.md)
- [Odzyskiwanie pamięci](../../../standard/garbage-collection/index.md)
