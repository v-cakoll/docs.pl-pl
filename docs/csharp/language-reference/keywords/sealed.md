---
title: sealed (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- sealed
- sealed_CSharpKeyword
helpviewer_keywords:
- sealed keyword [C#]
ms.assetid: 8e4ed5d3-10be-47db-9488-0da2008e6f3f
ms.openlocfilehash: 674c7e1cd87b95318f739ab22876f4bfe5ae73d8
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43514032"
---
# <a name="sealed-c-reference"></a>sealed (odwołanie w C#)
Po zastosowaniu do klasy, `sealed` modyfikator uniemożliwia innych klas z niego dziedziczącego. W poniższym przykładzie klasa `B` dziedziczy z klasy `A`, ale klasa nie może dziedziczyć z klasy `B`.  
  
```csharp  
class A {}      
sealed class B : A {}  
```  
  
 Można również użyć `sealed` modyfikator metoda lub właściwość, która zastępuje metodę wirtualną lub właściwości w klasie bazowej. Dzięki temu można umożliwić klasy pochodzi od klasy i uniemożliwić zastępowanie konkretnych metod wirtualnych lub właściwości.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie `Z` dziedziczy `Y` , ale `Z` nie może przesłonić funkcji wirtualnej `F` zadeklarowanego w `X` i zamkniętych w `Y`.  
  
 [!code-csharp[csrefKeywordsModifiers#16](../../../csharp/language-reference/keywords/codesnippet/CSharp/sealed_1.cs)]  
  
 Definiując nowe metody lub właściwości w klasie, można zapobiec klas pochodnych zastępowania ich nie deklarując je jako [wirtualnego](../../../csharp/language-reference/keywords/virtual.md).  
  
 Jest to błąd, aby użyć [abstrakcyjne](../../../csharp/language-reference/keywords/abstract.md) modyfikator za pomocą klasy zapieczętowanej ponieważ klasy abstrakcyjnej muszą być dziedziczone przez klasę, która dostarcza implementację metody abstrakcyjne lub właściwości.  
  
 Po zastosowaniu do metody lub właściwości, `sealed` modyfikator zawsze musi być używany z [zastąpienia](../../../csharp/language-reference/keywords/override.md).  
  
 Ponieważ struktury niejawnie są zamknięte, nie może być dziedziczona.  
  
 Aby uzyskać więcej informacji, zobacz [dziedziczenia](../../../csharp/programming-guide/classes-and-structs/inheritance.md).  
  
 Aby uzyskać więcej przykładów, zobacz [abstrakcyjnych i zapieczętowanych klas i składowych klasy](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csrefKeywordsModifiers#17](../../../csharp/language-reference/keywords/codesnippet/CSharp/sealed_2.cs)]  
  
 W poprzednim przykładzie możesz spróbować dziedziczą z klasy zapieczętowanej przy użyciu następujących instrukcji:  
  
 `class MyDerivedC: SealedClass {}   // Error`  
  
 Wynik jest komunikat o błędzie:  
  
 `'MyDerivedC': cannot derive from sealed type 'SealedClass'`  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="remarks"></a>Uwagi  
 Aby ustalić, czy ma być Zapieczętuj klasę, metodę lub właściwość, zazwyczaj należy rozważyć następujące dwa punkty:  
  
-   Potencjalnych korzyści, że wyprowadzanie klas mogą uzyskać za pośrednictwem możliwość dostosowania swojej klasy.  
  
-   Ryzyko, że wyprowadzanie klas można zmodyfikować klas w taki sposób, że będzie już działać poprawnie lub oczekuje.  
  
## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../../../csharp/language-reference/index.md)  
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)  
- [Klasy statyczne i statyczne elementy członkowskie klas](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)  
- [Klasy abstrakcyjne i zapieczętowane oraz elementy członkowskie klas](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)  
- [Modyfikatory dostępu](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)  
- [Modyfikatory](../../../csharp/language-reference/keywords/modifiers.md)  
- [override](../../../csharp/language-reference/keywords/override.md)  
- [virtual](../../../csharp/language-reference/keywords/virtual.md)
