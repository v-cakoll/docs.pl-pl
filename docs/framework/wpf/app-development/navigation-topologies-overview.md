---
title: "Przegląd Topologia nawigacji"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- linear topology [WPF]
- fixed hierarchical topology [WPF]
- fixed linear topology [WPF]
- topologies [WPF]
- navigation topologies [WPF]
- dynamically-generated topology
ms.assetid: 5d5ee837-629a-4933-869a-186dc22ac43d
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: dbe7fe80639537293413d8fb923033909a2451e9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="navigation-topologies-overview"></a><span data-ttu-id="19496-102">Przegląd Topologia nawigacji</span><span class="sxs-lookup"><span data-stu-id="19496-102">Navigation Topologies Overview</span></span>
<a name="introduction"></a><span data-ttu-id="19496-103">Ten przegląd zawiera wprowadzenie do topologii nawigacji w [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].</span><span class="sxs-lookup"><span data-stu-id="19496-103">This overview provides an introduction to navigation topologies in [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].</span></span> <span data-ttu-id="19496-104">Następnie omówiono trzy popularne topologie nawigacji, z próbek.</span><span class="sxs-lookup"><span data-stu-id="19496-104">Three common navigation topologies, with samples, are subsequently discussed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="19496-105">Przed przeczytaniem tego tematu, należy zapoznać się z pojęciem strukturze nawigacji w [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] przy użyciu funkcji strony.</span><span class="sxs-lookup"><span data-stu-id="19496-105">Before reading this topic, you should be familiar with the concept of structured navigation in [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] using page functions.</span></span> <span data-ttu-id="19496-106">Aby uzyskać więcej informacji na obu tych tematów, zobacz [strukturalnych omówienie nawigacji](../../../../docs/framework/wpf/app-development/structured-navigation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="19496-106">For more information on both of these topics, see [Structured Navigation Overview](../../../../docs/framework/wpf/app-development/structured-navigation-overview.md).</span></span>  
  
 <span data-ttu-id="19496-107">Ten temat zawiera następujące sekcje:</span><span class="sxs-lookup"><span data-stu-id="19496-107">This topic contains the following sections:</span></span>  
  
-   [<span data-ttu-id="19496-108">Topologie nawigacji</span><span class="sxs-lookup"><span data-stu-id="19496-108">Navigation Topologies</span></span>](#Navigation_Topologies)  
  
-   [<span data-ttu-id="19496-109">Topologie strukturze nawigacji</span><span class="sxs-lookup"><span data-stu-id="19496-109">Structured Navigation Topologies</span></span>](#Structured_Navigation_Topologies)  
  
-   [<span data-ttu-id="19496-110">Nawigacji za pośrednictwem stałym topologii liniowy</span><span class="sxs-lookup"><span data-stu-id="19496-110">Navigation over a Fixed Linear Topology</span></span>](#Navigation_over_a_Fixed_Linear_Topology)  
  
-   [<span data-ttu-id="19496-111">Dynamiczne nawigacji w topologii hierarchicznej stałej</span><span class="sxs-lookup"><span data-stu-id="19496-111">Dynamic Navigation over a Fixed Hierarchical Topology</span></span>](#Dynamic_Navigation_over_a_Fixed_Hierarchical_Topology)  
  
-   [<span data-ttu-id="19496-112">Nawigacji na dynamicznie generowanym topologii</span><span class="sxs-lookup"><span data-stu-id="19496-112">Navigation over a Dynamically Generated Topology</span></span>](#Navigation_over_a_Dynamically_Generated_Topology)  
  
<a name="Navigation_Topologies"></a>   
## <a name="navigation-topologies"></a><span data-ttu-id="19496-113">Topologie nawigacji</span><span class="sxs-lookup"><span data-stu-id="19496-113">Navigation Topologies</span></span>  
 <span data-ttu-id="19496-114">W [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], nawigacji zazwyczaj składa się z stron (<xref:System.Windows.Controls.Page>) na hiperłącza (<xref:System.Windows.Documents.Hyperlink>) który przejdź do innych stron, po kliknięciu.</span><span class="sxs-lookup"><span data-stu-id="19496-114">In [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], navigation typically consists of pages (<xref:System.Windows.Controls.Page>) with hyperlinks (<xref:System.Windows.Documents.Hyperlink>) that navigate to other pages when clicked.</span></span> <span data-ttu-id="19496-115">Strony, które są przejście są identyfikowane przez [!INCLUDE[TLA#tla_uri#plural](../../../../includes/tlasharptla-urisharpplural-md.md)] (zobacz [identyfikatorów URI pakietu na platformie WPF](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md)).</span><span class="sxs-lookup"><span data-stu-id="19496-115">Pages that are navigated to are identified by [!INCLUDE[TLA#tla_uri#plural](../../../../includes/tlasharptla-urisharpplural-md.md)] (see [Pack URIs in WPF](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md)).</span></span> <span data-ttu-id="19496-116">Należy wziąć pod uwagę następujące prosty przykład pokazujący stron, hiperłącza, i [!INCLUDE[TLA#tla_uri#plural](../../../../includes/tlasharptla-urisharpplural-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="19496-116">Consider the following simple example that shows pages, hyperlinks, and [!INCLUDE[TLA#tla_uri#plural](../../../../includes/tlasharptla-urisharpplural-md.md)]:</span></span>  
  
 [!code-xaml[NavigationTopologiesOverviewSnippets#Page1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationTopologiesOverviewSnippets/CS/Page1.xaml#page1)]  
  
 [!code-xaml[NavigationTopologiesOverviewSnippets#Page2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationTopologiesOverviewSnippets/CS/Page2.xaml#page2)]  
  
 <span data-ttu-id="19496-117">Te strony są rozmieszczone w *topologii nawigacji* której strukturę zależy od sposobu można przechodzić między stronami.</span><span class="sxs-lookup"><span data-stu-id="19496-117">These pages are arranged in a *navigation topology* whose structure is determined by how you can navigate between the pages.</span></span> <span data-ttu-id="19496-118">Ta topologia określonego nawigacji jest odpowiednie w scenariuszach prostego, ale nawigacji może wymagać bardziej złożonej topologii, niektóre z nich można zdefiniować tylko gdy aplikacja jest uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="19496-118">This particular navigation topology is suitable in simple scenarios, although navigation can require more complex topologies, some of which can only be defined when an application is running.</span></span>  
  
 <span data-ttu-id="19496-119">W tym temacie omówiono trzy popularne topologie nawigacji: *stałej liniowej*, *stałej hierarchiczna*, i *dynamicznie generowanym*.</span><span class="sxs-lookup"><span data-stu-id="19496-119">This topic covers three common navigation topologies: *fixed linear*, *fixed hierarchical*, and *dynamically generated*.</span></span> <span data-ttu-id="19496-120">Każdej topologii nawigacji przedstawiono próbkę, który ma [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] , takich jak to przedstawiono na poniższej ilustracji:</span><span class="sxs-lookup"><span data-stu-id="19496-120">Each navigation topology is demonstrated with a sample that has a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] like the one that is shown in the following figure:</span></span>  
  
 <span data-ttu-id="19496-121">![Zadanie stron z elementami danych](../../../../docs/framework/wpf/app-development/media/navigationtopologyfigure6.png "NavigationTopologyFigure6")</span><span class="sxs-lookup"><span data-stu-id="19496-121">![Task pages with data items](../../../../docs/framework/wpf/app-development/media/navigationtopologyfigure6.png "NavigationTopologyFigure6")</span></span>  
  
<a name="Structured_Navigation_Topologies"></a>   
## <a name="structured-navigation-topologies"></a><span data-ttu-id="19496-122">Topologie strukturze nawigacji</span><span class="sxs-lookup"><span data-stu-id="19496-122">Structured Navigation Topologies</span></span>  
 <span data-ttu-id="19496-123">Istnieją dwa ogólne typy topologii nawigacji:</span><span class="sxs-lookup"><span data-stu-id="19496-123">There are two broad types of navigation topologies:</span></span>  
  
-   <span data-ttu-id="19496-124">**Stałe topologii**: zdefiniowany w czasie kompilacji i nie zmienia się w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="19496-124">**Fixed Topology**: defined at compile time and does not change at run time.</span></span> <span data-ttu-id="19496-125">Stały topologii są przydatne w przypadku nawigację stałym sekwencji stron w kolejności liniowego lub hierarchicznej.</span><span class="sxs-lookup"><span data-stu-id="19496-125">Fixed topologies are useful for navigation through a fixed sequence of pages in either a linear or hierarchical order.</span></span>  
  
-   <span data-ttu-id="19496-126">**Dynamiczne topologii**: zdefiniowany w czasie wykonywania w oparciu o dane wejściowe, zbierane od użytkownika, aplikacji lub systemu.</span><span class="sxs-lookup"><span data-stu-id="19496-126">**Dynamic Topology**: defined at run time based on input that is collected from the user, the application, or the system.</span></span> <span data-ttu-id="19496-127">Topologie dynamiczne są przydatne, gdy strony może zostać przesłane w różnych sekwencji.</span><span class="sxs-lookup"><span data-stu-id="19496-127">Dynamic topologies are useful when pages can be navigated in different sequences.</span></span>  
  
 <span data-ttu-id="19496-128">Chociaż można utworzyć za pomocą stron topologie nawigacji, przykłady używać funkcji strony, ponieważ zapewniają dodatkową pomoc, który upraszcza obsługę przekazywanie i zwracający dane na stronach topologii.</span><span class="sxs-lookup"><span data-stu-id="19496-128">Although it is possible to create navigation topologies using pages, the samples use page functions because they provide additional support that simplifies support for passing and returning data through the pages of a topology.</span></span>  
  
<a name="Navigation_over_a_Fixed_Linear_Topology"></a>   
## <a name="navigation-over-a-fixed-linear-topology"></a><span data-ttu-id="19496-129">Nawigacji za pośrednictwem stałym topologii liniowy</span><span class="sxs-lookup"><span data-stu-id="19496-129">Navigation over a Fixed Linear Topology</span></span>  
 <span data-ttu-id="19496-130">Stałe topologii liniowego jest odpowiednikiem struktury kreatora, który ma co najmniej jeden stronach kreatora, które są przejście w stałej kolejności.</span><span class="sxs-lookup"><span data-stu-id="19496-130">A fixed linear topology is analogous to the structure of a wizard that has one or more wizard pages that are navigated in a fixed sequence.</span></span> <span data-ttu-id="19496-131">Na poniższej ilustracji przedstawiono wysokiego poziomu struktury i przepływu kreatora przy stałym topologii liniowej.</span><span class="sxs-lookup"><span data-stu-id="19496-131">The following figure shows the high-level structure and flow of a wizard with a fixed linear topology.</span></span>  
  
 <span data-ttu-id="19496-132">![Diagram topologii nawigacji](../../../../docs/framework/wpf/app-development/media/navigationtopologyfigure1.png "NavigationTopologyFigure1")</span><span class="sxs-lookup"><span data-stu-id="19496-132">![Navigation topology diagram](../../../../docs/framework/wpf/app-development/media/navigationtopologyfigure1.png "NavigationTopologyFigure1")</span></span>  
  
 <span data-ttu-id="19496-133">Następujące typowe zachowania do nawigowania za pośrednictwem stałym topologii liniowej:</span><span class="sxs-lookup"><span data-stu-id="19496-133">The typical behaviors for navigating over a fixed linear topology include the following:</span></span>  
  
-   <span data-ttu-id="19496-134">Przejście ze strony wywołania do strony uruchamiania, która inicjuje kreatora i przechodzi do pierwszej strony kreatora.</span><span class="sxs-lookup"><span data-stu-id="19496-134">Navigating from the calling page to a launcher page that initializes the wizard and navigates to the first wizard page.</span></span> <span data-ttu-id="19496-135">Strona uruchamiania ( [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]-mniej <xref:System.Windows.Navigation.PageFunction%601>) nie jest wymagana, ponieważ wywołujący strony można wywołać bezpośrednio pierwszej stronie kreatora.</span><span class="sxs-lookup"><span data-stu-id="19496-135">A launcher page (a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]-less <xref:System.Windows.Navigation.PageFunction%601>) is not required, since a calling page can call the first wizard page directly.</span></span> <span data-ttu-id="19496-136">Przy użyciu strony uruchamiania, jednak może uprościć Kreatora inicjowania, zwłaszcza w wypadku inicjowania jest złożony.</span><span class="sxs-lookup"><span data-stu-id="19496-136">Using a launcher page, however, can simplify wizard initialization, particularly if initialization is complex.</span></span>  
  
-   <span data-ttu-id="19496-137">Użytkownicy mogą przechodzić między stronami przy użyciu Wstecz i do przodu przycisków (lub hiperłącza).</span><span class="sxs-lookup"><span data-stu-id="19496-137">Users can navigate between pages by using Back and Forward buttons (or hyperlinks).</span></span>  
  
-   <span data-ttu-id="19496-138">Użytkownicy mogą przechodzić między stronami przy użyciu arkusza.</span><span class="sxs-lookup"><span data-stu-id="19496-138">Users can navigate between pages using the journal.</span></span>  
  
-   <span data-ttu-id="19496-139">Użytkownicy mogą anulować pracę z kreatorem z dowolnej strony kreatora, naciskając przycisk Anuluj.</span><span class="sxs-lookup"><span data-stu-id="19496-139">Users can cancel the wizard from any wizard page by pressing a Cancel button.</span></span>  
  
-   <span data-ttu-id="19496-140">Użytkownicy mogą akceptować kreatora na ostatniej stronie kreatora, naciskając przycisk Zakończ.</span><span class="sxs-lookup"><span data-stu-id="19496-140">Users can accept the wizard on the last wizard page by pressing a Finish button.</span></span>  
  
-   <span data-ttu-id="19496-141">Kreator zostało anulowane, Kreator zwraca wynik w odpowiednich i nie zwraca żadnych danych.</span><span class="sxs-lookup"><span data-stu-id="19496-141">If a wizard is canceled, the wizard returns an appropriate result, and does not return any data.</span></span>  
  
-   <span data-ttu-id="19496-142">Jeśli użytkownik akceptuje kreatora, Kreator zwraca wynik w odpowiednich i zwraca dane zebrane.</span><span class="sxs-lookup"><span data-stu-id="19496-142">If a user accepts a wizard, the wizard returns an appropriate result, and returns the data it collected.</span></span>  
  
-   <span data-ttu-id="19496-143">Po ukończeniu pracy kreatora (akceptowane lub anulowane), stron, które obejmuje kreatora są usuwane z dziennika.</span><span class="sxs-lookup"><span data-stu-id="19496-143">When the wizard is complete (accepted or canceled), the pages that the wizard comprises are removed from the journal.</span></span> <span data-ttu-id="19496-144">Dzięki temu każde wystąpienie Kreatora samodzielnie, zapobiegając potencjalnych danych lub nieprawidłowości stanu.</span><span class="sxs-lookup"><span data-stu-id="19496-144">This keeps each instance of the wizard isolated, thereby avoiding potential data or state anomalies.</span></span>  
  
<a name="Dynamic_Navigation_over_a_Fixed_Hierarchical_Topology"></a>   
## <a name="dynamic-navigation-over-a-fixed-hierarchical-topology"></a><span data-ttu-id="19496-145">Dynamiczne nawigacji w topologii hierarchicznej stałej</span><span class="sxs-lookup"><span data-stu-id="19496-145">Dynamic Navigation over a Fixed Hierarchical Topology</span></span>  
 <span data-ttu-id="19496-146">W niektórych aplikacjach strony umożliwiają nawigacji do dwóch lub więcej innych stron, jak pokazano na poniższej ilustracji.</span><span class="sxs-lookup"><span data-stu-id="19496-146">In some applications, pages allow navigation to two or more other pages, as shown in the following figure.</span></span>  
  
 <span data-ttu-id="19496-147">![Strona, która może przejść do wielu stron](../../../../docs/framework/wpf/app-development/media/navigationtopologyfigure2.png "NavigationTopologyFigure2")</span><span class="sxs-lookup"><span data-stu-id="19496-147">![A page that can navigate to multiple pages](../../../../docs/framework/wpf/app-development/media/navigationtopologyfigure2.png "NavigationTopologyFigure2")</span></span>  
  
 <span data-ttu-id="19496-148">Ta struktura jest określane jako stały topologii hierarchicznej i sekwencji, w którym przecina w hierarchii jest często określana w czasie wykonywania przez użytkownika lub aplikacji.</span><span class="sxs-lookup"><span data-stu-id="19496-148">This structure is known as a fixed hierarchical topology, and the sequence in which the hierarchy is traversed is often determined at run time by either the application or the user.</span></span> <span data-ttu-id="19496-149">W czasie wykonywania każdej strony w hierarchii, które umożliwia nawigacji do dwóch lub więcej stron zbiera dane wymagane do określenia, aby przejść do strony.</span><span class="sxs-lookup"><span data-stu-id="19496-149">At run time, each page in the hierarchy that allows navigation to two or more other pages gathers the data required to determine which page to navigate to.</span></span> <span data-ttu-id="19496-150">Poniższa ilustracja przedstawia jedną z kilku sekwencji nawigacji możliwe oparte na powyższej ilustracji.</span><span class="sxs-lookup"><span data-stu-id="19496-150">The following figure illustrates one of several possible navigation sequences based on the previous figure.</span></span>  
  
 <span data-ttu-id="19496-151">![Diagram topologii nawigacji](../../../../docs/framework/wpf/app-development/media/navigationtopologyfigure3.png "NavigationTopologyFigure3")</span><span class="sxs-lookup"><span data-stu-id="19496-151">![Navigation topology diagram](../../../../docs/framework/wpf/app-development/media/navigationtopologyfigure3.png "NavigationTopologyFigure3")</span></span>  
  
 <span data-ttu-id="19496-152">Mimo że sekwencji, w którym są przejście stron w strukturze hierarchicznej stałej jest określana w czasie wykonywania, środowisko użytkownika jest taka sama jak czynności użytkownika dla stałej topologii liniowej:</span><span class="sxs-lookup"><span data-stu-id="19496-152">Even though the sequence in which pages in a fixed hierarchical structure are navigated is determined at run time, the user experience is the same as the user experience for a fixed linear topology:</span></span>  
  
-   <span data-ttu-id="19496-153">Przejście ze strony wywołania do strony uruchamiania, która inicjuje kreatora i przechodzi do pierwszej strony kreatora.</span><span class="sxs-lookup"><span data-stu-id="19496-153">Navigating from the calling page to a launcher page that initializes the wizard and navigates to the first wizard page.</span></span> <span data-ttu-id="19496-154">Strona uruchamiania ( [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]-mniej <xref:System.Windows.Navigation.PageFunction%601>) nie jest wymagana, ponieważ wywołujący strony można wywołać bezpośrednio pierwszej stronie kreatora.</span><span class="sxs-lookup"><span data-stu-id="19496-154">A launcher page (a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]-less <xref:System.Windows.Navigation.PageFunction%601>) is not required, since a calling page can call the first wizard page directly.</span></span> <span data-ttu-id="19496-155">Przy użyciu strony uruchamiania, jednak może uprościć Kreatora inicjowania, zwłaszcza w wypadku inicjowania jest złożony.</span><span class="sxs-lookup"><span data-stu-id="19496-155">Using a launcher page, however, can simplify wizard initialization, particularly if initialization is complex.</span></span>  
  
-   <span data-ttu-id="19496-156">Użytkownicy mogą przechodzić między stronami przy użyciu Wstecz i do przodu przycisków (lub hiperłącza).</span><span class="sxs-lookup"><span data-stu-id="19496-156">Users can navigate between pages by using Back and Forward buttons (or hyperlinks).</span></span>  
  
-   <span data-ttu-id="19496-157">Użytkownicy mogą przechodzić między stronami przy użyciu arkusza.</span><span class="sxs-lookup"><span data-stu-id="19496-157">Users can navigate between pages using the journal.</span></span>  
  
-   <span data-ttu-id="19496-158">Użytkownicy mogą zmieniać kolejności nawigacji, jeśli nawigowania wstecz dziennika.</span><span class="sxs-lookup"><span data-stu-id="19496-158">Users can change the navigation sequence if they navigate back through the journal.</span></span>  
  
-   <span data-ttu-id="19496-159">Użytkownicy mogą anulować pracę z kreatorem z dowolnej strony kreatora, naciskając przycisk Anuluj.</span><span class="sxs-lookup"><span data-stu-id="19496-159">Users can cancel the wizard from any wizard page by pressing a Cancel button.</span></span>  
  
-   <span data-ttu-id="19496-160">Użytkownicy mogą akceptować kreatora na ostatniej stronie kreatora, naciskając przycisk Zakończ.</span><span class="sxs-lookup"><span data-stu-id="19496-160">Users can accept the wizard on the last wizard page by pressing a Finish button.</span></span>  
  
-   <span data-ttu-id="19496-161">Kreator zostało anulowane, Kreator zwraca wynik w odpowiednich i nie zwraca żadnych danych.</span><span class="sxs-lookup"><span data-stu-id="19496-161">If a wizard is canceled, the wizard returns an appropriate result, and does not return any data.</span></span>  
  
-   <span data-ttu-id="19496-162">Jeśli użytkownik akceptuje kreatora, Kreator zwraca wynik w odpowiednich i zwraca dane zebrane.</span><span class="sxs-lookup"><span data-stu-id="19496-162">If a user accepts a wizard, the wizard returns an appropriate result, and returns the data it collected.</span></span>  
  
-   <span data-ttu-id="19496-163">Po ukończeniu pracy kreatora (akceptowane lub anulowane), stron, które obejmuje kreatora są usuwane z dziennika.</span><span class="sxs-lookup"><span data-stu-id="19496-163">When the wizard is complete (accepted or canceled), the pages that the wizard comprises are removed from the journal.</span></span> <span data-ttu-id="19496-164">Dzięki temu każde wystąpienie Kreatora samodzielnie, zapobiegając potencjalnych danych lub nieprawidłowości stanu.</span><span class="sxs-lookup"><span data-stu-id="19496-164">This keeps each instance of the wizard isolated, thereby avoiding potential data or state anomalies.</span></span>  
  
<a name="Navigation_over_a_Dynamically_Generated_Topology"></a>   
## <a name="navigation-over-a-dynamically-generated-topology"></a><span data-ttu-id="19496-165">Nawigacji na dynamicznie generowanym topologii</span><span class="sxs-lookup"><span data-stu-id="19496-165">Navigation over a Dynamically Generated Topology</span></span>  
 <span data-ttu-id="19496-166">W niektórych aplikacjach sekwencji, w którym są przejście dwóch lub więcej stron tylko można określić w czasie wykonywania przez użytkownika, aplikacji lub danych zewnętrznych.</span><span class="sxs-lookup"><span data-stu-id="19496-166">In some applications, the sequence in which two or more pages are navigated can only be determined at run time, whether by the user, the application, or external data.</span></span> <span data-ttu-id="19496-167">Na poniższym rysunku przedstawiono zestaw stron z sekwencją nieokreślonej nawigacji.</span><span class="sxs-lookup"><span data-stu-id="19496-167">The following figure illustrates a set of pages with an undetermined navigation sequence.</span></span>  
  
 <span data-ttu-id="19496-168">![Diagram topologii nawigacji](../../../../docs/framework/wpf/app-development/media/navigationtopologyfigure4.png "NavigationTopologyFigure4")</span><span class="sxs-lookup"><span data-stu-id="19496-168">![Navigation topology diagram](../../../../docs/framework/wpf/app-development/media/navigationtopologyfigure4.png "NavigationTopologyFigure4")</span></span>  
  
 <span data-ttu-id="19496-169">Następny rysunek przedstawia sekwencji nawigacji, który został wybrany przez użytkownika w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="19496-169">The next figure illustrates a navigation sequence that was chosen by the user at run time.</span></span>  
  
 <span data-ttu-id="19496-170">![Diagram nawigacji](../../../../docs/framework/wpf/app-development/media/navigationtopologyfigure5.png "NavigationTopologyFigure5")</span><span class="sxs-lookup"><span data-stu-id="19496-170">![Navigation diagram](../../../../docs/framework/wpf/app-development/media/navigationtopologyfigure5.png "NavigationTopologyFigure5")</span></span>  
  
 <span data-ttu-id="19496-171">Sekwencja nawigacji jest określany jako dynamicznie generowanym topologii.</span><span class="sxs-lookup"><span data-stu-id="19496-171">The navigation sequence is known as a dynamically generated topology.</span></span> <span data-ttu-id="19496-172">Dla użytkownika jako w innych topologiach nawigacji środowisko użytkownika jest taki sam jak dla poprzedniego topologie jest:</span><span class="sxs-lookup"><span data-stu-id="19496-172">For the user, as with the other navigation topologies, the user experience is the same as it is for the previous topologies:</span></span>  
  
-   <span data-ttu-id="19496-173">Przejście ze strony wywołania do strony uruchamiania, która inicjuje kreatora i przechodzi do pierwszej strony kreatora.</span><span class="sxs-lookup"><span data-stu-id="19496-173">Navigating from the calling page to a launcher page that initializes the wizard and navigates to the first wizard page.</span></span> <span data-ttu-id="19496-174">Strona uruchamiania ( [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]-mniej <xref:System.Windows.Navigation.PageFunction%601>) nie jest wymagana, ponieważ wywołujący strony można wywołać bezpośrednio pierwszej stronie kreatora.</span><span class="sxs-lookup"><span data-stu-id="19496-174">A launcher page (a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]-less <xref:System.Windows.Navigation.PageFunction%601>) is not required, since a calling page can call the first wizard page directly.</span></span> <span data-ttu-id="19496-175">Przy użyciu strony uruchamiania, jednak może uprościć Kreatora inicjowania, zwłaszcza w wypadku inicjowania jest złożony.</span><span class="sxs-lookup"><span data-stu-id="19496-175">Using a launcher page, however, can simplify wizard initialization, particularly if initialization is complex.</span></span>  
  
-   <span data-ttu-id="19496-176">Użytkownicy mogą przechodzić między stronami przy użyciu Wstecz i do przodu przycisków (lub hiperłącza).</span><span class="sxs-lookup"><span data-stu-id="19496-176">Users can navigate between pages by using Back and Forward buttons (or hyperlinks).</span></span>  
  
-   <span data-ttu-id="19496-177">Użytkownicy mogą przechodzić między stronami przy użyciu arkusza.</span><span class="sxs-lookup"><span data-stu-id="19496-177">Users can navigate between pages using the journal.</span></span>  
  
-   <span data-ttu-id="19496-178">Użytkownicy mogą anulować pracę z kreatorem z dowolnej strony kreatora, naciskając przycisk Anuluj.</span><span class="sxs-lookup"><span data-stu-id="19496-178">Users can cancel the wizard from any wizard page by pressing a Cancel button.</span></span>  
  
-   <span data-ttu-id="19496-179">Użytkownicy mogą akceptować kreatora na ostatniej stronie kreatora, naciskając przycisk Zakończ.</span><span class="sxs-lookup"><span data-stu-id="19496-179">Users can accept the wizard on the last wizard page by pressing a Finish button.</span></span>  
  
-   <span data-ttu-id="19496-180">Kreator zostało anulowane, Kreator zwraca wynik w odpowiednich i nie zwraca żadnych danych.</span><span class="sxs-lookup"><span data-stu-id="19496-180">If a wizard is canceled, the wizard returns an appropriate result, and does not return any data.</span></span>  
  
-   <span data-ttu-id="19496-181">Jeśli użytkownik akceptuje kreatora, Kreator zwraca wynik w odpowiednich i zwraca dane zebrane.</span><span class="sxs-lookup"><span data-stu-id="19496-181">If a user accepts a wizard, the wizard returns an appropriate result, and returns the data it collected.</span></span>  
  
-   <span data-ttu-id="19496-182">Po ukończeniu pracy kreatora (akceptowane lub anulowane), stron, które obejmuje kreatora są usuwane z dziennika.</span><span class="sxs-lookup"><span data-stu-id="19496-182">When the wizard is complete (accepted or canceled), the pages that the wizard comprises are removed from the journal.</span></span> <span data-ttu-id="19496-183">Dzięki temu każde wystąpienie Kreatora samodzielnie, zapobiegając potencjalnych danych lub nieprawidłowości stanu.</span><span class="sxs-lookup"><span data-stu-id="19496-183">This keeps each instance of the wizard isolated, thereby avoiding potential data or state anomalies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19496-184">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="19496-184">See Also</span></span>  
 <xref:System.Windows.Controls.Page>  
 <xref:System.Windows.Navigation.PageFunction%601>  
 <xref:System.Windows.Navigation.NavigationService>  
 [<span data-ttu-id="19496-185">Strukturyzowana nawigacja — omówienie</span><span class="sxs-lookup"><span data-stu-id="19496-185">Structured Navigation Overview</span></span>](../../../../docs/framework/wpf/app-development/structured-navigation-overview.md)
