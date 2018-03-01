---
title: "Porady: wykonywanie incjalizacji obiektów z opóźnieniem"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- lazy initialization in .NET, how to perform
ms.assetid: 8cd68620-dcc3-4f20-8835-c728a6820e71
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1728165dbed9a011afe6e621df86be7b372a684f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-perform-lazy-initialization-of-objects"></a>Porady: wykonywanie incjalizacji obiektów z opóźnieniem
<xref:System.Lazy%601?displayProperty=nameWithType> Klasa upraszcza pracy wykonania inicjowania z opóźnieniem i tworzenie wystąpień obiektów. Inicjowanie obiektów w sposób opóźnieniem, można uniknąć konieczności tworzenia ich w ogóle, jeśli nigdy nie są one potrzebne lub można odroczyć inicjalizacji, aż najpierw uzyskiwania do nich. Aby uzyskać więcej informacji, zobacz [Incjalizacji](../../../docs/framework/performance/lazy-initialization.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak zainicjować wartości z <xref:System.Lazy%601>. Załóżmy, że opóźnieniem zmiennej może nie być potrzebne, w zależności od innego kodu, która ustawia `someCondition` zmiennej wartość PRAWDA lub FAŁSZ.  
  
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
 Poniższy przykład przedstawia użycie <xref:System.Threading.ThreadLocal%601?displayProperty=nameWithType> klasy można zainicjować typu, który jest widoczny tylko dla bieżącego wystąpienia obiektu w bieżącym wątku.  
  
 [!code-csharp[CDS#13](../../../samples/snippets/csharp/VS_Snippets_Misc/cds/cs/cds2.cs#13)]
 [!code-vb[CDS#13](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds/vb/lazyhowto.vb#13)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Threading.LazyInitializer?displayProperty=nameWithType>  
 [Inicjowanie z opóźnieniem](../../../docs/framework/performance/lazy-initialization.md)
