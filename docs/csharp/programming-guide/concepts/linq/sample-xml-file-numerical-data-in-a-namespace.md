---
title: 'Przykładowy plik XML: Dane liczbowe w Namespace3'
ms.date: 07/20/2015
ms.assetid: 51750cab-3c66-4511-90fb-b9d211308d31
ms.openlocfilehash: 5a752f477d17cee50b98bc88bd39cabda2bd3bf6
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43393571"
---
# <a name="sample-xml-file-numerical-data-in-a-namespace"></a><span data-ttu-id="47a7f-102">Przykładowy plik XML: Dane liczbowe w Namespace</span><span class="sxs-lookup"><span data-stu-id="47a7f-102">Sample XML File: Numerical Data in a Namespace</span></span>
<span data-ttu-id="47a7f-103">Następujący plik XML jest używany w różne przykłady w [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="47a7f-103">The following XML file is used in various examples in the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] documentation.</span></span> <span data-ttu-id="47a7f-104">Ten plik zawiera dane liczbowe, sumowanie, średniej i grupowania.</span><span class="sxs-lookup"><span data-stu-id="47a7f-104">This file contains numerical data for summing, averaging, and grouping.</span></span> <span data-ttu-id="47a7f-105">Kod XML jest w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="47a7f-105">The XML is in a namespace.</span></span>  
  
## <a name="data"></a><span data-ttu-id="47a7f-106">Dane</span><span class="sxs-lookup"><span data-stu-id="47a7f-106">Data</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="47a7f-107">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="47a7f-107">See Also</span></span>  
 [<span data-ttu-id="47a7f-108">Przykładowe dokumenty XML (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="47a7f-108">Sample XML Documents (LINQ to XML)</span></span>](../../../../csharp/programming-guide/concepts/linq/sample-xml-documents-linq-to-xml.md)
