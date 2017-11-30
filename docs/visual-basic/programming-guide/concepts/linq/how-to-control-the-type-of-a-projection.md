---
title: 'Porady: kontrolowanie typu projekcji (Visual Basic)'
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a0171276-0b46-4817-aee5-a8d5191b12fe
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 32c2c747fd2f1137fbf2ead28886669c041d065c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
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
