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
# <a name="generating-data-type-classes-from-xml"></a><span data-ttu-id="346d2-102">Generowanie klas typów danych z kodu XML</span><span class="sxs-lookup"><span data-stu-id="346d2-102">Generating Data Type Classes from XML</span></span>
[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] <span data-ttu-id="346d2-103">zawiera nową funkcję umożliwiającą generowanie klas typów danych z pliku XML.</span><span class="sxs-lookup"><span data-stu-id="346d2-103">includes a new feature to generate data type classes from XML.</span></span> <span data-ttu-id="346d2-104">W tym temacie opisano sposób automatycznie wygenerować typy danych dla źródła danych RSS bloga platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="346d2-104">This topic describes how to automatically generate data types for the .NET Blog RSS feed.</span></span>  
  
### <a name="obtaining-the-xml-from-the-net-blog-rss-feed"></a><span data-ttu-id="346d2-105">Uzyskiwanie kodu XML z RSS bloga platformy .NET kanału informacyjnego</span><span class="sxs-lookup"><span data-stu-id="346d2-105">Obtaining the XML from the .NET Blog RSS feed</span></span>  
  
1.  <span data-ttu-id="346d2-106">W programie Internet Explorer przejdź do [kanału informacyjnego RSS bloga platformy .NET](https://devblogs.microsoft.com/dotnet/feed/).</span><span class="sxs-lookup"><span data-stu-id="346d2-106">In Internet Explorer, navigate to the [.NET Blog RSS feed](https://devblogs.microsoft.com/dotnet/feed/).</span></span>  
  
2.  <span data-ttu-id="346d2-107">Kliknij prawym przyciskiem myszy strony i wybierz **Wyświetl źródło**.</span><span class="sxs-lookup"><span data-stu-id="346d2-107">Right-click the page and select **View Source**.</span></span>  
  
3.  <span data-ttu-id="346d2-108">Skopiuj tekst kanału informacyjnego, naciskając klawisz **Ctrl + A** aby zaznaczyć cały tekst i **klawisze Ctrl + C** do skopiowania.</span><span class="sxs-lookup"><span data-stu-id="346d2-108">Copy the text of the feed by pressing **Ctrl+A** to select all text, and **Ctrl+C** to copy.</span></span>  
  
### <a name="creating-the-data-types"></a><span data-ttu-id="346d2-109">Tworzenie typów danych</span><span class="sxs-lookup"><span data-stu-id="346d2-109">Creating the data types</span></span>  
  
1.  <span data-ttu-id="346d2-110">Otwórz plik kodu, w którym serwer proxy ma być używany.</span><span class="sxs-lookup"><span data-stu-id="346d2-110">Open a code file where the proxy is to be used.</span></span> <span data-ttu-id="346d2-111">Ten plik powinien być częścią [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] projektu.</span><span class="sxs-lookup"><span data-stu-id="346d2-111">This file should be part of a [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] project.</span></span>  
  
2.  <span data-ttu-id="346d2-112">Umieść kursor w lokalizacji w pliku poza wszelkie istniejące klasy.</span><span class="sxs-lookup"><span data-stu-id="346d2-112">Place the cursor in a location in the file outside any existing classes.</span></span>  
  
3.  <span data-ttu-id="346d2-113">Wybierz **Edytuj**, **Wklej specjalne**, **Wklej XML jako klasy**.</span><span class="sxs-lookup"><span data-stu-id="346d2-113">Select **Edit**, **Paste Special**, **Paste XML as Classes**.</span></span>  
  
4.  <span data-ttu-id="346d2-114">Klasy o nazwie `link`, `rss`, `rssChannel`, `rssChannelImage`, `rssChannelItem` i `rssChannelItemGuid` są tworzone przy użyciu wymaganych elementów członkowskich do uzyskiwania dostępu do elementów w kanale informacyjnym RSS.</span><span class="sxs-lookup"><span data-stu-id="346d2-114">Classes called `link`, `rss`, `rssChannel`, `rssChannelImage`, `rssChannelItem` and `rssChannelItemGuid` are created with the necessary members for accessing the elements in the RSS feed.</span></span>  
  
### <a name="using-the-generated-classes"></a><span data-ttu-id="346d2-115">Za pomocą wygenerowanych klas</span><span class="sxs-lookup"><span data-stu-id="346d2-115">Using the generated classes</span></span>  
  
1.  <span data-ttu-id="346d2-116">Wygenerowany klasy służy w kodzie, takich jak innych klas.</span><span class="sxs-lookup"><span data-stu-id="346d2-116">Once the classes are generated, they can be used in code like any other classes.</span></span> <span data-ttu-id="346d2-117">Poniższy kod zwraca nowe wystąpienie klasy `rssChannelImage` klasy.</span><span class="sxs-lookup"><span data-stu-id="346d2-117">The following code example returns a new instance of the `rssChannelImage` class.</span></span>  
  
    ```  
    var channelImage = new rssChannelImage()   
    {   
        title = "MyImage",   
        link = "http://www.contoso.com/images/channelImage.jpg",   
        url = "http://www.contoso.com/entries/myEntry.html"   
    };  
    ```
