---
title: 'Przykładowy plik XML: dane liczbowe w przestrzeni nazw'
ms.date: 07/20/2015
ms.assetid: f01cc0a1-fb55-4b42-8380-16f4be47d6f4
ms.openlocfilehash: 3a067afc6d59c76a50c7c9f91673bb631edd085b
ms.sourcegitcommit: 9ee6cd851b6e176a5811ea28ed0d5935c71950f9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68869099"
---
# <a name="sample-xml-file-numerical-data-in-a-namespace"></a><span data-ttu-id="6d673-102">Przykładowy plik XML: dane liczbowe w przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="6d673-102">Sample XML File: Numerical Data in a Namespace</span></span>
<span data-ttu-id="6d673-103">Następujący plik XML jest używany w różnych przykładach w [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="6d673-103">The following XML file is used in various examples in the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] documentation.</span></span> <span data-ttu-id="6d673-104">Ten plik zawiera dane liczbowe dla sumowania, uśredniania i grupowania.</span><span class="sxs-lookup"><span data-stu-id="6d673-104">This file contains numerical data for summing, averaging, and grouping.</span></span> <span data-ttu-id="6d673-105">KOD XML znajduje się w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="6d673-105">The XML is in a namespace.</span></span>  
  
## <a name="data"></a><span data-ttu-id="6d673-106">Dane</span><span class="sxs-lookup"><span data-stu-id="6d673-106">Data</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6d673-107">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6d673-107">See also</span></span>

- [<span data-ttu-id="6d673-108">Przykładowe dokumenty XML (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="6d673-108">Sample XML Documents (LINQ to XML)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-documents-linq-to-xml.md)
