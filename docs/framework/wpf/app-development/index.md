---
title: Projektowanie aplikacji
ms.date: 01/26/2018
helpviewer_keywords:
- WPF [WPF], about application development
- application development [WPF], about
ms.assetid: 2996ce5e-81e9-49ae-881b-952db3dd1b7e
ms.openlocfilehash: 5ff9f58b72982f79e70b80f60c10828c3b54e5bb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186004"
---
# <a name="application-development"></a><span data-ttu-id="6119a-102">Projektowanie aplikacji</span><span class="sxs-lookup"><span data-stu-id="6119a-102">Application Development</span></span>
<a name="introduction"></a><span data-ttu-id="6119a-103">Windows Presentation Foundation (WPF) to struktura prezentacji, która może służyć do tworzenia następujących typów aplikacji:</span><span class="sxs-lookup"><span data-stu-id="6119a-103">Windows Presentation Foundation (WPF) is a presentation framework that can be used to develop the following types of applications:</span></span>  
  
- <span data-ttu-id="6119a-104">Aplikacje autonomiczne (aplikacje systemu Windows w tradycyjnym stylu utworzone jako zestawy wykonywalne, które są instalowane i uruchamiane z komputera klienckiego).</span><span class="sxs-lookup"><span data-stu-id="6119a-104">Standalone Applications (traditional style Windows applications built as executable assemblies that are installed to and run from the client computer).</span></span>  
  
- <span data-ttu-id="6119a-105">Aplikacje przeglądarki XAML (XBAPs) (aplikacje składające się ze stron nawigacyjnych, które są zbudowane jako zestawy wykonywalne i hostowane przez przeglądarki internetowe, takie jak Microsoft Internet Explorer lub Mozilla Firefox).</span><span class="sxs-lookup"><span data-stu-id="6119a-105">XAML browser applications (XBAPs) (applications composed of navigation pages that are built as executable assemblies and hosted by Web browsers such as Microsoft Internet Explorer or Mozilla Firefox).</span></span>  
  
- <span data-ttu-id="6119a-106">Niestandardowe biblioteki sterowania (zestawy niewykonalne zawierające kontrolki wielokrotnegoużynia).</span><span class="sxs-lookup"><span data-stu-id="6119a-106">Custom Control Libraries (non-executable assemblies containing reusable controls).</span></span>  
  
- <span data-ttu-id="6119a-107">Biblioteki klas (zestawy niewykonalne zawierające klasy wielokrotnegoużynia).</span><span class="sxs-lookup"><span data-stu-id="6119a-107">Class Libraries (non-executable assemblies that contain reusable classes).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6119a-108">Za pomocą WPF typów w usłudze systemu Windows jest zdecydowanie odradzane.</span><span class="sxs-lookup"><span data-stu-id="6119a-108">Using WPF types in a Windows service is strongly discouraged.</span></span> <span data-ttu-id="6119a-109">Jeśli spróbujesz użyć tych funkcji w usłudze systemu Windows, mogą one nie działać zgodnie z oczekiwaniami.</span><span class="sxs-lookup"><span data-stu-id="6119a-109">If you attempt to use these features in a Windows service, they may not work as expected.</span></span>  
  
 <span data-ttu-id="6119a-110">Aby utworzyć ten zestaw aplikacji, WPF implementuje wiele usług.</span><span class="sxs-lookup"><span data-stu-id="6119a-110">To build this set of applications, WPF implements a host of services.</span></span> <span data-ttu-id="6119a-111">Ten temat zawiera omówienie tych usług i gdzie znaleźć więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="6119a-111">This topic provides an overview of these services and where to find more information.</span></span>  

<a name="Application_Management"></a>
## <a name="application-management"></a><span data-ttu-id="6119a-112">Zarządzanie aplikacjami</span><span class="sxs-lookup"><span data-stu-id="6119a-112">Application Management</span></span>  
 <span data-ttu-id="6119a-113">Aplikacje WPF wykonywalne często wymagają podstawowego zestawu funkcji, który zawiera następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="6119a-113">Executable WPF applications commonly require a core set of functionality that includes the following:</span></span>  
  
- <span data-ttu-id="6119a-114">Tworzenie wspólnej infrastruktury aplikacji i zarządzanie nimi (w tym tworzenie metody punktu wejścia i pętli komunikatów systemu Windows w celu odbierania komunikatów systemowych i wejściowych).</span><span class="sxs-lookup"><span data-stu-id="6119a-114">Creating and managing common application infrastructure (including creating an entry point method and a Windows message loop to receive system and input messages).</span></span>  
  
- <span data-ttu-id="6119a-115">Śledzenie i interakcja z okresem istnienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6119a-115">Tracking and interacting with the lifetime of an application.</span></span>  
  
- <span data-ttu-id="6119a-116">Pobieranie i przetwarzanie parametrów wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="6119a-116">Retrieving and processing command-line parameters.</span></span>  
  
- <span data-ttu-id="6119a-117">Udostępnianie właściwości i [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] zasobów zakresu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6119a-117">Sharing application-scope properties and [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] resources.</span></span>  
  
- <span data-ttu-id="6119a-118">Wykrywanie i przetwarzanie nieobsługiwał wyjątków.</span><span class="sxs-lookup"><span data-stu-id="6119a-118">Detecting and processing unhandled exceptions.</span></span>  
  
- <span data-ttu-id="6119a-119">Zwracanie kodów wyjścia.</span><span class="sxs-lookup"><span data-stu-id="6119a-119">Returning exit codes.</span></span>  
  
- <span data-ttu-id="6119a-120">Zarządzanie oknami w aplikacjach autonomicznych.</span><span class="sxs-lookup"><span data-stu-id="6119a-120">Managing windows in standalone applications.</span></span>  
  
- <span data-ttu-id="6119a-121">Śledzenie nawigacji w aplikacjach przeglądarki XAML (XBAPs) i autonomicznych aplikacjach z oknami nawigacyjnymi i ramkami.</span><span class="sxs-lookup"><span data-stu-id="6119a-121">Tracking navigation in XAML browser applications (XBAPs), and standalone applications with navigation windows and frames.</span></span>  
  
 <span data-ttu-id="6119a-122">Te możliwości są implementowane <xref:System.Windows.Application> przez klasę, która jest dodawany do aplikacji przy użyciu *definicji aplikacji*.</span><span class="sxs-lookup"><span data-stu-id="6119a-122">These capabilities are implemented by the <xref:System.Windows.Application> class, which you add to your applications using an *application definition*.</span></span>  
  
 <span data-ttu-id="6119a-123">Aby uzyskać więcej informacji, zobacz [Omówienie zarządzania aplikacjami](application-management-overview.md).</span><span class="sxs-lookup"><span data-stu-id="6119a-123">For more information, see [Application Management Overview](application-management-overview.md).</span></span>  
  
<a name="WPF_Application_Resource__Content__and_Data_Files"></a>
## <a name="wpf-application-resource-content-and-data-files"></a><span data-ttu-id="6119a-124">Zasoby aplikacji WPF, zawartość, pliki danych</span><span class="sxs-lookup"><span data-stu-id="6119a-124">WPF Application Resource, Content, and Data Files</span></span>  
 <span data-ttu-id="6119a-125">WPF WPF rozszerza podstawową obsługę w programie Microsoft .NET Framework dla osadzonych zasobów z obsługą trzech rodzajów plików danych niekonywalnych: zasobów, zawartości i danych.</span><span class="sxs-lookup"><span data-stu-id="6119a-125">WPF extends the core support in the Microsoft .NET Framework for embedded resources with support for three kinds of non-executable data files: resource, content, and data.</span></span> <span data-ttu-id="6119a-126">Aby uzyskać więcej informacji, zobacz [Zasoby aplikacji WPF, zawartość i pliki danych](wpf-application-resource-content-and-data-files.md).</span><span class="sxs-lookup"><span data-stu-id="6119a-126">For more information, see [WPF Application Resource, Content, and Data Files](wpf-application-resource-content-and-data-files.md).</span></span>  
  
 <span data-ttu-id="6119a-127">Kluczowym składnikiem obsługi plików danych niewykonalnych WPF WPF jest możliwość identyfikowania i ładowania ich przy użyciu unikatowego identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="6119a-127">A key component of the support for WPF non-executable data files is the ability to identify and load them using a unique URI.</span></span> <span data-ttu-id="6119a-128">Aby uzyskać więcej informacji, zobacz [Pack URI w WPF](pack-uris-in-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="6119a-128">For more information, see [Pack URIs in WPF](pack-uris-in-wpf.md).</span></span>  
  
<a name="Windows_and_Dialog_Boxes"></a>
## <a name="windows-and-dialog-boxes"></a><span data-ttu-id="6119a-129">Okna i okna dialogowe</span><span class="sxs-lookup"><span data-stu-id="6119a-129">Windows and Dialog Boxes</span></span>  
 <span data-ttu-id="6119a-130">Użytkownicy wchodzą w interakcje z aplikacjami autonomicznymi WPF za pośrednictwem systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="6119a-130">Users interact with WPF standalone applications through windows.</span></span> <span data-ttu-id="6119a-131">Celem okna jest hostować zawartość aplikacji i udostępniać funkcje aplikacji, które zwykle umożliwia użytkownikom interakcję z zawartością.</span><span class="sxs-lookup"><span data-stu-id="6119a-131">The purpose of a window is to host application content and expose application functionality that usually allows users to interact with the content.</span></span> <span data-ttu-id="6119a-132">W WPF WPF okna są <xref:System.Windows.Window> hermetyzowane przez klasę, która obsługuje:</span><span class="sxs-lookup"><span data-stu-id="6119a-132">In WPF, windows are encapsulated by the <xref:System.Windows.Window> class, which supports:</span></span>  
  
- <span data-ttu-id="6119a-133">Tworzenie i pokazywanie okien.</span><span class="sxs-lookup"><span data-stu-id="6119a-133">Creating and showing windows.</span></span>  
  
- <span data-ttu-id="6119a-134">Ustanawianie relacji właściciel/okno należące do właściciela.</span><span class="sxs-lookup"><span data-stu-id="6119a-134">Establishing owner/owned window relationships.</span></span>  
  
- <span data-ttu-id="6119a-135">Konfigurowanie wyglądu okna (na przykład rozmiar, lokalizacja, ikony, tekst paska tytułu, obramowanie).</span><span class="sxs-lookup"><span data-stu-id="6119a-135">Configuring window appearance (for example, size, location, icons, title bar text, border).</span></span>  
  
- <span data-ttu-id="6119a-136">Śledzenie i interakcja z okresem istnienia okna.</span><span class="sxs-lookup"><span data-stu-id="6119a-136">Tracking and interacting with the lifetime of a window.</span></span>  
  
 <span data-ttu-id="6119a-137">Aby uzyskać więcej informacji, zobacz [Omówienie systemu Windows WPF](wpf-windows-overview.md).</span><span class="sxs-lookup"><span data-stu-id="6119a-137">For more information, see [WPF Windows Overview](wpf-windows-overview.md).</span></span>  
  
 <span data-ttu-id="6119a-138"><xref:System.Windows.Window>obsługuje możliwość tworzenia specjalnego typu okna znanego jako okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="6119a-138"><xref:System.Windows.Window> supports the ability to create a special type of window known as a dialog box.</span></span> <span data-ttu-id="6119a-139">Można tworzyć zarówno modalne, jak i niemodalne typy okien dialogowych.</span><span class="sxs-lookup"><span data-stu-id="6119a-139">Both modal and modeless types of dialog boxes can be created.</span></span>  
  
 <span data-ttu-id="6119a-140">Dla wygody i korzyści z ponownego użycia i spójnego środowiska użytkownika w różnych aplikacjach, WPF udostępnia trzy typowe okna dialogowe systemu Windows: <xref:Microsoft.Win32.OpenFileDialog>, <xref:Microsoft.Win32.SaveFileDialog>, i <xref:System.Windows.Controls.PrintDialog>.</span><span class="sxs-lookup"><span data-stu-id="6119a-140">For convenience, and the benefits of reusability and a consistent user experience across applications, WPF exposes three of the common Windows dialog boxes: <xref:Microsoft.Win32.OpenFileDialog>, <xref:Microsoft.Win32.SaveFileDialog>, and <xref:System.Windows.Controls.PrintDialog>.</span></span>  
  
 <span data-ttu-id="6119a-141">Okno komunikatu to specjalny typ okna dialogowego do wyświetlania ważnych informacji tekstowych użytkownikom oraz do zadawania prostych pytań Tak/Nie/OK/Anuluj.</span><span class="sxs-lookup"><span data-stu-id="6119a-141">A message box is a special type of dialog box for showing important textual information to users, and for asking simple Yes/No/OK/Cancel questions.</span></span> <span data-ttu-id="6119a-142"><xref:System.Windows.MessageBox> Klasy służy do tworzenia i pokazywalek komunikatów.</span><span class="sxs-lookup"><span data-stu-id="6119a-142">You use the <xref:System.Windows.MessageBox> class to create and show message boxes.</span></span>  
  
 <span data-ttu-id="6119a-143">Aby uzyskać więcej informacji, zobacz [Omówienie okien dialogowych](dialog-boxes-overview.md).</span><span class="sxs-lookup"><span data-stu-id="6119a-143">For more information, see [Dialog Boxes Overview](dialog-boxes-overview.md).</span></span>  
  
<a name="Navigation"></a>
## <a name="navigation"></a><span data-ttu-id="6119a-144">Nawigacja</span><span class="sxs-lookup"><span data-stu-id="6119a-144">Navigation</span></span>  
 <span data-ttu-id="6119a-145">WPF WPF obsługuje nawigację<xref:System.Windows.Controls.Page>w stylu sieci<xref:System.Windows.Documents.Hyperlink>Web przy użyciu stron ( ) i hiperłączy ( ).</span><span class="sxs-lookup"><span data-stu-id="6119a-145">WPF supports Web-style navigation using pages (<xref:System.Windows.Controls.Page>) and hyperlinks (<xref:System.Windows.Documents.Hyperlink>).</span></span> <span data-ttu-id="6119a-146">Nawigacja może być zaimplementowana na wiele sposobów, które obejmują następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="6119a-146">Navigation can be implemented in a variety of ways that include the following:</span></span>  
  
- <span data-ttu-id="6119a-147">Strony autonomiczne hostowane w przeglądarce sieci Web.</span><span class="sxs-lookup"><span data-stu-id="6119a-147">Standalone pages that are hosted in a Web browser.</span></span>  
  
- <span data-ttu-id="6119a-148">Strony skompilowane w XBAP, który jest obsługiwany w przeglądarce sieci Web.</span><span class="sxs-lookup"><span data-stu-id="6119a-148">Pages compiled into an XBAP that is hosted in a Web browser.</span></span>  
  
- <span data-ttu-id="6119a-149">Strony skompilowane w samodzielną aplikację i hostowane przez okno nawigacji (<xref:System.Windows.Navigation.NavigationWindow>).</span><span class="sxs-lookup"><span data-stu-id="6119a-149">Pages compiled into a standalone application and hosted by a navigation window (<xref:System.Windows.Navigation.NavigationWindow>).</span></span>  
  
- <span data-ttu-id="6119a-150">Strony hostowane przez ramkę<xref:System.Windows.Controls.Frame>( ), które mogą być hostowane na stronie autonomicznej lub strony skompilowane do XBAP lub aplikacji autonomicznej.</span><span class="sxs-lookup"><span data-stu-id="6119a-150">Pages that are hosted by a frame (<xref:System.Windows.Controls.Frame>), which may be hosted in a standalone page, or a page compiled into either an XBAP or a standalone application.</span></span>  
  
 <span data-ttu-id="6119a-151">Aby ułatwić nawigację, WPF implementuje następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="6119a-151">To facilitate navigation, WPF implements the following:</span></span>  
  
- <span data-ttu-id="6119a-152"><xref:System.Windows.Navigation.NavigationService>, udostępniony aparat nawigacyjny do przetwarzania żądań nawigacji używanych przez <xref:System.Windows.Controls.Frame>program <xref:System.Windows.Navigation.NavigationWindow>, oraz XBAPs do obsługi nawigacji wewnątrz aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6119a-152"><xref:System.Windows.Navigation.NavigationService>, the shared navigation engine for processing navigation requests that is used by <xref:System.Windows.Controls.Frame>, <xref:System.Windows.Navigation.NavigationWindow>, and XBAPs to support intra-application navigation.</span></span>  
  
- <span data-ttu-id="6119a-153">Metody nawigacji do inicjowania nawigacji.</span><span class="sxs-lookup"><span data-stu-id="6119a-153">Navigation methods to initiate navigation.</span></span>  
  
- <span data-ttu-id="6119a-154">Zdarzenia nawigacji do śledzenia i interakcji z okresem istnienia nawigacji.</span><span class="sxs-lookup"><span data-stu-id="6119a-154">Navigation events to track and interact with navigation lifetime.</span></span>  
  
- <span data-ttu-id="6119a-155">Zapamiętywanie nawigacji do tyłu i do przodu za pomocą dziennika, który można również sprawdzić i manipulować.</span><span class="sxs-lookup"><span data-stu-id="6119a-155">Remembering back and forward navigation using a journal, which can also be inspected and manipulated.</span></span>  
  
 <span data-ttu-id="6119a-156">Aby uzyskać więcej informacji, zobacz [Omówienie nawigacji](navigation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="6119a-156">For information, see [Navigation Overview](navigation-overview.md).</span></span>  
  
 <span data-ttu-id="6119a-157">WPF WPF obsługuje również specjalny typ nawigacji znany jako nawigacji strukturalnej.</span><span class="sxs-lookup"><span data-stu-id="6119a-157">WPF also supports a special type of navigation known as structured navigation.</span></span> <span data-ttu-id="6119a-158">Nawigacja strukturalna może służyć do wywołania jednej lub więcej stron, które zwracają dane w sposób strukturalny i przewidywalny, który jest zgodny z funkcjami wywołującymi.</span><span class="sxs-lookup"><span data-stu-id="6119a-158">Structured navigation can be used to call one or more pages that return data in a structured and predictable way that is consistent with calling functions.</span></span> <span data-ttu-id="6119a-159">Ta funkcja zależy <xref:System.Windows.Navigation.PageFunction%601> od klasy, która jest opisana dalej w [ustrukturyzowanym przeglądzie nawigacji.](structured-navigation-overview.md)</span><span class="sxs-lookup"><span data-stu-id="6119a-159">This capability depends on the <xref:System.Windows.Navigation.PageFunction%601> class, which is described further in [Structured Navigation Overview](structured-navigation-overview.md).</span></span> <span data-ttu-id="6119a-160"><xref:System.Windows.Navigation.PageFunction%601>służy również uproszczeniu tworzenia złożonych topologii nawigacji, które są opisane w [Przeglądzie Topologii Nawigacji](navigation-topologies-overview.md).</span><span class="sxs-lookup"><span data-stu-id="6119a-160"><xref:System.Windows.Navigation.PageFunction%601> also serves to simplify the creation of complex navigation topologies, which are described in [Navigation Topologies Overview](navigation-topologies-overview.md).</span></span>  
  
<a name="Hosting"></a>
## <a name="hosting"></a><span data-ttu-id="6119a-161">Hosting</span><span class="sxs-lookup"><span data-stu-id="6119a-161">Hosting</span></span>  
 <span data-ttu-id="6119a-162">XBAPs mogą być hostowane w programie Microsoft Internet Explorer lub Firefox.</span><span class="sxs-lookup"><span data-stu-id="6119a-162">XBAPs can be hosted in Microsoft Internet Explorer or Firefox.</span></span> <span data-ttu-id="6119a-163">Każdy model hostingu ma swój własny zestaw zagadnień i ograniczeń, które są objęte [hostingiem](hosting-wpf-applications.md).</span><span class="sxs-lookup"><span data-stu-id="6119a-163">Each hosting model has its own set of considerations and constraints that are covered in [Hosting](hosting-wpf-applications.md).</span></span>  
  
<a name="Build_and_Deploy"></a>
## <a name="build-and-deploy"></a><span data-ttu-id="6119a-164">Wdróż i konfiguruj</span><span class="sxs-lookup"><span data-stu-id="6119a-164">Build and Deploy</span></span>  
 <span data-ttu-id="6119a-165">Mimo że proste aplikacje WPF można utworzyć z wiersza polecenia przy użyciu kompilatorów wiersza polecenia, WPF integruje się z programem Visual Studio, aby zapewnić dodatkową obsługę, która uprościła proces tworzenia i kompilacji.</span><span class="sxs-lookup"><span data-stu-id="6119a-165">Although simple WPF applications can be built from a command prompt using command-line compilers, WPF integrates with Visual Studio to provide additional support that simplified the development and build process.</span></span> <span data-ttu-id="6119a-166">Aby uzyskać więcej informacji, zobacz [Tworzenie aplikacji WPF](building-a-wpf-application-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="6119a-166">For more information, see [Building a WPF Application](building-a-wpf-application-wpf.md).</span></span>  
  
 <span data-ttu-id="6119a-167">W zależności od typu aplikacji, które tworzysz, istnieje jedna lub więcej opcji wdrażania do wyboru.</span><span class="sxs-lookup"><span data-stu-id="6119a-167">Depending on the type of application you build, there are one or more deployment options to choose from.</span></span> <span data-ttu-id="6119a-168">Aby uzyskać więcej informacji, zobacz [Wdrażanie aplikacji WPF](deploying-a-wpf-application-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="6119a-168">For more information, see [Deploying a WPF Application](deploying-a-wpf-application-wpf.md).</span></span>  
  
<a name="related_topics"></a>
## <a name="related-topics"></a><span data-ttu-id="6119a-169">Tematy pokrewne</span><span class="sxs-lookup"><span data-stu-id="6119a-169">Related Topics</span></span>  
  
|<span data-ttu-id="6119a-170">Tytuł</span><span class="sxs-lookup"><span data-stu-id="6119a-170">Title</span></span>|<span data-ttu-id="6119a-171">Opis</span><span class="sxs-lookup"><span data-stu-id="6119a-171">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="6119a-172">Przegląd Zarządzanie aplikacjami</span><span class="sxs-lookup"><span data-stu-id="6119a-172">Application Management Overview</span></span>](application-management-overview.md)|<span data-ttu-id="6119a-173">Zawiera omówienie <xref:System.Windows.Application> klasy, w tym zarządzanie okresem istnienia aplikacji, oknami, zasobami aplikacji i nawigacją.</span><span class="sxs-lookup"><span data-stu-id="6119a-173">Provides an overview of the <xref:System.Windows.Application> class including managing application lifetime, windows, application resources, and navigation.</span></span>|  
|[<span data-ttu-id="6119a-174">Okna w WPF</span><span class="sxs-lookup"><span data-stu-id="6119a-174">Windows in WPF</span></span>](windows-in-wpf-applications.md)|<span data-ttu-id="6119a-175">Zawiera szczegółowe informacje na temat zarządzania <xref:System.Windows.Window> oknami w aplikacji, w tym jak używać klasy i okien dialogowych.</span><span class="sxs-lookup"><span data-stu-id="6119a-175">Provides details of managing windows in your application including how to use the <xref:System.Windows.Window> class and dialog boxes.</span></span>|  
|[<span data-ttu-id="6119a-176">Przegląd Nawigacja</span><span class="sxs-lookup"><span data-stu-id="6119a-176">Navigation Overview</span></span>](navigation-overview.md)|<span data-ttu-id="6119a-177">Zawiera omówienie zarządzania nawigacją między stronami aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6119a-177">Provides an overview of managing navigation between pages of your application.</span></span>|  
|[<span data-ttu-id="6119a-178">Hosting</span><span class="sxs-lookup"><span data-stu-id="6119a-178">Hosting</span></span>](hosting-wpf-applications.md)|<span data-ttu-id="6119a-179">Zawiera przegląd aplikacji przeglądarki XAML (XBAPs).</span><span class="sxs-lookup"><span data-stu-id="6119a-179">Provides an overview of XAML browser applications (XBAPs).</span></span>|  
|[<span data-ttu-id="6119a-180">Buduj i wdrażaj</span><span class="sxs-lookup"><span data-stu-id="6119a-180">Build and Deploy</span></span>](building-and-deploying-wpf-applications.md)|<span data-ttu-id="6119a-181">W tym artykule opisano, jak skompilować i wdrożyć aplikację WPF.</span><span class="sxs-lookup"><span data-stu-id="6119a-181">Describes how to build and deploy your WPF application.</span></span>|  
|[<span data-ttu-id="6119a-182">Wprowadzenie do platformy WPF w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="6119a-182">Introduction to WPF in Visual Studio</span></span>](../getting-started/introduction-to-wpf-in-vs.md)|<span data-ttu-id="6119a-183">Opisuje główne funkcje WPF.</span><span class="sxs-lookup"><span data-stu-id="6119a-183">Describes the main features of WPF.</span></span>|  
|[<span data-ttu-id="6119a-184">Instruktaż: Moja pierwsza aplikacja komputerowa WPF</span><span class="sxs-lookup"><span data-stu-id="6119a-184">Walkthrough: My first WPF desktop application</span></span>](../getting-started/walkthrough-my-first-wpf-desktop-application.md)|<span data-ttu-id="6119a-185">Przewodnik, który pokazuje, jak utworzyć aplikację WPF przy użyciu nawigacji strony, układ, formanty, obrazy, style i powiązania.</span><span class="sxs-lookup"><span data-stu-id="6119a-185">A walkthrough that shows how to create a WPF application using page navigation, layout, controls, images, styles, and binding.</span></span>|
