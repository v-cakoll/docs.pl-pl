---
title: 'Przykładowy plik XML: Dane liczbowe w {1 & gt'
ms.date: 07/20/2015
ms.assetid: f01cc0a1-fb55-4b42-8380-16f4be47d6f4
ms.openlocfilehash: 71ff5229d4f2342880bdf50f288355a676b78722
ms.sourcegitcommit: 70c76a12449439bac0f7a359866be5a0311ce960
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/25/2018
ms.locfileid: "39244312"
---
# <a name="sample-xml-file-numerical-data-in-a-namespace"></a><span data-ttu-id="f5fa7-102">Przykładowy plik XML: Dane liczbowe w Namespace</span><span class="sxs-lookup"><span data-stu-id="f5fa7-102">Sample XML File: Numerical Data in a Namespace</span></span>
<span data-ttu-id="f5fa7-103">Następujący plik XML jest używany w różne przykłady w [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="f5fa7-103">The following XML file is used in various examples in the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] documentation.</span></span> <span data-ttu-id="f5fa7-104">Ten plik zawiera dane liczbowe, sumowanie, średniej i grupowania.</span><span class="sxs-lookup"><span data-stu-id="f5fa7-104">This file contains numerical data for summing, averaging, and grouping.</span></span> <span data-ttu-id="f5fa7-105">Kod XML jest w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="f5fa7-105">The XML is in a namespace.</span></span>  
  
## <a name="data"></a><span data-ttu-id="f5fa7-106">Dane</span><span class="sxs-lookup"><span data-stu-id="f5fa7-106">Data</span></span>  
  
```xml  
<Root xmlns='http://www.adatum.com'>  
  <TaxRate>7.25</TaxRate>  
  <Data>  
    <Category>A</Category>  
    <Quantity>3</Quantity>  
    <Price>24.50</Price>  
  </Data>  
  <Data>  
    <Category>B</Category>  
    <Quantity>1</Quantity>  
    <Price>89.99</Price>  
  </Data>  
  <Data>  
    <Category>A</Category>  
    <Quantity>5</Quantity>  
    <Price>4.95</Price>  
  </Data>  
  <Data>  
    <Category>A</Category>  
    <Quantity>3</Quantity>  
    <Price>66.00</Price>  
  </Data>  
  <Data>  
    <Category>B</Category>  
    <Quantity>10</Quantity>  
    <Price>.99</Price>  
  </Data>  
  <Data>  
    <Category>A</Category>  
    <Quantity>15</Quantity>  
    <Price>29.00</Price>  
  </Data>  
  <Data>  
    <Category>B</Category>  
    <Quantity>8</Quantity>  
    <Price>6.99</Price>  
  </Data>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f5fa7-107">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f5fa7-107">See Also</span></span>  
 [<span data-ttu-id="f5fa7-108">Przykładowe dokumenty XML (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="f5fa7-108">Sample XML Documents (LINQ to XML)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-documents-linq-to-xml.md)
