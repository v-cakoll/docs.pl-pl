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
ms.openlocfilehash: 28463bfd3e54e49461d9ce785d26e5dfca62e438
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61722994"
---
# <a name="how-to-perform-lazy-initialization-of-objects"></a><span data-ttu-id="f7d6b-102">Instrukcje: wykonywanie inicjalizacji obiektów z opóźnieniem</span><span class="sxs-lookup"><span data-stu-id="f7d6b-102">How to: Perform Lazy Initialization of Objects</span></span>
<span data-ttu-id="f7d6b-103"><xref:System.Lazy%601?displayProperty=nameWithType> Klasa upraszcza pracę wykonywanie incjalizacji i wystąpienia obiektów.</span><span class="sxs-lookup"><span data-stu-id="f7d6b-103">The <xref:System.Lazy%601?displayProperty=nameWithType> class simplifies the work of performing lazy initialization and instantiation of objects.</span></span> <span data-ttu-id="f7d6b-104">Inicjowanie obiektów w sposób z opóźnieniem, można uniknąć konieczności tworzenia ich w ogóle, jeśli nigdy nie są one potrzebne lub można odroczyć ich inicjowania, aż najpierw są one używane.</span><span class="sxs-lookup"><span data-stu-id="f7d6b-104">By initializing objects in a lazy manner, you can avoid having to create them at all if they are never needed, or you can postpone their initialization until they are first accessed.</span></span> <span data-ttu-id="f7d6b-105">Aby uzyskać więcej informacji, zobacz [inicjowania z opóźnieniem](../../../docs/framework/performance/lazy-initialization.md).</span><span class="sxs-lookup"><span data-stu-id="f7d6b-105">For more information, see [Lazy Initialization](../../../docs/framework/performance/lazy-initialization.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f7d6b-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="f7d6b-106">Example</span></span>  
 <span data-ttu-id="f7d6b-107">Poniższy przykład pokazuje, jak zainicjować wartość składającą się z <xref:System.Lazy%601>.</span><span class="sxs-lookup"><span data-stu-id="f7d6b-107">The following example shows how to initialize a value with <xref:System.Lazy%601>.</span></span> <span data-ttu-id="f7d6b-108">Przyjęto założenie, że zmienna z opóźnieniem nie konieczne może być w zależności od innego kodu, który ustawia `someCondition` zmiennej na wartość true lub false.</span><span class="sxs-lookup"><span data-stu-id="f7d6b-108">Assume that the lazy variable might not be needed, depending on some other code that sets the `someCondition` variable to true or false.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="f7d6b-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="f7d6b-109">Example</span></span>  
 <span data-ttu-id="f7d6b-110">Poniższy przykład pokazuje, jak używać <xref:System.Threading.ThreadLocal%601?displayProperty=nameWithType> klasy, aby zainicjować typu, która jest widoczna tylko dla bieżącego wystąpienia obiektu dla bieżącego wątku.</span><span class="sxs-lookup"><span data-stu-id="f7d6b-110">The following example shows how to use the <xref:System.Threading.ThreadLocal%601?displayProperty=nameWithType> class to initialize a type that is visible only to the current object instance on the current thread.</span></span>  
  
 [!code-csharp[CDS#13](../../../samples/snippets/csharp/VS_Snippets_Misc/cds/cs/cds2.cs#13)]
 [!code-vb[CDS#13](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds/vb/lazyhowto.vb#13)]  
  
## <a name="see-also"></a><span data-ttu-id="f7d6b-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f7d6b-111">See also</span></span>

- <xref:System.Threading.LazyInitializer?displayProperty=nameWithType>
- [<span data-ttu-id="f7d6b-112">Inicjowanie z opóźnieniem</span><span class="sxs-lookup"><span data-stu-id="f7d6b-112">Lazy Initialization</span></span>](../../../docs/framework/performance/lazy-initialization.md)
