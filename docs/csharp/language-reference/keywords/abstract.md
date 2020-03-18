---
title: streszczenie — odwołanie do języka C#
ms.date: 07/20/2015
f1_keywords:
- abstract
- abstract_CSharpKeyword
helpviewer_keywords:
- abstract keyword [C#]
ms.assetid: b0797770-c1f3-4b4d-9441-b9122602a6bb
ms.openlocfilehash: 96e8bbce2e67c316d5cd1cd78e3e2506dabead25
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713865"
---
# <a name="abstract-c-reference"></a>abstract (odwołanie w C#)
Modyfikator `abstract` wskazuje, że modyfikowana rzecz ma brakjącą lub niekompletną implementację. Modyfikator abstrakcyjny może służyć z klas, metody, właściwości, indeksatory i zdarzenia. Użyj `abstract` modyfikatora w deklaracji klasy, aby wskazać, że klasa jest przeznaczona tylko do klasy podstawowej innych klas, nie tworzone samodzielnie. Elementy członkowskie oznaczone jako abstrakcyjne muszą być implementowane przez klasy nieabstrakcyjne, które wynikają z klasy abstrakcyjnej.
  
## <a name="example"></a>Przykład  
 W tym przykładzie `Square` klasa musi zapewnić `GetArea` implementację, `Shape`ponieważ pochodzi z:  
  
 [!code-csharp[csrefKeywordsModifiers#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#1)]
  
 Klasy abstrakcyjne mają następujące funkcje:  
  
- Nie można utworzyć wystąpienia klasy abstrakcyjnej.  
  
- Klasa abstrakcyjna może zawierać metody abstrakcyjne i akcesory.  
  
- Nie jest możliwe modyfikowanie klasy abstrakcyjnej za pomocą [modyfikatora zapieczętowanego,](./sealed.md) ponieważ dwa modyfikatory mają przeciwstawne znaczenie. Modyfikator `sealed` zapobiega dziedziczenia klasy `abstract` i modyfikator wymaga klasy do dziedziczenia.  
  
- Klasa nieabstrakcyjna pochodząca z klasy abstrakcyjnej musi zawierać rzeczywiste implementacje wszystkich dziedziczonych metod abstrakcyjnych i akcesorów.  
  
 Użyj `abstract` modyfikatora w deklaracji metody lub właściwości, aby wskazać, że metoda lub właściwość nie zawiera implementacji.  
  
 Metody abstrakcyjne mają następujące funkcje:  
  
- Metoda abstrakcyjna jest niejawnie metodą wirtualną.  
  
- Deklaracje metody abstrakcyjne są dozwolone tylko w klasach abstrakcyjnych.  
  
- Ponieważ deklaracja metody abstrakcyjnej nie zapewnia rzeczywistej implementacji, nie ma treści metody; deklaracja metody po prostu kończy się średnikiem i nie ma żadnych nawiasów klamrowych ({ }) po podpisie. Przykład:  
  
    ```csharp  
    public abstract void MyMethod();  
    ```  
  
     Implementacja jest dostarczana przez [override](./override.md)metody , który jest członkiem klasy nieabstrakcyjnej.  
  
- Jest to błąd, aby użyć modyfikatorów [statycznych](./static.md) lub [wirtualnych](./virtual.md) w deklaracji metody abstrakcyjnej.  
  
 Właściwości abstrakcyjne zachowują się jak metody abstrakcyjne, z wyjątkiem różnic w składni deklaracji i wywołania.  
  
- Jest to błąd, `abstract` aby użyć modyfikatora we właściwości statycznej.  
  
- Właściwość dziedziczona abstrakcyjne mogą być zastąpione w klasie pochodnej, dołączając deklarację właściwości, która używa modyfikatora [zastępowania.](./override.md)  
  
 Aby uzyskać więcej informacji na temat klas abstrakcyjnych, zobacz [Klasy abstrakcyjne i zapieczętowane oraz Elementy członkowskie klasy](../../programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).  
  
 Klasa abstrakcyjna musi zapewnić implementację dla wszystkich elementów członkowskich interfejsu.  
  
 Klasa abstrakcyjna, która implementuje interfejs może mapować metody interfejsu na metody abstrakcyjne. Przykład:  
  
[!code-csharp[csrefKeywordsModifiers#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#2)]
  
## <a name="example"></a>Przykład  
 W tym przykładzie `DerivedClass` klasa pochodzi z klasy `BaseClass`abstrakcyjnej . Klasa abstrakcyjna zawiera metodę `AbstractMethod`abstrakcyjną i dwie `X` `Y`właściwości abstrakcyjne i .  
  
[!code-csharp[csrefKeywordsModifiers#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#3)]
  
 W poprzednim przykładzie, jeśli spróbujesz utworzyć wystąpienia klasy abstrakcyjnej przy użyciu instrukcji w stylu:  
  
```csharp
BaseClass bc = new BaseClass();   // Error  
```  
  
Pojawi się błąd mówiący, że kompilator nie może utworzyć wystąpienia klasy abstrakcyjnej "BaseClass".  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Odwołanie do języka C#](../index.md)
- [Przewodnik programowania języka C#](../../programming-guide/index.md)
- [Modyfikatory](index.md)
- [virtual](./virtual.md)
- [override](./override.md)
- [Słowa kluczowe języka C#](./index.md)
