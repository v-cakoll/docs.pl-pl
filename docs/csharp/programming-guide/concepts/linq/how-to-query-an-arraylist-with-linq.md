---
title: 'Porady: zapytanie w ArrayList za pomocą LINQ (C#)'
ms.date: 07/20/2015
ms.assetid: 2bfb471c-6e9a-4e60-bd83-4a1778abde11
ms.openlocfilehash: 8aaf90843fa85cf20a92a40644f085769404aa85
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-query-an-arraylist-with-linq-c"></a><span data-ttu-id="08485-102">Porady: zapytanie w ArrayList za pomocą LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="08485-102">How to: Query an ArrayList with LINQ (C#)</span></span>
<span data-ttu-id="08485-103">W przypadku używania LINQ do zapytania nieogólnego <xref:System.Collections.IEnumerable> kolekcji, takie jak <xref:System.Collections.ArrayList>, musisz jawnie zadeklarować typu zmienną zakresu w celu odzwierciedlenia określonego typu obiektu w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="08485-103">When using LINQ to query non-generic <xref:System.Collections.IEnumerable> collections such as <xref:System.Collections.ArrayList>, you must explicitly declare the type of the range variable to reflect the specific type of the objects in the collection.</span></span> <span data-ttu-id="08485-104">Na przykład, jeśli masz <xref:System.Collections.ArrayList> z `Student` obiektów, z [klauzuli from](../../../../csharp/language-reference/keywords/from-clause.md) powinna wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="08485-104">For example, if you have an <xref:System.Collections.ArrayList> of `Student` objects, your [from clause](../../../../csharp/language-reference/keywords/from-clause.md) should look like this:</span></span>  
  
```  
var query = from Student s in arrList  
...  
```  
  
 <span data-ttu-id="08485-105">Określenie typu zmiennej zakresu, są rzutowanie każdego elementu w <xref:System.Collections.ArrayList> do `Student`.</span><span class="sxs-lookup"><span data-stu-id="08485-105">By specifying the type of the range variable, you are casting each item in the <xref:System.Collections.ArrayList> to a `Student`.</span></span>  
  
 <span data-ttu-id="08485-106">Użycie zmiennej zakresu jawnie typu w wyrażeniu zapytania jest odpowiednikiem wywołania <xref:System.Linq.Enumerable.Cast%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="08485-106">The use of an explicitly typed range variable in a query expression is equivalent to calling the <xref:System.Linq.Enumerable.Cast%2A> method.</span></span> <span data-ttu-id="08485-107"><xref:System.Linq.Enumerable.Cast%2A> zgłasza wyjątek, jeśli nie można wykonać określone rzutowanie.</span><span class="sxs-lookup"><span data-stu-id="08485-107"><xref:System.Linq.Enumerable.Cast%2A> throws an exception if the specified cast cannot be performed.</span></span> <span data-ttu-id="08485-108"><xref:System.Linq.Enumerable.Cast%2A> i <xref:System.Linq.Enumerable.OfType%2A> są dwie metody standardowe — Operator zapytań, które pracują na inny niż ogólny <xref:System.Collections.IEnumerable> typów.</span><span class="sxs-lookup"><span data-stu-id="08485-108"><xref:System.Linq.Enumerable.Cast%2A> and <xref:System.Linq.Enumerable.OfType%2A> are the two Standard Query Operator methods that operate on non-generic <xref:System.Collections.IEnumerable> types.</span></span> <span data-ttu-id="08485-109">Aby uzyskać więcej informacji, zobacz [relacje typu w operacjach zapytań LINQ](../../../../csharp/programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).</span><span class="sxs-lookup"><span data-stu-id="08485-109">For more information, see [Type Relationships in LINQ Query Operations](../../../../csharp/programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="08485-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="08485-110">Example</span></span>  
 <span data-ttu-id="08485-111">W poniższym przykładzie przedstawiono prostego zapytania za pośrednictwem <xref:System.Collections.ArrayList>.</span><span class="sxs-lookup"><span data-stu-id="08485-111">The following example shows a simple query over an <xref:System.Collections.ArrayList>.</span></span> <span data-ttu-id="08485-112">Należy pamiętać, że w tym przykładzie użyto inicjatory obiektów, gdy kod wywołuje <xref:System.Collections.ArrayList.Add%2A> metody, ale nie jest wymagane.</span><span class="sxs-lookup"><span data-stu-id="08485-112">Note that this example uses object initializers when the code calls the <xref:System.Collections.ArrayList.Add%2A> method, but this is not a requirement.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="08485-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="08485-113">See Also</span></span>  
 [<span data-ttu-id="08485-114">LINQ do obiektów (C#)</span><span class="sxs-lookup"><span data-stu-id="08485-114">LINQ to Objects (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)
