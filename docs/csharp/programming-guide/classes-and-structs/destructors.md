---
title: Finalizatory - Przewodnik programowania C#
ms.date: 10/08/2018
helpviewer_keywords:
- ~ [C#], in finalizers
- C# language, finalizers
- finalizers [C#]
ms.assetid: 1ae6e46d-a4b1-4a49-abe5-b97f53d9e049
ms.openlocfilehash: c8ad738baa3ff76cf9ae8367f2fd2a1fb44a79d6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79170302"
---
# <a name="finalizers-c-programming-guide"></a>Finalizatory (Przewodnik programowania C#)
Finalizatory (które są również nazywane **destruktory)** są używane do wykonywania wszelkich niezbędnych oczyszczania końcowego, gdy wystąpienie klasy jest zbierane przez moduł zbierający elementy bezużyteczne.  
  
## <a name="remarks"></a>Uwagi  
  
- Finalizatorów nie można zdefiniować w strukturach. Są one używane tylko z klasami.  
  
- Klasa może mieć tylko jeden finalizator.  
  
- Finalizatorów nie można dziedziczyć lub przeciążony.  
  
- Finalizatorów nie można wywołać. Są one wywoływane automatycznie.  
  
- Finalizator nie ma modyfikatorów lub parametry.  
  
 Na przykład poniżej jest deklaracja finalizatora `Car` dla klasy.
  
 [!code-csharp[csProgGuideObjects#86](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#86)]  

Finalizator można również zaimplementować jako definicję treści wyrażenia, jak pokazano w poniższym przykładzie.

[!code-csharp[expression-bodied-finalizer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-destructor.cs#1)]  
  
 Finalizator niejawnie wywołuje <xref:System.Object.Finalize%2A> klasy podstawowej obiektu. W związku z tym wywołanie finalizatora jest niejawnie tłumaczone na następujący kod:  
  
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
  
 Oznacza to, `Finalize` że metoda jest wywoływana cyklicznie dla wszystkich wystąpień w łańcuchu dziedziczenia, od najbardziej pochodnych do najmniej pochodnych.  
  
> [!NOTE]
> Puste finalizatory nie powinny być używane. Gdy klasa zawiera finalizator, wpis jest `Finalize` tworzony w kolejce. Gdy finalizator jest wywoływana, moduł zbierający elementy bezużyteczne jest wywoływany do przetwarzania kolejki. Pusty finalizator powoduje tylko niepotrzebną utratę wydajności.  
  
 Programista nie ma kontroli nad, gdy finalizator jest wywoływana, ponieważ jest to określane przez moduł zbierający elementy bezużyteczne. Moduł zbierający elementy bezużyteczne sprawdza obiekty, które nie są już używane przez aplikację. Jeśli uzna obiekt kwalifikujących się do finalizacji, wywołuje finalizator (jeśli istnieje) i odzyskuje pamięć używaną do przechowywania obiektu.

 W aplikacjach .NET Framework (ale nie w aplikacjach .NET Core) finalizatory są również wywoływane po zakończeniu programu.
  
 Istnieje możliwość wymuszenia <xref:System.GC.Collect%2A>wyrzucania elementów bezużytecznych przez wywołanie , ale przez większość czasu należy tego unikać, ponieważ może to spowodować problemy z wydajnością.  
  
## <a name="using-finalizers-to-release-resources"></a>Korzystanie z finalizatorów do zwalniania zasobów  
 Ogólnie rzecz biorąc C# nie wymaga tyle zarządzania pamięcią, ile jest potrzebne podczas tworzenia z językiem, który nie jest docelowy w czasie wykonywania z wyrzucania elementów bezużytecznych. Dzieje się tak, ponieważ moduł zbierający elementy bezużyteczne programu .NET Framework niejawnie zarządza alokacją i zwalnianiem pamięci dla obiektów. Jednak gdy aplikacja hermetyzuje zasoby niezarządzane, takie jak okna, pliki i połączenia sieciowe, należy użyć finalizatorów, aby zwolnić te zasoby. Gdy obiekt kwalifikuje się do finalizacji, moduł `Finalize` zbierający elementy bezużyteczne uruchamia metodę obiektu.  
  
## <a name="explicit-release-of-resources"></a>Jawne uwolnienie zasobów  
 Jeśli aplikacja używa drogiego zasobu zewnętrznego, zaleca się również zapewnienie sposobu jawnie zwolnić zasób przed moduł zbierający elementy bezużyteczne zwalnia obiekt. Można to zrobić, `Dispose` implementując <xref:System.IDisposable> metodę z interfejsu, który wykonuje niezbędne oczyszczania dla obiektu. Może to znacznie poprawić wydajność aplikacji. Nawet przy tej jawnej kontroli nad zasobami finalizator staje się `Dispose` zabezpieczeniem, aby oczyścić zasoby, jeśli wywołanie metody nie powiodło się.  
  
 Aby uzyskać więcej informacji na temat oczyszczania zasobów, zobacz następujące tematy:  
  
- [Oczyszczanie zasobów niezarządzanych](../../../standard/garbage-collection/unmanaged.md)  
  
- [Implementacja metody Dispose](../../../standard/garbage-collection/implementing-dispose.md)  
  
- [za pomocą instrukcji](../../language-reference/keywords/using-statement.md)  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy trzy klasy, które tworzą łańcuch dziedziczenia. Klasa `First` jest klasą `Second` podstawową, `First`pochodzi `Third` od , `Second`i pochodzi od . Wszystkie trzy mają finalizatorów. W `Main`przypadku wystąpienia klasy najbardziej pochodnych jest tworzony. Po uruchomieniu programu należy zauważyć, że finalizatory dla trzech klas są wywoływane automatycznie i w kolejności, od najbardziej pochodnych do najmniej pochodnych.  
  
 [!code-csharp[csProgGuideObjects#85](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#85)]  
  
## <a name="c-language-specification"></a>specyfikacja języka C#  

Aby uzyskać więcej informacji, zobacz [Destruktory](~/_csharplang/spec/classes.md#destructors) sekcji [specyfikacji języka Języka C#.](/dotnet/csharp/language-reference/language-specification/introduction)
  
## <a name="see-also"></a>Zobacz też

- <xref:System.IDisposable>
- [Przewodnik programowania języka C#](../index.md)
- [Konstruktory](./constructors.md)
- [Odzyskiwanie pamięci](../../../standard/garbage-collection/index.md)
