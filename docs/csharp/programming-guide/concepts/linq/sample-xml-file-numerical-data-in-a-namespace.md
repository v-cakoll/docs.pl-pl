---
title: 'Przykładowy plik XML: dane liczbowe w obszarze nazw3'
ms.date: 07/20/2015
ms.assetid: 51750cab-3c66-4511-90fb-b9d211308d31
ms.openlocfilehash: 02788b73a7af9922b5a50237f2d2e401cba8abe2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "66483705"
---
# <a name="sample-xml-file-numerical-data-in-a-namespace"></a><span data-ttu-id="17435-102">Przykładowy plik XML: dane liczbowe w przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="17435-102">Sample XML File: Numerical Data in a Namespace</span></span>
<span data-ttu-id="17435-103">Poniższy plik XML jest używany w [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] różnych przykładach w dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="17435-103">The following XML file is used in various examples in the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] documentation.</span></span> <span data-ttu-id="17435-104">Ten plik zawiera dane liczbowe do sumowania, uśredniania i grupowania.</span><span class="sxs-lookup"><span data-stu-id="17435-104">This file contains numerical data for summing, averaging, and grouping.</span></span> <span data-ttu-id="17435-105">Kod XML znajduje się w obszarze nazw.</span><span class="sxs-lookup"><span data-stu-id="17435-105">The XML is in a namespace.</span></span>  
  
## <a name="data"></a><span data-ttu-id="17435-106">Dane</span><span class="sxs-lookup"><span data-stu-id="17435-106">Data</span></span>  
  
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
