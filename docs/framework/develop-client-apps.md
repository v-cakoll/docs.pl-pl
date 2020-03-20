---
title: Tworzenie aplikacji klienckich opartych na systemie Windows za pomocą programu .NET Framework
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
ms.openlocfilehash: b6b5f47980e7c0c87128b9efb782e637ed7144f4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79181636"
---
# <a name="develop-client-applications-with-net-framework"></a><span data-ttu-id="076c0-102">Tworzenie aplikacji klienckich za pomocą programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="076c0-102">Develop client applications with .NET Framework</span></span>

<span data-ttu-id="076c0-103">Istnieje kilka sposobów tworzenia aplikacji opartych na systemie Windows za pomocą programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="076c0-103">There are several ways to develop Windows-based applications with .NET Framework.</span></span> <span data-ttu-id="076c0-104">Można użyć dowolnego z następujących narzędzi i struktur:</span><span class="sxs-lookup"><span data-stu-id="076c0-104">You can use any of these tools and frameworks:</span></span>

- [<span data-ttu-id="076c0-105">Platforma uniwersalna systemu Windows (UWP)</span><span class="sxs-lookup"><span data-stu-id="076c0-105">Universal Windows Platform (UWP)</span></span>](/windows/uwp/)
- [<span data-ttu-id="076c0-106">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="076c0-106">Windows Presentation Foundation (WPF)</span></span>](./wpf/index.md)
- [<span data-ttu-id="076c0-107">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="076c0-107">Windows Forms</span></span>](./winforms/index.md)

<span data-ttu-id="076c0-108">Ta sekcja zawiera artykuły opisujące sposób tworzenia aplikacji opartych na systemie Windows przy użyciu programu Windows Presentation Foundation lub Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="076c0-108">This section contains articles that describe how to create Windows-based applications by using Windows Presentation Foundation or Windows Forms.</span></span> <span data-ttu-id="076c0-109">Można jednak również tworzyć aplikacje sieci Web przy użyciu programu .NET Framework i aplikacji klienckich dla komputerów lub urządzeń udostępnianych za pośrednictwem sklepu Microsoft Store (aplikacje platformy uniwersalnej systemu Windows).</span><span class="sxs-lookup"><span data-stu-id="076c0-109">However, you can also create web applications using .NET Framework and client applications for computers or devices that you make available through Microsoft Store (UWP apps).</span></span>

## <a name="related-sections"></a><span data-ttu-id="076c0-110">Powiązane sekcje</span><span class="sxs-lookup"><span data-stu-id="076c0-110">Related sections</span></span>

<span data-ttu-id="076c0-111">[Uniwersalna platforma systemu Windows](/windows/uwp/)</span><span class="sxs-lookup"><span data-stu-id="076c0-111">[Universal Windows Platform](/windows/uwp/)</span></span>\
<span data-ttu-id="076c0-112">W tym artykule opisano sposób tworzenia aplikacji platformy uniwersalnej systemu i platformy uniwersalnej systemu, które można udostępnić użytkownikom za pośrednictwem sklepu Microsoft Store.</span><span class="sxs-lookup"><span data-stu-id="076c0-112">Describes how to create UWP applications that you can make available to users through Microsoft Store.</span></span>

<span data-ttu-id="076c0-113">[Interfejs API platformy .NET dla aplikacji platformy uniwersalnej systemu Windows](/dotnet/api/index?view=dotnet-uwp-10.0)</span><span class="sxs-lookup"><span data-stu-id="076c0-113">[.NET API for UWP apps](/dotnet/api/index?view=dotnet-uwp-10.0)</span></span>\
<span data-ttu-id="076c0-114">Odwołanie do typów platformy .NET, które obsługują aplikacje platformy uniwersalnej systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="076c0-114">Reference for .NET types that support UWP apps.</span></span>
  
<span data-ttu-id="076c0-115">[Tworzenie dla wielu platform](../standard/cross-platform/index.md)</span><span class="sxs-lookup"><span data-stu-id="076c0-115">[Develop for Multiple Platforms](../standard/cross-platform/index.md)</span></span>\
<span data-ttu-id="076c0-116">W tym artykule opisano różne metody, za pomocą programu .NET Framework do kierowania wielu typów aplikacji klienckich.</span><span class="sxs-lookup"><span data-stu-id="076c0-116">Describes the different methods you can use .NET Framework to target multiple client app types.</span></span>

<span data-ttu-id="076c0-117">[Wprowadzenie do ASP.NET witryn sieci Web](https://dotnet.microsoft.com/apps/aspnet/web-apps)</span><span class="sxs-lookup"><span data-stu-id="076c0-117">[Get Started with ASP.NET Web Sites](https://dotnet.microsoft.com/apps/aspnet/web-apps)</span></span>\
<span data-ttu-id="076c0-118">W tym artykule opisano sposoby tworzenia aplikacji sieci Web przy użyciu ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="076c0-118">Describes the ways you can develop web apps using ASP.NET.</span></span>

<span data-ttu-id="076c0-119">[Interfejs API platformy .NET dla systemu Windows Phone Silverlight](https://docs.microsoft.com/previous-versions/windows/apps/jj207211\(v=vs.105\))</span><span class="sxs-lookup"><span data-stu-id="076c0-119">[.NET API for Windows Phone Silverlight](https://docs.microsoft.com/previous-versions/windows/apps/jj207211\(v=vs.105\))</span></span>\
<span data-ttu-id="076c0-120">Wyświetla listę interfejsów API programu .NET Framework, których można używać do tworzenia aplikacji za pomocą programu Windows Phone Silverlight.</span><span class="sxs-lookup"><span data-stu-id="076c0-120">Lists .NET Framework APIs you can use for building apps with Windows Phone Silverlight.</span></span>

## <a name="see-also"></a><span data-ttu-id="076c0-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="076c0-121">See also</span></span>

- [<span data-ttu-id="076c0-122">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="076c0-122">.NET Standard</span></span>](../standard/net-standard.md)
- [<span data-ttu-id="076c0-123">Przegląd</span><span class="sxs-lookup"><span data-stu-id="076c0-123">Overview</span></span>](./get-started/overview.md)
- [<span data-ttu-id="076c0-124">Podręcznik programowania</span><span class="sxs-lookup"><span data-stu-id="076c0-124">Development Guide</span></span>](./development-guide.md)
- [<span data-ttu-id="076c0-125">Aplikacje usług systemu Windows</span><span class="sxs-lookup"><span data-stu-id="076c0-125">Windows Service Applications</span></span>](./windows-services/index.md)
