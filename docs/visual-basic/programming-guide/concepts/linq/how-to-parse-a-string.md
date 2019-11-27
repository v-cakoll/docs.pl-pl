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
# <a name="how-to-parse-a-string-visual-basic"></a>Instrukcje: analizowanie ciągu (Visual Basic)
W tym temacie pokazano, jak utworzyć drzewo XML w C#.  
  
## <a name="example"></a>Przykład  
 Można przeanalizować ciąg w Visual Basic przy użyciu metody `XElement.Parse`. Jednak bardziej wydajne jest użycie literałów XML, jak pokazano w poniższym kodzie, ponieważ literały XML nie cierpią od tych samych kar za wydajność, co analizowanie XML z ciągu.  
  
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
  
## <a name="see-also"></a>Zobacz także

- [Analizowanie kodu XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)
