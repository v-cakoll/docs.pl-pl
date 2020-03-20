---
title: Generowanie klas typów danych z kodu XML
ms.date: 03/30/2017
ms.assetid: e4e5e4e8-527f-44d1-92fa-8904a08784ea
ms.openlocfilehash: d66cbd1806b90d21a483d0c470f953ddfb9c4fca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184134"
---
# <a name="generating-data-type-classes-from-xml"></a>Generowanie klas typów danych z kodu XML
.NET Framework 4.5 zawiera nową funkcję do generowania klas typów danych z XML. W tym temacie opisano sposób automatycznego generowania typów danych dla kanału informacyjnego RSS bloga .NET.  
  
### <a name="obtaining-the-xml-from-the-net-blog-rss-feed"></a>Uzyskiwanie kodu XML z kanału informacyjnego RSS bloga .NET  
  
1. W programie Internet Explorer przejdź do [kanału informacyjnego .NET Blog RSS](https://devblogs.microsoft.com/dotnet/feed/).  
  
2. Kliknij prawym przyciskiem myszy stronę i wybierz polecenie **Wyświetl źródło**.  
  
3. Skopiuj tekst kanału informacyjnego, naciskając **klawisze Ctrl+A,** aby zaznaczyć cały tekst, oraz **klawisze Ctrl+C** do skopiowania.  
  
### <a name="creating-the-data-types"></a>Tworzenie typów danych  
  
1. Otwórz plik kodu, w którym ma być używany serwer proxy. Ten plik powinien być częścią projektu .NET Framework 4.5.  
  
2. Umieść kursor w lokalizacji w pliku poza istniejącymi klasami.  
  
3. Wybierz **edytuj,** **wklej specjalnie,** **Wklej XML jako klasy**.  
  
4. Klasy `link`o `rss` `rssChannel`nazwie `rssChannelImage` `rssChannelItem` , `rssChannelItemGuid` , i są tworzone z elementami niezbędnymi do uzyskania dostępu do elementów w kanale RSS.  
  
### <a name="using-the-generated-classes"></a>Korzystanie z wygenerowanych klas  
  
1. Po wygenerowaniu klas, mogą być używane w kodzie, jak inne klasy. Poniższy przykład kodu zwraca nowe `rssChannelImage` wystąpienie klasy.  
  
    ```csharp
    var channelImage = new rssChannelImage()
    {
        title = "MyImage",
        link = "http://www.contoso.com/images/channelImage.jpg",
        url = "http://www.contoso.com/entries/myEntry.html"
    };  
    ```
