---
title: "Przykładowe interfejsu IXmlSerializable technologii usług sieci Web"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0202d3f1-a50b-427d-a5bb-79208b8f1c22
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: be0c76371bda9e91e0becf8a9e09beb44e44dd3c
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="web-services-ixmlserializable-technology-sample"></a>Przykładowe interfejsu IXmlSerializable technologii usług sieci Web
[Pobieranie próbki](http://download.microsoft.com/download/4/7/B/47B2164C-E780-4B10-8DE4-2CB5B886E0A6/Technologies/Serialization/Xml%20Serialization/IXmlSerializable.zip.exe)  
  
 Ten przykład przedstawia sposób użycia <xref:System.Xml.Serialization.IXmlSerializable> do sterowania serializacją niestandardowych typów w usługach sieci Web ASP.NET.  
  
### <a name="to-build-the-sample-using-visual-studio"></a>Aby samodzielnie tworzyć przykładowy przy użyciu programu Visual Studio  
  
1.  Otwórz [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] i wybierz **nowej witryny sieci Web** z **pliku** menu.  
  
2.  W lewym okienku **nowej witryny sieci Web** okno dialogowe, wybierz odpowiedni język programowania, a następnie w okienku po prawej stronie wybierz **usługi sieci Web ASP.NET**.  
  
3.  Typ **interfejsu IXmlSerializable** jako nazwa nową usługę sieci Web.  
  
4.  W oknie Solution Explorer, kliknij prawym przyciskiem myszy ikonę dla Service.asmx i wybierz **usunąć**; Powtórz ten krok dla pliku plik codebehind Service.asmx.  
  
5.  Kliknij prawym przyciskiem myszy projekt w katalogu i zaznacz **Dodaj istniejący element**. W oknie dialogowym Przejdź do podkatalogu usługi katalogu specyficzny dla języka.  
  
6.  Wybierz Service.asmx, a następnie powtórz ten krok dla PLiku związanym kodzie Service.asmx.  
  
7.  Otwórz [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)] i przejdź do katalogu, która zawiera katalog IXmlSerializable, który został utworzony w kroku 3 powyżej.  
  
8.  Kliknij prawym przyciskiem myszy ikonę katalogu interfejsu IXmlSerializable i wybierz **udostępnianie i zabezpieczenia**.  
  
9. Na karcie Udostępnianie w sieci Web wybierz **Udostępnij ten Folder**i Potwierdź ustawienia domyślne, włącznie z nazwą interfejsu IXmlSerializable.  
  
10. Kliknij przycisk **OK**.  
  
### <a name="to-run-the-sample"></a>Aby uruchomić przykładowy  
  
1.  Otwórz okno przeglądarki, a następnie wybierz jego paskiem adresu.  
  
2.  Typ **http://localhost/IXmlSerializable/Service.asmx**.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Xml.Serialization.IXmlSerializable>  
 <xref:System.Xml.Serialization>  
 <xref:System.Xml.XmlConvert>  
 <xref:System.Xml.XmlQualifiedName>  
 <xref:System.Xml.XmlReader>  
 <xref:System.Xml.Schema.XmlSchema>  
 <xref:System.Xml.Schema.XmlSchemaSet>  
 <xref:System.Xml.XmlUrlResolver>  
 <xref:System.Xml.XmlWriter>
