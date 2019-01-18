---
title: 'Instrukcje: Wykonywanie Incjalizacji obiektów'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- lazy initialization in .NET, how to perform
ms.assetid: 8cd68620-dcc3-4f20-8835-c728a6820e71
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f3bcdbfacf02d84848934e21d58ed6fff7d37d52
ms.sourcegitcommit: 542aa405b295955eb055765f33723cb8b588d0d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2019
ms.locfileid: "54362889"
---
# <a name="how-to-perform-lazy-initialization-of-objects"></a>Instrukcje: Wykonywanie Incjalizacji obiektów
<xref:System.Lazy%601?displayProperty=nameWithType> Klasa upraszcza pracę wykonywanie incjalizacji i wystąpienia obiektów. Inicjowanie obiektów w sposób z opóźnieniem, można uniknąć konieczności tworzenia ich w ogóle, jeśli nigdy nie są one potrzebne lub można odroczyć ich inicjowania, aż najpierw są one używane. Aby uzyskać więcej informacji, zobacz [inicjowania z opóźnieniem](../../../docs/framework/performance/lazy-initialization.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak zainicjować wartość składającą się z <xref:System.Lazy%601>. Przyjęto założenie, że zmienna z opóźnieniem nie konieczne może być w zależności od innego kodu, który ustawia `someCondition` zmiennej na wartość true lub false.  
  
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
 Poniższy przykład pokazuje, jak używać <xref:System.Threading.ThreadLocal%601?displayProperty=nameWithType> klasy, aby zainicjować typu, która jest widoczna tylko dla bieżącego wystąpienia obiektu dla bieżącego wątku.  
  
 [!code-csharp[CDS#13](../../../samples/snippets/csharp/VS_Snippets_Misc/cds/cs/cds2.cs#13)]
 [!code-vb[CDS#13](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds/vb/lazyhowto.vb#13)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Threading.LazyInitializer?displayProperty=nameWithType>  
 [Inicjowanie z opóźnieniem](../../../docs/framework/performance/lazy-initialization.md)
