---
title: "Porady: przeanalizować składni ciągu (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 896e1b4b-f9bd-4975-8bc1-55b6badce1ac
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 10b80c72cae70437ff812c4b67b2532d708f1e69
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-parse-a-string-visual-basic"></a>Porady: przeanalizować składni ciągu (Visual Basic)
W tym temacie przedstawiono sposób tworzenia drzewo XML w języku C#.  
  
## <a name="example"></a>Przykład  
 Może przeanalizować składni ciągu w [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] przy użyciu `XElement.Parse` metody. Jednak jest bardziej wydajne, aby użyć literałów XML, jak pokazano w następującym kodem, ponieważ literałów XML nie boryka się z tym samym spadku wydajności jako analizy pliku XML z ciągu.  
  
 Przy użyciu literałów XML, można po prostu skopiuj i Wklej kod XML w Twojej [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] program.  
  
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
