---
title: 'Instrukcje: Kwerenda ArrayList za pomocą LINQ (C#)'
ms.date: 07/20/2015
ms.assetid: 2bfb471c-6e9a-4e60-bd83-4a1778abde11
ms.openlocfilehash: 51c42296b8acb6be1c9c4505f9af3d6fbaf248ce
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253452"
---
# <a name="how-to-query-an-arraylist-with-linq-c"></a>Instrukcje: Kwerenda ArrayList za pomocą LINQ (C#)
W przypadku korzystania z programu LINQ do wykonywania <xref:System.Collections.IEnumerable> zapytań dotyczących kolekcji <xref:System.Collections.ArrayList>innych niż ogólne, takich jak, należy jawnie zadeklarować typ zmiennej zakresu, aby odzwierciedlała określony typ obiektów w kolekcji. Na przykład jeśli masz <xref:System.Collections.ArrayList> `Student` obiekty, [klauzula FROM](../../../language-reference/keywords/from-clause.md) powinna wyglądać następująco:  
  
```csharp  
var query = from Student s in arrList  
//...
```  
  
 Określenie typu zmiennej zakresu powoduje rzutowanie każdego elementu w <xref:System.Collections.ArrayList>. `Student`  
  
 Użycie jawnie wpisanej zmiennej zakresu w wyrażeniu zapytania jest równoznaczne z wywołaniem <xref:System.Linq.Enumerable.Cast%2A> metody. <xref:System.Linq.Enumerable.Cast%2A>zgłasza wyjątek, jeśli nie można wykonać określonego rzutowania. <xref:System.Linq.Enumerable.Cast%2A>i <xref:System.Linq.Enumerable.OfType%2A> są dwoma standardowymi metodami operatorów zapytań, które działają na typach <xref:System.Collections.IEnumerable> innych niż ogólne. Aby uzyskać więcej informacji, zobacz temat [relacje typu w operacjach zapytań LINQ](./type-relationships-in-linq-query-operations.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano proste zapytanie w <xref:System.Collections.ArrayList>. Należy zauważyć, że w tym przykładzie są używane Inicjatory obiektów, <xref:System.Collections.ArrayList.Add%2A> gdy kod wywołuje metodę, ale nie jest to wymagane.  
  
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
