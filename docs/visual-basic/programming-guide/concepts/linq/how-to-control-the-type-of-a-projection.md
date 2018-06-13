---
title: 'Porady: kontrolowanie typu projekcji (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: a0171276-0b46-4817-aee5-a8d5191b12fe
ms.openlocfilehash: efeb247c2b7662c71ec97ea1d8c1839361d82e14
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33640296"
---
# <a name="how-to-control-the-type-of-a-projection-visual-basic"></a>Porady: kontrolowanie typu projekcji (Visual Basic)
Projekcja to proces biorąc jeden zestaw danych, filtrowania jej zmiana jego kształtu i nawet zmianę jej typu. Wyrażenia zapytań większości wykonać projekcje. Wynikiem obliczania większość wyrażenia zapytań w tej sekcji <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement>, można jednak sterować typ projekcji, aby utworzyć kolekcje innych typów. W tym temacie pokazano, jak to zrobić.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie zdefiniowano nowy typ `Customer`. Wyrażenia zapytania następnie tworzy nowy `Customer` obiekty w `Select` klauzuli. Powoduje to, że typ tego wyrażenia zapytania <xref:System.Collections.Generic.IEnumerable%601> z `Customer`.  
  
 W tym przykładzie użyto następujących dokumentu XML: [przykładowego pliku XML: Klienci i zamówienia (LINQ do XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md).  
  
```vb  
Public Class Customer  
    Private customerIDValue As String  
    Public Property CustomerID() As String  
        Get  
            Return customerIDValue  
        End Get  
        Set(ByVal value As String)  
            customerIDValue = value  
        End Set  
    End Property  
  
    Private companyNameValue As String  
    Public Property CompanyName() As String  
        Get  
            Return companyNameValue  
        End Get  
        Set(ByVal value As String)  
            companyNameValue = value  
        End Set  
    End Property  
  
    Private contactNameValue As String  
    Public Property ContactName() As String  
        Get  
            Return contactNameValue  
        End Get  
        Set(ByVal value As String)  
            contactNameValue = value  
        End Set  
    End Property  
  
    Public Sub New(ByVal customerID As String, _  
                   ByVal companyName As String, _  
                   ByVal contactName As String)  
        CustomerIDValue = customerID  
        CompanyNameValue = companyName  
        ContactNameValue = contactName  
    End Sub  
  
    Public Overrides Function ToString() As String  
        Return String.Format("{0}:{1}:{2}", Me.CustomerID, Me.CompanyName, Me.ContactName)  
    End Function  
End Class  
  
Sub Main()  
    Dim custOrd As XElement = XElement.Load("CustomersOrders.xml")  
    Dim custList As IEnumerable(Of Customer) = _  
        From el In custOrd.<Customers>.<Customer> _  
        Select New Customer( _  
            el.@<CustomerID>, _  
            el.<CompanyName>.Value, _  
            el.<ContactName>.Value _  
        )  
    For Each cust In custList  
        Console.WriteLine(cust)  
    Next  
End Sub  
```  
  
 Ten kod generuje następujące dane wyjściowe:  
  
```  
GREAL:Great Lakes Food Market:Howard Snyder  
HUNGC:Hungry Coyote Import Store:Yoshi Latimer  
LAZYK:Lazy K Kountry Store:John Steel  
LETSS:Let's Stop N Shop:Jaime Yorres  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Linq.Enumerable.Select%2A>  
 [Projekcje i przekształcenia (LINQ do XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
