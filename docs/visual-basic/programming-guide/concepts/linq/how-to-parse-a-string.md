---
title: 'Instrukcje: Przeanalizować składni ciągu (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 896e1b4b-f9bd-4975-8bc1-55b6badce1ac
ms.openlocfilehash: 815e94b3b41c2c0cc1d18d598307ab292919bea4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61942600"
---
# <a name="how-to-parse-a-string-visual-basic"></a><span data-ttu-id="bf80c-102">Instrukcje: Przeanalizować składni ciągu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bf80c-102">How to: Parse a String (Visual Basic)</span></span>
<span data-ttu-id="bf80c-103">W tym temacie przedstawiono sposób tworzenia drzewa XML w C#.</span><span class="sxs-lookup"><span data-stu-id="bf80c-103">This topic shows how to create an XML tree in C#.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bf80c-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="bf80c-104">Example</span></span>  
 <span data-ttu-id="bf80c-105">Ciąg w języku Visual Basic można analizować za pomocą `XElement.Parse` metody.</span><span class="sxs-lookup"><span data-stu-id="bf80c-105">You can parse a string in Visual Basic by using the `XElement.Parse` method.</span></span> <span data-ttu-id="bf80c-106">Jednak jest bardziej wydajne, aby użyć literałów XML, jak pokazano w poniższym kodzie, ponieważ literały XML nie borykają się z tym samym spadku wydajności jako analizowanie kodu XML z ciągu.</span><span class="sxs-lookup"><span data-stu-id="bf80c-106">However, it is more efficient to use XML literals, as shown in following code, because XML literals do not suffer from the same performance penalties as parsing XML from a string.</span></span>  
  
 <span data-ttu-id="bf80c-107">Przy użyciu literałów XML, można po prostu skopiować i wkleić kod XML do programu Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="bf80c-107">By using XML literals, you can just copy and paste your XML into your Visual Basic program.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bf80c-108">Analizowanie tekstu lub podczas ładowania dokumentu XML z pliku tekstowego jest mniej wydajne niż konstrukcja funkcjonalna.</span><span class="sxs-lookup"><span data-stu-id="bf80c-108">Parsing text or loading an XML document from a text file is less efficient than functional construction.</span></span> <span data-ttu-id="bf80c-109">Jeśli są inicjowanie drzewa XML z kodu, zajmuje mniej czasu procesora, aby użyć konstrukcja funkcjonalna, niż można przeanalizować tekstu.</span><span class="sxs-lookup"><span data-stu-id="bf80c-109">If you are initializing an XML tree from code, it takes less processor time to use functional construction than to parse text.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="bf80c-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bf80c-110">See also</span></span>

- [<span data-ttu-id="bf80c-111">Analizowanie kodu XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bf80c-111">Parsing XML (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)
