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
ms.openlocfilehash: 08f6342095706e5ffe9479f5236457d21474152a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174202"
---
# <a name="navigation-topologies-overview"></a><span data-ttu-id="681c7-102">Przegląd Topologia nawigacji</span><span class="sxs-lookup"><span data-stu-id="681c7-102">Navigation Topologies Overview</span></span>
<a name="introduction"></a><span data-ttu-id="681c7-103">Ten przegląd zawiera wprowadzenie do topologii nawigacji w WPF.</span><span class="sxs-lookup"><span data-stu-id="681c7-103">This overview provides an introduction to navigation topologies in WPF.</span></span> <span data-ttu-id="681c7-104">Następnie omówione są trzy typowe topologie nawigacji z próbkami.</span><span class="sxs-lookup"><span data-stu-id="681c7-104">Three common navigation topologies, with samples, are subsequently discussed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="681c7-105">Przed przeczytaniem tego tematu, należy zapoznać się z pojęciem nawigacji strukturalnej w WPF przy użyciu funkcji strony.</span><span class="sxs-lookup"><span data-stu-id="681c7-105">Before reading this topic, you should be familiar with the concept of structured navigation in WPF using page functions.</span></span> <span data-ttu-id="681c7-106">Aby uzyskać więcej informacji na temat obu tych tematów, zobacz [Omówienie nawigacji strukturalnej](structured-navigation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="681c7-106">For more information on both of these topics, see [Structured Navigation Overview](structured-navigation-overview.md).</span></span>  
  
 <span data-ttu-id="681c7-107">Ten temat zawiera następujące sekcje:</span><span class="sxs-lookup"><span data-stu-id="681c7-107">This topic contains the following sections:</span></span>  
  
- [<span data-ttu-id="681c7-108">Topologie nawigacji</span><span class="sxs-lookup"><span data-stu-id="681c7-108">Navigation Topologies</span></span>](#Navigation_Topologies)  
  
- [<span data-ttu-id="681c7-109">Ustrukturyzowane topologie nawigacji</span><span class="sxs-lookup"><span data-stu-id="681c7-109">Structured Navigation Topologies</span></span>](#Structured_Navigation_Topologies)  
  
- [<span data-ttu-id="681c7-110">Nawigacja po stałej topologii liniowej</span><span class="sxs-lookup"><span data-stu-id="681c7-110">Navigation over a Fixed Linear Topology</span></span>](#Navigation_over_a_Fixed_Linear_Topology)  
  
- [<span data-ttu-id="681c7-111">Nawigacja dynamiczna nad stałą topologią hierarchiczną</span><span class="sxs-lookup"><span data-stu-id="681c7-111">Dynamic Navigation over a Fixed Hierarchical Topology</span></span>](#Dynamic_Navigation_over_a_Fixed_Hierarchical_Topology)  
  
- [<span data-ttu-id="681c7-112">Nawigacja po topologii generowanej dynamicznie</span><span class="sxs-lookup"><span data-stu-id="681c7-112">Navigation over a Dynamically Generated Topology</span></span>](#Navigation_over_a_Dynamically_Generated_Topology)  
  
<a name="Navigation_Topologies"></a>
## <a name="navigation-topologies"></a><span data-ttu-id="681c7-113">Topologie nawigacji</span><span class="sxs-lookup"><span data-stu-id="681c7-113">Navigation Topologies</span></span>  
 <span data-ttu-id="681c7-114">W WPF WPF nawigacja<xref:System.Windows.Controls.Page>zazwyczaj składa się<xref:System.Windows.Documents.Hyperlink>ze stron ( ) z hiperłączami ( ), które nawigują do innych stron po kliknięciu.</span><span class="sxs-lookup"><span data-stu-id="681c7-114">In WPF, navigation typically consists of pages (<xref:System.Windows.Controls.Page>) with hyperlinks (<xref:System.Windows.Documents.Hyperlink>) that navigate to other pages when clicked.</span></span> <span data-ttu-id="681c7-115">Strony, do których nawigowane są identyfikowane za pomocą jednolitych identyfikatorów zasobów (URI) (patrz [Uri pakietów w WPF).](pack-uris-in-wpf.md)</span><span class="sxs-lookup"><span data-stu-id="681c7-115">Pages that are navigated to are identified by uniform resource identifiers (URIs) (see [Pack URIs in WPF](pack-uris-in-wpf.md)).</span></span> <span data-ttu-id="681c7-116">Rozważmy następujący prosty przykład, który pokazuje strony, hiperłącza i jednolite identyfikatory zasobów (URI):</span><span class="sxs-lookup"><span data-stu-id="681c7-116">Consider the following simple example that shows pages, hyperlinks, and uniform resource identifiers (URIs):</span></span>  
  
 [!code-xaml[NavigationTopologiesOverviewSnippets#Page1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationTopologiesOverviewSnippets/CS/Page1.xaml#page1)]  
  
 [!code-xaml[NavigationTopologiesOverviewSnippets#Page2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationTopologiesOverviewSnippets/CS/Page2.xaml#page2)]  
  
 <span data-ttu-id="681c7-117">Strony te są rozmieszczone w *topologii nawigacji,* której struktura zależy od sposobu nawigacji między stronami.</span><span class="sxs-lookup"><span data-stu-id="681c7-117">These pages are arranged in a *navigation topology* whose structure is determined by how you can navigate between the pages.</span></span> <span data-ttu-id="681c7-118">Ta szczególna topologia nawigacji jest odpowiednia w prostych scenariuszach, chociaż nawigacja może wymagać bardziej złożonych topologii, z których niektóre można zdefiniować tylko wtedy, gdy aplikacja jest uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="681c7-118">This particular navigation topology is suitable in simple scenarios, although navigation can require more complex topologies, some of which can only be defined when an application is running.</span></span>  
  
 <span data-ttu-id="681c7-119">W tym temacie omówiono trzy typowe topologie nawigacji: *liniowy stały,* *stały hierarchiczny*i *generowany dynamicznie.*</span><span class="sxs-lookup"><span data-stu-id="681c7-119">This topic covers three common navigation topologies: *fixed linear*, *fixed hierarchical*, and *dynamically generated*.</span></span> <span data-ttu-id="681c7-120">Każda topologia nawigacji jest pokazana za [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] pomocą próbki, która ma podobny ten, który jest pokazany na poniższym rysunku:</span><span class="sxs-lookup"><span data-stu-id="681c7-120">Each navigation topology is demonstrated with a sample that has a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] like the one that is shown in the following figure:</span></span>  
  
 ![Strony zadań z elementami danych i przyciskami nawigacyjnymi.](./media/navigation-topologies-overview/navigation-topology-data-items.png)  
  
<a name="Structured_Navigation_Topologies"></a>
## <a name="structured-navigation-topologies"></a><span data-ttu-id="681c7-122">Ustrukturyzowane topologie nawigacji</span><span class="sxs-lookup"><span data-stu-id="681c7-122">Structured Navigation Topologies</span></span>  
 <span data-ttu-id="681c7-123">Istnieją dwa szerokie rodzaje topologii nawigacji:</span><span class="sxs-lookup"><span data-stu-id="681c7-123">There are two broad types of navigation topologies:</span></span>  
  
- <span data-ttu-id="681c7-124">**Stała topologia:** zdefiniowana w czasie kompilacji i nie zmienia się w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="681c7-124">**Fixed Topology**: defined at compile time and does not change at run time.</span></span> <span data-ttu-id="681c7-125">Poprawione topologie są przydatne do nawigacji po stałej sekwencji stron w kolejności liniowej lub hierarchicznej.</span><span class="sxs-lookup"><span data-stu-id="681c7-125">Fixed topologies are useful for navigation through a fixed sequence of pages in either a linear or hierarchical order.</span></span>  
  
- <span data-ttu-id="681c7-126">**Topologia dynamiczna:** zdefiniowana w czasie wykonywania na podstawie danych wejściowych zebranych od użytkownika, aplikacji lub systemu.</span><span class="sxs-lookup"><span data-stu-id="681c7-126">**Dynamic Topology**: defined at run time based on input that is collected from the user, the application, or the system.</span></span> <span data-ttu-id="681c7-127">Dynamiczne topologie są przydatne, gdy strony mogą poruszać się w różnych sekwencjach.</span><span class="sxs-lookup"><span data-stu-id="681c7-127">Dynamic topologies are useful when pages can be navigated in different sequences.</span></span>  
  
 <span data-ttu-id="681c7-128">Chociaż istnieje możliwość tworzenia topologii nawigacji przy użyciu stron, przykłady używają funkcji strony, ponieważ zapewniają dodatkową obsługę, która upraszcza obsługę przekazywania i zwracania danych za pośrednictwem stron topologii.</span><span class="sxs-lookup"><span data-stu-id="681c7-128">Although it is possible to create navigation topologies using pages, the samples use page functions because they provide additional support that simplifies support for passing and returning data through the pages of a topology.</span></span>  
  
<a name="Navigation_over_a_Fixed_Linear_Topology"></a>
## <a name="navigation-over-a-fixed-linear-topology"></a><span data-ttu-id="681c7-129">Nawigacja po stałej topologii liniowej</span><span class="sxs-lookup"><span data-stu-id="681c7-129">Navigation over a Fixed Linear Topology</span></span>  
 <span data-ttu-id="681c7-130">Stała topologia liniowa jest analogiczna do struktury kreatora, który ma jedną lub więcej stron kreatora, które są nawigowane w stałej kolejności.</span><span class="sxs-lookup"><span data-stu-id="681c7-130">A fixed linear topology is analogous to the structure of a wizard that has one or more wizard pages that are navigated in a fixed sequence.</span></span> <span data-ttu-id="681c7-131">Na poniższej ilustracji przedstawiono strukturę wysokiego poziomu i przepływ kreatora o stałej topologii liniowej:</span><span class="sxs-lookup"><span data-stu-id="681c7-131">The following figure shows the high-level structure and flow of a wizard with a fixed linear topology:</span></span>  
  
 ![Diagram przedstawiający stałą topologię liniową.](./media/navigation-topologies-overview/navigation-topology-fixed-linear.png)  
  
 <span data-ttu-id="681c7-133">Typowe zachowania podczas nawigacji po stałej topologii liniowej są następujące:</span><span class="sxs-lookup"><span data-stu-id="681c7-133">The typical behaviors for navigating over a fixed linear topology include the following:</span></span>  
  
- <span data-ttu-id="681c7-134">Przechodzenie ze strony wywołującej do strony uruchamiania, która inicjuje kreatora i przechodzi do pierwszej strony kreatora.</span><span class="sxs-lookup"><span data-stu-id="681c7-134">Navigating from the calling page to a launcher page that initializes the wizard and navigates to the first wizard page.</span></span> <span data-ttu-id="681c7-135">Strona uruchamiania (a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] <xref:System.Windows.Navigation.PageFunction%601>-less) nie jest wymagana, ponieważ strona wywołująca może wywołać pierwszą stronę kreatora bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="681c7-135">A launcher page (a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]-less <xref:System.Windows.Navigation.PageFunction%601>) is not required, since a calling page can call the first wizard page directly.</span></span> <span data-ttu-id="681c7-136">Za pomocą strony uruchamiania, jednak można uprościć inicjowania kreatora, szczególnie jeśli inicjowanie jest złożone.</span><span class="sxs-lookup"><span data-stu-id="681c7-136">Using a launcher page, however, can simplify wizard initialization, particularly if initialization is complex.</span></span>  
  
- <span data-ttu-id="681c7-137">Użytkownicy mogą nawigować między stronami za pomocą przycisków Wstecz i Dalej (lub hiperłączy).</span><span class="sxs-lookup"><span data-stu-id="681c7-137">Users can navigate between pages by using Back and Forward buttons (or hyperlinks).</span></span>  
  
- <span data-ttu-id="681c7-138">Użytkownicy mogą nawigować między stronami za pomocą arkusza.</span><span class="sxs-lookup"><span data-stu-id="681c7-138">Users can navigate between pages using the journal.</span></span>  
  
- <span data-ttu-id="681c7-139">Użytkownicy mogą anulować kreatora z dowolnej strony kreatora, naciskając przycisk Anuluj.</span><span class="sxs-lookup"><span data-stu-id="681c7-139">Users can cancel the wizard from any wizard page by pressing a Cancel button.</span></span>  
  
- <span data-ttu-id="681c7-140">Użytkownicy mogą zaakceptować kreatora na ostatniej stronie kreatora, naciskając przycisk Zakończ.</span><span class="sxs-lookup"><span data-stu-id="681c7-140">Users can accept the wizard on the last wizard page by pressing a Finish button.</span></span>  
  
- <span data-ttu-id="681c7-141">Jeśli kreator zostanie anulowany, kreator zwraca odpowiedni wynik i nie zwraca żadnych danych.</span><span class="sxs-lookup"><span data-stu-id="681c7-141">If a wizard is canceled, the wizard returns an appropriate result, and does not return any data.</span></span>  
  
- <span data-ttu-id="681c7-142">Jeśli użytkownik zaakceptuje kreatora, kreator zwraca odpowiedni wynik i zwraca zebrane dane.</span><span class="sxs-lookup"><span data-stu-id="681c7-142">If a user accepts a wizard, the wizard returns an appropriate result, and returns the data it collected.</span></span>  
  
- <span data-ttu-id="681c7-143">Po zakończeniu pracy kreatora (zaakceptowaniu lub anulowaniu) strony, w skład których wchodzi kreator, zostaną usunięte z dziennika.</span><span class="sxs-lookup"><span data-stu-id="681c7-143">When the wizard is complete (accepted or canceled), the pages that the wizard comprises are removed from the journal.</span></span> <span data-ttu-id="681c7-144">Dzięki temu każde wystąpienie kreatora jest izolowane, co pozwala uniknąć potencjalnych anomalii danych lub stanu.</span><span class="sxs-lookup"><span data-stu-id="681c7-144">This keeps each instance of the wizard isolated, thereby avoiding potential data or state anomalies.</span></span>  
  
<a name="Dynamic_Navigation_over_a_Fixed_Hierarchical_Topology"></a>
## <a name="dynamic-navigation-over-a-fixed-hierarchical-topology"></a><span data-ttu-id="681c7-145">Nawigacja dynamiczna nad stałą topologią hierarchiczną</span><span class="sxs-lookup"><span data-stu-id="681c7-145">Dynamic Navigation over a Fixed Hierarchical Topology</span></span>  
 <span data-ttu-id="681c7-146">W niektórych aplikacjach strony umożliwiają nawigację do dwóch lub więcej innych stron, jak pokazano na poniższym rysunku:</span><span class="sxs-lookup"><span data-stu-id="681c7-146">In some applications, pages allow navigation to two or more other pages, as shown in the following figure:</span></span>
  
 ![Diagram przedstawiający stronę, która może przejść do wielu stron.](./media/navigation-topologies-overview/navigation-topology-multiple-pages.png)  
  
 <span data-ttu-id="681c7-148">Ta struktura jest znana jako stała hierarchiczna topologia, a sekwencja, w której hierarchia jest przechodzenia jest często określana w czasie wykonywania przez aplikację lub użytkownika.</span><span class="sxs-lookup"><span data-stu-id="681c7-148">This structure is known as a fixed hierarchical topology, and the sequence in which the hierarchy is traversed is often determined at run time by either the application or the user.</span></span> <span data-ttu-id="681c7-149">W czasie wykonywania każda strona w hierarchii, która umożliwia nawigację do dwóch lub więcej innych stron, zbiera dane wymagane do określenia, do której strony chcesz przejść.</span><span class="sxs-lookup"><span data-stu-id="681c7-149">At run time, each page in the hierarchy that allows navigation to two or more other pages gathers the data required to determine which page to navigate to.</span></span> <span data-ttu-id="681c7-150">Na poniższym rysunku przedstawiono jedną z kilku możliwych sekwencji nawigacji na podstawie poprzedniego rysunku:</span><span class="sxs-lookup"><span data-stu-id="681c7-150">The following figure illustrates one of several possible navigation sequences based on the previous figure:</span></span>  
  
 ![Diagram, który pokazuje możliwą sekwencję nawigacji.](./media/navigation-topologies-overview/navigation-topology-fixed-hierarchical.png)  
  
 <span data-ttu-id="681c7-152">Mimo że sekwencja, w której są nawigowane strony w stałej strukturze hierarchicznej, jest określana w czasie wykonywania, środowisko użytkownika jest takie samo jak środowisko użytkownika dla stałej topologii liniowej:</span><span class="sxs-lookup"><span data-stu-id="681c7-152">Even though the sequence in which pages in a fixed hierarchical structure are navigated is determined at run time, the user experience is the same as the user experience for a fixed linear topology:</span></span>  
  
- <span data-ttu-id="681c7-153">Przechodzenie ze strony wywołującej do strony uruchamiania, która inicjuje kreatora i przechodzi do pierwszej strony kreatora.</span><span class="sxs-lookup"><span data-stu-id="681c7-153">Navigating from the calling page to a launcher page that initializes the wizard and navigates to the first wizard page.</span></span> <span data-ttu-id="681c7-154">Strona uruchamiania (a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] <xref:System.Windows.Navigation.PageFunction%601>-less) nie jest wymagana, ponieważ strona wywołująca może wywołać pierwszą stronę kreatora bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="681c7-154">A launcher page (a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]-less <xref:System.Windows.Navigation.PageFunction%601>) is not required, since a calling page can call the first wizard page directly.</span></span> <span data-ttu-id="681c7-155">Za pomocą strony uruchamiania, jednak można uprościć inicjowania kreatora, szczególnie jeśli inicjowanie jest złożone.</span><span class="sxs-lookup"><span data-stu-id="681c7-155">Using a launcher page, however, can simplify wizard initialization, particularly if initialization is complex.</span></span>  
  
- <span data-ttu-id="681c7-156">Użytkownicy mogą nawigować między stronami za pomocą przycisków Wstecz i Dalej (lub hiperłączy).</span><span class="sxs-lookup"><span data-stu-id="681c7-156">Users can navigate between pages by using Back and Forward buttons (or hyperlinks).</span></span>  
  
- <span data-ttu-id="681c7-157">Użytkownicy mogą nawigować między stronami za pomocą arkusza.</span><span class="sxs-lookup"><span data-stu-id="681c7-157">Users can navigate between pages using the journal.</span></span>  
  
- <span data-ttu-id="681c7-158">Użytkownicy mogą zmienić sekwencję nawigacji, jeśli nawigują z powrotem po dzienniku.</span><span class="sxs-lookup"><span data-stu-id="681c7-158">Users can change the navigation sequence if they navigate back through the journal.</span></span>  
  
- <span data-ttu-id="681c7-159">Użytkownicy mogą anulować kreatora z dowolnej strony kreatora, naciskając przycisk Anuluj.</span><span class="sxs-lookup"><span data-stu-id="681c7-159">Users can cancel the wizard from any wizard page by pressing a Cancel button.</span></span>  
  
- <span data-ttu-id="681c7-160">Użytkownicy mogą zaakceptować kreatora na ostatniej stronie kreatora, naciskając przycisk Zakończ.</span><span class="sxs-lookup"><span data-stu-id="681c7-160">Users can accept the wizard on the last wizard page by pressing a Finish button.</span></span>  
  
- <span data-ttu-id="681c7-161">Jeśli kreator zostanie anulowany, kreator zwraca odpowiedni wynik i nie zwraca żadnych danych.</span><span class="sxs-lookup"><span data-stu-id="681c7-161">If a wizard is canceled, the wizard returns an appropriate result, and does not return any data.</span></span>  
  
- <span data-ttu-id="681c7-162">Jeśli użytkownik zaakceptuje kreatora, kreator zwraca odpowiedni wynik i zwraca zebrane dane.</span><span class="sxs-lookup"><span data-stu-id="681c7-162">If a user accepts a wizard, the wizard returns an appropriate result, and returns the data it collected.</span></span>  
  
- <span data-ttu-id="681c7-163">Po zakończeniu pracy kreatora (zaakceptowaniu lub anulowaniu) strony, w skład których wchodzi kreator, zostaną usunięte z dziennika.</span><span class="sxs-lookup"><span data-stu-id="681c7-163">When the wizard is complete (accepted or canceled), the pages that the wizard comprises are removed from the journal.</span></span> <span data-ttu-id="681c7-164">Dzięki temu każde wystąpienie kreatora jest izolowane, co pozwala uniknąć potencjalnych anomalii danych lub stanu.</span><span class="sxs-lookup"><span data-stu-id="681c7-164">This keeps each instance of the wizard isolated, thereby avoiding potential data or state anomalies.</span></span>  
  
<a name="Navigation_over_a_Dynamically_Generated_Topology"></a>
## <a name="navigation-over-a-dynamically-generated-topology"></a><span data-ttu-id="681c7-165">Nawigacja po topologii generowanej dynamicznie</span><span class="sxs-lookup"><span data-stu-id="681c7-165">Navigation over a Dynamically Generated Topology</span></span>  
 <span data-ttu-id="681c7-166">W niektórych aplikacjach sekwencja, w której nawigowane są dwie lub więcej stron, może być określona tylko w czasie wykonywania, czy przez użytkownika, aplikacji lub danych zewnętrznych.</span><span class="sxs-lookup"><span data-stu-id="681c7-166">In some applications, the sequence in which two or more pages are navigated can only be determined at run time, whether by the user, the application, or external data.</span></span> <span data-ttu-id="681c7-167">Na poniższym rysunku przedstawiono zestaw stron z nieokreśloną sekwencją nawigacji:</span><span class="sxs-lookup"><span data-stu-id="681c7-167">The following figure illustrates a set of pages with an undetermined navigation sequence:</span></span>  
  
 ![Zestaw stron z nieokreśloną sekwencją nawigacji.](./media/navigation-topologies-overview/navigation-topology-dynamically-generated.png)  
  
 <span data-ttu-id="681c7-169">Następny rysunek ilustruje sekwencję nawigacji, która została wybrana przez użytkownika w czasie wykonywania:</span><span class="sxs-lookup"><span data-stu-id="681c7-169">The next figure illustrates a navigation sequence that was chosen by the user at run time:</span></span>  
  
 ![Diagram przedstawiający sekwencję nawigacji wybraną w czasie wykonywania.](./media/navigation-topologies-overview/navigation-topology-sequence-chosen-run-time.png)  
  
 <span data-ttu-id="681c7-171">Sekwencja nawigacji jest znana jako dynamicznie generowana topologia.</span><span class="sxs-lookup"><span data-stu-id="681c7-171">The navigation sequence is known as a dynamically generated topology.</span></span> <span data-ttu-id="681c7-172">Dla użytkownika, podobnie jak w przypadku innych topologii nawigacji, środowisko użytkownika jest takie samo, jak w przypadku poprzednich topologii:</span><span class="sxs-lookup"><span data-stu-id="681c7-172">For the user, as with the other navigation topologies, the user experience is the same as it is for the previous topologies:</span></span>  
  
- <span data-ttu-id="681c7-173">Przechodzenie ze strony wywołującej do strony uruchamiania, która inicjuje kreatora i przechodzi do pierwszej strony kreatora.</span><span class="sxs-lookup"><span data-stu-id="681c7-173">Navigating from the calling page to a launcher page that initializes the wizard and navigates to the first wizard page.</span></span> <span data-ttu-id="681c7-174">Strona uruchamiania (a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] <xref:System.Windows.Navigation.PageFunction%601>-less) nie jest wymagana, ponieważ strona wywołująca może wywołać pierwszą stronę kreatora bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="681c7-174">A launcher page (a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]-less <xref:System.Windows.Navigation.PageFunction%601>) is not required, since a calling page can call the first wizard page directly.</span></span> <span data-ttu-id="681c7-175">Za pomocą strony uruchamiania, jednak można uprościć inicjowania kreatora, szczególnie jeśli inicjowanie jest złożone.</span><span class="sxs-lookup"><span data-stu-id="681c7-175">Using a launcher page, however, can simplify wizard initialization, particularly if initialization is complex.</span></span>  
  
- <span data-ttu-id="681c7-176">Użytkownicy mogą nawigować między stronami za pomocą przycisków Wstecz i Dalej (lub hiperłączy).</span><span class="sxs-lookup"><span data-stu-id="681c7-176">Users can navigate between pages by using Back and Forward buttons (or hyperlinks).</span></span>  
  
- <span data-ttu-id="681c7-177">Użytkownicy mogą nawigować między stronami za pomocą arkusza.</span><span class="sxs-lookup"><span data-stu-id="681c7-177">Users can navigate between pages using the journal.</span></span>  
  
- <span data-ttu-id="681c7-178">Użytkownicy mogą anulować kreatora z dowolnej strony kreatora, naciskając przycisk Anuluj.</span><span class="sxs-lookup"><span data-stu-id="681c7-178">Users can cancel the wizard from any wizard page by pressing a Cancel button.</span></span>  
  
- <span data-ttu-id="681c7-179">Użytkownicy mogą zaakceptować kreatora na ostatniej stronie kreatora, naciskając przycisk Zakończ.</span><span class="sxs-lookup"><span data-stu-id="681c7-179">Users can accept the wizard on the last wizard page by pressing a Finish button.</span></span>  
  
- <span data-ttu-id="681c7-180">Jeśli kreator zostanie anulowany, kreator zwraca odpowiedni wynik i nie zwraca żadnych danych.</span><span class="sxs-lookup"><span data-stu-id="681c7-180">If a wizard is canceled, the wizard returns an appropriate result, and does not return any data.</span></span>  
  
- <span data-ttu-id="681c7-181">Jeśli użytkownik zaakceptuje kreatora, kreator zwraca odpowiedni wynik i zwraca zebrane dane.</span><span class="sxs-lookup"><span data-stu-id="681c7-181">If a user accepts a wizard, the wizard returns an appropriate result, and returns the data it collected.</span></span>  
  
- <span data-ttu-id="681c7-182">Po zakończeniu pracy kreatora (zaakceptowaniu lub anulowaniu) strony, w skład których wchodzi kreator, zostaną usunięte z dziennika.</span><span class="sxs-lookup"><span data-stu-id="681c7-182">When the wizard is complete (accepted or canceled), the pages that the wizard comprises are removed from the journal.</span></span> <span data-ttu-id="681c7-183">Dzięki temu każde wystąpienie kreatora jest izolowane, co pozwala uniknąć potencjalnych anomalii danych lub stanu.</span><span class="sxs-lookup"><span data-stu-id="681c7-183">This keeps each instance of the wizard isolated, thereby avoiding potential data or state anomalies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="681c7-184">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="681c7-184">See also</span></span>

- <xref:System.Windows.Controls.Page>
- <xref:System.Windows.Navigation.PageFunction%601>
- <xref:System.Windows.Navigation.NavigationService>
- [<span data-ttu-id="681c7-185">Przegląd Strukturyzowana nawigacja</span><span class="sxs-lookup"><span data-stu-id="681c7-185">Structured Navigation Overview</span></span>](structured-navigation-overview.md)
