---
title: 'Instrukcje: Kwerenda ArrayList za pomocą LINQ (C#)'
ms.date: 07/20/2015
ms.assetid: 2bfb471c-6e9a-4e60-bd83-4a1778abde11
ms.openlocfilehash: dca201a23b316cc16bc746ea920303814c8c7c87
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69592922"
---
# <a name="how-to-query-an-arraylist-with-linq-c"></a><span data-ttu-id="4cc4d-102">Instrukcje: Kwerenda ArrayList za pomocą LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="4cc4d-102">How to: Query an ArrayList with LINQ (C#)</span></span>
<span data-ttu-id="4cc4d-103">W przypadku korzystania z programu LINQ do wykonywania <xref:System.Collections.IEnumerable> zapytań dotyczących kolekcji <xref:System.Collections.ArrayList>innych niż ogólne, takich jak, należy jawnie zadeklarować typ zmiennej zakresu, aby odzwierciedlała określony typ obiektów w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="4cc4d-103">When using LINQ to query non-generic <xref:System.Collections.IEnumerable> collections such as <xref:System.Collections.ArrayList>, you must explicitly declare the type of the range variable to reflect the specific type of the objects in the collection.</span></span> <span data-ttu-id="4cc4d-104">Na przykład jeśli masz <xref:System.Collections.ArrayList> `Student` obiekty, [klauzula FROM](../../../language-reference/keywords/from-clause.md) powinna wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="4cc4d-104">For example, if you have an <xref:System.Collections.ArrayList> of `Student` objects, your [from clause](../../../language-reference/keywords/from-clause.md) should look like this:</span></span>  
  
```  
var query = from Student s in arrList  
...  
```  
  
 <span data-ttu-id="4cc4d-105">Określenie typu zmiennej zakresu powoduje rzutowanie każdego elementu w <xref:System.Collections.ArrayList>. `Student`</span><span class="sxs-lookup"><span data-stu-id="4cc4d-105">By specifying the type of the range variable, you are casting each item in the <xref:System.Collections.ArrayList> to a `Student`.</span></span>  
  
 <span data-ttu-id="4cc4d-106">Użycie jawnie wpisanej zmiennej zakresu w wyrażeniu zapytania jest równoznaczne z wywołaniem <xref:System.Linq.Enumerable.Cast%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="4cc4d-106">The use of an explicitly typed range variable in a query expression is equivalent to calling the <xref:System.Linq.Enumerable.Cast%2A> method.</span></span> <span data-ttu-id="4cc4d-107"><xref:System.Linq.Enumerable.Cast%2A>zgłasza wyjątek, jeśli nie można wykonać określonego rzutowania.</span><span class="sxs-lookup"><span data-stu-id="4cc4d-107"><xref:System.Linq.Enumerable.Cast%2A> throws an exception if the specified cast cannot be performed.</span></span> <span data-ttu-id="4cc4d-108"><xref:System.Linq.Enumerable.Cast%2A>i <xref:System.Linq.Enumerable.OfType%2A> są dwoma standardowymi metodami operatorów zapytań, które działają na typach <xref:System.Collections.IEnumerable> innych niż ogólne.</span><span class="sxs-lookup"><span data-stu-id="4cc4d-108"><xref:System.Linq.Enumerable.Cast%2A> and <xref:System.Linq.Enumerable.OfType%2A> are the two Standard Query Operator methods that operate on non-generic <xref:System.Collections.IEnumerable> types.</span></span> <span data-ttu-id="4cc4d-109">Aby uzyskać więcej informacji, zobacz temat [relacje typu w operacjach zapytań LINQ](./type-relationships-in-linq-query-operations.md).</span><span class="sxs-lookup"><span data-stu-id="4cc4d-109">For more information, see [Type Relationships in LINQ Query Operations](./type-relationships-in-linq-query-operations.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4cc4d-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="4cc4d-110">Example</span></span>  
 <span data-ttu-id="4cc4d-111">W poniższym przykładzie pokazano proste zapytanie w <xref:System.Collections.ArrayList>.</span><span class="sxs-lookup"><span data-stu-id="4cc4d-111">The following example shows a simple query over an <xref:System.Collections.ArrayList>.</span></span> <span data-ttu-id="4cc4d-112">Należy zauważyć, że w tym przykładzie są używane Inicjatory obiektów, <xref:System.Collections.ArrayList.Add%2A> gdy kod wywołuje metodę, ale nie jest to wymagane.</span><span class="sxs-lookup"><span data-stu-id="4cc4d-112">Note that this example uses object initializers when the code calls the <xref:System.Collections.ArrayList.Add%2A> method, but this is not a requirement.</span></span>  
  
```csharp  
using System;  
using System.Collections;  
using System.Linq;  
  
namespace NonGenericLINQ  
{  
    public class Student  
    {  
        public string FirstName { get; set; }  
        public string LastName { get; set; }  
        public int[] Scores { get; set; }  
    }  
  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            ArrayList arrList = new ArrayList();  
            arrList.Add(  
                new Student  
                    {  
                        FirstName = "Svetlana", LastName = "Omelchenko", Scores = new int[] { 98, 92, 81, 60 }  
                    });  
            arrList.Add(  
                new Student  
                    {  
                        FirstName = "Claire", LastName = "O’Donnell", Scores = new int[] { 75, 84, 91, 39 }  
                    });  
            arrList.Add(  
                new Student  
                    {  
                        FirstName = "Sven", LastName = "Mortensen", Scores = new int[] { 88, 94, 65, 91 }  
                    });  
            arrList.Add(  
                new Student  
                    {  
                        FirstName = "Cesar", LastName = "Garcia", Scores = new int[] { 97, 89, 85, 82 }  
                    });  
  
            var query = from Student student in arrList  
                        where student.Scores[0] > 95  
                        select student;  
  
            foreach (Student s in query)  
                Console.WriteLine(s.LastName + ": " + s.Scores[0]);  
  
            // Keep the console window open in debug mode.  
            Console.WriteLine("Press any key to exit.");  
            Console.ReadKey();  
        }  
    }  
}  
/* Output:   
    Omelchenko: 98  
    Garcia: 97  
*/  
```  
  
## <a name="see-also"></a><span data-ttu-id="4cc4d-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4cc4d-113">See also</span></span>

- [<span data-ttu-id="4cc4d-114">LINQ to Objects (C#)</span><span class="sxs-lookup"><span data-stu-id="4cc4d-114">LINQ to Objects (C#)</span></span>](./linq-to-objects.md)
