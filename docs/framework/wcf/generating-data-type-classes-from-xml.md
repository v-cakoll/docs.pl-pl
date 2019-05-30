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
# <a name="generating-data-type-classes-from-xml"></a><span data-ttu-id="f4405-102">Generowanie klas typów danych z kodu XML</span><span class="sxs-lookup"><span data-stu-id="f4405-102">Generating Data Type Classes from XML</span></span>
<span data-ttu-id="f4405-103">.NET framework 4.5 zawiera nową funkcję umożliwiającą generowanie klas typów danych z pliku XML.</span><span class="sxs-lookup"><span data-stu-id="f4405-103">.NET Framework 4.5 includes a new feature to generate data type classes from XML.</span></span> <span data-ttu-id="f4405-104">W tym temacie opisano sposób automatycznie wygenerować typy danych dla źródła danych RSS bloga platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="f4405-104">This topic describes how to automatically generate data types for the .NET Blog RSS feed.</span></span>  
  
### <a name="obtaining-the-xml-from-the-net-blog-rss-feed"></a><span data-ttu-id="f4405-105">Uzyskiwanie kodu XML z RSS bloga platformy .NET kanału informacyjnego</span><span class="sxs-lookup"><span data-stu-id="f4405-105">Obtaining the XML from the .NET Blog RSS feed</span></span>  
  
1. <span data-ttu-id="f4405-106">W programie Internet Explorer przejdź do [kanału informacyjnego RSS bloga platformy .NET](https://devblogs.microsoft.com/dotnet/feed/).</span><span class="sxs-lookup"><span data-stu-id="f4405-106">In Internet Explorer, navigate to the [.NET Blog RSS feed](https://devblogs.microsoft.com/dotnet/feed/).</span></span>  
  
2. <span data-ttu-id="f4405-107">Kliknij prawym przyciskiem myszy strony i wybierz **Wyświetl źródło**.</span><span class="sxs-lookup"><span data-stu-id="f4405-107">Right-click the page and select **View Source**.</span></span>  
  
3. <span data-ttu-id="f4405-108">Skopiuj tekst kanału informacyjnego, naciskając klawisz **Ctrl + A** aby zaznaczyć cały tekst i **klawisze Ctrl + C** do skopiowania.</span><span class="sxs-lookup"><span data-stu-id="f4405-108">Copy the text of the feed by pressing **Ctrl+A** to select all text, and **Ctrl+C** to copy.</span></span>  
  
### <a name="creating-the-data-types"></a><span data-ttu-id="f4405-109">Tworzenie typów danych</span><span class="sxs-lookup"><span data-stu-id="f4405-109">Creating the data types</span></span>  
  
1. <span data-ttu-id="f4405-110">Otwórz plik kodu, w którym serwer proxy ma być używany.</span><span class="sxs-lookup"><span data-stu-id="f4405-110">Open a code file where the proxy is to be used.</span></span> <span data-ttu-id="f4405-111">Ten plik powinien być częścią projektu platformy .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="f4405-111">This file should be part of a .NET Framework 4.5 project.</span></span>  
  
2. <span data-ttu-id="f4405-112">Umieść kursor w lokalizacji w pliku poza wszelkie istniejące klasy.</span><span class="sxs-lookup"><span data-stu-id="f4405-112">Place the cursor in a location in the file outside any existing classes.</span></span>  
  
3. <span data-ttu-id="f4405-113">Wybierz **Edytuj**, **Wklej specjalne**, **Wklej XML jako klasy**.</span><span class="sxs-lookup"><span data-stu-id="f4405-113">Select **Edit**, **Paste Special**, **Paste XML as Classes**.</span></span>  
  
4. <span data-ttu-id="f4405-114">Klasy o nazwie `link`, `rss`, `rssChannel`, `rssChannelImage`, `rssChannelItem` i `rssChannelItemGuid` są tworzone przy użyciu wymaganych elementów członkowskich do uzyskiwania dostępu do elementów w kanale informacyjnym RSS.</span><span class="sxs-lookup"><span data-stu-id="f4405-114">Classes called `link`, `rss`, `rssChannel`, `rssChannelImage`, `rssChannelItem` and `rssChannelItemGuid` are created with the necessary members for accessing the elements in the RSS feed.</span></span>  
  
### <a name="using-the-generated-classes"></a><span data-ttu-id="f4405-115">Za pomocą wygenerowanych klas</span><span class="sxs-lookup"><span data-stu-id="f4405-115">Using the generated classes</span></span>  
  
1. <span data-ttu-id="f4405-116">Wygenerowany klasy służy w kodzie, takich jak innych klas.</span><span class="sxs-lookup"><span data-stu-id="f4405-116">Once the classes are generated, they can be used in code like any other classes.</span></span> <span data-ttu-id="f4405-117">Poniższy kod zwraca nowe wystąpienie klasy `rssChannelImage` klasy.</span><span class="sxs-lookup"><span data-stu-id="f4405-117">The following code example returns a new instance of the `rssChannelImage` class.</span></span>  
  
    ```  
    var channelImage = new rssChannelImage()   
    {   
        title = "MyImage",   
        link = "http://www.contoso.com/images/channelImage.jpg",   
        url = "http://www.contoso.com/entries/myEntry.html"   
    };  
    ```
