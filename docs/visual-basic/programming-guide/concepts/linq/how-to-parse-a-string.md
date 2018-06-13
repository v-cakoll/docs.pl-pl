---
title: 'Porady: przeanalizować składni ciągu (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 896e1b4b-f9bd-4975-8bc1-55b6badce1ac
ms.openlocfilehash: da12ec98e03acceae375bbed4fc6ad4c2a71ec2d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33640244"
---
# <a name="how-to-parse-a-string-visual-basic"></a><span data-ttu-id="8a04d-102">Porady: przeanalizować składni ciągu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8a04d-102">How to: Parse a String (Visual Basic)</span></span>
<span data-ttu-id="8a04d-103">W tym temacie przedstawiono sposób tworzenia drzewo XML w języku C#.</span><span class="sxs-lookup"><span data-stu-id="8a04d-103">This topic shows how to create an XML tree in C#.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8a04d-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="8a04d-104">Example</span></span>  
 <span data-ttu-id="8a04d-105">Ciąg w Visual Basic można analizować przy użyciu `XElement.Parse` metody.</span><span class="sxs-lookup"><span data-stu-id="8a04d-105">You can parse a string in Visual Basic by using the `XElement.Parse` method.</span></span> <span data-ttu-id="8a04d-106">Jednak jest bardziej wydajne, aby użyć literałów XML, jak pokazano w następującym kodem, ponieważ literałów XML nie boryka się z tym samym spadku wydajności jako analizy pliku XML z ciągu.</span><span class="sxs-lookup"><span data-stu-id="8a04d-106">However, it is more efficient to use XML literals, as shown in following code, because XML literals do not suffer from the same performance penalties as parsing XML from a string.</span></span>  
  
 <span data-ttu-id="8a04d-107">Przy użyciu literałów XML, można po prostu skopiuj i Wklej kod XML w programie Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="8a04d-107">By using XML literals, you can just copy and paste your XML into your Visual Basic program.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8a04d-108">Analizowanie tekstu lub ładowania dokumentu XML z pliku tekstowego jest mniej wydajne niż konstrukcji funkcjonalności.</span><span class="sxs-lookup"><span data-stu-id="8a04d-108">Parsing text or loading an XML document from a text file is less efficient than functional construction.</span></span> <span data-ttu-id="8a04d-109">Jeśli są inicjowanie drzewo XML z kodu, zajmuje mniej czasu procesora na korzystanie z funkcjonalności konstrukcji, niż można przeanalizować tekstu.</span><span class="sxs-lookup"><span data-stu-id="8a04d-109">If you are initializing an XML tree from code, it takes less processor time to use functional construction than to parse text.</span></span>  
  
```vb  
Dim contacts as XElement = _  
    <Contacts>  
        <Contact>  
            <Name>Patrick Hines</Name>  
            <Phone Type="home">206-555-0144</Phone>  
            <Phone Type="work">425-555-0145</Phone>  
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
            <Phone Type="mobile">206-555-0163</Phone>  
            <Address>  
            <Street1>123 Main St</Street1>  
            <City>Mercer Island</City>  
            <State>WA</State>  
            <Postal>68042</Postal>  
            </Address>  
            <NetWorth>11</NetWorth>  
        </Contact>  
    </Contacts>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8a04d-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8a04d-110">See Also</span></span>  
 [<span data-ttu-id="8a04d-111">Analiza kodu XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8a04d-111">Parsing XML (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)
