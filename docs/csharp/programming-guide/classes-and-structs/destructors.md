---
title: Finalizatory — Przewodnik programowania w języku C#
ms.date: 10/08/2018
helpviewer_keywords:
- ~ [C#], in finalizers
- C# language, finalizers
- finalizers [C#]
ms.assetid: 1ae6e46d-a4b1-4a49-abe5-b97f53d9e049
ms.openlocfilehash: 62fc531a8064a8a5cb144a89aa9975b3199db976
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990115"
---
# <a name="finalizers-c-programming-guide"></a>Finalizatory (Przewodnik programowania w języku C#)
Finalizatory (nazywane również **destruktorami**) służą do wykonywania wszelkich niezbędnych ostatecznych oczyszczeniów, gdy wystąpienie klasy jest zbierane przez moduł wyrzucania elementów bezużytecznych.  
  
## <a name="remarks"></a>Uwagi  
  
- Finalizatory nie mogą być zdefiniowane w strukturach. Są one używane tylko z klasami.  
  
- Klasa może mieć tylko jeden finalizator.  
  
- Finalizatory nie mogą być dziedziczone ani przeciążone.  
  
- Nie można wywołać finalizatorów. Są one wywoływane automatycznie.  
  
- Finalizator nie przyjmuje modyfikatorów ani nie ma parametrów.  
  
 Na przykład poniżej znajduje się deklaracja finalizatora dla `Car` klasy.
  
 [!code-csharp[csProgGuideObjects#86](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#86)]  

Finalizator może być również zaimplementowany jako definicja treści wyrażenia, jak pokazano w poniższym przykładzie.

[!code-csharp[expression-bodied-finalizer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-destructor.cs#1)]  
  
 Finalizator niejawnie wywołuje <xref:System.Object.Finalize%2A> klasę bazową obiektu. W związku z tym wywołanie finalizatora jest niejawnie tłumaczone na następujący kod:  
  
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
  
 Ten projekt oznacza, że `Finalize` Metoda jest wywoływana cyklicznie dla wszystkich wystąpień w łańcuchu dziedziczenia, od najbardziej pochodnego do najmniej pochodnego.  
  
> [!NOTE]
> Nie należy używać pustych finalizatorów. Gdy Klasa zawiera finalizator, w kolejce zostaje utworzony wpis `Finalize` . Gdy finalizator jest wywoływany, Moduł wyrzucania elementów bezużytecznych jest wywoływany w celu przetworzenia kolejki. Pusty finalizator powoduje jedynie niepotrzebną utratę wydajności.  
  
 Programista nie ma kontroli nad tym, kiedy finalizator jest wywoływany; Moduł zbierający elementy bezużyteczne decyduje o tym, kiedy ma być wywoływana. Moduł wyrzucania elementów bezużytecznych sprawdza obiekty, które nie są już używane przez aplikację. Jeśli uzna, że obiekt kwalifikuje się do finalizacji, wywołuje finalizator (jeśli istnieje) i ponownie przejmuje pamięć używaną do przechowywania obiektu.

 W aplikacjach .NET Framework (ale nie w aplikacjach .NET Core) finalizatory są również wywoływane po zakończeniu działania programu.
  
 Istnieje możliwość wymuszenia wyrzucania elementów bezużytecznych przez wywołanie <xref:System.GC.Collect%2A> , ale większość czasu, należy unikać tego wywołania, ponieważ może to spowodować problemy z wydajnością.  
  
## <a name="using-finalizers-to-release-resources"></a>Korzystanie z finalizatorów do zwolnienia zasobów  
 Ogólnie rzecz biorąc, język C# nie wymaga jak dużo zarządzania pamięcią w ramach dewelopera jako języków, które nie są przeznaczone do środowiska uruchomieniowego z wyrzucaniem elementów bezużytecznych. Dzieje się tak, ponieważ moduł wyrzucania elementów bezużytecznych platformy .NET niejawnie zarządza alokacją i ilością pamięci dla obiektów. Jeśli jednak aplikacja hermetyzuje niezarządzane zasoby, takie jak Windows, pliki i połączenia sieciowe, należy użyć finalizatorów do zwolnienia tych zasobów. Gdy obiekt kwalifikuje się do finalizacji, Moduł wyrzucania elementów bezużytecznych uruchamia `Finalize` metodę obiektu.
  
## <a name="explicit-release-of-resources"></a>Jawne wydanie zasobów  
 Jeśli aplikacja korzysta z kosztownych zasobów zewnętrznych, zalecamy również zapewnienie jawnie zwolnienia zasobu, zanim moduł wyrzucania elementów bezużytecznych zwolni obiekt. Aby zwolnić zasób, zaimplementuj `Dispose` metodę z <xref:System.IDisposable> interfejsu, który wykonuje niezbędne czyszczenie dla obiektu. Może to znacząco poprawić wydajność aplikacji. Nawet w przypadku tej jawnej kontroli nad zasobami finalizator jest środkiem do czyszczenia zasobów, jeśli wywołanie `Dispose` metody zakończy się niepowodzeniem.  
  
 Więcej informacji o czyszczeniu zasobów znajduje się w następujących artykułach:  
  
- [Oczyszczanie zasobów niezarządzanych](../../../standard/garbage-collection/unmanaged.md)  
  
- [Implementacja metody Dispose](../../../standard/garbage-collection/implementing-dispose.md)  
  
- [using, instrukcja](../../language-reference/keywords/using-statement.md)  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy trzy klasy, które tworzą łańcuch dziedziczenia. Klasa `First` jest klasą bazową, pochodzi `Second` od `First` , i pochodzi `Third` od `Second` . Wszystkie trzy mają finalizatory. W programie `Main` tworzone jest wystąpienie klasy najczęściej pochodnej. Po uruchomieniu programu należy zauważyć, że finalizatory dla trzech klas są wywoływane automatycznie i w kolejności, od najbardziej pochodnego do najmniej pochodnego.  
  
 [!code-csharp[csProgGuideObjects#85](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#85)]  
  
## <a name="c-language-specification"></a>specyfikacja języka C#  

Aby uzyskać więcej informacji, zobacz sekcję [destruktory](~/_csharplang/spec/classes.md#destructors) w [specyfikacji języka C#](/dotnet/csharp/language-reference/language-specification/introduction).
  
## <a name="see-also"></a>Zobacz też

- <xref:System.IDisposable>
- [Przewodnik programowania w języku C#](../index.md)
- [Konstruktory](./constructors.md)
- [Odzyskiwanie pamięci](../../../standard/garbage-collection/index.md)
