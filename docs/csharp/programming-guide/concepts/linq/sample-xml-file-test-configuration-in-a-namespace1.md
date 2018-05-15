---
title: 'Przykładowy plik XML: Przetestować konfigurację w Namespace1'
ms.date: 07/20/2015
ms.assetid: e75ad1bc-5636-4623-9a34-a286a8c485d6
ms.openlocfilehash: 04d66eaa7fd134fdf368614ca94261b80c16d4d9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="sample-xml-file-test-configuration-in-a-namespace"></a><span data-ttu-id="f9d47-102">Przykładowy plik XML: Przetestować konfigurację w Namespace</span><span class="sxs-lookup"><span data-stu-id="f9d47-102">Sample XML File: Test Configuration in a Namespace</span></span>
<span data-ttu-id="f9d47-103">Następujący plik XML jest używany w różnych przykłady w [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="f9d47-103">The following XML file is used in various examples in the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] documentation.</span></span> <span data-ttu-id="f9d47-104">Jest to plik konfiguracji testu.</span><span class="sxs-lookup"><span data-stu-id="f9d47-104">This is a test configuration file.</span></span> <span data-ttu-id="f9d47-105">Plik XML jest w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="f9d47-105">The XML is in a namespace.</span></span>  
  
## <a name="testconfiginnamespacexml"></a><span data-ttu-id="f9d47-106">TestConfigInNamespace.xml</span><span class="sxs-lookup"><span data-stu-id="f9d47-106">TestConfigInNamespace.xml</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f9d47-107">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f9d47-107">See Also</span></span>  
 [<span data-ttu-id="f9d47-108">Przykładowe dokumenty XML (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="f9d47-108">Sample XML Documents (LINQ to XML)</span></span>](../../../../csharp/programming-guide/concepts/linq/sample-xml-documents-linq-to-xml.md)
