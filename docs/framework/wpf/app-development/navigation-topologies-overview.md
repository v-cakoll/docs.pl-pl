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
ms.openlocfilehash: 716cfbe7d12ccc2233d018f0346f84cf2fc5e733
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61794683"
---
# <a name="navigation-topologies-overview"></a><span data-ttu-id="67e67-102">Przegląd Topologia nawigacji</span><span class="sxs-lookup"><span data-stu-id="67e67-102">Navigation Topologies Overview</span></span>
<a name="introduction"></a> <span data-ttu-id="67e67-103">W tym omówieniu przedstawiono wprowadzenie do topologii nawigacji w [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].</span><span class="sxs-lookup"><span data-stu-id="67e67-103">This overview provides an introduction to navigation topologies in [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].</span></span> <span data-ttu-id="67e67-104">Następnie opisano trzy popularne topologie nawigacji, z przykładami.</span><span class="sxs-lookup"><span data-stu-id="67e67-104">Three common navigation topologies, with samples, are subsequently discussed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="67e67-105">Przed odczytaniem w tym temacie, należy zapoznać się z pojęciem strukturyzowana Nawigacja w [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] za pomocą funkcji strony.</span><span class="sxs-lookup"><span data-stu-id="67e67-105">Before reading this topic, you should be familiar with the concept of structured navigation in [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] using page functions.</span></span> <span data-ttu-id="67e67-106">Aby uzyskać więcej informacji na temat obu tych tematów, zobacz [ze strukturą Przegląd Nawigacja](structured-navigation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="67e67-106">For more information on both of these topics, see [Structured Navigation Overview](structured-navigation-overview.md).</span></span>  
  
 <span data-ttu-id="67e67-107">Ten temat zawiera następujące sekcje:</span><span class="sxs-lookup"><span data-stu-id="67e67-107">This topic contains the following sections:</span></span>  
  
- [<span data-ttu-id="67e67-108">Topologie nawigacji</span><span class="sxs-lookup"><span data-stu-id="67e67-108">Navigation Topologies</span></span>](#Navigation_Topologies)  
  
- [<span data-ttu-id="67e67-109">Topologie strukturyzowana Nawigacja</span><span class="sxs-lookup"><span data-stu-id="67e67-109">Structured Navigation Topologies</span></span>](#Structured_Navigation_Topologies)  
  
- [<span data-ttu-id="67e67-110">Nawigacja za pośrednictwem stały liniowa topologia</span><span class="sxs-lookup"><span data-stu-id="67e67-110">Navigation over a Fixed Linear Topology</span></span>](#Navigation_over_a_Fixed_Linear_Topology)  
  
- [<span data-ttu-id="67e67-111">Dynamicznej nawigacji nad stały hierarchiczna topologia</span><span class="sxs-lookup"><span data-stu-id="67e67-111">Dynamic Navigation over a Fixed Hierarchical Topology</span></span>](#Dynamic_Navigation_over_a_Fixed_Hierarchical_Topology)  
  
- [<span data-ttu-id="67e67-112">Nawigacja w dynamicznie generowanym topologii</span><span class="sxs-lookup"><span data-stu-id="67e67-112">Navigation over a Dynamically Generated Topology</span></span>](#Navigation_over_a_Dynamically_Generated_Topology)  
  
<a name="Navigation_Topologies"></a>   
## <a name="navigation-topologies"></a><span data-ttu-id="67e67-113">Topologie nawigacji</span><span class="sxs-lookup"><span data-stu-id="67e67-113">Navigation Topologies</span></span>  
 <span data-ttu-id="67e67-114">W [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], nawigacji zwykle składa się z stron (<xref:System.Windows.Controls.Page>) za pomocą hiperlinków (<xref:System.Windows.Documents.Hyperlink>), przejdź do innych stron, po kliknięciu.</span><span class="sxs-lookup"><span data-stu-id="67e67-114">In [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], navigation typically consists of pages (<xref:System.Windows.Controls.Page>) with hyperlinks (<xref:System.Windows.Documents.Hyperlink>) that navigate to other pages when clicked.</span></span> <span data-ttu-id="67e67-115">Stron, które są przejście, są identyfikowane przez [!INCLUDE[TLA#tla_uri#plural](../../../../includes/tlasharptla-urisharpplural-md.md)] (zobacz [pakiet URI w WPF](pack-uris-in-wpf.md)).</span><span class="sxs-lookup"><span data-stu-id="67e67-115">Pages that are navigated to are identified by [!INCLUDE[TLA#tla_uri#plural](../../../../includes/tlasharptla-urisharpplural-md.md)] (see [Pack URIs in WPF](pack-uris-in-wpf.md)).</span></span> <span data-ttu-id="67e67-116">Należy wziąć pod uwagę następujące prosty przykład pokazujący hiperłącza, strony i [!INCLUDE[TLA#tla_uri#plural](../../../../includes/tlasharptla-urisharpplural-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="67e67-116">Consider the following simple example that shows pages, hyperlinks, and [!INCLUDE[TLA#tla_uri#plural](../../../../includes/tlasharptla-urisharpplural-md.md)]:</span></span>  
  
 [!code-xaml[NavigationTopologiesOverviewSnippets#Page1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationTopologiesOverviewSnippets/CS/Page1.xaml#page1)]  
  
 [!code-xaml[NavigationTopologiesOverviewSnippets#Page2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationTopologiesOverviewSnippets/CS/Page2.xaml#page2)]  
  
 <span data-ttu-id="67e67-117">Te strony są rozmieszczane w *topologia nawigacji* której strukturę zależy od sposobu można nawigować między stronami.</span><span class="sxs-lookup"><span data-stu-id="67e67-117">These pages are arranged in a *navigation topology* whose structure is determined by how you can navigate between the pages.</span></span> <span data-ttu-id="67e67-118">Ta topologia nawigacji w szczególności jest odpowiedni w przypadku prostych scenariuszy, chociaż nawigacji mogą wymagać bardziej złożonych topologii, niektóre z nich mogą być definiowane tylko gdy aplikacja jest uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="67e67-118">This particular navigation topology is suitable in simple scenarios, although navigation can require more complex topologies, some of which can only be defined when an application is running.</span></span>  
  
 <span data-ttu-id="67e67-119">W tym temacie opisano trzy popularne topologie nawigacji: *stała liniowa*, *stała hierarchiczna*, i *dynamicznie generowanym*.</span><span class="sxs-lookup"><span data-stu-id="67e67-119">This topic covers three common navigation topologies: *fixed linear*, *fixed hierarchical*, and *dynamically generated*.</span></span> <span data-ttu-id="67e67-120">Każda topologia nawigacji przedstawiono przykład, który ma [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] jak te, które przedstawiono na poniższej ilustracji:</span><span class="sxs-lookup"><span data-stu-id="67e67-120">Each navigation topology is demonstrated with a sample that has a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] like the one that is shown in the following figure:</span></span>  
  
 ![Strony zadania przy użyciu elementów danych i przycisków nawigacji.](./media/navigation-topologies-overview/navigation-topology-data-items.png)  
  
<a name="Structured_Navigation_Topologies"></a>   
## <a name="structured-navigation-topologies"></a><span data-ttu-id="67e67-122">Topologie strukturyzowana Nawigacja</span><span class="sxs-lookup"><span data-stu-id="67e67-122">Structured Navigation Topologies</span></span>  
 <span data-ttu-id="67e67-123">Istnieją dwa ogólne typy topologie nawigacji:</span><span class="sxs-lookup"><span data-stu-id="67e67-123">There are two broad types of navigation topologies:</span></span>  
  
- <span data-ttu-id="67e67-124">**Stała topologia**: zdefiniowany w czasie kompilacji i nie zmienia się w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="67e67-124">**Fixed Topology**: defined at compile time and does not change at run time.</span></span> <span data-ttu-id="67e67-125">Naprawiono topologii są przydatne do nawigacji za pomocą stałych sekwencji stron w kolejności liniowy lub hierarchiczny.</span><span class="sxs-lookup"><span data-stu-id="67e67-125">Fixed topologies are useful for navigation through a fixed sequence of pages in either a linear or hierarchical order.</span></span>  
  
- <span data-ttu-id="67e67-126">**Dynamiczne topologii**: zdefiniowany w czasie wykonywania, w oparciu o dane wejściowe, które są zbierane od użytkownika, aplikacji lub systemu.</span><span class="sxs-lookup"><span data-stu-id="67e67-126">**Dynamic Topology**: defined at run time based on input that is collected from the user, the application, or the system.</span></span> <span data-ttu-id="67e67-127">Dynamiczne topologii są przydatne, gdy strony można nawigować w różnych sekwencji.</span><span class="sxs-lookup"><span data-stu-id="67e67-127">Dynamic topologies are useful when pages can be navigated in different sequences.</span></span>  
  
 <span data-ttu-id="67e67-128">Chociaż istnieje możliwość utworzenia topologie nawigacji za pomocą stron, przykłady funkcji strony należy użyć w sytuacji, ponieważ zapewniają dodatkową pomoc, która upraszcza obsługę przekazywanie i zwracanie danych na stronach topologii.</span><span class="sxs-lookup"><span data-stu-id="67e67-128">Although it is possible to create navigation topologies using pages, the samples use page functions because they provide additional support that simplifies support for passing and returning data through the pages of a topology.</span></span>  
  
<a name="Navigation_over_a_Fixed_Linear_Topology"></a>   
## <a name="navigation-over-a-fixed-linear-topology"></a><span data-ttu-id="67e67-129">Nawigacja za pośrednictwem stały liniowa topologia</span><span class="sxs-lookup"><span data-stu-id="67e67-129">Navigation over a Fixed Linear Topology</span></span>  
 <span data-ttu-id="67e67-130">Naprawiono liniowa topologia jest analogiczne do struktury kreatora, który ma co najmniej jednej strony kreatora, które są przejście w stałej kolejności.</span><span class="sxs-lookup"><span data-stu-id="67e67-130">A fixed linear topology is analogous to the structure of a wizard that has one or more wizard pages that are navigated in a fixed sequence.</span></span> <span data-ttu-id="67e67-131">Na poniższej ilustracji przedstawiono ogólną strukturę i przepływ kreatora bez stały liniowa topologia:</span><span class="sxs-lookup"><span data-stu-id="67e67-131">The following figure shows the high-level structure and flow of a wizard with a fixed linear topology:</span></span>  
  
 ![Diagram, który pokazuje stały liniowa topologia.](./media/navigation-topologies-overview/navigation-topology-fixed-linear.png)  
  
 <span data-ttu-id="67e67-133">Następujące typowe zachowania do nawigowania w stałym liniowa topologia:</span><span class="sxs-lookup"><span data-stu-id="67e67-133">The typical behaviors for navigating over a fixed linear topology include the following:</span></span>  
  
- <span data-ttu-id="67e67-134">Przechodząc ze strony wywołania do strony uruchamiania, która inicjuje kreatora i przechodzi do pierwszej strony kreatora.</span><span class="sxs-lookup"><span data-stu-id="67e67-134">Navigating from the calling page to a launcher page that initializes the wizard and navigates to the first wizard page.</span></span> <span data-ttu-id="67e67-135">Strona uruchamiania ( [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]— mniej <xref:System.Windows.Navigation.PageFunction%601>) nie jest wymagane, ponieważ wywołujący strony można bezpośrednio wywoływać pierwszej stronie kreatora.</span><span class="sxs-lookup"><span data-stu-id="67e67-135">A launcher page (a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]-less <xref:System.Windows.Navigation.PageFunction%601>) is not required, since a calling page can call the first wizard page directly.</span></span> <span data-ttu-id="67e67-136">Przy użyciu strony uruchamiania, jednak można uprościć inicjowanie kreatora, szczególnie w przypadku, gdy inicjalizacja jest złożony.</span><span class="sxs-lookup"><span data-stu-id="67e67-136">Using a launcher page, however, can simplify wizard initialization, particularly if initialization is complex.</span></span>  
  
- <span data-ttu-id="67e67-137">Użytkownicy mogą przejść między stronami, korzystając z tyłu i do przodu przycisków (lub hiperłącza).</span><span class="sxs-lookup"><span data-stu-id="67e67-137">Users can navigate between pages by using Back and Forward buttons (or hyperlinks).</span></span>  
  
- <span data-ttu-id="67e67-138">Użytkownicy mogą przejść między stronami przy użyciu arkusza.</span><span class="sxs-lookup"><span data-stu-id="67e67-138">Users can navigate between pages using the journal.</span></span>  
  
- <span data-ttu-id="67e67-139">Użytkownikom można anulować kreatora z dowolnej strony kreatora, naciskając przycisk Anuluj.</span><span class="sxs-lookup"><span data-stu-id="67e67-139">Users can cancel the wizard from any wizard page by pressing a Cancel button.</span></span>  
  
- <span data-ttu-id="67e67-140">Użytkownicy mogą zaakceptować kreatora na ostatniej stronie kreatora, naciskając przycisk Zakończ.</span><span class="sxs-lookup"><span data-stu-id="67e67-140">Users can accept the wizard on the last wizard page by pressing a Finish button.</span></span>  
  
- <span data-ttu-id="67e67-141">Jeśli Kreator zostanie anulowane, Kreator zwraca odpowiedni wynik i nie zwraca żadnych danych.</span><span class="sxs-lookup"><span data-stu-id="67e67-141">If a wizard is canceled, the wizard returns an appropriate result, and does not return any data.</span></span>  
  
- <span data-ttu-id="67e67-142">Jeśli użytkownik zaakceptuje kreatora, Kreator zwraca odpowiedni wynik i zwraca dane zebrane.</span><span class="sxs-lookup"><span data-stu-id="67e67-142">If a user accepts a wizard, the wizard returns an appropriate result, and returns the data it collected.</span></span>  
  
- <span data-ttu-id="67e67-143">Po ukończeniu pracy kreatora (zaakceptowane lub anulowane), stron, które obejmuje kreatora są usuwane z dziennika.</span><span class="sxs-lookup"><span data-stu-id="67e67-143">When the wizard is complete (accepted or canceled), the pages that the wizard comprises are removed from the journal.</span></span> <span data-ttu-id="67e67-144">Dzięki temu każde wystąpienie Kreatora izolowane, zapobiegając potencjalnych danych lub nieprawidłowości stanu.</span><span class="sxs-lookup"><span data-stu-id="67e67-144">This keeps each instance of the wizard isolated, thereby avoiding potential data or state anomalies.</span></span>  
  
<a name="Dynamic_Navigation_over_a_Fixed_Hierarchical_Topology"></a>   
## <a name="dynamic-navigation-over-a-fixed-hierarchical-topology"></a><span data-ttu-id="67e67-145">Dynamicznej nawigacji nad stały hierarchiczna topologia</span><span class="sxs-lookup"><span data-stu-id="67e67-145">Dynamic Navigation over a Fixed Hierarchical Topology</span></span>  
 <span data-ttu-id="67e67-146">W niektórych aplikacjach strony umożliwiają przechodzenie do co najmniej dwóch innych stron, jak pokazano na poniższej ilustracji:</span><span class="sxs-lookup"><span data-stu-id="67e67-146">In some applications, pages allow navigation to two or more other pages, as shown in the following figure:</span></span> 
  
 ![Diagram przedstawiający strona, która można przejść do wielu stron.](./media/navigation-topologies-overview/navigation-topology-multiple-pages.png)  
  
 <span data-ttu-id="67e67-148">Ta struktura jest znany jako stały topologii hierarchicznej i sekwencji, w którym hierarchii, o ile jest często określana w czasie wykonywania przez użytkownika lub aplikacji.</span><span class="sxs-lookup"><span data-stu-id="67e67-148">This structure is known as a fixed hierarchical topology, and the sequence in which the hierarchy is traversed is often determined at run time by either the application or the user.</span></span> <span data-ttu-id="67e67-149">W czasie wykonywania każda strona w hierarchii, która umożliwia przechodzenie do co najmniej dwóch innych stron zbiera dane wymagane do określenia, które strony dla przejścia.</span><span class="sxs-lookup"><span data-stu-id="67e67-149">At run time, each page in the hierarchy that allows navigation to two or more other pages gathers the data required to determine which page to navigate to.</span></span> <span data-ttu-id="67e67-150">Na poniższym rysunku przedstawiono jeden z kilku sekwencji nawigacji możliwe oparte na poprzedniej ilustracji:</span><span class="sxs-lookup"><span data-stu-id="67e67-150">The following figure illustrates one of several possible navigation sequences based on the previous figure:</span></span>  
  
 ![Diagram przedstawiający sekwencję nawigacji to możliwe.](./media/navigation-topologies-overview/navigation-topology-fixed-hierarchical.png)  
  
 <span data-ttu-id="67e67-152">Mimo że sekwencji, w którym są przejście stron w strukturze hierarchicznej stałej jest określana w czasie wykonywania, środowisko użytkownika jest taki sam jak środowiska użytkownika dla stałych liniowa topologia:</span><span class="sxs-lookup"><span data-stu-id="67e67-152">Even though the sequence in which pages in a fixed hierarchical structure are navigated is determined at run time, the user experience is the same as the user experience for a fixed linear topology:</span></span>  
  
- <span data-ttu-id="67e67-153">Przechodząc ze strony wywołania do strony uruchamiania, która inicjuje kreatora i przechodzi do pierwszej strony kreatora.</span><span class="sxs-lookup"><span data-stu-id="67e67-153">Navigating from the calling page to a launcher page that initializes the wizard and navigates to the first wizard page.</span></span> <span data-ttu-id="67e67-154">Strona uruchamiania ( [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]— mniej <xref:System.Windows.Navigation.PageFunction%601>) nie jest wymagane, ponieważ wywołujący strony można bezpośrednio wywoływać pierwszej stronie kreatora.</span><span class="sxs-lookup"><span data-stu-id="67e67-154">A launcher page (a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]-less <xref:System.Windows.Navigation.PageFunction%601>) is not required, since a calling page can call the first wizard page directly.</span></span> <span data-ttu-id="67e67-155">Przy użyciu strony uruchamiania, jednak można uprościć inicjowanie kreatora, szczególnie w przypadku, gdy inicjalizacja jest złożony.</span><span class="sxs-lookup"><span data-stu-id="67e67-155">Using a launcher page, however, can simplify wizard initialization, particularly if initialization is complex.</span></span>  
  
- <span data-ttu-id="67e67-156">Użytkownicy mogą przejść między stronami, korzystając z tyłu i do przodu przycisków (lub hiperłącza).</span><span class="sxs-lookup"><span data-stu-id="67e67-156">Users can navigate between pages by using Back and Forward buttons (or hyperlinks).</span></span>  
  
- <span data-ttu-id="67e67-157">Użytkownicy mogą przejść między stronami przy użyciu arkusza.</span><span class="sxs-lookup"><span data-stu-id="67e67-157">Users can navigate between pages using the journal.</span></span>  
  
- <span data-ttu-id="67e67-158">Użytkownicy mogą zmienić sekwencję nawigacji, jeśli ich poruszanie się wstecz arkusza.</span><span class="sxs-lookup"><span data-stu-id="67e67-158">Users can change the navigation sequence if they navigate back through the journal.</span></span>  
  
- <span data-ttu-id="67e67-159">Użytkownikom można anulować kreatora z dowolnej strony kreatora, naciskając przycisk Anuluj.</span><span class="sxs-lookup"><span data-stu-id="67e67-159">Users can cancel the wizard from any wizard page by pressing a Cancel button.</span></span>  
  
- <span data-ttu-id="67e67-160">Użytkownicy mogą zaakceptować kreatora na ostatniej stronie kreatora, naciskając przycisk Zakończ.</span><span class="sxs-lookup"><span data-stu-id="67e67-160">Users can accept the wizard on the last wizard page by pressing a Finish button.</span></span>  
  
- <span data-ttu-id="67e67-161">Jeśli Kreator zostanie anulowane, Kreator zwraca odpowiedni wynik i nie zwraca żadnych danych.</span><span class="sxs-lookup"><span data-stu-id="67e67-161">If a wizard is canceled, the wizard returns an appropriate result, and does not return any data.</span></span>  
  
- <span data-ttu-id="67e67-162">Jeśli użytkownik zaakceptuje kreatora, Kreator zwraca odpowiedni wynik i zwraca dane zebrane.</span><span class="sxs-lookup"><span data-stu-id="67e67-162">If a user accepts a wizard, the wizard returns an appropriate result, and returns the data it collected.</span></span>  
  
- <span data-ttu-id="67e67-163">Po ukończeniu pracy kreatora (zaakceptowane lub anulowane), stron, które obejmuje kreatora są usuwane z dziennika.</span><span class="sxs-lookup"><span data-stu-id="67e67-163">When the wizard is complete (accepted or canceled), the pages that the wizard comprises are removed from the journal.</span></span> <span data-ttu-id="67e67-164">Dzięki temu każde wystąpienie Kreatora izolowane, zapobiegając potencjalnych danych lub nieprawidłowości stanu.</span><span class="sxs-lookup"><span data-stu-id="67e67-164">This keeps each instance of the wizard isolated, thereby avoiding potential data or state anomalies.</span></span>  
  
<a name="Navigation_over_a_Dynamically_Generated_Topology"></a>   
## <a name="navigation-over-a-dynamically-generated-topology"></a><span data-ttu-id="67e67-165">Nawigacja w dynamicznie generowanym topologii</span><span class="sxs-lookup"><span data-stu-id="67e67-165">Navigation over a Dynamically Generated Topology</span></span>  
 <span data-ttu-id="67e67-166">W niektórych aplikacjach sekwencji, w którym są przejście, dwóch lub więcej stron można tylko można określić w czasie wykonywania przez użytkownika, aplikacji lub danych zewnętrznych.</span><span class="sxs-lookup"><span data-stu-id="67e67-166">In some applications, the sequence in which two or more pages are navigated can only be determined at run time, whether by the user, the application, or external data.</span></span> <span data-ttu-id="67e67-167">Na poniższym rysunku przedstawiono zestaw stron z sekwencją nieokreślonej nawigacji:</span><span class="sxs-lookup"><span data-stu-id="67e67-167">The following figure illustrates a set of pages with an undetermined navigation sequence:</span></span>  
  
 ![Zestaw stron z sekwencją nieokreślonej nawigacji.](./media/navigation-topologies-overview/navigation-topology-dynamically-generated.png)  
  
 <span data-ttu-id="67e67-169">Następny rysunek przedstawia sekwencję nawigacji, który został wybrany przez użytkownika w czasie wykonywania:</span><span class="sxs-lookup"><span data-stu-id="67e67-169">The next figure illustrates a navigation sequence that was chosen by the user at run time:</span></span>  
  
 ![Diagram przedstawiający sekwencję nawigacji wybranej w czasie wykonywania.](./media/navigation-topologies-overview/navigation-topology-sequence-chosen-run-time.png)  
  
 <span data-ttu-id="67e67-171">Sekwencję nawigacji jest określany jako dynamicznie generowanym topologii.</span><span class="sxs-lookup"><span data-stu-id="67e67-171">The navigation sequence is known as a dynamically generated topology.</span></span> <span data-ttu-id="67e67-172">Dla użytkownika jako przy użyciu innych topologie nawigacji środowisko użytkownika jest taka sama jak w przypadku poprzedniego topologii:</span><span class="sxs-lookup"><span data-stu-id="67e67-172">For the user, as with the other navigation topologies, the user experience is the same as it is for the previous topologies:</span></span>  
  
- <span data-ttu-id="67e67-173">Przechodząc ze strony wywołania do strony uruchamiania, która inicjuje kreatora i przechodzi do pierwszej strony kreatora.</span><span class="sxs-lookup"><span data-stu-id="67e67-173">Navigating from the calling page to a launcher page that initializes the wizard and navigates to the first wizard page.</span></span> <span data-ttu-id="67e67-174">Strona uruchamiania ( [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]— mniej <xref:System.Windows.Navigation.PageFunction%601>) nie jest wymagane, ponieważ wywołujący strony można bezpośrednio wywoływać pierwszej stronie kreatora.</span><span class="sxs-lookup"><span data-stu-id="67e67-174">A launcher page (a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]-less <xref:System.Windows.Navigation.PageFunction%601>) is not required, since a calling page can call the first wizard page directly.</span></span> <span data-ttu-id="67e67-175">Przy użyciu strony uruchamiania, jednak można uprościć inicjowanie kreatora, szczególnie w przypadku, gdy inicjalizacja jest złożony.</span><span class="sxs-lookup"><span data-stu-id="67e67-175">Using a launcher page, however, can simplify wizard initialization, particularly if initialization is complex.</span></span>  
  
- <span data-ttu-id="67e67-176">Użytkownicy mogą przejść między stronami, korzystając z tyłu i do przodu przycisków (lub hiperłącza).</span><span class="sxs-lookup"><span data-stu-id="67e67-176">Users can navigate between pages by using Back and Forward buttons (or hyperlinks).</span></span>  
  
- <span data-ttu-id="67e67-177">Użytkownicy mogą przejść między stronami przy użyciu arkusza.</span><span class="sxs-lookup"><span data-stu-id="67e67-177">Users can navigate between pages using the journal.</span></span>  
  
- <span data-ttu-id="67e67-178">Użytkownikom można anulować kreatora z dowolnej strony kreatora, naciskając przycisk Anuluj.</span><span class="sxs-lookup"><span data-stu-id="67e67-178">Users can cancel the wizard from any wizard page by pressing a Cancel button.</span></span>  
  
- <span data-ttu-id="67e67-179">Użytkownicy mogą zaakceptować kreatora na ostatniej stronie kreatora, naciskając przycisk Zakończ.</span><span class="sxs-lookup"><span data-stu-id="67e67-179">Users can accept the wizard on the last wizard page by pressing a Finish button.</span></span>  
  
- <span data-ttu-id="67e67-180">Jeśli Kreator zostanie anulowane, Kreator zwraca odpowiedni wynik i nie zwraca żadnych danych.</span><span class="sxs-lookup"><span data-stu-id="67e67-180">If a wizard is canceled, the wizard returns an appropriate result, and does not return any data.</span></span>  
  
- <span data-ttu-id="67e67-181">Jeśli użytkownik zaakceptuje kreatora, Kreator zwraca odpowiedni wynik i zwraca dane zebrane.</span><span class="sxs-lookup"><span data-stu-id="67e67-181">If a user accepts a wizard, the wizard returns an appropriate result, and returns the data it collected.</span></span>  
  
- <span data-ttu-id="67e67-182">Po ukończeniu pracy kreatora (zaakceptowane lub anulowane), stron, które obejmuje kreatora są usuwane z dziennika.</span><span class="sxs-lookup"><span data-stu-id="67e67-182">When the wizard is complete (accepted or canceled), the pages that the wizard comprises are removed from the journal.</span></span> <span data-ttu-id="67e67-183">Dzięki temu każde wystąpienie Kreatora izolowane, zapobiegając potencjalnych danych lub nieprawidłowości stanu.</span><span class="sxs-lookup"><span data-stu-id="67e67-183">This keeps each instance of the wizard isolated, thereby avoiding potential data or state anomalies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67e67-184">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="67e67-184">See also</span></span>

- <xref:System.Windows.Controls.Page>
- <xref:System.Windows.Navigation.PageFunction%601>
- <xref:System.Windows.Navigation.NavigationService>
- [<span data-ttu-id="67e67-185">Strukturyzowana nawigacja — omówienie</span><span class="sxs-lookup"><span data-stu-id="67e67-185">Structured Navigation Overview</span></span>](structured-navigation-overview.md)
