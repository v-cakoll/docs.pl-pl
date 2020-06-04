---
title: 'Instrukcje: kontrolowanie typu projekcji'
ms.date: 07/20/2015
ms.assetid: a0171276-0b46-4817-aee5-a8d5191b12fe
ms.openlocfilehash: 6b809188f68805afcca960bd809e079d997e79c9
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84357260"
---
# <a name="how-to-control-the-type-of-a-projection-visual-basic"></a>Instrukcje: kontrolowanie typu projekcji (Visual Basic)
Projekcja to proces przejmowania jednego zestawu danych, filtrowanie go, zmiana jego kształtu, a nawet zmiana jego typu. Większość wyrażeń zapytania wykonuje projekcje. Większość wyrażeń zapytania przedstawionych w tej sekcji szacuje się <xref:System.Collections.Generic.IEnumerable%601> na <xref:System.Xml.Linq.XElement> , ale można kontrolować typ projekcji, aby tworzyć Kolekcje innych typów. W tym temacie pokazano, jak to zrobić.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie zdefiniowano nowy typ, `Customer` . Wyrażenie zapytania następnie tworzy wystąpienie nowych `Customer` obiektów w `Select` klauzuli. Powoduje to, że typ wyrażenia zapytania ma być <xref:System.Collections.Generic.IEnumerable%601> `Customer` .  
  
 W tym przykładzie zastosowano następujący dokument XML: [przykładowy plik XML: Customers i Orders (LINQ to XML)](sample-xml-file-customers-and-orders-linq-to-xml.md).  
  
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
  
```console  
GREAL:Great Lakes Food Market:Howard Snyder  
HUNGC:Hungry Coyote Import Store:Yoshi Latimer  
LAZYK:Lazy K Kountry Store:John Steel  
LETSS:Let's Stop N Shop:Jaime Yorres  
```  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Linq.Enumerable.Select%2A>
- [Projekcje i przekształcenia (LINQ to XML) (Visual Basic)](projections-and-transformations-linq-to-xml.md)
