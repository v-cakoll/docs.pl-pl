---
title: Generowanie klas typów danych z kodu XML
ms.date: 03/30/2017
ms.assetid: e4e5e4e8-527f-44d1-92fa-8904a08784ea
ms.openlocfilehash: 977b12b5c61c196a4f033361d37785e4ed0af73a
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73975856"
---
# <a name="generating-data-type-classes-from-xml"></a>Generowanie klas typów danych z kodu XML
.NET Framework 4,5 zawiera nową funkcję do generowania klas typów danych z pliku XML. W tym temacie opisano sposób automatycznego generowania typów danych dla kanału informacyjnego RSS w blogu platformy .NET.  
  
### <a name="obtaining-the-xml-from-the-net-blog-rss-feed"></a>Uzyskiwanie kodu XML ze źródła danych RSS blogu platformy .NET  
  
1. W programie Internet Explorer przejdź do [kanału informacyjnego RSS blogu platformy .NET](https://devblogs.microsoft.com/dotnet/feed/).  
  
2. Kliknij prawym przyciskiem myszy stronę i wybierz polecenie **Wyświetl źródło**.  
  
3. Skopiuj tekst kanału informacyjnego, naciskając **klawisze Ctrl + A** , aby zaznaczyć cały tekst, a następnie **klawisze CTRL + C** , aby skopiować.  
  
### <a name="creating-the-data-types"></a>Tworzenie typów danych  
  
1. Otwórz plik kodu, w którym ma być używany serwer proxy. Ten plik powinien być częścią projektu .NET Framework 4,5.  
  
2. Umieść kursor w lokalizacji w pliku poza istniejącymi klasami.  
  
3. Wybierz pozycję **Edytuj**, **Wklej specjalnie**, **Wklej kod XML jako klasy**.  
  
4. Klasy o nazwie `link`, `rss`, `rssChannel`, `rssChannelImage`, `rssChannelItem` i `rssChannelItemGuid` są tworzone z członkami niezbędnymi do uzyskiwania dostępu do elementów w kanale informacyjnym RSS.  
  
### <a name="using-the-generated-classes"></a>Korzystanie z wygenerowanych klas  
  
1. Po wygenerowaniu klasy mogą być używane w kodzie, podobnie jak w przypadku innych klas. Poniższy przykład kodu zwraca nowe wystąpienie klasy `rssChannelImage`.  
  
    ```csharp
    var channelImage = new rssChannelImage()   
    {   
        title = "MyImage",   
        link = "http://www.contoso.com/images/channelImage.jpg",   
        url = "http://www.contoso.com/entries/myEntry.html"   
    };  
    ```
