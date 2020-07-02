---
title: Tworzenie aplikacji klienckich opartych na systemie Windows za pomocą .NET Framework
description: Opracowywanie aplikacji opartych na systemie Windows przy użyciu platformy .NET. Można użyć platforma uniwersalna systemu Windows (platformy UWP), Windows Presentation Foundation (WPF) lub Windows Forms.
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
ms.openlocfilehash: 5920ecfae60274a8a504e4d300e531fd8b512901
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619393"
---
# <a name="develop-client-applications-with-net-framework"></a><span data-ttu-id="3cfa2-104">Tworzenie aplikacji klienckich za pomocą .NET Framework</span><span class="sxs-lookup"><span data-stu-id="3cfa2-104">Develop client applications with .NET Framework</span></span>

<span data-ttu-id="3cfa2-105">Istnieje kilka sposobów tworzenia aplikacji opartych na systemie Windows przy użyciu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3cfa2-105">There are several ways to develop Windows-based applications with .NET Framework.</span></span> <span data-ttu-id="3cfa2-106">Można użyć dowolnego z tych narzędzi i platform:</span><span class="sxs-lookup"><span data-stu-id="3cfa2-106">You can use any of these tools and frameworks:</span></span>

- [<span data-ttu-id="3cfa2-107">Platforma uniwersalna systemu Windows (UWP)</span><span class="sxs-lookup"><span data-stu-id="3cfa2-107">Universal Windows Platform (UWP)</span></span>](/windows/uwp/)
- [<span data-ttu-id="3cfa2-108">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="3cfa2-108">Windows Presentation Foundation (WPF)</span></span>](./wpf/index.md)
- [<span data-ttu-id="3cfa2-109">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3cfa2-109">Windows Forms</span></span>](./winforms/index.md)

<span data-ttu-id="3cfa2-110">Ta sekcja zawiera artykuły opisujące sposób tworzenia aplikacji opartych na systemie Windows przy użyciu Windows Presentation Foundation lub Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="3cfa2-110">This section contains articles that describe how to create Windows-based applications by using Windows Presentation Foundation or Windows Forms.</span></span> <span data-ttu-id="3cfa2-111">Można jednak tworzyć aplikacje sieci Web przy użyciu .NET Framework i aplikacji klienckich dla komputerów lub urządzeń udostępnianych za pośrednictwem Microsoft Store (aplikacje platformy UWP).</span><span class="sxs-lookup"><span data-stu-id="3cfa2-111">However, you can also create web applications using .NET Framework and client applications for computers or devices that you make available through Microsoft Store (UWP apps).</span></span>

## <a name="related-sections"></a><span data-ttu-id="3cfa2-112">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="3cfa2-112">Related sections</span></span>

<span data-ttu-id="3cfa2-113">[platforma uniwersalna systemu Windows](/windows/uwp/)</span><span class="sxs-lookup"><span data-stu-id="3cfa2-113">[Universal Windows Platform](/windows/uwp/)</span></span>\
<span data-ttu-id="3cfa2-114">Opisuje sposób tworzenia aplikacji platformy UWP, które mogą być dostępne dla użytkowników za poorednictwem Microsoft Store.</span><span class="sxs-lookup"><span data-stu-id="3cfa2-114">Describes how to create UWP applications that you can make available to users through Microsoft Store.</span></span>

<span data-ttu-id="3cfa2-115">[Interfejs API platformy .NET dla aplikacji platformy UWP](/dotnet/api/index?view=dotnet-uwp-10.0)</span><span class="sxs-lookup"><span data-stu-id="3cfa2-115">[.NET API for UWP apps](/dotnet/api/index?view=dotnet-uwp-10.0)</span></span>\
<span data-ttu-id="3cfa2-116">Dokumentacja dla typów .NET, które obsługują aplikacje platformy UWP.</span><span class="sxs-lookup"><span data-stu-id="3cfa2-116">Reference for .NET types that support UWP apps.</span></span>
  
<span data-ttu-id="3cfa2-117">[Programowanie dla wielu platform](../standard/cross-platform/index.md)</span><span class="sxs-lookup"><span data-stu-id="3cfa2-117">[Develop for Multiple Platforms](../standard/cross-platform/index.md)</span></span>\
<span data-ttu-id="3cfa2-118">W tym artykule opisano różne metody, których można użyć .NET Framework do określania wielu typów aplikacji klienckich.</span><span class="sxs-lookup"><span data-stu-id="3cfa2-118">Describes the different methods you can use .NET Framework to target multiple client app types.</span></span>

<span data-ttu-id="3cfa2-119">[Wprowadzenie do witryn sieci Web ASP.NET](https://dotnet.microsoft.com/apps/aspnet/web-apps)</span><span class="sxs-lookup"><span data-stu-id="3cfa2-119">[Get Started with ASP.NET Web Sites](https://dotnet.microsoft.com/apps/aspnet/web-apps)</span></span>\
<span data-ttu-id="3cfa2-120">Opisuje sposoby opracowywania aplikacji sieci Web przy użyciu usługi ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="3cfa2-120">Describes the ways you can develop web apps using ASP.NET.</span></span>

<span data-ttu-id="3cfa2-121">[Interfejs API platformy .NET dla Windows Phone Silverlight](https://docs.microsoft.com/previous-versions/windows/apps/jj207211\(v=vs.105\))</span><span class="sxs-lookup"><span data-stu-id="3cfa2-121">[.NET API for Windows Phone Silverlight](https://docs.microsoft.com/previous-versions/windows/apps/jj207211\(v=vs.105\))</span></span>\
<span data-ttu-id="3cfa2-122">Wyświetla listę .NET Framework interfejsów API, których można użyć do kompilowania aplikacji przy użyciu Windows Phone Silverlight.</span><span class="sxs-lookup"><span data-stu-id="3cfa2-122">Lists .NET Framework APIs you can use for building apps with Windows Phone Silverlight.</span></span>

## <a name="see-also"></a><span data-ttu-id="3cfa2-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3cfa2-123">See also</span></span>

- [<span data-ttu-id="3cfa2-124">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="3cfa2-124">.NET Standard</span></span>](../standard/net-standard.md)
- [<span data-ttu-id="3cfa2-125">Omówienie</span><span class="sxs-lookup"><span data-stu-id="3cfa2-125">Overview</span></span>](./get-started/overview.md)
- [<span data-ttu-id="3cfa2-126">Przewodnik programowania</span><span class="sxs-lookup"><span data-stu-id="3cfa2-126">Development Guide</span></span>](./development-guide.md)
- [<span data-ttu-id="3cfa2-127">Aplikacje usług systemu Windows</span><span class="sxs-lookup"><span data-stu-id="3cfa2-127">Windows Service Applications</span></span>](./windows-services/index.md)
