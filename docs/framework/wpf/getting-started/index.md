---
title: Wprowadzenie (WPF)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- getting started [WPF]
- introduction [WPF]
- WPF [WPF], getting started
ms.assetid: 04f91da8-708c-46c7-8172-f1695ec847cd
caps.latest.revision: "60"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7684cb379f3cd24da008342c26e14bbf70c10d07
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="getting-started-wpf"></a><span data-ttu-id="ebf21-102">Wprowadzenie (WPF)</span><span class="sxs-lookup"><span data-stu-id="ebf21-102">Getting Started (WPF)</span></span>
<span data-ttu-id="ebf21-103">Windows Presentation Foundation (WPF) to platforma interfejsu użytkownika, która tworzy aplikacje klienta.</span><span class="sxs-lookup"><span data-stu-id="ebf21-103">Windows Presentation Foundation (WPF) is a UI framework that creates desktop client applications.</span></span> <span data-ttu-id="ebf21-104">Platformy programistycznej WPF obsługuje szeroką gamę funkcje tworzenia aplikacji, w tym modelu aplikacji, zasobów, formantów, grafiki, układ, wiązania z danymi, dokumentów i zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="ebf21-104">The WPF development platform supports a broad set of application development features, including an application model, resources, controls, graphics, layout, data binding, documents, and security.</span></span> <span data-ttu-id="ebf21-105">Jest to podzbiór platformy .NET, więc jeśli aplikacje zostały wcześniej wbudowana z programu .NET Framework za pomocą programu ASP.NET lub program Windows Forms, środowisko programowania należy się zapoznać.</span><span class="sxs-lookup"><span data-stu-id="ebf21-105">It is a subset of the .NET Framework, so if you have previously built applications with the .NET Framework using ASP.NET or Windows Forms, the programming experience should be familiar.</span></span> <span data-ttu-id="ebf21-106">WPF używa Extensible Application Markup Language (XAML), aby zapewnić deklaratywne modelu programowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ebf21-106">WPF uses the Extensible Application Markup Language (XAML) to provide a declarative model for application programming.</span></span> <span data-ttu-id="ebf21-107">Ta sekcja zawiera tematy dotyczące wprowadzić i ułatwiające rozpoczęcie pracy z użyciem WPF.</span><span class="sxs-lookup"><span data-stu-id="ebf21-107">This section has topics that introduce and help you get started with WPF.</span></span>  
  
## <a name="where-should-i-start"></a><span data-ttu-id="ebf21-108">Gdzie powinna zaczynać?</span><span class="sxs-lookup"><span data-stu-id="ebf21-108">Where Should I Start?</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ebf21-109">Chcę, aby od razu...</span><span class="sxs-lookup"><span data-stu-id="ebf21-109">I want to jump right in…</span></span>|[<span data-ttu-id="ebf21-110">Wskazówki: Pierwszy WPF pulpitu aplikację</span><span class="sxs-lookup"><span data-stu-id="ebf21-110">Walkthrough: My first WPF desktop application</span></span>](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md)|  
|<span data-ttu-id="ebf21-111">Sposób projektowania aplikacji interfejsu użytkownika?</span><span class="sxs-lookup"><span data-stu-id="ebf21-111">How do I design the application UI?</span></span>|[<span data-ttu-id="ebf21-112">Projektowanie XAML w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="ebf21-112">Designing XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)|  
|<span data-ttu-id="ebf21-113">Jesteś nowym użytkownikiem .NET?</span><span class="sxs-lookup"><span data-stu-id="ebf21-113">New to .NET?</span></span>|<span data-ttu-id="ebf21-114">[Omówienie programu .NET Framework](https://msdn.microsoft.com/en-us/library/zw4w595w\(v=vs.140\).aspx)</span><span class="sxs-lookup"><span data-stu-id="ebf21-114">[Overview of the .NET Framework](https://msdn.microsoft.com/en-us/library/zw4w595w\(v=vs.140\).aspx)</span></span><br /><br /> [<span data-ttu-id="ebf21-115">Podstawy aplikacji .NET framework</span><span class="sxs-lookup"><span data-stu-id="ebf21-115">.NET Framework Application Essentials</span></span>](../../../../docs/standard/application-essentials.md)<br /><br /> <span data-ttu-id="ebf21-116">[Wprowadzenie do języka Visual C# i Visual Basic](https://msdn.microsoft.com/en-us/library/dd492171\(v=vs.140\).aspx)</span><span class="sxs-lookup"><span data-stu-id="ebf21-116">[Getting Started with Visual C# and Visual Basic](https://msdn.microsoft.com/en-us/library/dd492171\(v=vs.140\).aspx)</span></span>|  
|<span data-ttu-id="ebf21-117">Powiedz mi więcej o WPF...</span><span class="sxs-lookup"><span data-stu-id="ebf21-117">Tell me more about WPF…</span></span>|[<span data-ttu-id="ebf21-118">Wprowadzenie do platformy WPF w programie Visual Studio 2015</span><span class="sxs-lookup"><span data-stu-id="ebf21-118">Introduction to WPF in Visual Studio 2015</span></span>](../../../../docs/framework/wpf/getting-started/introduction-to-wpf-in-vs.md)<br /><br /> [<span data-ttu-id="ebf21-119">Omówienie XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="ebf21-119">XAML Overview (WPF)</span></span>](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)<br /><br /> [<span data-ttu-id="ebf21-120">Formanty</span><span class="sxs-lookup"><span data-stu-id="ebf21-120">Controls</span></span>](../../../../docs/framework/wpf/controls/index.md)<br /><br /> [<span data-ttu-id="ebf21-121">Omówienie powiązania danych</span><span class="sxs-lookup"><span data-stu-id="ebf21-121">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)|  
|<span data-ttu-id="ebf21-122">Jesteś deweloperem formularzy systemu Windows?</span><span class="sxs-lookup"><span data-stu-id="ebf21-122">Are you a Windows Forms developer?</span></span>|[<span data-ttu-id="ebf21-123">Formanty i równoważne WPF formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="ebf21-123">Windows Forms Controls and Equivalent WPF Controls</span></span>](../../../../docs/framework/wpf/advanced/windows-forms-controls-and-equivalent-wpf-controls.md)<br /><br /> [<span data-ttu-id="ebf21-124">WPF i współdziałanie formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="ebf21-124">WPF and Windows Forms Interoperation</span></span>](../../../../docs/framework/wpf/advanced/wpf-and-windows-forms-interoperation.md)|  
  
## <a name="see-also"></a><span data-ttu-id="ebf21-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ebf21-125">See Also</span></span>  
 [<span data-ttu-id="ebf21-126">Biblioteka klas</span><span class="sxs-lookup"><span data-stu-id="ebf21-126">Class Library</span></span>](../../../../docs/framework/wpf/class-library-wpf.md)  
 [<span data-ttu-id="ebf21-127">Projektowanie aplikacji</span><span class="sxs-lookup"><span data-stu-id="ebf21-127">Application Development</span></span>](../../../../docs/framework/wpf/app-development/index.md)  
 [<span data-ttu-id="ebf21-128">Centrum deweloperów .NET framework</span><span class="sxs-lookup"><span data-stu-id="ebf21-128">.NET Framework Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=187437)
