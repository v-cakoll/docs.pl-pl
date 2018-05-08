---
title: 'Porady: przeanalizować składni ciągu (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 896e1b4b-f9bd-4975-8bc1-55b6badce1ac
ms.openlocfilehash: da12ec98e03acceae375bbed4fc6ad4c2a71ec2d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-parse-a-string-visual-basic"></a>Porady: przeanalizować składni ciągu (Visual Basic)
W tym temacie przedstawiono sposób tworzenia drzewo XML w języku C#.  
  
## <a name="example"></a>Przykład  
 Ciąg w Visual Basic można analizować przy użyciu `XElement.Parse` metody. Jednak jest bardziej wydajne, aby użyć literałów XML, jak pokazano w następującym kodem, ponieważ literałów XML nie boryka się z tym samym spadku wydajności jako analizy pliku XML z ciągu.  
  
 Przy użyciu literałów XML, można po prostu skopiuj i Wklej kod XML w programie Visual Basic.  
  
> [!NOTE]
>  Analizowanie tekstu lub ładowania dokumentu XML z pliku tekstowego jest mniej wydajne niż konstrukcji funkcjonalności. Jeśli są inicjowanie drzewo XML z kodu, zajmuje mniej czasu procesora na korzystanie z funkcjonalności konstrukcji, niż można przeanalizować tekstu.  
  
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
 [Analiza kodu XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)
