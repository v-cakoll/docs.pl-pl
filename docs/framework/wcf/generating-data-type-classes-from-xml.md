---
title: Generowanie klas typów danych z kodu XML
ms.date: 03/30/2017
ms.assetid: e4e5e4e8-527f-44d1-92fa-8904a08784ea
ms.openlocfilehash: 6b38a0aea3101c70b3c3ec0c8feb4ee88018b64e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="generating-data-type-classes-from-xml"></a>Generowanie klas typów danych z kodu XML
[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] zawiera nową funkcję do generowania klasy typów danych z pliku XML. W tym temacie opisano, jak można automatycznie wygenerować typy danych dla źródła danych RSS blogu .NET.  
  
### <a name="obtaining-the-xml-from-the-net-blog-rss-feed"></a>Uzyskiwanie XML w funkcji RSS blogu .NET źródła danych  
  
1.  W programie Internet Explorer przejdź do [kanału informacyjnego RSS blogu .NET](https://blogs.msdn.microsoft.com/dotnet/feed/).  
  
2.  Kliknij prawym przyciskiem myszy strony i wybierz **Wyświetl źródło**.  
  
3.  Skopiuj tekst kanału informacyjnego przez naciśnięcie przycisku **Ctrl + A** aby zaznaczyć cały tekst i **klawisze Ctrl + C** do skopiowania.  
  
### <a name="creating-the-data-types"></a>Tworzenie typów danych  
  
1.  Otwórz plik kodu, gdy serwer proxy ma być używany. Ten plik powinien być częścią [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] projektu.  
  
2.  Umieść kursor w lokalizacji w pliku poza wszelkie istniejące klasy.  
  
3.  Wybierz **Edytuj**, **Wklej specjalne**, **Wklej kod XML jako klasy**.  
  
4.  Klasy o nazwie `link`, `rss`, `rssChannel`, `rssChannelImage`, `rssChannelItem` i `rssChannelItemGuid` są tworzone z członkami niezbędne do uzyskiwania dostępu do elementów w kanału informacyjnego RSS.  
  
### <a name="using-the-generated-classes"></a>Przy użyciu wygenerowane klasy  
  
1.  Gdy zostaną wygenerowane klasy, użyciem w kodzie, podobnie jak inne klasy. Poniższy przykład kodu zwraca nowe wystąpienie klasy `rssChannelImage` klasy.  
  
    ```  
    var channelImage = new rssChannelImage()   
    {   
        title = "MyImage",   
        link = "http://www.contoso.com/images/channelImage.jpg",   
        url = "http://www.contoso.com/entries/myEntry.html"   
    };  
    ```
