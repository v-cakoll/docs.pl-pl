---
title: Przegląd Topologia nawigacji
ms.date: 03/30/2017
helpviewer_keywords:
- linear topology [WPF]
- fixed hierarchical topology [WPF]
- fixed linear topology [WPF]
- topologies [WPF]
- navigation topologies [WPF]
- dynamically-generated topology
ms.assetid: 5d5ee837-629a-4933-869a-186dc22ac43d
ms.openlocfilehash: b62432d64393f4fb749af2e25c42e2e0161de219
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69950746"
---
# <a name="navigation-topologies-overview"></a><span data-ttu-id="17c96-102">Przegląd Topologia nawigacji</span><span class="sxs-lookup"><span data-stu-id="17c96-102">Navigation Topologies Overview</span></span>
<a name="introduction"></a><span data-ttu-id="17c96-103">To omówienie zawiera wprowadzenie do topologii nawigacji w [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]programie.</span><span class="sxs-lookup"><span data-stu-id="17c96-103">This overview provides an introduction to navigation topologies in [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].</span></span> <span data-ttu-id="17c96-104">Trzy popularne topologie nawigacji wraz z przykładami zostały omówione w dalszej części.</span><span class="sxs-lookup"><span data-stu-id="17c96-104">Three common navigation topologies, with samples, are subsequently discussed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="17c96-105">Przed przeczytaniem tego tematu należy zapoznać się z koncepcją nawigacji [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] strukturalnej przy użyciu funkcji strony.</span><span class="sxs-lookup"><span data-stu-id="17c96-105">Before reading this topic, you should be familiar with the concept of structured navigation in [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] using page functions.</span></span> <span data-ttu-id="17c96-106">Aby uzyskać więcej informacji na temat obu tych tematów, zobacz [Omówienie nawigacji strukturalnej](structured-navigation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="17c96-106">For more information on both of these topics, see [Structured Navigation Overview](structured-navigation-overview.md).</span></span>  
  
 <span data-ttu-id="17c96-107">Ten temat zawiera następujące sekcje:</span><span class="sxs-lookup"><span data-stu-id="17c96-107">This topic contains the following sections:</span></span>  
  
- [<span data-ttu-id="17c96-108">Topologie nawigacji</span><span class="sxs-lookup"><span data-stu-id="17c96-108">Navigation Topologies</span></span>](#Navigation_Topologies)  
  
- [<span data-ttu-id="17c96-109">Topologie nawigacji strukturalnej</span><span class="sxs-lookup"><span data-stu-id="17c96-109">Structured Navigation Topologies</span></span>](#Structured_Navigation_Topologies)  
  
- [<span data-ttu-id="17c96-110">Nawigowanie po stałej topologii liniowej</span><span class="sxs-lookup"><span data-stu-id="17c96-110">Navigation over a Fixed Linear Topology</span></span>](#Navigation_over_a_Fixed_Linear_Topology)  
  
- [<span data-ttu-id="17c96-111">Dynamiczna Nawigacja w ramach stałej topologii hierarchicznej</span><span class="sxs-lookup"><span data-stu-id="17c96-111">Dynamic Navigation over a Fixed Hierarchical Topology</span></span>](#Dynamic_Navigation_over_a_Fixed_Hierarchical_Topology)  
  
- [<span data-ttu-id="17c96-112">Nawigacja w ramach dynamicznie generowanej topologii</span><span class="sxs-lookup"><span data-stu-id="17c96-112">Navigation over a Dynamically Generated Topology</span></span>](#Navigation_over_a_Dynamically_Generated_Topology)  
  
<a name="Navigation_Topologies"></a>   
## <a name="navigation-topologies"></a><span data-ttu-id="17c96-113">Topologie nawigacji</span><span class="sxs-lookup"><span data-stu-id="17c96-113">Navigation Topologies</span></span>  
 <span data-ttu-id="17c96-114">W [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]programie Nawigacja zwykle składa się ze<xref:System.Windows.Controls.Page>stron () za<xref:System.Windows.Documents.Hyperlink>pomocą hiperlinków (), które przeprowadzą do innych stron po kliknięciu.</span><span class="sxs-lookup"><span data-stu-id="17c96-114">In [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], navigation typically consists of pages (<xref:System.Windows.Controls.Page>) with hyperlinks (<xref:System.Windows.Documents.Hyperlink>) that navigate to other pages when clicked.</span></span> <span data-ttu-id="17c96-115">Strony, do których prowadzi przechodzenie, są [!INCLUDE[TLA#tla_uri#plural](../../../../includes/tlasharptla-urisharpplural-md.md)] identyfikowane przez (zobacz [identyfikatory URI pakietu w WPF](pack-uris-in-wpf.md)).</span><span class="sxs-lookup"><span data-stu-id="17c96-115">Pages that are navigated to are identified by [!INCLUDE[TLA#tla_uri#plural](../../../../includes/tlasharptla-urisharpplural-md.md)] (see [Pack URIs in WPF](pack-uris-in-wpf.md)).</span></span> <span data-ttu-id="17c96-116">Rozważmy następujący prosty przykład pokazujący strony, hiperłącza i [!INCLUDE[TLA#tla_uri#plural](../../../../includes/tlasharptla-urisharpplural-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="17c96-116">Consider the following simple example that shows pages, hyperlinks, and [!INCLUDE[TLA#tla_uri#plural](../../../../includes/tlasharptla-urisharpplural-md.md)]:</span></span>  
  
 [!code-xaml[NavigationTopologiesOverviewSnippets#Page1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationTopologiesOverviewSnippets/CS/Page1.xaml#page1)]  
  
 [!code-xaml[NavigationTopologiesOverviewSnippets#Page2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationTopologiesOverviewSnippets/CS/Page2.xaml#page2)]  
  
 <span data-ttu-id="17c96-117">Te strony są rozmieszczone w *topologii nawigacyjnej* , której struktura jest określana w sposób, w jaki można przechodzić między stronami.</span><span class="sxs-lookup"><span data-stu-id="17c96-117">These pages are arranged in a *navigation topology* whose structure is determined by how you can navigate between the pages.</span></span> <span data-ttu-id="17c96-118">Ta topologia nawigacji jest odpowiednia w prostych scenariuszach, chociaż Nawigacja może wymagać bardziej złożonych topologii, a niektóre z nich można zdefiniować tylko wtedy, gdy aplikacja jest uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="17c96-118">This particular navigation topology is suitable in simple scenarios, although navigation can require more complex topologies, some of which can only be defined when an application is running.</span></span>  
  
 <span data-ttu-id="17c96-119">W tym temacie opisano trzy popularne topologie nawigacji: *stałe liniowe*, *stałe*, hierarchiczne i *dynamicznie generowane*.</span><span class="sxs-lookup"><span data-stu-id="17c96-119">This topic covers three common navigation topologies: *fixed linear*, *fixed hierarchical*, and *dynamically generated*.</span></span> <span data-ttu-id="17c96-120">Każda topologia nawigacji jest przedstawiona przy użyciu przykładu [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] , który ma taki sam sposób jak ten, który jest przedstawiony na poniższym rysunku:</span><span class="sxs-lookup"><span data-stu-id="17c96-120">Each navigation topology is demonstrated with a sample that has a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] like the one that is shown in the following figure:</span></span>  
  
 ![Strony zadań z elementami danych i przyciskami nawigacji.](./media/navigation-topologies-overview/navigation-topology-data-items.png)  
  
<a name="Structured_Navigation_Topologies"></a>   
## <a name="structured-navigation-topologies"></a><span data-ttu-id="17c96-122">Topologie nawigacji strukturalnej</span><span class="sxs-lookup"><span data-stu-id="17c96-122">Structured Navigation Topologies</span></span>  
 <span data-ttu-id="17c96-123">Istnieją dwa popularne typy topologii nawigacyjnej:</span><span class="sxs-lookup"><span data-stu-id="17c96-123">There are two broad types of navigation topologies:</span></span>  
  
- <span data-ttu-id="17c96-124">**Stała topologia**: zdefiniowana w czasie kompilacji i nie zmienia się w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="17c96-124">**Fixed Topology**: defined at compile time and does not change at run time.</span></span> <span data-ttu-id="17c96-125">Stałe topologie są przydatne do nawigacji przez stałą sekwencję stron w kolejności liniowej lub hierarchicznej.</span><span class="sxs-lookup"><span data-stu-id="17c96-125">Fixed topologies are useful for navigation through a fixed sequence of pages in either a linear or hierarchical order.</span></span>  
  
- <span data-ttu-id="17c96-126">**Topologia dynamiczna**: zdefiniowana w czasie wykonywania na podstawie danych wejściowych zbieranych od użytkownika, aplikacji lub systemu.</span><span class="sxs-lookup"><span data-stu-id="17c96-126">**Dynamic Topology**: defined at run time based on input that is collected from the user, the application, or the system.</span></span> <span data-ttu-id="17c96-127">Topologie dynamiczne są przydatne, gdy strony można nawigować w różnych sekwencjach.</span><span class="sxs-lookup"><span data-stu-id="17c96-127">Dynamic topologies are useful when pages can be navigated in different sequences.</span></span>  
  
 <span data-ttu-id="17c96-128">Chociaż istnieje możliwość tworzenia topologii nawigacji przy użyciu stron, przykłady używają funkcji strony, ponieważ zapewniają dodatkową pomoc techniczną, która upraszcza obsługę przekazywania i zwracania danych za pośrednictwem stron topologii.</span><span class="sxs-lookup"><span data-stu-id="17c96-128">Although it is possible to create navigation topologies using pages, the samples use page functions because they provide additional support that simplifies support for passing and returning data through the pages of a topology.</span></span>  
  
<a name="Navigation_over_a_Fixed_Linear_Topology"></a>   
## <a name="navigation-over-a-fixed-linear-topology"></a><span data-ttu-id="17c96-129">Nawigowanie po stałej topologii liniowej</span><span class="sxs-lookup"><span data-stu-id="17c96-129">Navigation over a Fixed Linear Topology</span></span>  
 <span data-ttu-id="17c96-130">Stała topologia liniowa jest analogiczna do struktury kreatora, która zawiera co najmniej jedną stronę kreatora, która jest używana w ustalonej kolejności.</span><span class="sxs-lookup"><span data-stu-id="17c96-130">A fixed linear topology is analogous to the structure of a wizard that has one or more wizard pages that are navigated in a fixed sequence.</span></span> <span data-ttu-id="17c96-131">Na poniższej ilustracji przedstawiono strukturę i przepływ kreatora ze stałą topologią liniową:</span><span class="sxs-lookup"><span data-stu-id="17c96-131">The following figure shows the high-level structure and flow of a wizard with a fixed linear topology:</span></span>  
  
 ![Diagram przedstawiający stałą topologię liniową.](./media/navigation-topologies-overview/navigation-topology-fixed-linear.png)  
  
 <span data-ttu-id="17c96-133">Typowe zachowania w przypadku nawigowania po ustalonej topologii liniowej obejmują następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="17c96-133">The typical behaviors for navigating over a fixed linear topology include the following:</span></span>  
  
- <span data-ttu-id="17c96-134">Nawigowanie ze strony wywołującej do strony uruchamiania, która inicjuje kreatora i przechodzi do pierwszej strony kreatora.</span><span class="sxs-lookup"><span data-stu-id="17c96-134">Navigating from the calling page to a launcher page that initializes the wizard and navigates to the first wizard page.</span></span> <span data-ttu-id="17c96-135">Strona uruchamiania (a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]-less <xref:System.Windows.Navigation.PageFunction%601>) nie jest wymagana, ponieważ strona wywołująca może bezpośrednio wywołać pierwszą stronę kreatora.</span><span class="sxs-lookup"><span data-stu-id="17c96-135">A launcher page (a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]-less <xref:System.Windows.Navigation.PageFunction%601>) is not required, since a calling page can call the first wizard page directly.</span></span> <span data-ttu-id="17c96-136">Za pomocą strony uruchamiania można jednak uprościć inicjowanie kreatora, szczególnie jeśli Inicjalizacja jest złożona.</span><span class="sxs-lookup"><span data-stu-id="17c96-136">Using a launcher page, however, can simplify wizard initialization, particularly if initialization is complex.</span></span>  
  
- <span data-ttu-id="17c96-137">Użytkownicy mogą przechodzić między stronami przy użyciu przycisków Wstecz i dalej (lub hiperlinków).</span><span class="sxs-lookup"><span data-stu-id="17c96-137">Users can navigate between pages by using Back and Forward buttons (or hyperlinks).</span></span>  
  
- <span data-ttu-id="17c96-138">Użytkownicy mogą przechodzić między stronami przy użyciu dziennika.</span><span class="sxs-lookup"><span data-stu-id="17c96-138">Users can navigate between pages using the journal.</span></span>  
  
- <span data-ttu-id="17c96-139">Użytkownicy mogą anulować pracę kreatora z dowolnej strony kreatora, naciskając przycisk Anuluj.</span><span class="sxs-lookup"><span data-stu-id="17c96-139">Users can cancel the wizard from any wizard page by pressing a Cancel button.</span></span>  
  
- <span data-ttu-id="17c96-140">Użytkownicy mogą zaakceptować kreatora na ostatniej stronie kreatora, naciskając przycisk Zakończ.</span><span class="sxs-lookup"><span data-stu-id="17c96-140">Users can accept the wizard on the last wizard page by pressing a Finish button.</span></span>  
  
- <span data-ttu-id="17c96-141">Jeśli Kreator zostanie anulowany, Kreator zwróci odpowiedni wynik i nie zwróci żadnych danych.</span><span class="sxs-lookup"><span data-stu-id="17c96-141">If a wizard is canceled, the wizard returns an appropriate result, and does not return any data.</span></span>  
  
- <span data-ttu-id="17c96-142">Jeśli użytkownik zaakceptuje kreatora, Kreator zwróci odpowiedni wynik i zwróci zebrane dane.</span><span class="sxs-lookup"><span data-stu-id="17c96-142">If a user accepts a wizard, the wizard returns an appropriate result, and returns the data it collected.</span></span>  
  
- <span data-ttu-id="17c96-143">Po zakończeniu pracy kreatora (zaakceptowane lub anulowane) strony, które składają się Kreator, są usuwane z dziennika.</span><span class="sxs-lookup"><span data-stu-id="17c96-143">When the wizard is complete (accepted or canceled), the pages that the wizard comprises are removed from the journal.</span></span> <span data-ttu-id="17c96-144">Pozwala to na odizolowanie każdego wystąpienia kreatora, co pozwala uniknąć potencjalnych różnic danych lub stanu.</span><span class="sxs-lookup"><span data-stu-id="17c96-144">This keeps each instance of the wizard isolated, thereby avoiding potential data or state anomalies.</span></span>  
  
<a name="Dynamic_Navigation_over_a_Fixed_Hierarchical_Topology"></a>   
## <a name="dynamic-navigation-over-a-fixed-hierarchical-topology"></a><span data-ttu-id="17c96-145">Dynamiczna Nawigacja w ramach stałej topologii hierarchicznej</span><span class="sxs-lookup"><span data-stu-id="17c96-145">Dynamic Navigation over a Fixed Hierarchical Topology</span></span>  
 <span data-ttu-id="17c96-146">W niektórych aplikacjach strony umożliwiają nawigację do dwóch lub więcej stron, jak pokazano na poniższym rysunku:</span><span class="sxs-lookup"><span data-stu-id="17c96-146">In some applications, pages allow navigation to two or more other pages, as shown in the following figure:</span></span> 
  
 ![Diagram pokazujący stronę, która może przechodzić do wielu stron.](./media/navigation-topologies-overview/navigation-topology-multiple-pages.png)  
  
 <span data-ttu-id="17c96-148">Ta struktura jest znana jako stała hierarchiczna topologia, a sekwencja, w której przechodzą hierarchie, jest często określana w czasie wykonywania przez aplikację lub użytkownika.</span><span class="sxs-lookup"><span data-stu-id="17c96-148">This structure is known as a fixed hierarchical topology, and the sequence in which the hierarchy is traversed is often determined at run time by either the application or the user.</span></span> <span data-ttu-id="17c96-149">W czasie wykonywania każda Strona w hierarchii, która umożliwia nawigowanie do dwóch lub więcej stron, zbiera dane wymagane do określenia, do której strony należy przejść.</span><span class="sxs-lookup"><span data-stu-id="17c96-149">At run time, each page in the hierarchy that allows navigation to two or more other pages gathers the data required to determine which page to navigate to.</span></span> <span data-ttu-id="17c96-150">Na poniższej ilustracji przedstawiono jedną z kilku możliwych sekwencji nawigacji na podstawie poprzedniej ilustracji:</span><span class="sxs-lookup"><span data-stu-id="17c96-150">The following figure illustrates one of several possible navigation sequences based on the previous figure:</span></span>  
  
 ![Diagram, który pokazuje możliwe sekwencję nawigacji.](./media/navigation-topologies-overview/navigation-topology-fixed-hierarchical.png)  
  
 <span data-ttu-id="17c96-152">Mimo że przechodzenie między stronami w stałej strukturze hierarchicznej jest określane w czasie wykonywania, środowisko użytkownika jest takie samo jak środowisko użytkownika dla stałej topologii liniowej:</span><span class="sxs-lookup"><span data-stu-id="17c96-152">Even though the sequence in which pages in a fixed hierarchical structure are navigated is determined at run time, the user experience is the same as the user experience for a fixed linear topology:</span></span>  
  
- <span data-ttu-id="17c96-153">Nawigowanie ze strony wywołującej do strony uruchamiania, która inicjuje kreatora i przechodzi do pierwszej strony kreatora.</span><span class="sxs-lookup"><span data-stu-id="17c96-153">Navigating from the calling page to a launcher page that initializes the wizard and navigates to the first wizard page.</span></span> <span data-ttu-id="17c96-154">Strona uruchamiania (a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]-less <xref:System.Windows.Navigation.PageFunction%601>) nie jest wymagana, ponieważ strona wywołująca może bezpośrednio wywołać pierwszą stronę kreatora.</span><span class="sxs-lookup"><span data-stu-id="17c96-154">A launcher page (a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]-less <xref:System.Windows.Navigation.PageFunction%601>) is not required, since a calling page can call the first wizard page directly.</span></span> <span data-ttu-id="17c96-155">Za pomocą strony uruchamiania można jednak uprościć inicjowanie kreatora, szczególnie jeśli Inicjalizacja jest złożona.</span><span class="sxs-lookup"><span data-stu-id="17c96-155">Using a launcher page, however, can simplify wizard initialization, particularly if initialization is complex.</span></span>  
  
- <span data-ttu-id="17c96-156">Użytkownicy mogą przechodzić między stronami przy użyciu przycisków Wstecz i dalej (lub hiperlinków).</span><span class="sxs-lookup"><span data-stu-id="17c96-156">Users can navigate between pages by using Back and Forward buttons (or hyperlinks).</span></span>  
  
- <span data-ttu-id="17c96-157">Użytkownicy mogą przechodzić między stronami przy użyciu dziennika.</span><span class="sxs-lookup"><span data-stu-id="17c96-157">Users can navigate between pages using the journal.</span></span>  
  
- <span data-ttu-id="17c96-158">Użytkownicy mogą zmienić sekwencję nawigacji, jeśli nawigują ponownie w dzienniku.</span><span class="sxs-lookup"><span data-stu-id="17c96-158">Users can change the navigation sequence if they navigate back through the journal.</span></span>  
  
- <span data-ttu-id="17c96-159">Użytkownicy mogą anulować pracę kreatora z dowolnej strony kreatora, naciskając przycisk Anuluj.</span><span class="sxs-lookup"><span data-stu-id="17c96-159">Users can cancel the wizard from any wizard page by pressing a Cancel button.</span></span>  
  
- <span data-ttu-id="17c96-160">Użytkownicy mogą zaakceptować kreatora na ostatniej stronie kreatora, naciskając przycisk Zakończ.</span><span class="sxs-lookup"><span data-stu-id="17c96-160">Users can accept the wizard on the last wizard page by pressing a Finish button.</span></span>  
  
- <span data-ttu-id="17c96-161">Jeśli Kreator zostanie anulowany, Kreator zwróci odpowiedni wynik i nie zwróci żadnych danych.</span><span class="sxs-lookup"><span data-stu-id="17c96-161">If a wizard is canceled, the wizard returns an appropriate result, and does not return any data.</span></span>  
  
- <span data-ttu-id="17c96-162">Jeśli użytkownik zaakceptuje kreatora, Kreator zwróci odpowiedni wynik i zwróci zebrane dane.</span><span class="sxs-lookup"><span data-stu-id="17c96-162">If a user accepts a wizard, the wizard returns an appropriate result, and returns the data it collected.</span></span>  
  
- <span data-ttu-id="17c96-163">Po zakończeniu pracy kreatora (zaakceptowane lub anulowane) strony, które składają się Kreator, są usuwane z dziennika.</span><span class="sxs-lookup"><span data-stu-id="17c96-163">When the wizard is complete (accepted or canceled), the pages that the wizard comprises are removed from the journal.</span></span> <span data-ttu-id="17c96-164">Pozwala to na odizolowanie każdego wystąpienia kreatora, co pozwala uniknąć potencjalnych różnic danych lub stanu.</span><span class="sxs-lookup"><span data-stu-id="17c96-164">This keeps each instance of the wizard isolated, thereby avoiding potential data or state anomalies.</span></span>  
  
<a name="Navigation_over_a_Dynamically_Generated_Topology"></a>   
## <a name="navigation-over-a-dynamically-generated-topology"></a><span data-ttu-id="17c96-165">Nawigacja w ramach dynamicznie generowanej topologii</span><span class="sxs-lookup"><span data-stu-id="17c96-165">Navigation over a Dynamically Generated Topology</span></span>  
 <span data-ttu-id="17c96-166">W niektórych aplikacjach sekwencja, w której są przechodź dwie lub więcej stron, można określić tylko w czasie wykonywania, niezależnie od tego, czy użytkownik, aplikacja lub dane zewnętrzne.</span><span class="sxs-lookup"><span data-stu-id="17c96-166">In some applications, the sequence in which two or more pages are navigated can only be determined at run time, whether by the user, the application, or external data.</span></span> <span data-ttu-id="17c96-167">Na poniższej ilustracji przedstawiono zestaw stron z nieokreśloną sekwencją nawigacji:</span><span class="sxs-lookup"><span data-stu-id="17c96-167">The following figure illustrates a set of pages with an undetermined navigation sequence:</span></span>  
  
 ![Zestaw stron z nieokreśloną sekwencją nawigacji.](./media/navigation-topologies-overview/navigation-topology-dynamically-generated.png)  
  
 <span data-ttu-id="17c96-169">Następny rysunek ilustruje sekwencję nawigacji, która została wybrana przez użytkownika w czasie wykonywania:</span><span class="sxs-lookup"><span data-stu-id="17c96-169">The next figure illustrates a navigation sequence that was chosen by the user at run time:</span></span>  
  
 ![Diagram pokazujący sekwencję nawigacji wybraną w czasie wykonywania.](./media/navigation-topologies-overview/navigation-topology-sequence-chosen-run-time.png)  
  
 <span data-ttu-id="17c96-171">Sekwencja nawigacji jest znana jako topologia generowana dynamicznie.</span><span class="sxs-lookup"><span data-stu-id="17c96-171">The navigation sequence is known as a dynamically generated topology.</span></span> <span data-ttu-id="17c96-172">Dla użytkownika, podobnie jak w przypadku innych topologii nawigacyjnej, środowisko użytkownika jest takie samo, jak w przypadku poprzednich topologii:</span><span class="sxs-lookup"><span data-stu-id="17c96-172">For the user, as with the other navigation topologies, the user experience is the same as it is for the previous topologies:</span></span>  
  
- <span data-ttu-id="17c96-173">Nawigowanie ze strony wywołującej do strony uruchamiania, która inicjuje kreatora i przechodzi do pierwszej strony kreatora.</span><span class="sxs-lookup"><span data-stu-id="17c96-173">Navigating from the calling page to a launcher page that initializes the wizard and navigates to the first wizard page.</span></span> <span data-ttu-id="17c96-174">Strona uruchamiania (a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]-less <xref:System.Windows.Navigation.PageFunction%601>) nie jest wymagana, ponieważ strona wywołująca może bezpośrednio wywołać pierwszą stronę kreatora.</span><span class="sxs-lookup"><span data-stu-id="17c96-174">A launcher page (a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]-less <xref:System.Windows.Navigation.PageFunction%601>) is not required, since a calling page can call the first wizard page directly.</span></span> <span data-ttu-id="17c96-175">Za pomocą strony uruchamiania można jednak uprościć inicjowanie kreatora, szczególnie jeśli Inicjalizacja jest złożona.</span><span class="sxs-lookup"><span data-stu-id="17c96-175">Using a launcher page, however, can simplify wizard initialization, particularly if initialization is complex.</span></span>  
  
- <span data-ttu-id="17c96-176">Użytkownicy mogą przechodzić między stronami przy użyciu przycisków Wstecz i dalej (lub hiperlinków).</span><span class="sxs-lookup"><span data-stu-id="17c96-176">Users can navigate between pages by using Back and Forward buttons (or hyperlinks).</span></span>  
  
- <span data-ttu-id="17c96-177">Użytkownicy mogą przechodzić między stronami przy użyciu dziennika.</span><span class="sxs-lookup"><span data-stu-id="17c96-177">Users can navigate between pages using the journal.</span></span>  
  
- <span data-ttu-id="17c96-178">Użytkownicy mogą anulować pracę kreatora z dowolnej strony kreatora, naciskając przycisk Anuluj.</span><span class="sxs-lookup"><span data-stu-id="17c96-178">Users can cancel the wizard from any wizard page by pressing a Cancel button.</span></span>  
  
- <span data-ttu-id="17c96-179">Użytkownicy mogą zaakceptować kreatora na ostatniej stronie kreatora, naciskając przycisk Zakończ.</span><span class="sxs-lookup"><span data-stu-id="17c96-179">Users can accept the wizard on the last wizard page by pressing a Finish button.</span></span>  
  
- <span data-ttu-id="17c96-180">Jeśli Kreator zostanie anulowany, Kreator zwróci odpowiedni wynik i nie zwróci żadnych danych.</span><span class="sxs-lookup"><span data-stu-id="17c96-180">If a wizard is canceled, the wizard returns an appropriate result, and does not return any data.</span></span>  
  
- <span data-ttu-id="17c96-181">Jeśli użytkownik zaakceptuje kreatora, Kreator zwróci odpowiedni wynik i zwróci zebrane dane.</span><span class="sxs-lookup"><span data-stu-id="17c96-181">If a user accepts a wizard, the wizard returns an appropriate result, and returns the data it collected.</span></span>  
  
- <span data-ttu-id="17c96-182">Po zakończeniu pracy kreatora (zaakceptowane lub anulowane) strony, które składają się Kreator, są usuwane z dziennika.</span><span class="sxs-lookup"><span data-stu-id="17c96-182">When the wizard is complete (accepted or canceled), the pages that the wizard comprises are removed from the journal.</span></span> <span data-ttu-id="17c96-183">Pozwala to na odizolowanie każdego wystąpienia kreatora, co pozwala uniknąć potencjalnych różnic danych lub stanu.</span><span class="sxs-lookup"><span data-stu-id="17c96-183">This keeps each instance of the wizard isolated, thereby avoiding potential data or state anomalies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17c96-184">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="17c96-184">See also</span></span>

- <xref:System.Windows.Controls.Page>
- <xref:System.Windows.Navigation.PageFunction%601>
- <xref:System.Windows.Navigation.NavigationService>
- [<span data-ttu-id="17c96-185">Strukturyzowana nawigacja — omówienie</span><span class="sxs-lookup"><span data-stu-id="17c96-185">Structured Navigation Overview</span></span>](structured-navigation-overview.md)
