---
title: 'Instrukcje: zapytanie do ArrayList za pomocą LINQ (C#)'
ms.date: 07/20/2015
ms.assetid: 2bfb471c-6e9a-4e60-bd83-4a1778abde11
ms.openlocfilehash: c22cd6ef22b5ca182266c1e8db10151e07567fc6
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73969823"
---
# <a name="how-to-query-an-arraylist-with-linq-c"></a><span data-ttu-id="ff9f6-102">Instrukcje: zapytanie do ArrayList za pomocą LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="ff9f6-102">How to: Query an ArrayList with LINQ (C#)</span></span>
<span data-ttu-id="ff9f6-103">Używając LINQ do wykonywania zapytań dotyczących nieogólnych kolekcji <xref:System.Collections.IEnumerable>, takich jak <xref:System.Collections.ArrayList>, należy jawnie zadeklarować typ zmiennej zakresu w celu odzwierciedlenia określonego typu obiektów w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="ff9f6-103">When using LINQ to query non-generic <xref:System.Collections.IEnumerable> collections such as <xref:System.Collections.ArrayList>, you must explicitly declare the type of the range variable to reflect the specific type of the objects in the collection.</span></span> <span data-ttu-id="ff9f6-104">Na przykład jeśli masz <xref:System.Collections.ArrayList> obiektów `Student`, [klauzula FROM](../../../language-reference/keywords/from-clause.md) powinna wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="ff9f6-104">For example, if you have an <xref:System.Collections.ArrayList> of `Student` objects, your [from clause](../../../language-reference/keywords/from-clause.md) should look like this:</span></span>  
  
```csharp
var query = from Student s in arrList  
//...
```  
  
 <span data-ttu-id="ff9f6-105">Określając typ zmiennej zakresu, rzutuje każdy element w <xref:System.Collections.ArrayList> do `Student`.</span><span class="sxs-lookup"><span data-stu-id="ff9f6-105">By specifying the type of the range variable, you are casting each item in the <xref:System.Collections.ArrayList> to a `Student`.</span></span>  
  
 <span data-ttu-id="ff9f6-106">Użycie jawnie wpisanej zmiennej zakresu w wyrażeniu zapytania jest równoważne wywołaniu metody <xref:System.Linq.Enumerable.Cast%2A>.</span><span class="sxs-lookup"><span data-stu-id="ff9f6-106">The use of an explicitly typed range variable in a query expression is equivalent to calling the <xref:System.Linq.Enumerable.Cast%2A> method.</span></span> <span data-ttu-id="ff9f6-107"><xref:System.Linq.Enumerable.Cast%2A> zgłasza wyjątek, jeśli nie można wykonać określonego rzutowania.</span><span class="sxs-lookup"><span data-stu-id="ff9f6-107"><xref:System.Linq.Enumerable.Cast%2A> throws an exception if the specified cast cannot be performed.</span></span> <span data-ttu-id="ff9f6-108"><xref:System.Linq.Enumerable.Cast%2A> i <xref:System.Linq.Enumerable.OfType%2A> to dwie metody standardowego operatora zapytań, które działają na nieogólnych typach <xref:System.Collections.IEnumerable>.</span><span class="sxs-lookup"><span data-stu-id="ff9f6-108"><xref:System.Linq.Enumerable.Cast%2A> and <xref:System.Linq.Enumerable.OfType%2A> are the two Standard Query Operator methods that operate on non-generic <xref:System.Collections.IEnumerable> types.</span></span> <span data-ttu-id="ff9f6-109">Aby uzyskać więcej informacji, zobacz temat [relacje typu w operacjach zapytań LINQ](./type-relationships-in-linq-query-operations.md).</span><span class="sxs-lookup"><span data-stu-id="ff9f6-109">For more information, see [Type Relationships in LINQ Query Operations](./type-relationships-in-linq-query-operations.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ff9f6-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="ff9f6-110">Example</span></span>  
 <span data-ttu-id="ff9f6-111">W poniższym przykładzie pokazano proste zapytanie dla <xref:System.Collections.ArrayList>.</span><span class="sxs-lookup"><span data-stu-id="ff9f6-111">The following example shows a simple query over an <xref:System.Collections.ArrayList>.</span></span> <span data-ttu-id="ff9f6-112">Należy zauważyć, że w tym przykładzie są używane Inicjatory obiektów, gdy kod wywołuje metodę <xref:System.Collections.ArrayList.Add%2A>, ale nie jest to wymagane.</span><span class="sxs-lookup"><span data-stu-id="ff9f6-112">Note that this example uses object initializers when the code calls the <xref:System.Collections.ArrayList.Add%2A> method, but this is not a requirement.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ff9f6-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ff9f6-113">See also</span></span>

- [<span data-ttu-id="ff9f6-114">LINQ to Objects (C#)</span><span class="sxs-lookup"><span data-stu-id="ff9f6-114">LINQ to Objects (C#)</span></span>](./linq-to-objects.md)
