---
title: Finalizatory (C# Programming Guide)
ms.date: 10/08/2018
helpviewer_keywords:
- ~ [C#], in finalizers
- C# language, finalizers
- finalizers [C#]
ms.assetid: 1ae6e46d-a4b1-4a49-abe5-b97f53d9e049
ms.openlocfilehash: 2b24884d2650a5e799eda630bc65f3c5a5c2508a
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53127267"
---
# <a name="finalizers-c-programming-guide"></a>Finalizatory (C# Programming Guide)
Finalizatory (są one również nazywane **destruktory**) są używane do wykonywania wszelkich niezbędnych końcowego oczyszczania, gdy wystąpienie klasy są gromadzone przez moduł odśmiecania pamięci.  
  
## <a name="remarks"></a>Uwagi  
  
-   Nie można zdefiniować finalizatory w strukturach. Są one używane tylko z klasami.  
  
-   Klasa może mieć tylko jedną finalizatora.  
  
-   Finalizatory nie może być dziedziczona ani przeciążone.  
  
-   Nie można wywołać finalizatorów. Są one wywoływane automatycznie.  
  
-   Finalizator zająć Modyfikatory lub nie mieć parametrów.  
  
 Na przykład Oto deklaracja finalizatora dla `Car` klasy.
  
 [!code-csharp[csProgGuideObjects#86](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/destructors_1.cs)]  

Finalizator może też być implementowany jako definicja treści wyrażenia, co ilustruje poniższy przykład.

[!code-csharp[expression-bodied-finalizer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-destructor.cs#1)]  
  
 Niejawnie wywołuje finalizator <xref:System.Object.Finalize%2A> w klasie bazowej obiektu. W związku z tym wywołanie finalizator niejawnie jest tłumaczona na następujący kod:  
  
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
  
 Oznacza to, że `Finalize` metoda jest wywoływana rekursywnie dla wszystkich wystąpień w łańcuch dziedziczenia z najbardziej pochodnego do najmniej pochodnego.  
  
> [!NOTE]
>  Nie należy używać puste finalizatory. Gdy klasa zawiera finalizator, zapis jest tworzony w `Finalize` kolejki. Wywołanego finalizator moduł odśmiecania pamięci jest wywoływana, aby przetworzyć kolejkę. Pusty finalizator powoduje po prostu niepotrzebnego utrata wydajności.  
  
 Programistę nie ma kontroli nad po wywołaniu finalizatora, ponieważ jest to określane przez moduł odśmiecania pamięci. Moduł zbierający elementy bezużyteczne sprawdza, czy obiekty nie są już używane przez aplikację. Jeśli obiekt kwalifikuje się do finalizacji, wywołuje finalizator (jeśli istnieje) i odzyskuje pamięć używaną do przechowywania obiektu. 
 
 W aplikacjach .NET Framework (ale nie w aplikacjach platformy .NET Core) finalizatory są również nazywane, gdy zamyka program. 
  
 Istnieje możliwość wymuszenia wyrzucania elementów bezużytecznych przez wywołanie metody <xref:System.GC.Collect%2A>, ale w większości przypadków, to należy unikać, ponieważ mogą one stanowić problemy z wydajnością.  
  
## <a name="using-finalizers-to-release-resources"></a>Aby zwolnić zasoby przy użyciu finalizatory  
 Ogólnie rzecz biorąc C# nie wymaga tak dużej ilości pamięci zarządzania zgodnie z potrzebami, podczas pracy z językiem, który nie jest przeznaczony do aparatu plików wykonywalnych wyrzucania elementów bezużytecznych. To dlatego moduł odśmiecania pamięci środowiska .NET Framework niejawnie zarządza alokacją i zwolnieniem pamięci dla obiektów. Jednak w przypadku aplikacji hermetyzuje niezarządzane zasoby, takie jak windows, pliki i połączenia sieciowe, należy używać finalizatory zwolnienie tych zasobów. Gdy obiekt jest uprawniona do finalizacji, wyrzucanie elementów bezużytecznych działa `Finalize` metody obiektu.  
  
## <a name="explicit-release-of-resources"></a>Jawnego zwolnienia zasobów  
 Jeśli aplikacja używa kosztowne zewnętrznego zasobu, zalecamy również, zapewniają sposób jawnie zwalniać zasobu, zanim moduł odśmiecania pamięci zwalnia obiektu. Możesz to zrobić poprzez implementację `Dispose` metody z <xref:System.IDisposable> interfejsu, który wykonuje niezbędne czyszczenia dla obiektu. Może to znacznie poprawić wydajność aplikacji. Nawet w przypadku tego jawną kontrolę nad zasobami finalizator będzie odpowiadać za czyszczenie zasobów, jeśli wywołanie `Dispose` metody nie powiodło się.  
  
 Aby uzyskać więcej informacji na temat Oczyszczanie zasobów zobacz następujące tematy:  
  
-   [Oczyszczanie zasobów niezarządzanych](../../../standard/garbage-collection/unmanaged.md)  
  
-   [Implementacja metody Dispose](../../../standard/garbage-collection/implementing-dispose.md)  
  
-   [using, instrukcja](../../../csharp/language-reference/keywords/using-statement.md)  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy trzy klasy, które w łańcuchu dziedziczenia. Klasa `First` jest klasą bazową `Second` jest tworzony na podstawie `First`, i `Third` jest tworzony na podstawie `Second`. Wszystkie trzy mają finalizatory. W `Main`, tworzone jest wystąpienie klasy najbardziej pochodnego. Po uruchomieniu program, zwróć uwagę, że finalizatory dla trzech klas są wywoływane automatycznie i w kolejności, z najbardziej pochodnego do najmniej pochodnego.  
  
 [!code-csharp[csProgGuideObjects#85](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/destructors_2.cs)]  
  
## <a name="c-language-specification"></a>specyfikacja języka C#  

Aby uzyskać więcej informacji, zobacz [destruktory](~/_csharplang/spec/classes.md#destructors) części [ C# specyfikacji języka](../../language-reference/language-specification/index.md).
  
## <a name="see-also"></a>Zobacz także

- <xref:System.IDisposable>  
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Konstruktory](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
- [Odzyskiwanie pamięci](../../../standard/garbage-collection/index.md)
