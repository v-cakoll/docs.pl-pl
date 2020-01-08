---
title: Jak zbadać ArrayList za pomocą LINQ (C#)
ms.date: 07/20/2015
ms.assetid: 2bfb471c-6e9a-4e60-bd83-4a1778abde11
ms.openlocfilehash: b8edb90d33c92324d4f76c7e6977641fe4499d9d
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345706"
---
# <a name="how-to-query-an-arraylist-with-linq-c"></a>Jak zbadać ArrayList za pomocą LINQ (C#)
W przypadku używania LINQ do wykonywania zapytań dotyczących nieogólnych kolekcji <xref:System.Collections.IEnumerable>, takich jak <xref:System.Collections.ArrayList>, należy jawnie zadeklarować typ zmiennej zakresu w celu odzwierciedlenia określonego typu obiektów w kolekcji. Na przykład jeśli masz <xref:System.Collections.ArrayList> obiektów `Student`, [klauzula FROM](../../../language-reference/keywords/from-clause.md) powinna wyglądać następująco:  
  
```csharp
var query = from Student s in arrList  
//...
```  
  
 Określając typ zmiennej zakresu, rzutuje każdy element w <xref:System.Collections.ArrayList> na `Student`.  
  
 Użycie jawnie wpisanej zmiennej zakresu w wyrażeniu zapytania jest równoważne wywołaniu metody <xref:System.Linq.Enumerable.Cast%2A>. <xref:System.Linq.Enumerable.Cast%2A> zgłasza wyjątek, jeśli nie można wykonać określonego rzutowania. <xref:System.Linq.Enumerable.Cast%2A> i <xref:System.Linq.Enumerable.OfType%2A> to dwie metody standardowego operatora zapytań, które działają na nieogólnych typach <xref:System.Collections.IEnumerable>. Aby uzyskać więcej informacji, zobacz temat [relacje typu w operacjach zapytań LINQ](./type-relationships-in-linq-query-operations.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano proste zapytanie dotyczące <xref:System.Collections.ArrayList>. Należy zauważyć, że w tym przykładzie są używane Inicjatory obiektów, gdy kod wywołuje metodę <xref:System.Collections.ArrayList.Add%2A>, ale nie jest to wymagane.  
  
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
  
## <a name="see-also"></a>Zobacz także

- [LINQ to Objects (C#)](./linq-to-objects.md)
