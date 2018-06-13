---
title: sealed (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- sealed
- sealed_CSharpKeyword
helpviewer_keywords:
- sealed keyword [C#]
ms.assetid: 8e4ed5d3-10be-47db-9488-0da2008e6f3f
ms.openlocfilehash: bd4fe2cfe80930c121a11d03c848b2c4eca152d6
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2018
ms.locfileid: "34172126"
---
# <a name="sealed-c-reference"></a>sealed (odwołanie w C#)
Po zastosowaniu do klasy, `sealed` modyfikator uniemożliwia innym klasom dziedziczenie z tego. W poniższym przykładzie klasa `B` dziedziczy z klasy `A`, ale klasa nie może dziedziczyć po klasie `B`.  
  
```csharp  
class A {}      
sealed class B : A {}  
```  
  
 Można również użyć `sealed` modyfikator metoda lub właściwość, która zastępuje metody wirtualnej lub w klasie podstawowej. Dzięki temu można zezwolić klas pochodzi od klasy i uniemożliwić przesłanianie określonej wirtualnej metody lub właściwości.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie `Z` dziedziczy `Y` , ale `Z` nie może przesłonić funkcji wirtualnej `F` zadeklarowanego w `X` i zapieczętowany w `Y`.  
  
 [!code-csharp[csrefKeywordsModifiers#16](../../../csharp/language-reference/keywords/codesnippet/CSharp/sealed_1.cs)]  
  
 Podczas definiowania nowej metody lub właściwości w klasie, można zapobiec klas pochodnych zastąpieniem przez nie deklarowanie je jako [wirtualnego](../../../csharp/language-reference/keywords/virtual.md).  
  
 Jest błędem [abstrakcyjny](../../../csharp/language-reference/keywords/abstract.md) modyfikator z klasy zapieczętowanej, ponieważ klasa abstrakcyjna muszą być dziedziczone przez klasy, która udostępnia implementację metody abstrakcyjne lub właściwości.  
  
 Po zastosowaniu do metody lub właściwości, `sealed` modyfikator zawsze musi być używany z [zastąpienia](../../../csharp/language-reference/keywords/override.md).  
  
 Ponieważ niejawnie są zapieczętowane struktury, nie może być dziedziczona.  
  
 Aby uzyskać więcej informacji, zobacz [dziedziczenia](../../../csharp/programming-guide/classes-and-structs/inheritance.md).  
  
 Aby uzyskać więcej przykładów, zobacz [abstrakcyjne i zapieczętowane klasy oraz członkowie klas](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csrefKeywordsModifiers#17](../../../csharp/language-reference/keywords/codesnippet/CSharp/sealed_2.cs)]  
  
 W poprzednim przykładzie możesz spróbować dziedziczona z klasy zapieczętowanej przy użyciu następujących instrukcji:  
  
 `class MyDerivedC: SealedClass {}   // Error`  
  
 Wynik jest komunikat o błędzie:  
  
 `'MyDerivedC' cannot inherit from sealed class 'SealedClass'.`  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="remarks"></a>Uwagi  
 Aby ustalić, czy zapieczętować klasy, metody lub właściwości, zazwyczaj należy rozważyć następujące dwa punkty:  
  
-   Potencjalnych korzyści, że wyprowadzanie klas może uzyskać za pośrednictwem możliwość dostosowania swojej klasy.  
  
-   Ryzyko, że wyprowadzanie klas może zmodyfikować klas w taki sposób, że będzie już działać poprawnie lub oczekiwano.  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)  
 [Klasy statyczne i statyczne elementy członkowskie klas](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)  
 [Klasy abstrakcyjne i zapieczętowane oraz elementy członkowskie klas](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)  
 [Modyfikatory dostępu](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)  
 [Modyfikatory](../../../csharp/language-reference/keywords/modifiers.md)  
 [override](../../../csharp/language-reference/keywords/override.md)  
 [virtual](../../../csharp/language-reference/keywords/virtual.md)
