---
title: 'Instrukcje: wykonywanie inicjalizacji obiektów z opóźnieniem'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- lazy initialization in .NET, how to perform
ms.assetid: 8cd68620-dcc3-4f20-8835-c728a6820e71
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6fba47c0ff6425a375715dcd4c08d62e0f7f598c
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71046477"
---
# <a name="how-to-perform-lazy-initialization-of-objects"></a>Instrukcje: wykonywanie inicjalizacji obiektów z opóźnieniem
<xref:System.Lazy%601?displayProperty=nameWithType> Klasa upraszcza pracę wykonywaną podczas inicjowania z opóźnieniem i tworzenie wystąpienia obiektów. Inicjując obiekty w sposób opóźniony, można uniknąć konieczności ich tworzenia w ogóle, jeśli nigdy nie są potrzebne, lub można odroczyć ich inicjalizację do momentu pierwszego dostępu do nich. Aby uzyskać więcej informacji, zobacz [Inicjalizacja z opóźnieniem](lazy-initialization.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak zainicjować wartość za pomocą <xref:System.Lazy%601>. Załóżmy, że zmienna opóźniona może nie być wymagana, w zależności od innego kodu, który ustawia `someCondition` zmienną na wartość true lub false.  
  
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
 Poniższy przykład pokazuje, <xref:System.Threading.ThreadLocal%601?displayProperty=nameWithType> jak używać klasy do inicjowania typu, który jest widoczny tylko dla bieżącego wystąpienia obiektu w bieżącym wątku.  
  
 [!code-csharp[CDS#13](../../../samples/snippets/csharp/VS_Snippets_Misc/cds/cs/cds2.cs#13)]
 [!code-vb[CDS#13](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds/vb/lazyhowto.vb#13)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Threading.LazyInitializer?displayProperty=nameWithType>
- [Inicjowanie z opóźnieniem](lazy-initialization.md)
