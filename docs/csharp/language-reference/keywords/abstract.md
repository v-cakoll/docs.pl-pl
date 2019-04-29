---
title: abstract — C# odwołania
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- abstract
- abstract_CSharpKeyword
helpviewer_keywords:
- abstract keyword [C#]
ms.assetid: b0797770-c1f3-4b4d-9441-b9122602a6bb
ms.openlocfilehash: a85cf00a8dd1b406c7e5185fd332a507a3ca7c83
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61662234"
---
# <a name="abstract-c-reference"></a>abstract (odwołanie w C#)
`abstract` Modyfikator oznacza, że rzecz modyfikowanego ma implementacji brakujące lub niekompletne. Abstrakcyjna modyfikatora można używać z klas, metod, właściwości, indeksatorów i zdarzeń. Użyj `abstract` modyfikatora w deklaracji klasy, aby wskazać, że klasa jest przeznaczona do użycia wyłącznie jako klasa bazowa innych klas. Elementy członkowskie oznaczony jako abstrakcyjny lub zawarte w klasie abstrakcyjnej, muszą być zaimplementowane przez klasy, które pochodzą z klasy abstrakcyjnej.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie klasa `Square` musi dostarczać implementację `Area` ponieważ dziedziczy `ShapesClass`:  
  
 [!code-csharp[csrefKeywordsModifiers#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#1)]
  
 Klasy abstrakcyjne oferują następujące funkcje:  
  
- Nie można utworzyć wystąpienia klasy abstrakcyjnej.  
  
- Klasa abstrakcyjna może zawierać metody abstrakcyjne i metod dostępu.  
  
- Nie można modyfikować klasy abstrakcyjnej jest [zapieczętowanego](../../../csharp/language-reference/keywords/sealed.md) modyfikator ponieważ modyfikatorów mają znaczenie odwrotną. `sealed` Modyfikator zapobiega są dziedziczone przez klasy i `abstract` modyfikator wymaga klasy dziedziczone.  
  
- Nieabstrakcyjnej klasy pochodnej z klasy abstrakcyjnej muszą zawierać rzeczywistej implementacji wszystkie odziedziczone metody abstrakcyjne i metod dostępu.  
  
 Użyj `abstract` modyfikatora w deklaracji metody lub właściwości w celu wskazania, że metoda lub właściwość nie zawiera implementacji.  
  
 Metody abstrakcyjne oferują następujące funkcje:  
  
- Metoda abstrakcyjna jest niejawnie metodę wirtualną.  
  
- Deklaracje metody abstrakcyjne są dozwolone tylko w klas abstrakcyjnych.  
  
- Ponieważ deklaracja metody abstrakcyjnej zapewnia nie rzeczywiste wdrożenie, jest nie treści metody; Deklaracja metody po prostu kończy się średnikiem wiąże się nie nawiasów klamrowych ({}) po podpis. Na przykład:  
  
    ```csharp  
    public abstract void MyMethod();  
    ```  
  
     Implementacja znajduje się za pomocą metody [zastąpienia](../../../csharp/language-reference/keywords/override.md), który jest członkiem klasy nieabstrakcyjnej.  
  
- Jest to błąd, aby użyć [statyczne](../../../csharp/language-reference/keywords/static.md) lub [wirtualnego](../../../csharp/language-reference/keywords/virtual.md) Modyfikatory w deklaracji metody abstrakcyjnej.  
  
 Właściwości abstrakcyjne zachowują się jak metody abstrakcyjne, z wyjątkiem różnic w składni deklaracji i wywoływania.  
  
- Jest to błąd, aby użyć `abstract` modyfikator na właściwość statyczna.  
  
- To właściwość dziedziczona abstrakcyjna może zostać przesłonięta w klasie pochodnej przez tym deklaracja właściwości, która używa [zastąpienia](../../../csharp/language-reference/keywords/override.md) modyfikator.  
  
 Aby uzyskać więcej informacji na temat klasy abstrakcyjne, zobacz [abstrakcyjnych i zapieczętowanych klas i składowych klasy](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).  
  
 Klasa abstrakcyjna należy podać implementacja dla wszystkich członków interfejsu.  
  
 Klasa abstrakcyjna, która implementuje interfejs może mapować metod interfejsu do metody abstrakcyjne. Na przykład:  
  
[!code-csharp[csrefKeywordsModifiers#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#2)]
  
## <a name="example"></a>Przykład  
 W tym przykładzie klasa `DerivedClass` pochodzi z klasy abstrakcyjnej `BaseClass`. Abstrakcyjna klasa zawiera metody abstrakcyjnej, `AbstractMethod`, a dwie właściwości abstrakcyjnych, `X` i `Y`.  
  
[!code-csharp[csrefKeywordsModifiers#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#3)]
  
 W poprzednim przykładzie, jeśli użytkownik podejmie próbę utworzenia wystąpienia klasy abstrakcyjnej, przy użyciu instrukcji w następujący sposób:  
  
```csharp
BaseClass bc = new BaseClass();   // Error  
```  
  
Otrzymasz błąd informujący o tym, że kompilator nie można utworzyć wystąpienia klasy abstrakcyjnej "BaseClass".  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../../../csharp/language-reference/index.md)
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
- [Modyfikatory](../../../csharp/language-reference/keywords/modifiers.md)
- [virtual](../../../csharp/language-reference/keywords/virtual.md)
- [override](../../../csharp/language-reference/keywords/override.md)
- [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)
