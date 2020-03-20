---
title: 'Porady: wykonywanie incjalizacji obiektów z opóźnieniem'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- lazy initialization in .NET, how to perform
ms.assetid: 8cd68620-dcc3-4f20-8835-c728a6820e71
ms.openlocfilehash: d89d19a7a3edb57dcd6c0e37e6688701da8b3713
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180598"
---
# <a name="how-to-perform-lazy-initialization-of-objects"></a>Porady: wykonywanie incjalizacji obiektów z opóźnieniem
Klasa <xref:System.Lazy%601?displayProperty=nameWithType> upraszcza pracę wykonywania z opóźnieniem inicjowania i tworzenia wystąpienia obiektów. Inicjując obiekty w sposób leniwy, można uniknąć konieczności tworzenia ich w ogóle, jeśli nigdy nie są potrzebne lub można odroczyć ich inicjalizacji, dopóki nie są one po raz pierwszy dostępne. Aby uzyskać więcej informacji, zobacz [Inicjowanie z opóźnieniem](lazy-initialization.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano, <xref:System.Lazy%601>jak zainicjować wartość za pomocą pliku . Załóżmy, że zmienna z opóźnieniem może nie `someCondition` być potrzebne, w zależności od innego kodu, który ustawia zmienną na true lub false.  
  
```vb  
Dim someCondition As Boolean = False  
  
Sub Main()  
    'Initializing a value with a big computation, computed in parallel  
    Dim _data As Lazy(Of Integer) = New Lazy(Of Integer)(Function()  
                                                             Dim result =  
                                                                 ParallelEnumerable.Range(0, 1000).  
                                                                 Aggregate(Function(x, y)  
                                                                               Return x + y  
                                                                           End Function)  
                                                             Return result  
                                                         End Function)  
  
    '  do work that may or may not set someCondition to True  
    ' ...  
    '  Initialize the data only if needed  
    If someCondition = True Then  
  
        If (_data.Value > 100) Then  
  
            Console.WriteLine("Good data")  
        End If  
    End If  
End Sub  
```  
  
```csharp  
  static bool someCondition = false;
  //Initializing a value with a big computation, computed in parallel  
  Lazy<int> _data = new Lazy<int>(delegate  
  {  
      return ParallelEnumerable.Range(0, 1000).  
          Select(i => Compute(i)).Aggregate((x,y) => x + y);  
  }, LazyExecutionMode.EnsureSingleThreadSafeExecution);  
  
  // Do some work that may or may not set someCondition to true.  
  //  ...  
  // Initialize the data only if necessary  
  if (someCondition)  
  {  
    if (_data.Value > 100)  
      {  
          Console.WriteLine("Good data");  
      }  
  }  
```  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie <xref:System.Threading.ThreadLocal%601?displayProperty=nameWithType> pokazano, jak za pomocą klasy zainicjować typ, który jest widoczny tylko dla bieżącego wystąpienia obiektu w bieżącym wątku.  
  
 [!code-csharp[CDS#13](../../../samples/snippets/csharp/VS_Snippets_Misc/cds/cs/cds2.cs#13)]
 [!code-vb[CDS#13](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds/vb/lazyhowto.vb#13)]  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Threading.LazyInitializer?displayProperty=nameWithType>
- [Inicjalizacja z opóźnieniem](lazy-initialization.md)
