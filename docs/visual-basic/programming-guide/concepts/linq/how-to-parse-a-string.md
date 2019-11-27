---
title: 'Instrukcje: analizowanie ciągu'
ms.date: 07/20/2015
ms.assetid: 896e1b4b-f9bd-4975-8bc1-55b6badce1ac
ms.openlocfilehash: 31bae00eb3ebf0d8e64fc657693e8c0767c4f5d4
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344497"
---
# <a name="how-to-parse-a-string-visual-basic"></a><span data-ttu-id="f55db-102">Instrukcje: analizowanie ciągu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f55db-102">How to: Parse a String (Visual Basic)</span></span>
<span data-ttu-id="f55db-103">W tym temacie pokazano, jak utworzyć drzewo XML w C#.</span><span class="sxs-lookup"><span data-stu-id="f55db-103">This topic shows how to create an XML tree in C#.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f55db-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="f55db-104">Example</span></span>  
 <span data-ttu-id="f55db-105">Można przeanalizować ciąg w Visual Basic przy użyciu metody `XElement.Parse`.</span><span class="sxs-lookup"><span data-stu-id="f55db-105">You can parse a string in Visual Basic by using the `XElement.Parse` method.</span></span> <span data-ttu-id="f55db-106">Jednak bardziej wydajne jest użycie literałów XML, jak pokazano w poniższym kodzie, ponieważ literały XML nie cierpią od tych samych kar za wydajność, co analizowanie XML z ciągu.</span><span class="sxs-lookup"><span data-stu-id="f55db-106">However, it is more efficient to use XML literals, as shown in following code, because XML literals do not suffer from the same performance penalties as parsing XML from a string.</span></span>  
  
 <span data-ttu-id="f55db-107">Za pomocą literałów XML, można po prostu skopiować i wkleić kod XML do programu Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="f55db-107">By using XML literals, you can just copy and paste your XML into your Visual Basic program.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f55db-108">Analizowanie tekstu lub ładowanie dokumentu XML z pliku tekstowego jest mniej wydajne niż konstrukcja funkcjonalna.</span><span class="sxs-lookup"><span data-stu-id="f55db-108">Parsing text or loading an XML document from a text file is less efficient than functional construction.</span></span> <span data-ttu-id="f55db-109">Jeśli inicjujesz drzewo XML od kodu, trwa mniej czasu procesora, aby użyć konstrukcji funkcjonalnej niż w celu przeanalizowania tekstu.</span><span class="sxs-lookup"><span data-stu-id="f55db-109">If you are initializing an XML tree from code, it takes less processor time to use functional construction than to parse text.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f55db-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f55db-110">See also</span></span>

- [<span data-ttu-id="f55db-111">Analizowanie kodu XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f55db-111">Parsing XML (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)
