---
title: "Porady: uzyskiwanie dostępu do klasy kolekcji za pomocą instrukcji foreach (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- collection classes [C#], foreach statement
ms.assetid: a6b9cf5c-6c8d-4223-b12c-288949434493
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 0cf827e958d4dc3b951d17b53effd155356c0ca5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-access-a-collection-class-with-foreach-c-programming-guide"></a>Porady: uzyskiwanie dostępu do klasy kolekcji za pomocą instrukcji foreach (Przewodnik programowania w języku C#)
Poniższy przykładowy kod przedstawia sposób zapisania kolekcja nierodzajową klasę, która może być używany z [foreach](../../../csharp/language-reference/keywords/foreach-in.md). W przykładzie zdefiniowano klasę tokenizatora ciągu.  
  
> [!NOTE]
>  W tym przykładzie reprezentuje zalecaną praktyką tylko wtedy, gdy nie można użyć klasy rodzajowej kolekcji. Na przykład implementowania bezpiecznej kolekcji ogólnej klasy, która obsługuje <xref:System.Collections.Generic.IEnumerable%601>, zobacz [Iteratory](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7).  
  
 W tym przykładzie poniższy kod używa segmentu `Tokens` klasę, aby przerwać zdania "Jest przykładowe zdania". w tokenach przy użyciu "" i "-" jako separatora. Następnie kod wyświetla te tokeny przy użyciu `foreach` instrukcji.  
  
 [!code-csharp[csProgGuideCollections#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-access-a-collection-class-with-foreach_1.cs)]  
  
## <a name="example"></a>Przykład  
 Wewnętrznie `Tokens` klasy używa tablicy do przechowywania tokenów. Ponieważ implementuje tablice <xref:System.Collections.IEnumerator> i <xref:System.Collections.IEnumerable>, przykładów kodu można użyć metody wyliczania tablicy (<xref:System.Collections.IEnumerable.GetEnumerator%2A>, <xref:System.Collections.IEnumerator.MoveNext%2A>, <xref:System.Collections.IEnumerator.Reset%2A>, i <xref:System.Collections.IEnumerator.Current%2A>) zamiast definiując je w `Tokens` klasy. Definicjami metod znajdują się w tym przykładzie wyjaśnienie, jak są definiowane i co działają.  
  
 [!code-csharp[csProgGuideCollections#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-access-a-collection-class-with-foreach_2.cs)]  
  
 W języku C# nie jest niezbędna dla klasy kolekcji <xref:System.Collections.IEnumerable> i <xref:System.Collections.IEnumerator> aby był zgodny z `foreach`. Jeśli klasa ma wymagany <xref:System.Collections.IEnumerable.GetEnumerator%2A>, <xref:System.Collections.IEnumerator.MoveNext%2A>, <xref:System.Collections.IEnumerator.Reset%2A>, i <xref:System.Collections.IEnumerator.Current%2A> elementów członkowskich, będzie działać z `foreach`. Pominięcie interfejsy zaletą dzięki któremu można określić typ zwracany dla `Current` jest określony więcej niż <xref:System.Object>. Zapewnia to bezpieczeństwo typów.  
  
 Na przykład Zmień następujące wiersze w poprzednim przykładzie.  
  
```csharp  
// Change the Tokens class so that it no longer implements IEnumerable.  
public class Tokens  
{  
    // . . .  
  
    // Change the return type for the GetEnumerator method.  
    public TokenEnumerator GetEnumerator()  
    {   }  
  
    // Change TokenEnumerator so that it no longer implements IEnumerator.  
    public class TokenEnumerator  
    {  
        // . . .  
  
        // Change the return type of method Current to string.  
        public string Current  
        {   }  
    }  
 }  
```  
  
 Ponieważ `Current` zwraca wartość typu ciąg, kompilator może wykryć stosowania niezgodny typ `foreach` instrukcji, jak pokazano w poniższym kodzie.  
  
```csharp  
// Error: Cannot convert type string to int.  
foreach (int item in f)    
```  
  
 Wadą pominięcie <xref:System.Collections.IEnumerable> i <xref:System.Collections.IEnumerator> jest, że klasa kolekcji nie jest już współdziałać z `foreach` instrukcji lub równoważne instrukcje języków środowiska uruchomieniowego języka wspólnego.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Collections.Generic>  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Tablice](../../../csharp/programming-guide/arrays/index.md)  
 [Kolekcje](http://msdn.microsoft.com/library/e76533a9-5033-4a0b-b003-9c2be60d185b)
