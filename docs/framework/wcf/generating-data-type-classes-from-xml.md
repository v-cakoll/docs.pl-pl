---
title: "Generowanie klas typów danych z kodu XML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e4e5e4e8-527f-44d1-92fa-8904a08784ea
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: e0362673ebb7d686822fae594b3a41435ceb9a4d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="generating-data-type-classes-from-xml"></a><span data-ttu-id="053d8-102">Generowanie klas typów danych z kodu XML</span><span class="sxs-lookup"><span data-stu-id="053d8-102">Generating Data Type Classes from XML</span></span>
[!INCLUDE[net_v45](../../../includes/net-v45-md.md)]<span data-ttu-id="053d8-103">zawiera nową funkcję do generowania klasy typów danych z pliku XML.</span><span class="sxs-lookup"><span data-stu-id="053d8-103"> includes a new feature to generate data type classes from XML.</span></span> <span data-ttu-id="053d8-104">W tym temacie opisano, jak można automatycznie wygenerować typy danych dla źródła danych RSS blogu .NET.</span><span class="sxs-lookup"><span data-stu-id="053d8-104">This topic describes how to automatically generate data types for the .NET Blog RSS feed.</span></span>  
  
### <a name="obtaining-the-xml-from-the-net-blog-rss-feed"></a><span data-ttu-id="053d8-105">Uzyskiwanie XML w funkcji RSS blogu .NET źródła danych</span><span class="sxs-lookup"><span data-stu-id="053d8-105">Obtaining the XML from the .NET Blog RSS feed</span></span>  
  
1.  <span data-ttu-id="053d8-106">W programie Internet Explorer przejdź do [kanału informacyjnego RSS blogu .NET](https://blogs.msdn.microsoft.com/dotnet/feed/).</span><span class="sxs-lookup"><span data-stu-id="053d8-106">In Internet Explorer, navigate to the [.NET Blog RSS feed](https://blogs.msdn.microsoft.com/dotnet/feed/).</span></span>  
  
2.  <span data-ttu-id="053d8-107">Kliknij prawym przyciskiem myszy strony i wybierz **Wyświetl źródło**.</span><span class="sxs-lookup"><span data-stu-id="053d8-107">Right-click the page and select **View Source**.</span></span>  
  
3.  <span data-ttu-id="053d8-108">Skopiuj tekst kanału informacyjnego przez naciśnięcie przycisku **Ctrl + A** aby zaznaczyć cały tekst i **klawisze Ctrl + C** do skopiowania.</span><span class="sxs-lookup"><span data-stu-id="053d8-108">Copy the text of the feed by pressing **Ctrl+A** to select all text, and **Ctrl+C** to copy.</span></span>  
  
### <a name="creating-the-data-types"></a><span data-ttu-id="053d8-109">Tworzenie typów danych</span><span class="sxs-lookup"><span data-stu-id="053d8-109">Creating the data types</span></span>  
  
1.  <span data-ttu-id="053d8-110">Otwórz plik kodu, gdy serwer proxy ma być używany.</span><span class="sxs-lookup"><span data-stu-id="053d8-110">Open a code file where the proxy is to be used.</span></span> <span data-ttu-id="053d8-111">Ten plik powinien być częścią [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] projektu.</span><span class="sxs-lookup"><span data-stu-id="053d8-111">This file should be part of a [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] project.</span></span>  
  
2.  <span data-ttu-id="053d8-112">Umieść kursor w lokalizacji w pliku poza wszelkie istniejące klasy.</span><span class="sxs-lookup"><span data-stu-id="053d8-112">Place the cursor in a location in the file outside any existing classes.</span></span>  
  
3.  <span data-ttu-id="053d8-113">Wybierz **Edytuj**, **Wklej specjalne**, **Wklej kod XML jako klasy**.</span><span class="sxs-lookup"><span data-stu-id="053d8-113">Select **Edit**, **Paste Special**, **Paste XML as Classes**.</span></span>  
  
4.  <span data-ttu-id="053d8-114">Klasy o nazwie `link`, `rss`, `rssChannel`, `rssChannelImage`, `rssChannelItem` i `rssChannelItemGuid` są tworzone z członkami niezbędne do uzyskiwania dostępu do elementów w kanału informacyjnego RSS.</span><span class="sxs-lookup"><span data-stu-id="053d8-114">Classes called `link`, `rss`, `rssChannel`, `rssChannelImage`, `rssChannelItem` and `rssChannelItemGuid` are created with the necessary members for accessing the elements in the RSS feed.</span></span>  
  
### <a name="using-the-generated-classes"></a><span data-ttu-id="053d8-115">Przy użyciu wygenerowane klasy</span><span class="sxs-lookup"><span data-stu-id="053d8-115">Using the generated classes</span></span>  
  
1.  <span data-ttu-id="053d8-116">Gdy zostaną wygenerowane klasy, użyciem w kodzie, podobnie jak inne klasy.</span><span class="sxs-lookup"><span data-stu-id="053d8-116">Once the classes are generated, they can be used in code like any other classes.</span></span> <span data-ttu-id="053d8-117">Poniższy przykład kodu zwraca nowe wystąpienie klasy `rssChannelImage` klasy.</span><span class="sxs-lookup"><span data-stu-id="053d8-117">The following code example returns a new instance of the `rssChannelImage` class.</span></span>  
  
    ```  
    var channelImage = new rssChannelImage()   
    {   
        title = "MyImage",   
        link = "http://www.contoso.com/images/channelImage.jpg",   
        url = "http://www.contoso.com/entries/myEntry.html"   
    };  
    ```
