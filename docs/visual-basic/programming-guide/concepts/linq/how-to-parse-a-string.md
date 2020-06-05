---
title: 'Instrukcje: analizowanie ciągu'
ms.date: 07/20/2015
ms.assetid: 896e1b4b-f9bd-4975-8bc1-55b6badce1ac
ms.openlocfilehash: 0a9076fc516bb8e6bc74732ca252fabfeda43d53
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84398015"
---
# <a name="how-to-parse-a-string-visual-basic"></a>Instrukcje: analizowanie ciągu (Visual Basic)
W tym temacie przedstawiono sposób tworzenia drzewa XML w języku C#.  
  
## <a name="example"></a>Przykład  
 Można przeanalizować ciąg w Visual Basic przy użyciu `XElement.Parse` metody. Jednak bardziej wydajne jest użycie literałów XML, jak pokazano w poniższym kodzie, ponieważ literały XML nie cierpią od tych samych kar za wydajność, co analizowanie XML z ciągu.  
  
 Za pomocą literałów XML, można po prostu skopiować i wkleić kod XML do programu Visual Basic.  
  
> [!NOTE]
> Analizowanie tekstu lub ładowanie dokumentu XML z pliku tekstowego jest mniej wydajne niż konstrukcja funkcjonalna. Jeśli inicjujesz drzewo XML od kodu, trwa mniej czasu procesora, aby użyć konstrukcji funkcjonalnej niż w celu przeanalizowania tekstu.  
  
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
  
## <a name="see-also"></a>Zobacz też

- [Analizowanie kodu XML (Visual Basic)](parsing-xml.md)
