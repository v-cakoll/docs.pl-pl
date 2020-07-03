---
title: Wprowadzenie
description: Tworzenie aplikacji klienckich dla komputerów stacjonarnych za pomocą struktury interfejsu użytkownika Windows Presentation Foundation (WPF), podzestawu .NET Framework.
ms.date: 01/26/2018
helpviewer_keywords:
- getting started [WPF]
- introduction [WPF]
- WPF [WPF], getting started
ms.assetid: 04f91da8-708c-46c7-8172-f1695ec847cd
ms.openlocfilehash: 2977831bf17ac11a67f71037d26e4f4665131721
ms.sourcegitcommit: b6a1869f97a37f11a68c90afde1a520a6887dcbc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2020
ms.locfileid: "85853853"
---
# <a name="get-started-wpf"></a><span data-ttu-id="bf714-103">Wprowadzenie (WPF)</span><span class="sxs-lookup"><span data-stu-id="bf714-103">Get started (WPF)</span></span>

<span data-ttu-id="bf714-104">Windows Presentation Foundation (WPF) to struktura interfejsu użytkownika, która tworzy aplikacje klienckie dla komputerów stacjonarnych.</span><span class="sxs-lookup"><span data-stu-id="bf714-104">Windows Presentation Foundation (WPF) is a UI framework that creates desktop client applications.</span></span> <span data-ttu-id="bf714-105">Platforma programistyczna WPF obsługuje szeroką gamę funkcji tworzenia aplikacji, takich jak model aplikacji, zasoby, formanty, grafika, układ, powiązanie danych, dokumenty i zabezpieczenia.</span><span class="sxs-lookup"><span data-stu-id="bf714-105">The WPF development platform supports a broad set of application development features, including an application model, resources, controls, graphics, layout, data binding, documents, and security.</span></span> <span data-ttu-id="bf714-106">Jest to podzestaw .NET Framework, więc jeśli wcześniej skompilowano aplikacje z .NET Framework przy użyciu ASP.NET lub Windows Forms, środowisko programistyczne powinno być znane.</span><span class="sxs-lookup"><span data-stu-id="bf714-106">It is a subset of the .NET Framework, so if you have previously built applications with the .NET Framework using ASP.NET or Windows Forms, the programming experience should be familiar.</span></span> <span data-ttu-id="bf714-107">WPF używa Extensible Application Markup Language (XAML), aby zapewnić deklaratywny model dla programowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bf714-107">WPF uses the Extensible Application Markup Language (XAML) to provide a declarative model for application programming.</span></span> <span data-ttu-id="bf714-108">Ta sekcja zawiera tematy, które wprowadzają i ułatwiają rozpoczęcie pracy z programem WPF.</span><span class="sxs-lookup"><span data-stu-id="bf714-108">This section has topics that introduce and help you get started with WPF.</span></span>  
  
## <a name="where-should-i-start"></a><span data-ttu-id="bf714-109">Gdzie należy zacząć?</span><span class="sxs-lookup"><span data-stu-id="bf714-109">Where should I start?</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="bf714-110">Chcę przeskoczyć do prawej strony...</span><span class="sxs-lookup"><span data-stu-id="bf714-110">I want to jump right in…</span></span>|[<span data-ttu-id="bf714-111">Przewodnik: moja pierwsza aplikacja klasyczna WPF</span><span class="sxs-lookup"><span data-stu-id="bf714-111">Walkthrough: My first WPF desktop application</span></span>](walkthrough-my-first-wpf-desktop-application.md)|  
|<span data-ttu-id="bf714-112">Jak mogę Projektowanie interfejsu użytkownika aplikacji?</span><span class="sxs-lookup"><span data-stu-id="bf714-112">How do I design the application UI?</span></span>|[<span data-ttu-id="bf714-113">Projektowanie XAML w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="bf714-113">Designing XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)|  
|<span data-ttu-id="bf714-114">Jesteś nowym w programie .NET?</span><span class="sxs-lookup"><span data-stu-id="bf714-114">New to .NET?</span></span>|[<span data-ttu-id="bf714-115">Przegląd programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="bf714-115">Overview of the .NET Framework</span></span>](../../get-started/overview.md)<br /><br /> [<span data-ttu-id="bf714-116">Wprowadzenie do korzystania z Visual C# i Visual Basic</span><span class="sxs-lookup"><span data-stu-id="bf714-116">Getting Started with Visual C# and Visual Basic</span></span>](/visualstudio/ide/quickstart-visual-basic-console)|  
|<span data-ttu-id="bf714-117">Więcej informacji na temat platformy WPF...</span><span class="sxs-lookup"><span data-stu-id="bf714-117">Tell me more about WPF…</span></span>|[<span data-ttu-id="bf714-118">Wprowadzenie do platformy WPF w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="bf714-118">Introduction to WPF in Visual Studio</span></span>](introduction-to-wpf-in-vs.md)<br /><br /> [<span data-ttu-id="bf714-119">Omówienie XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="bf714-119">XAML Overview (WPF)</span></span>](../../../desktop-wpf/fundamentals/xaml.md)<br /><br /> [<span data-ttu-id="bf714-120">Formanty</span><span class="sxs-lookup"><span data-stu-id="bf714-120">Controls</span></span>](../controls/index.md)<br /><br /> [<span data-ttu-id="bf714-121">Przegląd powiązań danych</span><span class="sxs-lookup"><span data-stu-id="bf714-121">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)|  
|<span data-ttu-id="bf714-122">Jesteś deweloperem Windows Forms?</span><span class="sxs-lookup"><span data-stu-id="bf714-122">Are you a Windows Forms developer?</span></span>|[<span data-ttu-id="bf714-123">Kontrolki Windows Forms i ekwiwalentne kontrolki WPF</span><span class="sxs-lookup"><span data-stu-id="bf714-123">Windows Forms Controls and Equivalent WPF Controls</span></span>](../advanced/windows-forms-controls-and-equivalent-wpf-controls.md)<br /><br /> [<span data-ttu-id="bf714-124">Współdziałanie WPF i Windows Forms</span><span class="sxs-lookup"><span data-stu-id="bf714-124">WPF and Windows Forms Interoperation</span></span>](../advanced/wpf-and-windows-forms-interoperation.md)|  
  
## <a name="see-also"></a><span data-ttu-id="bf714-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bf714-125">See also</span></span>

- [<span data-ttu-id="bf714-126">Biblioteka klas</span><span class="sxs-lookup"><span data-stu-id="bf714-126">Class Library</span></span>](../class-library-wpf.md)
- [<span data-ttu-id="bf714-127">Opracowywanie aplikacji</span><span class="sxs-lookup"><span data-stu-id="bf714-127">Application Development</span></span>](../app-development/index.md)
- [<span data-ttu-id="bf714-128">Centrum deweloperów .NET Framework</span><span class="sxs-lookup"><span data-stu-id="bf714-128">.NET Framework Developer Center</span></span>](https://dotnet.microsoft.com)
