---
title: C# odwołanie abstrakcyjne
ms.date: 07/20/2015
f1_keywords:
- abstract
- abstract_CSharpKeyword
helpviewer_keywords:
- abstract keyword [C#]
ms.assetid: b0797770-c1f3-4b4d-9441-b9122602a6bb
ms.openlocfilehash: 96e8bbce2e67c316d5cd1cd78e3e2506dabead25
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713865"
---
# <a name="abstract-c-reference"></a>abstract (odwołanie w C#)
Modyfikator `abstract` wskazuje, że modyfikowany element nie ma lub niekompletnej implementacji. Modyfikator abstrakcyjny może być używany z klasami, metodami, właściwościami, indeksatorami i zdarzeniami. Użyj modyfikatora `abstract` w deklaracji klasy, aby wskazać, że Klasa jest przeznaczona tylko jako klasa bazowa innych klas, ale nie jest tworzona samodzielnie. Elementy członkowskie oznaczone jako abstrakcyjne muszą być zaimplementowane przez nieabstrakcyjne klasy, które pochodzą z klasy abstrakcyjnej.
  
## <a name="example"></a>Przykład  
 W tym przykładzie Klasa `Square` musi dostarczyć implementację `GetArea`, ponieważ pochodzi ona z `Shape`:  
  
 [!code-csharp[csrefKeywordsModifiers#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#1)]
  
 Klasy abstrakcyjne mają następujące funkcje:  
  
- Nie można utworzyć wystąpienia klasy abstrakcyjnej.  
  
- Klasa abstrakcyjna może zawierać metody abstrakcyjne i metod dostępu.  
  
- Nie można zmodyfikować klasy abstrakcyjnej za pomocą modyfikatora [zapieczętowanego](./sealed.md) , ponieważ dwa Modyfikatory mają przeciwległe znaczenie. Modyfikator `sealed` uniemożliwia dziedziczenie klasy, a modyfikator `abstract` wymaga dziedziczenia klasy.  
  
- Klasa nieabstrakcyjna pochodna klasy abstrakcyjnej musi zawierać rzeczywiste implementacje wszystkich dziedziczonych metod abstrakcyjnych i metody dostępu.  
  
 Użyj modyfikatora `abstract` w deklaracji metody lub właściwości, aby wskazać, że metoda lub właściwość nie zawiera implementacji.  
  
 Metody abstrakcyjne mają następujące funkcje:  
  
- Metoda abstrakcyjna jest niejawnie metodą wirtualną.  
  
- Deklaracje metody abstrakcyjnej są dozwolone tylko w klasach abstrakcyjnych.  
  
- Ponieważ Deklaracja metody abstrakcyjnej nie zapewnia rzeczywistej implementacji, nie istnieje treść metody; Deklaracja metody po prostu kończyć się średnikiem i nie ma nawiasów klamrowych ({}) po podpisie. Na przykład:  
  
    ```csharp  
    public abstract void MyMethod();  
    ```  
  
     Implementacja jest dostarczana przez [przesłonięcie](./override.md)metody, która jest elementem członkowskim klasy nieabstrakcyjnej.  
  
- Wystąpił błąd podczas używania modyfikatorów [static](./static.md) lub [Virtual](./virtual.md) w deklaracji metody abstrakcyjnej.  
  
 Właściwości abstrakcyjne zachowują się jak metody abstrakcyjne, z wyjątkiem różnic w składni deklaracji i wywołania.  
  
- Wystąpił błąd podczas używania modyfikatora `abstract` na właściwości statycznej.  
  
- Abstrakcyjna dziedziczona właściwość może zostać przesłonięta w klasie pochodnej przez dołączenie deklaracji właściwości, która używa modyfikatora [przesłaniania](./override.md) .  
  
 Aby uzyskać więcej informacji na temat klas abstrakcyjnych, zobacz [klasy abstrakcyjne i zapieczętowane oraz składowe klas](../../programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).  
  
 Klasa abstrakcyjna musi zapewniać implementację dla wszystkich elementów członkowskich interfejsu.  
  
 Klasa abstrakcyjna implementująca interfejs może mapować metody interfejsu na metody abstrakcyjne. Na przykład:  
  
[!code-csharp[csrefKeywordsModifiers#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#2)]
  
## <a name="example"></a>Przykład  
 W tym przykładzie Klasa `DerivedClass` pochodzi od klasy abstrakcyjnej `BaseClass`. Klasa abstrakcyjna zawiera metodę abstrakcyjną, `AbstractMethod`i dwie właściwości abstrakcyjne, `X` i `Y`.  
  
[!code-csharp[csrefKeywordsModifiers#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#3)]
  
 W poprzednim przykładzie, jeśli spróbujesz utworzyć wystąpienie klasy abstrakcyjnej przy użyciu instrukcji podobnej do:  
  
```csharp
BaseClass bc = new BaseClass();   // Error  
```  
  
Zostanie wyświetlony komunikat o błędzie informujący, że kompilator nie może utworzyć wystąpienia klasy abstrakcyjnej "BaseClass".  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Modyfikatory](index.md)
- [virtual](./virtual.md)
- [override](./override.md)
- [Słowa kluczowe języka C#](./index.md)
