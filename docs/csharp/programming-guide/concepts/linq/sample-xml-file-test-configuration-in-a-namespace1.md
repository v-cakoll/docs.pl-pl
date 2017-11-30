---
title: "Przykładowy plik XML: Przetestować konfigurację w Namespace1"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: e75ad1bc-5636-4623-9a34-a286a8c485d6
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: fecab66eae4b5ed93788435757aed555b708eb3f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="sample-xml-file-test-configuration-in-a-namespace"></a><span data-ttu-id="5b5e0-102">Przykładowy plik XML: Przetestować konfigurację w Namespace</span><span class="sxs-lookup"><span data-stu-id="5b5e0-102">Sample XML File: Test Configuration in a Namespace</span></span>
<span data-ttu-id="5b5e0-103">Następujący plik XML jest używany w różnych przykłady w [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="5b5e0-103">The following XML file is used in various examples in the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] documentation.</span></span> <span data-ttu-id="5b5e0-104">Jest to plik konfiguracji testu.</span><span class="sxs-lookup"><span data-stu-id="5b5e0-104">This is a test configuration file.</span></span> <span data-ttu-id="5b5e0-105">Plik XML jest w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="5b5e0-105">The XML is in a namespace.</span></span>  
  
## <a name="testconfiginnamespacexml"></a><span data-ttu-id="5b5e0-106">TestConfigInNamespace.xml</span><span class="sxs-lookup"><span data-stu-id="5b5e0-106">TestConfigInNamespace.xml</span></span>  
  
```xml  
<?xml version="1.0"?>  
<Tests xmlns="http://www.adatum.com">  
  <Test TestId="0001" TestType="CMD">  
    <Name>Convert number to string</Name>  
    <CommandLine>Examp1.EXE</CommandLine>  
    <Input>1</Input>  
    <Output>One</Output>  
  </Test>  
  <Test TestId="0002" TestType="CMD">  
    <Name>Find succeeding characters</Name>  
    <CommandLine>Examp2.EXE</CommandLine>  
    <Input>abc</Input>  
    <Output>def</Output>  
  </Test>  
  <Test TestId="0003" TestType="GUI">  
    <Name>Convert multiple numbers to strings</Name>  
    <CommandLine>Examp2.EXE /Verbose</CommandLine>  
    <Input>123</Input>  
    <Output>One Two Three</Output>  
  </Test>  
  <Test TestId="0004" TestType="GUI">  
    <Name>Find correlated key</Name>  
    <CommandLine>Examp3.EXE</CommandLine>  
    <Input>a1</Input>  
    <Output>b1</Output>  
  </Test>  
  <Test TestId="0005" TestType="GUI">  
    <Name>Count characters</Name>  
    <CommandLine>FinalExamp.EXE</CommandLine>  
    <Input>This is a test</Input>  
    <Output>14</Output>  
  </Test>  
  <Test TestId="0006" TestType="GUI">  
    <Name>Another Test</Name>  
    <CommandLine>Examp2.EXE</CommandLine>  
    <Input>Test Input</Input>  
    <Output>10</Output>  
  </Test>  
</Tests>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5b5e0-107">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5b5e0-107">See Also</span></span>  
 [<span data-ttu-id="5b5e0-108">Dokumenty XML próbki (LINQ do XML)</span><span class="sxs-lookup"><span data-stu-id="5b5e0-108">Sample XML Documents (LINQ to XML)</span></span>](../../../../csharp/programming-guide/concepts/linq/sample-xml-documents-linq-to-xml.md)
