---
title: Finalizatory (C# przewodnik programowania w języku)
ms.date: 05/10/2017
helpviewer_keywords:
- ~ [C#], in finalizers
- C# language, finalizers
- finalizers [C#]
ms.assetid: 1ae6e46d-a4b1-4a49-abe5-b97f53d9e049
ms.openlocfilehash: fc15818883736015419f8599d482185bbab5120a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="finalizers-c-programming-guide"></a>Finalizatory (C# przewodnik programowania w języku)
Finalizatory są używane do destruct wystąpień klas.  
  
## <a name="remarks"></a>Uwagi  
  
-   Finalizatory nie może być zdefiniowana w strukturach. Są one używane tylko z klasami.  
  
-   Klasa może zawierać tylko jeden finalizatora.  
  
-   Finalizatory nie może być dziedziczona ani przeciążony.  
  
-   Nie można wywoływać finalizatory. Są wywoływane automatycznie.  
  
-   Finalizator podjąć Modyfikatory lub nie ma parametrów.  
  
 Na przykład poniżej przedstawiono deklaracji finalizatora dla `Car` klasy.
  
 [!code-csharp[csProgGuideObjects#86](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/destructors_1.cs)]  

Finalizator może być wykonany również jako definicja treść wyrażenia, jak przedstawiono na poniższym przykładzie.

[!code-csharp[expression-bodied-finalizer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-destructor.cs#1)]  
  
 Finalizator niejawnie wywołuje <xref:System.Object.Finalize%2A> dla klasy podstawowej obiektu. W związku z tym wywołaniu finalizator jest niejawnie przekonwertowana na następujący kod:  
  
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
  
 Oznacza to, że `Finalize` metoda jest wywoływana rekursywnie dla wszystkich wystąpień w łańcuch dziedziczenia z większość opartych na najmniejszą pochodny.  
  
> [!NOTE]
>  Nie należy używać puste finalizatory. Jeśli klasa zawiera finalizator, wpis jest tworzony w `Finalize` kolejki. Po wywołaniu finalizator moduł garbage collector jest wywoływane w celu przetworzenia kolejki. Pusty finalizator tylko powoduje, że zbędne spadek wydajności.  
  
 Programista nie ma kontroli nad, gdy jest wywoływana finalizator, ponieważ jest to określane przez moduł garbage collector. Moduł zbierający elementy bezużyteczne sprawdza, czy obiekty, które są już używane przez aplikację. Jeśli obiekt uzna uprawnia do skorzystania z finalizacji, wywołuje finalizatora (jeśli istnieje) i zwraca pamięć używana do przechowywania obiektu. Finalizatory są również nazywane, gdy program jest kończona.  
  
 Można wymusić wyrzucanie elementów bezużytecznych przez wywołanie metody <xref:System.GC.Collect%2A>, ale w większości przypadków, to należy unikać, ponieważ może spowodować problemy z wydajnością.  
  
## <a name="using-finalizers-to-release-resources"></a>Przy użyciu finalizatory do zwolnienia zasobów  
 Ogólnie rzecz biorąc C# nie wymaga tyle zarządzania pamięcią, ile potrzeba podczas pracy z językiem, który nie ma środowiska wykonawczego o wyrzucanie elementów bezużytecznych. Jest to spowodowane modułu zbierającego elementy bezużyteczne .NET Framework niejawnie zarządza alokacji i wersji pamięci dla obiektów. Jednak gdy aplikacja hermetyzuje niezarządzane zasoby, takie jak windows, plików i połączenia sieciowe, należy używać finalizatory aby zwolnić zasoby. Gdy obiekt jest uprawniona do finalizacji, moduł zbierający elementy bezużyteczne uruchamia `Finalize` metody obiektu.  
  
## <a name="explicit-release-of-resources"></a>Jawnego zwolnienia zasobów  
 Jeśli aplikacja używa kosztowne zewnętrzny zasób, zalecamy również musisz zapewnić sposób jawnego zwolnienia zasobu przed moduł garbage collector zwolnienia obiektu. Aby to zrobić, implementacja `Dispose` metody z <xref:System.IDisposable> interfejsu, który wykonuje cleanup konieczne dla obiekt. Może to znacznie zwiększyć wydajność aplikacji. Nawet w przypadku tego jawną kontrolę zasobów finalizator staje się zabezpieczenia, aby wyczyścić zasoby, jeśli wywołanie `Dispose` metody nie powiodło się.  
  
 Aby uzyskać więcej informacji na temat Oczyszczanie zasobów zobacz następujące tematy:  
  
-   [Oczyszczanie zasobów niezarządzanych](../../../standard/garbage-collection/unmanaged.md)  
  
-   [Implementacja metody Dispose](../../../standard/garbage-collection/implementing-dispose.md)  
  
-   [using, instrukcja](../../../csharp/language-reference/keywords/using-statement.md)  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy trzech klas, które łańcuch dziedziczenia. Klasa `First` jest klasą bazową `Second` jest pochodną `First`, i `Third` jest pochodną `Second`. Wszystkie trzy ma finalizatory. W `Main`, tworzone jest wystąpienie klasy pochodnej większość. Po uruchomieniu tego programu, zwróć uwagę, że finalizatory dla trzech klas zostaną wywołane automatycznie i w kolejności, większość opartych na najmniejszą pochodny.  
  
 [!code-csharp[csProgGuideObjects#85](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/destructors_2.cs)]  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.IDisposable>  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Konstruktory](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
 [Odzyskiwanie pamięci](../../../standard/garbage-collection/index.md)
