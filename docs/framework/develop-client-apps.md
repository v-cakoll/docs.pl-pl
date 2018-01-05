---
title: "Wdrażanie aplikacji klienta za pomocą programu .NET Framework"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
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
caps.latest.revision: "24"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1f90cbac0e7f78d8965a75df281c0db6b213d9e4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="developing-client-applications-with-the-net-framework"></a><span data-ttu-id="31793-102">Wdrażanie aplikacji klienta za pomocą programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="31793-102">Developing Client Applications with the .NET Framework</span></span>
<span data-ttu-id="31793-103">Istnieje wiele sposobów tworzenia aplikacji opartych na systemie Windows w środowisku .NET Framework uruchamiane lokalnie na komputerach użytkowników lub urządzeń.</span><span class="sxs-lookup"><span data-stu-id="31793-103">There are multiple ways to develop Windows-based applications with the .NET framework that run locally on users' computers or devices.</span></span> <span data-ttu-id="31793-104">Ta sekcja zawiera tematy, które opisują sposób tworzenia aplikacji systemu Windows przy użyciu systemu Windows Presentation Foundation (WPF) lub za pomocą formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="31793-104">This section contains topics that describe how to create Windows-based applications by using Windows Presentation Foundation (WPF) or by using Windows Forms.</span></span> <span data-ttu-id="31793-105">Jednak również można utworzyć aplikacji sieci web przy użyciu programu .NET Framework i aplikacji klienckich dla komputerów lub urządzeń, które mają być dostępne za pośrednictwem Sklepu Windows lub Sklepu Windows Phone.</span><span class="sxs-lookup"><span data-stu-id="31793-105">However, you can also create web applications using the .NET Framework, and client applications for computers or devices that you make available through the Windows Store or Windows Phone Store.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="31793-106">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="31793-106">In This Section</span></span>  
 [<span data-ttu-id="31793-107">Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="31793-107">Windows Presentation Foundation</span></span>](../../docs/framework/wpf/index.md)  
 <span data-ttu-id="31793-108">Zawiera informacje dotyczące tworzenia aplikacji przy użyciu WPF.</span><span class="sxs-lookup"><span data-stu-id="31793-108">Provides information about developing applications by using WPF.</span></span>  
  
 [<span data-ttu-id="31793-109">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="31793-109">Windows Forms</span></span>](../../docs/framework/winforms/index.md)  
 <span data-ttu-id="31793-110">Zawiera informacje dotyczące tworzenia aplikacji za pomocą formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="31793-110">Provides information about developing applications by using Windows Forms.</span></span>  
  
 [<span data-ttu-id="31793-111">Typowe technologie klienckie</span><span class="sxs-lookup"><span data-stu-id="31793-111">Common Client Technologies</span></span>](../../docs/framework/common-client-technologies/index.md)  
 <span data-ttu-id="31793-112">Zawiera informacje o dodatkowych technologii, które mogą być używane podczas tworzenia aplikacji klienckich.</span><span class="sxs-lookup"><span data-stu-id="31793-112">Provides information about additional technologies that can be used when developing client applications.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="31793-113">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="31793-113">Related Sections</span></span>  
 [<span data-ttu-id="31793-114">Aplikacje ze Sklepu Windows</span><span class="sxs-lookup"><span data-stu-id="31793-114">Windows Store apps</span></span>](http://msdn.microsoft.com/windows/apps/)  
 <span data-ttu-id="31793-115">Opisuje sposób tworzenia aplikacji, które można udostępnić użytkownikom za pośrednictwem Sklepu Windows</span><span class="sxs-lookup"><span data-stu-id="31793-115">Describes how to create apps that you can make available to users through the Windows Store</span></span>  
  
 [<span data-ttu-id="31793-116">Platforma .NET dla aplikacji ze sklepu</span><span class="sxs-lookup"><span data-stu-id="31793-116">.NET for Store apps</span></span>](http://msdn.microsoft.com/library/windows/apps/br230302.aspx)  
 <span data-ttu-id="31793-117">Zawiera opis programu .NET Framework obsługę aplikacji ze sklepu, które można wdrożyć na komputerach z systemem Windows i urządzeń.</span><span class="sxs-lookup"><span data-stu-id="31793-117">Describes the .NET Framework support for Store apps, which can be deployed to Windows computers and devices.</span></span>  
  
 <span data-ttu-id="31793-118">[Interfejs API .NET dla programu Windows Phone Silverlight](http://msdn.microsoft.com/library/windows/apps/xaml/jj207211\(v=vs.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="31793-118">[.NET API for Windows Phone Silverlight](http://msdn.microsoft.com/library/windows/apps/xaml/jj207211\(v=vs.105\).aspx)</span></span>  
 <span data-ttu-id="31793-119">Lista interfejsów API architektury .NET Framework służy do tworzenia aplikacji w usłudze Windows Phone Silverlight</span><span class="sxs-lookup"><span data-stu-id="31793-119">List the .NET Framework APIs you can use for building apps with Windows Phone Silverlight</span></span>  
  
 [<span data-ttu-id="31793-120">Tworzenie aplikacji dla wielu platform</span><span class="sxs-lookup"><span data-stu-id="31793-120">Developing for Multiple Platforms</span></span>](../../docs/standard/cross-platform/index.md)  
 <span data-ttu-id="31793-121">Zawiera opis różnych metod, można użyć programu .NET Framework pod kątem wielu typów aplikacji klienta.</span><span class="sxs-lookup"><span data-stu-id="31793-121">Describes the different methods you can use the .NET Framework to target multiple client app types.</span></span>  
  
 [<span data-ttu-id="31793-122">Rozpoczynanie pracy z witryny sieci Web ASP.NET</span><span class="sxs-lookup"><span data-stu-id="31793-122">Get Started with ASP.NET Web Sites</span></span>](http://www.asp.net/get-started/websites)  
 <span data-ttu-id="31793-123">Opisuje sposoby można tworzyć aplikacje sieci web za pomocą programu ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="31793-123">Describes the ways you can develop web apps using ASP.NET.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31793-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="31793-124">See Also</span></span>  
 [<span data-ttu-id="31793-125">Biblioteka klas przenośnych</span><span class="sxs-lookup"><span data-stu-id="31793-125">Portable Class Library</span></span>](../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md)  
 [<span data-ttu-id="31793-126">Omówienie</span><span class="sxs-lookup"><span data-stu-id="31793-126">Overview</span></span>](../../docs/framework/get-started/overview.md)  
 [<span data-ttu-id="31793-127">Podręcznik programowania</span><span class="sxs-lookup"><span data-stu-id="31793-127">Development Guide</span></span>](../../docs/framework/development-guide.md)  
 [<span data-ttu-id="31793-128">Porady: tworzenie aplikacji pulpitu systemu Windows</span><span class="sxs-lookup"><span data-stu-id="31793-128">How to: Create a Windows Desktop Application</span></span>](http://msdn.microsoft.com/library/47021403-eaca-4c34-946a-a26c42a64148)  
 [<span data-ttu-id="31793-129">Aplikacje usług systemu Windows</span><span class="sxs-lookup"><span data-stu-id="31793-129">Windows Service Applications</span></span>](../../docs/framework/windows-services/index.md)
