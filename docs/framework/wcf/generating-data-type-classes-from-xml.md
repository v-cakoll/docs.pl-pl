---
title: Generowanie klas typów danych z kodu XML
ms.date: 03/30/2017
ms.assetid: e4e5e4e8-527f-44d1-92fa-8904a08784ea
ms.openlocfilehash: b99bb40105398dbd91b910c4a19828d069c3d9e7
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/30/2019
ms.locfileid: "66380220"
---
# <a name="generating-data-type-classes-from-xml"></a>Generowanie klas typów danych z kodu XML
.NET framework 4.5 zawiera nową funkcję umożliwiającą generowanie klas typów danych z pliku XML. W tym temacie opisano sposób automatycznie wygenerować typy danych dla źródła danych RSS bloga platformy .NET.  
  
### <a name="obtaining-the-xml-from-the-net-blog-rss-feed"></a>Uzyskiwanie kodu XML z RSS bloga platformy .NET kanału informacyjnego  
  
1. W programie Internet Explorer przejdź do [kanału informacyjnego RSS bloga platformy .NET](https://devblogs.microsoft.com/dotnet/feed/).  
  
2. Kliknij prawym przyciskiem myszy strony i wybierz **Wyświetl źródło**.  
  
3. Skopiuj tekst kanału informacyjnego, naciskając klawisz **Ctrl + A** aby zaznaczyć cały tekst i **klawisze Ctrl + C** do skopiowania.  
  
### <a name="creating-the-data-types"></a>Tworzenie typów danych  
  
1. Otwórz plik kodu, w którym serwer proxy ma być używany. Ten plik powinien być częścią projektu platformy .NET Framework 4.5.  
  
2. Umieść kursor w lokalizacji w pliku poza wszelkie istniejące klasy.  
  
3. Wybierz **Edytuj**, **Wklej specjalne**, **Wklej XML jako klasy**.  
  
4. Klasy o nazwie `link`, `rss`, `rssChannel`, `rssChannelImage`, `rssChannelItem` i `rssChannelItemGuid` są tworzone przy użyciu wymaganych elementów członkowskich do uzyskiwania dostępu do elementów w kanale informacyjnym RSS.  
  
### <a name="using-the-generated-classes"></a>Za pomocą wygenerowanych klas  
  
1. Wygenerowany klasy służy w kodzie, takich jak innych klas. Poniższy kod zwraca nowe wystąpienie klasy `rssChannelImage` klasy.  
  
    ```  
    var channelImage = new rssChannelImage()   
    {   
        title = "MyImage",   
        link = "http://www.contoso.com/images/channelImage.jpg",   
        url = "http://www.contoso.com/entries/myEntry.html"   
    };  
    ```
