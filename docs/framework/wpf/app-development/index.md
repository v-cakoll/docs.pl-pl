---
title: Projektowanie aplikacji
description: Dowiedz się, jak tworzyć różne aplikacje przy użyciu struktury Windows Presentation Foundation (WPF).
ms.date: 01/26/2018
helpviewer_keywords:
- WPF [WPF], about application development
- application development [WPF], about
ms.assetid: 2996ce5e-81e9-49ae-881b-952db3dd1b7e
ms.openlocfilehash: ac4227785f2fc398217b3aa8984176844264bbaa
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85613738"
---
# <a name="application-development"></a><span data-ttu-id="66a57-103">Projektowanie aplikacji</span><span class="sxs-lookup"><span data-stu-id="66a57-103">Application Development</span></span>
<a name="introduction"></a><span data-ttu-id="66a57-104">Windows Presentation Foundation (WPF) to struktura prezentacji, za pomocą której można opracowywać następujące typy aplikacji:</span><span class="sxs-lookup"><span data-stu-id="66a57-104">Windows Presentation Foundation (WPF) is a presentation framework that can be used to develop the following types of applications:</span></span>  
  
- <span data-ttu-id="66a57-105">Aplikacje autonomiczne (tradycyjne style systemu Windows skompilowane jako zestawy wykonywalne, które są instalowane i uruchamiane z komputera klienckiego).</span><span class="sxs-lookup"><span data-stu-id="66a57-105">Standalone Applications (traditional style Windows applications built as executable assemblies that are installed to and run from the client computer).</span></span>  
  
- <span data-ttu-id="66a57-106">Aplikacje przeglądarki XAML (XBAP) (aplikacje złożone z stron nawigacyjnych, które są wbudowane jako zestawy wykonywalne i obsługiwane przez przeglądarki sieci Web, takie jak Microsoft Internet Explorer lub Mozilla Firefox).</span><span class="sxs-lookup"><span data-stu-id="66a57-106">XAML browser applications (XBAPs) (applications composed of navigation pages that are built as executable assemblies and hosted by Web browsers such as Microsoft Internet Explorer or Mozilla Firefox).</span></span>  
  
- <span data-ttu-id="66a57-107">Niestandardowe biblioteki formantów (zestawy niewykonywalne zawierające kontrolki wielokrotnego użytku).</span><span class="sxs-lookup"><span data-stu-id="66a57-107">Custom Control Libraries (non-executable assemblies containing reusable controls).</span></span>  
  
- <span data-ttu-id="66a57-108">Biblioteki klas (zestawy niewykonywalne, które zawierają klasy wielokrotnego użytku).</span><span class="sxs-lookup"><span data-stu-id="66a57-108">Class Libraries (non-executable assemblies that contain reusable classes).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="66a57-109">Korzystanie z typów WPF w usłudze systemu Windows jest zdecydowanie odradzane.</span><span class="sxs-lookup"><span data-stu-id="66a57-109">Using WPF types in a Windows service is strongly discouraged.</span></span> <span data-ttu-id="66a57-110">Jeśli spróbujesz użyć tych funkcji w usłudze systemu Windows, mogą one nie zadziałały zgodnie z oczekiwaniami.</span><span class="sxs-lookup"><span data-stu-id="66a57-110">If you attempt to use these features in a Windows service, they may not work as expected.</span></span>  
  
 <span data-ttu-id="66a57-111">Aby skompilować ten zestaw aplikacji, WPF implementuje hosta usług.</span><span class="sxs-lookup"><span data-stu-id="66a57-111">To build this set of applications, WPF implements a host of services.</span></span> <span data-ttu-id="66a57-112">Ten temat zawiera omówienie tych usług i miejsca, w których można znaleźć więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="66a57-112">This topic provides an overview of these services and where to find more information.</span></span>  

<a name="Application_Management"></a>
## <a name="application-management"></a><span data-ttu-id="66a57-113">Zarządzanie aplikacjami</span><span class="sxs-lookup"><span data-stu-id="66a57-113">Application Management</span></span>  
 <span data-ttu-id="66a57-114">Wykonywalne aplikacje WPF często wymagają podstawowego zestawu funkcji, który obejmuje następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="66a57-114">Executable WPF applications commonly require a core set of functionality that includes the following:</span></span>  
  
- <span data-ttu-id="66a57-115">Tworzenie wspólnej infrastruktury aplikacji (w tym tworzenie metody punktu wejścia i pętla komunikatów systemu Windows w celu odbierania komunikatów systemowych i wejściowych) oraz zarządzanie nimi.</span><span class="sxs-lookup"><span data-stu-id="66a57-115">Creating and managing common application infrastructure (including creating an entry point method and a Windows message loop to receive system and input messages).</span></span>  
  
- <span data-ttu-id="66a57-116">Śledzenie i posługiwanie się okresem istnienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="66a57-116">Tracking and interacting with the lifetime of an application.</span></span>  
  
- <span data-ttu-id="66a57-117">Pobieranie i przetwarzanie parametrów wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="66a57-117">Retrieving and processing command-line parameters.</span></span>  
  
- <span data-ttu-id="66a57-118">Udostępnianie właściwości i zasobów zakresu aplikacji [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="66a57-118">Sharing application-scope properties and [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] resources.</span></span>  
  
- <span data-ttu-id="66a57-119">Wykrywanie i przetwarzanie nieobsługiwanych wyjątków.</span><span class="sxs-lookup"><span data-stu-id="66a57-119">Detecting and processing unhandled exceptions.</span></span>  
  
- <span data-ttu-id="66a57-120">Zwracanie kodów zakończenia.</span><span class="sxs-lookup"><span data-stu-id="66a57-120">Returning exit codes.</span></span>  
  
- <span data-ttu-id="66a57-121">Zarządzanie oknami w aplikacjach autonomicznych.</span><span class="sxs-lookup"><span data-stu-id="66a57-121">Managing windows in standalone applications.</span></span>  
  
- <span data-ttu-id="66a57-122">Śledzenie nawigacji w aplikacjach przeglądarki XAML (XBAP) i autonomicznych aplikacjach z oknami nawigacji i ramkami.</span><span class="sxs-lookup"><span data-stu-id="66a57-122">Tracking navigation in XAML browser applications (XBAPs), and standalone applications with navigation windows and frames.</span></span>  
  
 <span data-ttu-id="66a57-123">Te możliwości są implementowane przez <xref:System.Windows.Application> klasę, która jest dodawana do aplikacji przy użyciu *definicji aplikacji*.</span><span class="sxs-lookup"><span data-stu-id="66a57-123">These capabilities are implemented by the <xref:System.Windows.Application> class, which you add to your applications using an *application definition*.</span></span>  
  
 <span data-ttu-id="66a57-124">Aby uzyskać więcej informacji, zobacz [Omówienie zarządzania aplikacjami](application-management-overview.md).</span><span class="sxs-lookup"><span data-stu-id="66a57-124">For more information, see [Application Management Overview](application-management-overview.md).</span></span>  
  
<a name="WPF_Application_Resource__Content__and_Data_Files"></a>
## <a name="wpf-application-resource-content-and-data-files"></a><span data-ttu-id="66a57-125">Zasoby aplikacji WPF, zawartość, pliki danych</span><span class="sxs-lookup"><span data-stu-id="66a57-125">WPF Application Resource, Content, and Data Files</span></span>  
 <span data-ttu-id="66a57-126">WPF rozszerza podstawowe wsparcie w Microsoft .NET Framework dla zasobów osadzonych z obsługą trzech rodzajów niewykonywalnych plików danych: zasobu, zawartości i danych.</span><span class="sxs-lookup"><span data-stu-id="66a57-126">WPF extends the core support in the Microsoft .NET Framework for embedded resources with support for three kinds of non-executable data files: resource, content, and data.</span></span> <span data-ttu-id="66a57-127">Aby uzyskać więcej informacji, zapoznaj się z tematem [zasoby aplikacji WPF, zawartość i pliki danych](wpf-application-resource-content-and-data-files.md).</span><span class="sxs-lookup"><span data-stu-id="66a57-127">For more information, see [WPF Application Resource, Content, and Data Files](wpf-application-resource-content-and-data-files.md).</span></span>  
  
 <span data-ttu-id="66a57-128">Kluczowym elementem obsługi plików danych niewykonywalnych WPF jest możliwość identyfikowania i ładowania ich przy użyciu unikatowego identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="66a57-128">A key component of the support for WPF non-executable data files is the ability to identify and load them using a unique URI.</span></span> <span data-ttu-id="66a57-129">Aby uzyskać więcej informacji, zobacz [identyfikatory URI pakietów w WPF](pack-uris-in-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="66a57-129">For more information, see [Pack URIs in WPF](pack-uris-in-wpf.md).</span></span>  
  
<a name="Windows_and_Dialog_Boxes"></a>
## <a name="windows-and-dialog-boxes"></a><span data-ttu-id="66a57-130">Okna i okna dialogowe</span><span class="sxs-lookup"><span data-stu-id="66a57-130">Windows and Dialog Boxes</span></span>  
 <span data-ttu-id="66a57-131">Użytkownicy pracują z autonomicznymi aplikacjami WPF za pomocą systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="66a57-131">Users interact with WPF standalone applications through windows.</span></span> <span data-ttu-id="66a57-132">Przeznaczeniem okna jest hostowanie zawartości aplikacji i Uwidacznianie funkcjonalności aplikacji, która zwykle umożliwia użytkownikom współdziałanie z zawartością.</span><span class="sxs-lookup"><span data-stu-id="66a57-132">The purpose of a window is to host application content and expose application functionality that usually allows users to interact with the content.</span></span> <span data-ttu-id="66a57-133">W WPF systemy Windows są hermetyzowane przez <xref:System.Windows.Window> klasę, która obsługuje:</span><span class="sxs-lookup"><span data-stu-id="66a57-133">In WPF, windows are encapsulated by the <xref:System.Windows.Window> class, which supports:</span></span>  
  
- <span data-ttu-id="66a57-134">Tworzenie i wyświetlanie okien.</span><span class="sxs-lookup"><span data-stu-id="66a57-134">Creating and showing windows.</span></span>  
  
- <span data-ttu-id="66a57-135">Ustanawianie relacji okna właściciela/własności.</span><span class="sxs-lookup"><span data-stu-id="66a57-135">Establishing owner/owned window relationships.</span></span>  
  
- <span data-ttu-id="66a57-136">Konfigurowanie wyglądu okna (na przykład rozmiaru, lokalizacji, ikon, tekstu paska tytułu, obramowania).</span><span class="sxs-lookup"><span data-stu-id="66a57-136">Configuring window appearance (for example, size, location, icons, title bar text, border).</span></span>  
  
- <span data-ttu-id="66a57-137">Śledzenie i posługiwanie się okresem istnienia okna.</span><span class="sxs-lookup"><span data-stu-id="66a57-137">Tracking and interacting with the lifetime of a window.</span></span>  
  
 <span data-ttu-id="66a57-138">Aby uzyskać więcej informacji, zobacz [WPF Windows — omówienie](wpf-windows-overview.md).</span><span class="sxs-lookup"><span data-stu-id="66a57-138">For more information, see [WPF Windows Overview](wpf-windows-overview.md).</span></span>  
  
 <span data-ttu-id="66a57-139"><xref:System.Windows.Window>obsługuje możliwość tworzenia specjalnego typu okna znanego jako okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="66a57-139"><xref:System.Windows.Window> supports the ability to create a special type of window known as a dialog box.</span></span> <span data-ttu-id="66a57-140">Można utworzyć zarówno modalne, jak i niemodalne typy okien dialogowych.</span><span class="sxs-lookup"><span data-stu-id="66a57-140">Both modal and modeless types of dialog boxes can be created.</span></span>  
  
 <span data-ttu-id="66a57-141">Ze względu na wygodę i korzyści ze stosowania i spójnego środowiska użytkownika w aplikacjach, WPF uwidacznia trzy podstawowe okna dialogowe systemu Windows: <xref:Microsoft.Win32.OpenFileDialog> , <xref:Microsoft.Win32.SaveFileDialog> , i <xref:System.Windows.Controls.PrintDialog> .</span><span class="sxs-lookup"><span data-stu-id="66a57-141">For convenience, and the benefits of reusability and a consistent user experience across applications, WPF exposes three of the common Windows dialog boxes: <xref:Microsoft.Win32.OpenFileDialog>, <xref:Microsoft.Win32.SaveFileDialog>, and <xref:System.Windows.Controls.PrintDialog>.</span></span>  
  
 <span data-ttu-id="66a57-142">Okno komunikatu jest specjalnym typem okna dialogowego służącym do wyświetlania ważnych informacji tekstowych dla użytkowników, a w przypadku pytania proste tak/nie/OK/Anuluj.</span><span class="sxs-lookup"><span data-stu-id="66a57-142">A message box is a special type of dialog box for showing important textual information to users, and for asking simple Yes/No/OK/Cancel questions.</span></span> <span data-ttu-id="66a57-143">Użyj klasy, <xref:System.Windows.MessageBox> Aby utworzyć i wyświetlić okna komunikatów.</span><span class="sxs-lookup"><span data-stu-id="66a57-143">You use the <xref:System.Windows.MessageBox> class to create and show message boxes.</span></span>  
  
 <span data-ttu-id="66a57-144">Aby uzyskać więcej informacji, zobacz [okna dialogowe przegląd](dialog-boxes-overview.md).</span><span class="sxs-lookup"><span data-stu-id="66a57-144">For more information, see [Dialog Boxes Overview](dialog-boxes-overview.md).</span></span>  
  
<a name="Navigation"></a>
## <a name="navigation"></a><span data-ttu-id="66a57-145">Nawigacja</span><span class="sxs-lookup"><span data-stu-id="66a57-145">Navigation</span></span>  
 <span data-ttu-id="66a57-146">WPF obsługuje nawigowanie w stylu sieci Web za pomocą stron ( <xref:System.Windows.Controls.Page> ) i hiperlinków ( <xref:System.Windows.Documents.Hyperlink> ).</span><span class="sxs-lookup"><span data-stu-id="66a57-146">WPF supports Web-style navigation using pages (<xref:System.Windows.Controls.Page>) and hyperlinks (<xref:System.Windows.Documents.Hyperlink>).</span></span> <span data-ttu-id="66a57-147">Nawigację można zaimplementować na różne sposoby:</span><span class="sxs-lookup"><span data-stu-id="66a57-147">Navigation can be implemented in a variety of ways that include the following:</span></span>  
  
- <span data-ttu-id="66a57-148">Autonomiczne strony hostowane w przeglądarce internetowej.</span><span class="sxs-lookup"><span data-stu-id="66a57-148">Standalone pages that are hosted in a Web browser.</span></span>  
  
- <span data-ttu-id="66a57-149">Strony skompilowane w aplikacji XBAP, która jest hostowana w przeglądarce sieci Web.</span><span class="sxs-lookup"><span data-stu-id="66a57-149">Pages compiled into an XBAP that is hosted in a Web browser.</span></span>  
  
- <span data-ttu-id="66a57-150">Strony skompilowane w aplikacji autonomicznej i hostowane w oknie nawigacji ( <xref:System.Windows.Navigation.NavigationWindow> ).</span><span class="sxs-lookup"><span data-stu-id="66a57-150">Pages compiled into a standalone application and hosted by a navigation window (<xref:System.Windows.Navigation.NavigationWindow>).</span></span>  
  
- <span data-ttu-id="66a57-151">Strony hostowane przez ramkę ( <xref:System.Windows.Controls.Frame> ), które mogą być hostowane na stronie autonomicznej lub strony skompilowane w aplikacji XBAP lub autonomicznej.</span><span class="sxs-lookup"><span data-stu-id="66a57-151">Pages that are hosted by a frame (<xref:System.Windows.Controls.Frame>), which may be hosted in a standalone page, or a page compiled into either an XBAP or a standalone application.</span></span>  
  
 <span data-ttu-id="66a57-152">Aby ułatwić nawigację, WPF implementuje następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="66a57-152">To facilitate navigation, WPF implements the following:</span></span>  
  
- <span data-ttu-id="66a57-153"><xref:System.Windows.Navigation.NavigationService>udostępniony aparat nawigacyjny do przetwarzania żądań nawigacji, które są używane przez <xref:System.Windows.Controls.Frame> , <xref:System.Windows.Navigation.NavigationWindow> i aplikacje XBAP do obsługi nawigacji wewnątrz aplikacji.</span><span class="sxs-lookup"><span data-stu-id="66a57-153"><xref:System.Windows.Navigation.NavigationService>, the shared navigation engine for processing navigation requests that is used by <xref:System.Windows.Controls.Frame>, <xref:System.Windows.Navigation.NavigationWindow>, and XBAPs to support intra-application navigation.</span></span>  
  
- <span data-ttu-id="66a57-154">Metody nawigacji umożliwiające zainicjowanie nawigacji.</span><span class="sxs-lookup"><span data-stu-id="66a57-154">Navigation methods to initiate navigation.</span></span>  
  
- <span data-ttu-id="66a57-155">Zdarzenia nawigacji do śledzenia i współpracy z okresem istnienia nawigacji.</span><span class="sxs-lookup"><span data-stu-id="66a57-155">Navigation events to track and interact with navigation lifetime.</span></span>  
  
- <span data-ttu-id="66a57-156">Zapamiętywanie nawigacji z tyłu i do przodu przy użyciu dziennika, który można także sprawdzić i manipulować.</span><span class="sxs-lookup"><span data-stu-id="66a57-156">Remembering back and forward navigation using a journal, which can also be inspected and manipulated.</span></span>  
  
 <span data-ttu-id="66a57-157">Aby uzyskać więcej informacji, zobacz [Omówienie nawigacji](navigation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="66a57-157">For information, see [Navigation Overview](navigation-overview.md).</span></span>  
  
 <span data-ttu-id="66a57-158">WPF obsługuje również specjalny typ nawigacji znany jako Nawigacja strukturalna.</span><span class="sxs-lookup"><span data-stu-id="66a57-158">WPF also supports a special type of navigation known as structured navigation.</span></span> <span data-ttu-id="66a57-159">Strukturalna Nawigacja może służyć do wywoływania co najmniej jednej strony, która zwraca dane w sposób strukturalny i przewidywalny, który jest zgodny z funkcjami wywołującymi.</span><span class="sxs-lookup"><span data-stu-id="66a57-159">Structured navigation can be used to call one or more pages that return data in a structured and predictable way that is consistent with calling functions.</span></span> <span data-ttu-id="66a57-160">Ta funkcja zależy od <xref:System.Windows.Navigation.PageFunction%601> klasy, która jest opisana dokładniej w temacie [Omówienie nawigacji strukturalnej](structured-navigation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="66a57-160">This capability depends on the <xref:System.Windows.Navigation.PageFunction%601> class, which is described further in [Structured Navigation Overview](structured-navigation-overview.md).</span></span> <span data-ttu-id="66a57-161"><xref:System.Windows.Navigation.PageFunction%601>służy również do uproszczenia tworzenia złożonych topologii nawigacyjnej, które są opisane w [Omówienie topologii nawigacji](navigation-topologies-overview.md).</span><span class="sxs-lookup"><span data-stu-id="66a57-161"><xref:System.Windows.Navigation.PageFunction%601> also serves to simplify the creation of complex navigation topologies, which are described in [Navigation Topologies Overview](navigation-topologies-overview.md).</span></span>  
  
<a name="Hosting"></a>
## <a name="hosting"></a><span data-ttu-id="66a57-162">Hosting</span><span class="sxs-lookup"><span data-stu-id="66a57-162">Hosting</span></span>  
 <span data-ttu-id="66a57-163">Aplikacje XBAP mogą być hostowane w programie Microsoft Internet Explorer lub Firefox.</span><span class="sxs-lookup"><span data-stu-id="66a57-163">XBAPs can be hosted in Microsoft Internet Explorer or Firefox.</span></span> <span data-ttu-id="66a57-164">Każdy model hostingu ma swój własny zestaw zagadnień i ograniczeń, które są omówione w [hostingu](hosting-wpf-applications.md).</span><span class="sxs-lookup"><span data-stu-id="66a57-164">Each hosting model has its own set of considerations and constraints that are covered in [Hosting](hosting-wpf-applications.md).</span></span>  
  
<a name="Build_and_Deploy"></a>
## <a name="build-and-deploy"></a><span data-ttu-id="66a57-165">Wdróż i konfiguruj</span><span class="sxs-lookup"><span data-stu-id="66a57-165">Build and Deploy</span></span>  
 <span data-ttu-id="66a57-166">Chociaż proste aplikacje WPF można skompilować z wiersza polecenia przy użyciu kompilatorów wiersza polecenia, WPF integruje się z programem Visual Studio, aby zapewnić dodatkową pomoc techniczną, która uprości proces tworzenia i kompilowania.</span><span class="sxs-lookup"><span data-stu-id="66a57-166">Although simple WPF applications can be built from a command prompt using command-line compilers, WPF integrates with Visual Studio to provide additional support that simplified the development and build process.</span></span> <span data-ttu-id="66a57-167">Aby uzyskać więcej informacji, zobacz [Kompilowanie aplikacji WPF](building-a-wpf-application-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="66a57-167">For more information, see [Building a WPF Application](building-a-wpf-application-wpf.md).</span></span>  
  
 <span data-ttu-id="66a57-168">W zależności od typu skompilowanej aplikacji istnieje co najmniej jedna opcja wdrażania do wyboru.</span><span class="sxs-lookup"><span data-stu-id="66a57-168">Depending on the type of application you build, there are one or more deployment options to choose from.</span></span> <span data-ttu-id="66a57-169">Aby uzyskać więcej informacji, zobacz [wdrażanie aplikacji WPF](deploying-a-wpf-application-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="66a57-169">For more information, see [Deploying a WPF Application](deploying-a-wpf-application-wpf.md).</span></span>  
  
<a name="related_topics"></a>
## <a name="related-topics"></a><span data-ttu-id="66a57-170">Tematy pokrewne</span><span class="sxs-lookup"><span data-stu-id="66a57-170">Related Topics</span></span>  
  
|<span data-ttu-id="66a57-171">Tytuł</span><span class="sxs-lookup"><span data-stu-id="66a57-171">Title</span></span>|<span data-ttu-id="66a57-172">Opis</span><span class="sxs-lookup"><span data-stu-id="66a57-172">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="66a57-173">Przegląd Zarządzanie aplikacjami</span><span class="sxs-lookup"><span data-stu-id="66a57-173">Application Management Overview</span></span>](application-management-overview.md)|<span data-ttu-id="66a57-174">Zawiera przegląd <xref:System.Windows.Application> klasy, w tym zarządzanie okresem istnienia aplikacji, systemem Windows, zasobami aplikacji i nawigacją.</span><span class="sxs-lookup"><span data-stu-id="66a57-174">Provides an overview of the <xref:System.Windows.Application> class including managing application lifetime, windows, application resources, and navigation.</span></span>|  
|[<span data-ttu-id="66a57-175">Okna w WPF</span><span class="sxs-lookup"><span data-stu-id="66a57-175">Windows in WPF</span></span>](windows-in-wpf-applications.md)|<span data-ttu-id="66a57-176">Zawiera szczegółowe informacje dotyczące zarządzania oknami w aplikacji, w tym sposób używania <xref:System.Windows.Window> okien dialogowych i klas.</span><span class="sxs-lookup"><span data-stu-id="66a57-176">Provides details of managing windows in your application including how to use the <xref:System.Windows.Window> class and dialog boxes.</span></span>|  
|[<span data-ttu-id="66a57-177">Przegląd Nawigacja</span><span class="sxs-lookup"><span data-stu-id="66a57-177">Navigation Overview</span></span>](navigation-overview.md)|<span data-ttu-id="66a57-178">Zawiera omówienie zarządzania nawigacją między stronami aplikacji.</span><span class="sxs-lookup"><span data-stu-id="66a57-178">Provides an overview of managing navigation between pages of your application.</span></span>|  
|[<span data-ttu-id="66a57-179">Hosting</span><span class="sxs-lookup"><span data-stu-id="66a57-179">Hosting</span></span>](hosting-wpf-applications.md)|<span data-ttu-id="66a57-180">Zawiera omówienie aplikacji przeglądarki XAML (XBAP).</span><span class="sxs-lookup"><span data-stu-id="66a57-180">Provides an overview of XAML browser applications (XBAPs).</span></span>|  
|[<span data-ttu-id="66a57-181">Kompiluj i wdrażaj</span><span class="sxs-lookup"><span data-stu-id="66a57-181">Build and Deploy</span></span>](building-and-deploying-wpf-applications.md)|<span data-ttu-id="66a57-182">Opisuje sposób kompilowania i wdrażania aplikacji WPF.</span><span class="sxs-lookup"><span data-stu-id="66a57-182">Describes how to build and deploy your WPF application.</span></span>|  
|[<span data-ttu-id="66a57-183">Wprowadzenie do platformy WPF w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="66a57-183">Introduction to WPF in Visual Studio</span></span>](../getting-started/introduction-to-wpf-in-vs.md)|<span data-ttu-id="66a57-184">Opisuje główne funkcje platformy WPF.</span><span class="sxs-lookup"><span data-stu-id="66a57-184">Describes the main features of WPF.</span></span>|  
|[<span data-ttu-id="66a57-185">Przewodnik: moja pierwsza aplikacja klasyczna WPF</span><span class="sxs-lookup"><span data-stu-id="66a57-185">Walkthrough: My first WPF desktop application</span></span>](../getting-started/walkthrough-my-first-wpf-desktop-application.md)|<span data-ttu-id="66a57-186">Przewodnik, który pokazuje, jak utworzyć aplikację WPF za pomocą nawigacji, układu, kontrolek, obrazów, stylów i powiązania.</span><span class="sxs-lookup"><span data-stu-id="66a57-186">A walkthrough that shows how to create a WPF application using page navigation, layout, controls, images, styles, and binding.</span></span>|
