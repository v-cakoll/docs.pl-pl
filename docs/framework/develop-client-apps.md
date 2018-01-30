---
title: "Tworzenie aplikacji klienckich z systemem Windows za pomocą programu .NET Framework"
ms.date: 01/09/2018
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: article
helpviewer_keywords:
- client application services
- applications [Windows Forms]
- Windows Presentation Foundation, in Visual Studio
- WPF, in Visual Studio
- Windows applications
- rich client applications
- .NET applications, Windows applications
- Visual Basic code, creating applications
- Visual C#, creating applications
- client/server applications, Windows applications
ms.assetid: 2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4cfc8a0f176e3732e7fe6f088c9973bfbcdaf89a
ms.sourcegitcommit: f28752eab00d2bd97e971542c0f49ce63cfbc239
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2018
---
# <a name="developing-client-applications-with-the-net-framework"></a><span data-ttu-id="0fdfe-102">Wdrażanie aplikacji klienta za pomocą programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="0fdfe-102">Developing client applications with the .NET Framework</span></span>

<span data-ttu-id="0fdfe-103">Istnieje kilka sposobów tworzenia aplikacji opartych na systemie Windows za pomocą programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0fdfe-103">There are several ways to develop Windows-based applications with the .NET Framework.</span></span> <span data-ttu-id="0fdfe-104">Można użyć dowolnej z tych narzędzi i platform:</span><span class="sxs-lookup"><span data-stu-id="0fdfe-104">You can use any of these tools and frameworks:</span></span> 

* [<span data-ttu-id="0fdfe-105">Platforma uniwersalna systemu Windows (UWP)</span><span class="sxs-lookup"><span data-stu-id="0fdfe-105">Universal Windows Platform (UWP)</span></span>](https://developer.microsoft.com/windows/apps)
* [<span data-ttu-id="0fdfe-106">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="0fdfe-106">Windows Presentation Foundation (WPF)</span></span>](../../docs/framework/wpf/index.md)
* [<span data-ttu-id="0fdfe-107">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0fdfe-107">Windows Forms</span></span>](../../docs/framework/winforms/index.md)

<span data-ttu-id="0fdfe-108">Ta sekcja zawiera tematy, które opisują sposób tworzenia aplikacji systemu Windows przy użyciu technologii Windows Presentation Foundation lub za pomocą formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="0fdfe-108">This section contains topics that describe how to create Windows-based applications by using Windows Presentation Foundation or by using Windows Forms.</span></span> <span data-ttu-id="0fdfe-109">Jednak również można utworzyć aplikacji sieci web przy użyciu programu .NET Framework i aplikacji klienckich dla komputerów lub urządzeń, które mają być dostępne za pośrednictwem Microsoft Store.</span><span class="sxs-lookup"><span data-stu-id="0fdfe-109">However, you can also create web applications using the .NET Framework, and client applications for computers or devices that you make available through the Microsoft Store.</span></span>
 
## <a name="in-this-section"></a><span data-ttu-id="0fdfe-110">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="0fdfe-110">In this section</span></span>

[<span data-ttu-id="0fdfe-111">Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="0fdfe-111">Windows Presentation Foundation</span></span>](../../docs/framework/wpf/index.md)  
<span data-ttu-id="0fdfe-112">Zawiera informacje dotyczące tworzenia aplikacji przy użyciu WPF.</span><span class="sxs-lookup"><span data-stu-id="0fdfe-112">Provides information about developing applications by using WPF.</span></span>

[<span data-ttu-id="0fdfe-113">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0fdfe-113">Windows Forms</span></span>](../../docs/framework/winforms/index.md)  
<span data-ttu-id="0fdfe-114">Zawiera informacje dotyczące tworzenia aplikacji za pomocą formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="0fdfe-114">Provides information about developing applications by using Windows Forms.</span></span>

[<span data-ttu-id="0fdfe-115">Typowe technologie klienckie</span><span class="sxs-lookup"><span data-stu-id="0fdfe-115">Common Client Technologies</span></span>](../../docs/framework/common-client-technologies/index.md)  
<span data-ttu-id="0fdfe-116">Zawiera informacje o dodatkowych technologii, które mogą być używane podczas tworzenia aplikacji klienckich.</span><span class="sxs-lookup"><span data-stu-id="0fdfe-116">Provides information about additional technologies that can be used when developing client applications.</span></span>

## <a name="related-sections"></a><span data-ttu-id="0fdfe-117">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="0fdfe-117">Related sections</span></span>

[<span data-ttu-id="0fdfe-118">Platforma uniwersalna systemu Windows</span><span class="sxs-lookup"><span data-stu-id="0fdfe-118">Universal Windows Platform</span></span>](https://developer.microsoft.com/windows/apps)  
<span data-ttu-id="0fdfe-119">Opisuje sposób tworzenia aplikacji dla systemu Windows 10, które można udostępnić użytkownikom za pośrednictwem Sklepu Windows.</span><span class="sxs-lookup"><span data-stu-id="0fdfe-119">Describes how to create applications for Windows 10 that you can make available to users through the Windows Store.</span></span>

[<span data-ttu-id="0fdfe-120">Platforma .NET dla aplikacji platformy uniwersalnej systemu Windows</span><span class="sxs-lookup"><span data-stu-id="0fdfe-120">.NET for UWP apps</span></span>](https://msdn.microsoft.com/library/windows/apps/mt185501.aspx)  
<span data-ttu-id="0fdfe-121">Zawiera opis programu .NET Framework obsługę aplikacji ze sklepu, które można wdrożyć na komputerach z systemem Windows i urządzeń.</span><span class="sxs-lookup"><span data-stu-id="0fdfe-121">Describes the .NET Framework support for Store apps, which can be deployed to Windows computers and devices.</span></span>

<span data-ttu-id="0fdfe-122">[Interfejs API .NET dla programu Windows Phone Silverlight](https://docs.microsoft.com/en-us/previous-versions/windows/apps/jj207211\(v=vs.105\))</span><span class="sxs-lookup"><span data-stu-id="0fdfe-122">[.NET API for Windows Phone Silverlight](https://docs.microsoft.com/en-us/previous-versions/windows/apps/jj207211\(v=vs.105\))</span></span>  
<span data-ttu-id="0fdfe-123">Wyświetla listę interfejsów API architektury .NET Framework służy do tworzenia aplikacji w usłudze Windows Phone Silverlight.</span><span class="sxs-lookup"><span data-stu-id="0fdfe-123">Lists the .NET Framework APIs you can use for building apps with Windows Phone Silverlight.</span></span>
  
[<span data-ttu-id="0fdfe-124">Tworzenie aplikacji dla wielu platform</span><span class="sxs-lookup"><span data-stu-id="0fdfe-124">Developing for Multiple Platforms</span></span>](../../docs/standard/cross-platform/index.md)  
<span data-ttu-id="0fdfe-125">Zawiera opis różnych metod, można użyć programu .NET Framework pod kątem wielu typów aplikacji klienta.</span><span class="sxs-lookup"><span data-stu-id="0fdfe-125">Describes the different methods you can use the .NET Framework to target multiple client app types.</span></span>

[<span data-ttu-id="0fdfe-126">Rozpoczynanie pracy z witryny sieci Web ASP.NET</span><span class="sxs-lookup"><span data-stu-id="0fdfe-126">Get Started with ASP.NET Web Sites</span></span>](http://www.asp.net/get-started/websites)  
<span data-ttu-id="0fdfe-127">Opisuje sposoby można tworzyć aplikacje sieci web za pomocą programu ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="0fdfe-127">Describes the ways you can develop web apps using ASP.NET.</span></span>

## <a name="see-also"></a><span data-ttu-id="0fdfe-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0fdfe-128">See also</span></span>

[<span data-ttu-id="0fdfe-129">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="0fdfe-129">.NET Standard</span></span>](../../docs/standard/net-standard.md)  
[<span data-ttu-id="0fdfe-130">Omówienie</span><span class="sxs-lookup"><span data-stu-id="0fdfe-130">Overview</span></span>](../../docs/framework/get-started/overview.md)  
[<span data-ttu-id="0fdfe-131">Podręcznik programowania</span><span class="sxs-lookup"><span data-stu-id="0fdfe-131">Development Guide</span></span>](../../docs/framework/development-guide.md)  
[<span data-ttu-id="0fdfe-132">Aplikacje usług systemu Windows</span><span class="sxs-lookup"><span data-stu-id="0fdfe-132">Windows Service Applications</span></span>](../../docs/framework/windows-services/index.md)  
