---
title: "abstract (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- abstract
- abstract_CSharpKeyword
helpviewer_keywords: abstract keyword [C#]
ms.assetid: b0797770-c1f3-4b4d-9441-b9122602a6bb
caps.latest.revision: "24"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: bd26583c42302d8ce9ba4dd22119713548111236
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="abstract-c-reference"></a>abstract (odwołanie w C#)
`abstract` Modyfikator oznacza, że element jest modyfikowany ma implementacji brakujące lub niekompletne. Modyfikator abstract można używać z klas, metod, właściwości, indeksatorów i zdarzeń. Użyj `abstract` modyfikatora w deklaracji klasy, aby wskazać, że klasa jest przeznaczona tylko jako klasę podstawową innych klas. Elementy członkowskie oznaczony jako abstrakcyjny lub częścią klasa abstrakcyjna, musi być implementowana przez klasy, które pochodzi z klasy abstrakcyjnej.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie klasa `Square` musi zapewniać implementację elementu `Area` ponieważ dziedziczy `ShapesClass`:  
  
 [!code-csharp[csrefKeywordsModifiers#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/abstract_1.cs)]  
  
 Klasy abstrakcyjne są następujące funkcje:  
  
-   Nie można utworzyć wystąpienia klasy abstrakcyjnej.  
  
-   Abstrakcyjna klasa może zawierać metody abstrakcyjne i metody dostępu.  
  
-   Nie można modyfikować klasy abstrakcyjnej jest [zapieczętowanego](../../../csharp/language-reference/keywords/sealed.md) modyfikator ponieważ przeciwną znaczenie ma dwa modyfikatorów. `sealed` Modyfikator uniemożliwia dziedziczone przez klasy i `abstract` modyfikator wymaga klasy być dziedziczone.  
  
-   Nieabstrakcyjnej klasy pochodnej z klasy abstrakcyjnej muszą zawierać rzeczywiste implementacje wszystkich dziedziczonej metody abstrakcyjne i metody dostępu.  
  
 Użyj `abstract` modyfikatora w deklaracji metody lub właściwości, aby wskazać, że ta metoda lub właściwość nie zawiera implementacji.  
  
 Metody abstrakcyjne są następujące funkcje:  
  
-   Metoda abstrakcyjna niejawnie jest metoda wirtualna.  
  
-   Deklaracje metody abstrakcyjnej są dozwolone tylko w klasie abstrakcyjnej.  
  
-   Deklaracja metody abstrakcyjnej udostępnia nie rzeczywistego wykonania, więc nie istnieje żadne treści metody; Deklaracja metody kończy się po prostu średnikiem i nie ma żadnych nawiasy klamrowe ({}) po podpisu. Na przykład:  
  
    ```csharp  
    public abstract void MyMethod();  
    ```  
  
     Implementacja jest zapewniana przez metodę zastępującą[zastąpienia](../../../csharp/language-reference/keywords/override.md), który jest elementem członkowskim klasy nieabstrakcyjnej.  
  
-   Jest błędem [statycznych](../../../csharp/language-reference/keywords/static.md) lub [wirtualnego](../../../csharp/language-reference/keywords/virtual.md) Modyfikatory w deklaracji metody abstrakcyjnej.  
  
 Właściwości abstrakcyjne przypominają metody abstrakcyjne, z wyjątkiem różnice w deklaracji i wywołanie składni.  
  
-   Jest błędem `abstract` modyfikator na właściwość statyczna.  
  
-   Właściwość abstrakcyjną dziedziczone może zostać przesłonięta w klasie pochodnej przez tym deklaracji właściwości, która używa [zastąpienia](../../../csharp/language-reference/keywords/override.md) modyfikator.  
  
 Aby uzyskać więcej informacji na temat klas abstrakcyjnych, zobacz [abstrakcyjne i zapieczętowane klasy oraz członkowie klas](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).  
  
 Klasa abstrakcyjna musi zapewniać implementację dla wszystkich członków interfejsu.  
  
 Klasa abstrakcyjna, która implementuje interfejs mogą być mapowane na metody abstrakcyjne metod interfejsu. Na przykład:  
  
 [!code-csharp[csrefKeywordsModifiers#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/abstract_2.cs)]  
  
## <a name="example"></a>Przykład  
 W tym przykładzie klasa `DerivedClass` pochodzi z klasy abstrakcyjnej `BaseClass`. Abstrakcyjna klasa zawiera metody abstrakcyjnej `AbstractMethod`, a dwie właściwości abstrakcyjnych, `X` i `Y`.  
  
 [!code-csharp[csrefKeywordsModifiers#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/abstract_3.cs)]  
  
 W poprzednim przykładzie, jeśli podjęto próbę utworzenia wystąpienia klasy abstrakcyjnej przy użyciu instrukcji w następujący sposób:  
  
```csharp
BaseClass bc = new BaseClass();   // Error  
```  
  
wystąpi błąd informujący o tym, że kompilator nie można utworzyć wystąpienia klasy abstrakcyjnej "Baseclass —".  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Modyfikatory](../../../csharp/language-reference/keywords/modifiers.md)  
 [virtual](../../../csharp/language-reference/keywords/virtual.md)  
 [override](../../../csharp/language-reference/keywords/override.md)  
 [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)
