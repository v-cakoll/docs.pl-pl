---
title: Generowanie klas typów danych z kodu XML
ms.date: 03/30/2017
ms.assetid: e4e5e4e8-527f-44d1-92fa-8904a08784ea
ms.openlocfilehash: a6666f1ba23dd563bd7a005d458cd7fe8253c3af
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2019
ms.locfileid: "57679089"
---
# <a name="generating-data-type-classes-from-xml"></a>Generowanie klas typów danych z kodu XML
[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] zawiera nową funkcję umożliwiającą generowanie klas typów danych z pliku XML. W tym temacie opisano sposób automatycznie wygenerować typy danych dla źródła danych RSS bloga platformy .NET.  
  
### <a name="obtaining-the-xml-from-the-net-blog-rss-feed"></a>Uzyskiwanie kodu XML z RSS bloga platformy .NET kanału informacyjnego  
  
1.  W programie Internet Explorer przejdź do [kanału informacyjnego RSS bloga platformy .NET](https://devblogs.microsoft.com/dotnet/feed/).  
  
2.  Kliknij prawym przyciskiem myszy strony i wybierz **Wyświetl źródło**.  
  
3.  Skopiuj tekst kanału informacyjnego, naciskając klawisz **Ctrl + A** aby zaznaczyć cały tekst i **klawisze Ctrl + C** do skopiowania.  
  
### <a name="creating-the-data-types"></a>Tworzenie typów danych  
  
1.  Otwórz plik kodu, w którym serwer proxy ma być używany. Ten plik powinien być częścią [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] projektu.  
  
2.  Umieść kursor w lokalizacji w pliku poza wszelkie istniejące klasy.  
  
3.  Wybierz **Edytuj**, **Wklej specjalne**, **Wklej XML jako klasy**.  
  
4.  Klasy o nazwie `link`, `rss`, `rssChannel`, `rssChannelImage`, `rssChannelItem` i `rssChannelItemGuid` są tworzone przy użyciu wymaganych elementów członkowskich do uzyskiwania dostępu do elementów w kanale informacyjnym RSS.  
  
### <a name="using-the-generated-classes"></a>Za pomocą wygenerowanych klas  
  
1.  Wygenerowany klasy służy w kodzie, takich jak innych klas. Poniższy kod zwraca nowe wystąpienie klasy `rssChannelImage` klasy.  
  
    ```  
    var channelImage = new rssChannelImage()   
    {   
        title = "MyImage",   
        link = "http://www.contoso.com/images/channelImage.jpg",   
        url = "http://www.contoso.com/entries/myEntry.html"   
    };  
    ```
