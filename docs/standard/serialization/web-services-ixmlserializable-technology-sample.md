---
title: Przykład technologii IXmlSerializable usług sieci Web
ms.date: 03/30/2017
ms.assetid: 0202d3f1-a50b-427d-a5bb-79208b8f1c22
ms.openlocfilehash: 343755c062fc13891d84131a5f7682e2e1466a5a
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43866541"
---
# <a name="web-services-ixmlserializable-technology-sample"></a>Przykład technologii IXmlSerializable usług sieci Web
[Pobierz przykładowe](https://download.microsoft.com/download/4/7/B/47B2164C-E780-4B10-8DE4-2CB5B886E0A6/Technologies/Serialization/Xml%20Serialization/IXmlSerializable.zip.exe)  
  
 Ten przykład ilustruje sposób używania <xref:System.Xml.Serialization.IXmlSerializable> do kontrolowania serializacji niestandardowych typów w usługach sieci Web programu ASP.NET.  
  
### <a name="to-build-the-sample-using-visual-studio"></a>Aby skompilować przykład za pomocą programu Visual Studio  
  
1.  Otwórz [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] i wybierz **nową witrynę sieci Web** z **pliku** menu.  
  
2.  W okienku po lewej stronie **nową witrynę sieci Web** okno dialogowe, wybierz żądane język programowania, a następnie w okienku po prawej stronie wybierz **usługi sieci Web ASP.NET**.  
  
3.  Typ **IXmlSerializable** jako nazwę nowej usługi sieci Web.  
  
4.  W oknie Eksploratora rozwiązań kliknij prawym przyciskiem myszy ikonę Service.asmx i wybierz polecenie **Usuń**; Powtórz ten krok dla pliku związanym kodzie Service.asmx.  
  
5.  Kliknij prawym przyciskiem myszy projekt katalogu i wybierz **Dodaj istniejący element**. W oknie dialogowym Przejdź do podkatalogu usługi katalogu specyficzny dla języka.  
  
6.  Wybierz Service.asmx, a następnie powtórz ten krok dla PLiku związanym kodzie Service.asmx.  
  
7.  Otwórz [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)] i przejdź do katalogu, która zawiera katalog IXmlSerializable, który został utworzony w kroku 3 powyżej.  
  
8.  Kliknij prawym przyciskiem myszy ikonę IXmlSerializable katalogu, a następnie wybierz pozycję **udostępnianie i zabezpieczenia**.  
  
9. Na karcie Udostępnianie w sieci Web wybierz **Udostępnij ten Folder**i Potwierdź ustawienia domyślne, łącznie z nazwą IXmlSerializable.  
  
10. Kliknij przycisk **OK**.  
  
### <a name="to-run-the-sample"></a>Aby uruchomić przykład  
  
1.  Otwórz okno przeglądarki, a następnie wybierz jego paskiem adresu.  
  
2.  Typ **http://localhost/IXmlSerializable/Service.asmx**.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Xml.Serialization.IXmlSerializable>  
- <xref:System.Xml.Serialization>  
- <xref:System.Xml.XmlConvert>  
- <xref:System.Xml.XmlQualifiedName>  
- <xref:System.Xml.XmlReader>  
- <xref:System.Xml.Schema.XmlSchema>  
- <xref:System.Xml.Schema.XmlSchemaSet>  
- <xref:System.Xml.XmlUrlResolver>  
- <xref:System.Xml.XmlWriter>
