---
title: Tworzenie aplikacji klienckich z systemem Windows za pomocą programu .NET Framework
ms.date: 01/09/2018
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
ms.openlocfilehash: 987f8e25014e8ce6413c998f6eb78d821558ecec
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43518667"
---
# <a name="developing-client-applications-with-the-net-framework"></a><span data-ttu-id="cb187-102">Wdrażanie aplikacji klienta za pomocą programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="cb187-102">Developing client applications with the .NET Framework</span></span>

<span data-ttu-id="cb187-103">Istnieje kilka sposobów na opracowywanie aplikacji opartych na Windows za pomocą programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="cb187-103">There are several ways to develop Windows-based applications with the .NET Framework.</span></span> <span data-ttu-id="cb187-104">Można użyć dowolnego z tych narzędzi i platform:</span><span class="sxs-lookup"><span data-stu-id="cb187-104">You can use any of these tools and frameworks:</span></span> 

* [<span data-ttu-id="cb187-105">Platforma uniwersalna systemu Windows (UWP)</span><span class="sxs-lookup"><span data-stu-id="cb187-105">Universal Windows Platform (UWP)</span></span>](https://developer.microsoft.com/windows/apps)
* [<span data-ttu-id="cb187-106">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="cb187-106">Windows Presentation Foundation (WPF)</span></span>](../../docs/framework/wpf/index.md)
* [<span data-ttu-id="cb187-107">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="cb187-107">Windows Forms</span></span>](../../docs/framework/winforms/index.md)

<span data-ttu-id="cb187-108">Ta sekcja zawiera tematy, które opisują sposób tworzenia aplikacji systemu Windows za pomocą programu Windows Presentation Foundation lub za pomocą formularzy Windows.</span><span class="sxs-lookup"><span data-stu-id="cb187-108">This section contains topics that describe how to create Windows-based applications by using Windows Presentation Foundation or by using Windows Forms.</span></span> <span data-ttu-id="cb187-109">Jednak również można utworzyć aplikacji sieci web przy użyciu programu .NET Framework i aplikacji klienckich dla komputerów lub urządzeń, które mają być dostępne za pośrednictwem Microsoft Store.</span><span class="sxs-lookup"><span data-stu-id="cb187-109">However, you can also create web applications using the .NET Framework, and client applications for computers or devices that you make available through the Microsoft Store.</span></span>
 
## <a name="in-this-section"></a><span data-ttu-id="cb187-110">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="cb187-110">In this section</span></span>

[<span data-ttu-id="cb187-111">Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="cb187-111">Windows Presentation Foundation</span></span>](../../docs/framework/wpf/index.md)  
<span data-ttu-id="cb187-112">Zawiera informacje dotyczące tworzenia aplikacji za pomocą WPF.</span><span class="sxs-lookup"><span data-stu-id="cb187-112">Provides information about developing applications by using WPF.</span></span>

[<span data-ttu-id="cb187-113">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="cb187-113">Windows Forms</span></span>](../../docs/framework/winforms/index.md)  
<span data-ttu-id="cb187-114">Zawiera informacje dotyczące tworzenia aplikacji za pomocą Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="cb187-114">Provides information about developing applications by using Windows Forms.</span></span>

[<span data-ttu-id="cb187-115">Typowe technologie klienckie</span><span class="sxs-lookup"><span data-stu-id="cb187-115">Common Client Technologies</span></span>](../../docs/framework/common-client-technologies/index.md)  
<span data-ttu-id="cb187-116">Zawiera informacje o dodatkowych technologiach, które mogą być używane podczas tworzenia aplikacji klienckich.</span><span class="sxs-lookup"><span data-stu-id="cb187-116">Provides information about additional technologies that can be used when developing client applications.</span></span>

## <a name="related-sections"></a><span data-ttu-id="cb187-117">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="cb187-117">Related sections</span></span>

[<span data-ttu-id="cb187-118">Universal Windows Platform</span><span class="sxs-lookup"><span data-stu-id="cb187-118">Universal Windows Platform</span></span>](https://developer.microsoft.com/windows/apps)  
<span data-ttu-id="cb187-119">W tym artykule opisano, jak tworzyć aplikacje dla systemu Windows 10, które można udostępnić użytkownikom za pośrednictwem usługi Windows Store.</span><span class="sxs-lookup"><span data-stu-id="cb187-119">Describes how to create applications for Windows 10 that you can make available to users through the Windows Store.</span></span>

[<span data-ttu-id="cb187-120">Platforma .NET dla aplikacji platformy uniwersalnej systemu Windows</span><span class="sxs-lookup"><span data-stu-id="cb187-120">.NET for UWP apps</span></span>](https://msdn.microsoft.com/library/windows/apps/mt185501.aspx)  
<span data-ttu-id="cb187-121">W tym artykule opisano Obsługa programu .NET Framework dla aplikacji Store, które można wdrażać w Windows, komputerów i urządzeń.</span><span class="sxs-lookup"><span data-stu-id="cb187-121">Describes the .NET Framework support for Store apps, which can be deployed to Windows computers and devices.</span></span>

<span data-ttu-id="cb187-122">[Interfejs API .NET dla systemu Windows Phone Silverlight](https://docs.microsoft.com/previous-versions/windows/apps/jj207211\(v=vs.105\))</span><span class="sxs-lookup"><span data-stu-id="cb187-122">[.NET API for Windows Phone Silverlight](https://docs.microsoft.com/previous-versions/windows/apps/jj207211\(v=vs.105\))</span></span>  
<span data-ttu-id="cb187-123">Wyświetla listę API .NET Framework, można użyć do tworzenia aplikacji za pomocą programu Windows Phone Silverlight.</span><span class="sxs-lookup"><span data-stu-id="cb187-123">Lists the .NET Framework APIs you can use for building apps with Windows Phone Silverlight.</span></span>
  
[<span data-ttu-id="cb187-124">Tworzenie aplikacji dla wielu platform</span><span class="sxs-lookup"><span data-stu-id="cb187-124">Developing for Multiple Platforms</span></span>](../../docs/standard/cross-platform/index.md)  
<span data-ttu-id="cb187-125">W tym artykule opisano różne metody, można użyć programu .NET Framework pod kątem wielu typów aplikacji klienckich.</span><span class="sxs-lookup"><span data-stu-id="cb187-125">Describes the different methods you can use the .NET Framework to target multiple client app types.</span></span>

[<span data-ttu-id="cb187-126">Rozpoczynanie pracy z witrynami sieci Web platformy ASP.NET</span><span class="sxs-lookup"><span data-stu-id="cb187-126">Get Started with ASP.NET Web Sites</span></span>](http://www.asp.net/get-started/websites)  
<span data-ttu-id="cb187-127">W tym artykule opisano sposób, możesz opracowywać aplikacje sieci web za pomocą programu ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="cb187-127">Describes the ways you can develop web apps using ASP.NET.</span></span>

## <a name="see-also"></a><span data-ttu-id="cb187-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cb187-128">See also</span></span>

[<span data-ttu-id="cb187-129">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="cb187-129">.NET Standard</span></span>](../../docs/standard/net-standard.md)  
[<span data-ttu-id="cb187-130">Omówienie</span><span class="sxs-lookup"><span data-stu-id="cb187-130">Overview</span></span>](../../docs/framework/get-started/overview.md)  
[<span data-ttu-id="cb187-131">Podręcznik programowania</span><span class="sxs-lookup"><span data-stu-id="cb187-131">Development Guide</span></span>](../../docs/framework/development-guide.md)  
[<span data-ttu-id="cb187-132">Aplikacje usług systemu Windows</span><span class="sxs-lookup"><span data-stu-id="cb187-132">Windows Service Applications</span></span>](../../docs/framework/windows-services/index.md)  
