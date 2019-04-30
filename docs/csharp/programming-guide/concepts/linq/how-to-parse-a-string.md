---
title: 'Instrukcje: Przeanalizować ciąg (C#)'
ms.date: 07/20/2015
ms.assetid: 81e5686c-9658-42d8-a7e3-b11be0a2c98b
ms.openlocfilehash: c4d26f534c718d69c84a30b11de22249b241e084
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61667889"
---
# <a name="how-to-parse-a-string-c"></a><span data-ttu-id="07ac6-102">Instrukcje: Przeanalizować ciąg (C#)</span><span class="sxs-lookup"><span data-stu-id="07ac6-102">How to: Parse a String (C#)</span></span>
<span data-ttu-id="07ac6-103">W tym temacie przedstawiono sposób przeanalizować składni ciągu do utworzenia drzewa XML w języku C#.</span><span class="sxs-lookup"><span data-stu-id="07ac6-103">This topic shows how to parse a string to create an XML tree in C#.</span></span>  
  
## <a name="example"></a><span data-ttu-id="07ac6-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="07ac6-104">Example</span></span>  
 <span data-ttu-id="07ac6-105">Poniższy kod C# pokazano, jak można przeanalizować ciągu.</span><span class="sxs-lookup"><span data-stu-id="07ac6-105">The following C# code shows how to parse a string.</span></span>  
  
```csharp  
XElement contacts = XElement.Parse(  
    @"<Contacts>  
        <Contact>  
            <Name>Patrick Hines</Name>  
            <Phone Type=""home"">206-555-0144</Phone>  
            <Phone type=""work"">425-555-0145</Phone>  
            <Address>  
            <Street1>123 Main St</Street1>  
            <City>Mercer Island</City>  
            <State>WA</State>  
            <Postal>68042</Postal>  
            </Address>  
            <NetWorth>10</NetWorth>  
        </Contact>  
        <Contact>  
            <Name>Gretchen Rivas</Name>  
            <Phone Type=""mobile"">206-555-0163</Phone>  
            <Address>  
            <Street1>123 Main St</Street1>  
            <City>Mercer Island</City>  
            <State>WA</State>  
            <Postal>68042</Postal>  
            </Address>  
            <NetWorth>11</NetWorth>  
        </Contact>  
    </Contacts>");  
Console.WriteLine(contacts);  
```  
  
## <a name="see-also"></a><span data-ttu-id="07ac6-106">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="07ac6-106">See also</span></span>

- [<span data-ttu-id="07ac6-107">Analizowanie kodu XML (C#)</span><span class="sxs-lookup"><span data-stu-id="07ac6-107">Parsing XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/parsing-xml.md)
