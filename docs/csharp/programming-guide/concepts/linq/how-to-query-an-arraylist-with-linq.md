---
title: Jak zapytanie ArrayList z LINQ (C#)
ms.date: 07/20/2015
ms.assetid: 2bfb471c-6e9a-4e60-bd83-4a1778abde11
ms.openlocfilehash: fa185ba3793b628b0d65e1f513a70ec68f6f2425
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79168937"
---
# <a name="how-to-query-an-arraylist-with-linq-c"></a>Jak zapytanie ArrayList z LINQ (C#)
Korzystając z LINQ do <xref:System.Collections.IEnumerable> wykonywania <xref:System.Collections.ArrayList>zapytań nieogólnych kolekcji, takich jak , należy jawnie zadeklarować typ zmiennej zakresu, aby odzwierciedlić określony typ obiektów w kolekcji. Na przykład jeśli masz <xref:System.Collections.ArrayList> `Student` obiektów, from [klauzula](../../../language-reference/keywords/from-clause.md) powinna wyglądać tak:  
  
```csharp
var query = from Student s in arrList  
//...
```  
  
 Określając typ zmiennej zakresu, rzutujesz każdy element <xref:System.Collections.ArrayList> w `Student`pliku do .  
  
 Użycie jawnie wpisanej zmiennej zakresu w wyrażeniu zapytania jest równoważne wywołaniu <xref:System.Linq.Enumerable.Cast%2A> metody. <xref:System.Linq.Enumerable.Cast%2A>zgłasza wyjątek, jeśli nie można wykonać określonej rzutnie. <xref:System.Linq.Enumerable.Cast%2A>i <xref:System.Linq.Enumerable.OfType%2A> są dwie metody Standardowego operatora kwerendy, które działają na typy nierodzajowe. <xref:System.Collections.IEnumerable> Aby uzyskać więcej informacji, zobacz [Wpisywanie relacji w operacjach kwerend LINQ](./type-relationships-in-linq-query-operations.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono <xref:System.Collections.ArrayList>proste zapytanie za pomocą pliku . Należy zauważyć, że w tym przykładzie używa <xref:System.Collections.ArrayList.Add%2A> inicjatorów obiektów, gdy kod wywołuje metodę, ale nie jest to wymagane.  
  
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
  
## <a name="see-also"></a>Zobacz też

- [LINQ do obiektów (C#)](./linq-to-objects.md)
