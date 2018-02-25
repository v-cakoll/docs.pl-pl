---
title: "Porady: zapytanie w ArrayList za pomocą LINQ (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
ms.assetid: 2bfb471c-6e9a-4e60-bd83-4a1778abde11
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 2f32fcca4504ce3d3f297cfc1b81529dd027f9a6
ms.sourcegitcommit: 75a180acb5d8a2dbd4a52915ce8e980749fb1d05
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/24/2018
---
# <a name="how-to-query-an-arraylist-with-linq-c"></a>Porady: zapytanie w ArrayList za pomocą LINQ (C#)
W przypadku używania LINQ do zapytania nieogólnego <xref:System.Collections.IEnumerable> kolekcji, takie jak <xref:System.Collections.ArrayList>, musisz jawnie zadeklarować typu zmienną zakresu w celu odzwierciedlenia określonego typu obiektu w kolekcji. Na przykład, jeśli masz <xref:System.Collections.ArrayList> z `Student` obiektów, z [klauzuli from](../../../../csharp/language-reference/keywords/from-clause.md) powinna wyglądać następująco:  
  
```  
var query = from Student s in arrList  
...  
```  
  
 Określenie typu zmiennej zakresu, są rzutowanie każdego elementu w <xref:System.Collections.ArrayList> do `Student`.  
  
 Użycie zmiennej zakresu jawnie typu w wyrażeniu zapytania jest odpowiednikiem wywołania <xref:System.Linq.Enumerable.Cast%2A> metody. <xref:System.Linq.Enumerable.Cast%2A> zgłasza wyjątek, jeśli nie można wykonać określone rzutowanie. <xref:System.Linq.Enumerable.Cast%2A> i <xref:System.Linq.Enumerable.OfType%2A> są dwie metody standardowe — Operator zapytań, które pracują na inny niż ogólny <xref:System.Collections.IEnumerable> typów. Aby uzyskać więcej informacji, zobacz [relacje typu w operacjach zapytań LINQ](../../../../csharp/programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono prostego zapytania za pośrednictwem <xref:System.Collections.ArrayList>. Należy pamiętać, że w tym przykładzie użyto inicjatory obiektów, gdy kod wywołuje <xref:System.Collections.ArrayList.Add%2A> metody, ale nie jest wymagane.  
  
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
 [LINQ do obiektów (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)
