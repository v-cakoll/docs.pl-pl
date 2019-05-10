---
title: 'Instrukcje: Dodawanie obsługi zdarzeń z użyciem kodu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- event handlers [WPF], adding
- XAML [WPF], adding event handlers
ms.assetid: 269c61e0-6bd9-4291-9bed-1c5ee66da486
ms.openlocfilehash: 32e3926bb4c519b7be14a26484603d6d4ea88b6a
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64665793"
---
# <a name="how-to-add-an-event-handler-using-code"></a><span data-ttu-id="2eeb1-102">Instrukcje: Dodawanie obsługi zdarzeń z użyciem kodu</span><span class="sxs-lookup"><span data-stu-id="2eeb1-102">How to: Add an Event Handler Using Code</span></span>
<span data-ttu-id="2eeb1-103">W tym przykładzie przedstawiono sposób dodawania programu obsługi zdarzeń do elementu przy użyciu kodu.</span><span class="sxs-lookup"><span data-stu-id="2eeb1-103">This example shows how to add an event handler to an element by using code.</span></span>  
  
 <span data-ttu-id="2eeb1-104">Jeśli chcesz dodać program obsługi zdarzeń do [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] elementu, a na stronie znaczników, który zawiera element został już załadowany, należy dodać program obsługi przy użyciu kodu.</span><span class="sxs-lookup"><span data-stu-id="2eeb1-104">If you want to add an event handler to a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] element, and the markup page that contains the element has already been loaded, you must add the handler using code.</span></span> <span data-ttu-id="2eeb1-105">Alternatywnie jeśli są tworzone w górę drzewa elementów, aplikacji całkowicie przy użyciu kodu i nie deklarując wszelkie elementy przy użyciu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], można wywołać konkretnych metod, aby dodać procedury obsługi zdarzeń do drzewa element skonstruowany.</span><span class="sxs-lookup"><span data-stu-id="2eeb1-105">Alternatively, if you are building up the element tree for an application entirely using code and not declaring any elements using [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], you can call specific methods to add event handlers to the constructed element tree.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2eeb1-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="2eeb1-106">Example</span></span>  
 <span data-ttu-id="2eeb1-107">Poniższy przykład dodaje nowy <xref:System.Windows.Controls.Button> do istniejącej strony, który jest wstępnie zdefiniowany w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2eeb1-107">The following example adds a new <xref:System.Windows.Controls.Button> to an existing page that is initially defined in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span> <span data-ttu-id="2eeb1-108">Plik związany z kodem implementuje metodę programu obsługi zdarzeń i dodaje tę metodę jako nowy program obsługi zdarzeń na <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="2eeb1-108">A code-behind file implements an event handler method and then adds that method as a new event handler on the <xref:System.Windows.Controls.Button>.</span></span>  
  
 <span data-ttu-id="2eeb1-109">C# Przykładzie użyto `+=` operatora, aby przypisać program obsługi zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="2eeb1-109">The C# example uses the `+=` operator to assign a handler to an event.</span></span> <span data-ttu-id="2eeb1-110">Jest to ten sam operator, który jest używany do przypisywania obsługi w [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] model obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="2eeb1-110">This is the same operator that is used to assign a handler in the [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] event handling model.</span></span> <span data-ttu-id="2eeb1-111">Microsoft Visual Basic nie obsługuje tego operatora jako środek Dodawanie obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="2eeb1-111">Microsoft Visual Basic does not support this operator as a means of adding event handlers.</span></span> <span data-ttu-id="2eeb1-112">Zamiast tego wymaga jednej z dwóch technik:</span><span class="sxs-lookup"><span data-stu-id="2eeb1-112">It instead requires one of two techniques:</span></span>  
  
- <span data-ttu-id="2eeb1-113">Użyj <xref:System.Windows.UIElement.AddHandler%2A> metoda wraz z `AddressOf` operatora, aby odwoływać się do wdrożenia programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="2eeb1-113">Use the <xref:System.Windows.UIElement.AddHandler%2A> method, together with an `AddressOf` operator, to reference the event handler implementation.</span></span>  
  
- <span data-ttu-id="2eeb1-114">Użyj `Handles` — słowo kluczowe w definicji procedury obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="2eeb1-114">Use the `Handles` keyword as part of the event handler definition.</span></span> <span data-ttu-id="2eeb1-115">Ta technika nie jest wyświetlany w tym miejscu; zobacz [Visual Basic i obsługa zdarzeń WPF](visual-basic-and-wpf-event-handling.md).</span><span class="sxs-lookup"><span data-stu-id="2eeb1-115">This technique is not shown here; see [Visual Basic and WPF Event Handling](visual-basic-and-wpf-event-handling.md).</span></span>  
  
 [!code-xaml[RoutedEventAddRemoveHandler#XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventAddRemoveHandler/CSharp/default.xaml#xaml)]  
  
 [!code-csharp[RoutedEventAddRemoveHandler#Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventAddRemoveHandler/CSharp/default.xaml.cs#handler)]
 [!code-vb[RoutedEventAddRemoveHandler#Handler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventAddRemoveHandler/VisualBasic/default.xaml.vb#handler)]  
  
> [!NOTE]
>  <span data-ttu-id="2eeb1-116">Dodawanie obsługi zdarzeń w początkowo przeanalizowany [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] strony jest znacznie prostsza.</span><span class="sxs-lookup"><span data-stu-id="2eeb1-116">Adding an event handler in the initially parsed [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] page is much simpler.</span></span> <span data-ttu-id="2eeb1-117">W elemencie obiektu, którym chcesz dodać program obsługi zdarzeń należy dodać atrybut, który jest zgodna z nazwą zdarzenia, które mają być obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="2eeb1-117">Within the object element where you want to add the event handler, add an attribute that matches the name of the event that you want to handle.</span></span> <span data-ttu-id="2eeb1-118">Następnie określ wartość tego atrybutu jako nazwę metody obsługi zdarzeń, które zdefiniowane w pliku związanym z kodem [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] strony.</span><span class="sxs-lookup"><span data-stu-id="2eeb1-118">Then specify the value of that attribute as the name of the event handler method that you defined in the code-behind file of the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] page.</span></span> <span data-ttu-id="2eeb1-119">Aby uzyskać więcej informacji, zobacz [Przegląd XAML (WPF)](xaml-overview-wpf.md) lub [Przegląd zdarzeń kierowane](routed-events-overview.md).</span><span class="sxs-lookup"><span data-stu-id="2eeb1-119">For more information, see [XAML Overview (WPF)](xaml-overview-wpf.md) or [Routed Events Overview](routed-events-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2eeb1-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2eeb1-120">See also</span></span>

- [<span data-ttu-id="2eeb1-121">Przegląd zdarzeń trasowanych</span><span class="sxs-lookup"><span data-stu-id="2eeb1-121">Routed Events Overview</span></span>](routed-events-overview.md)
- [<span data-ttu-id="2eeb1-122">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="2eeb1-122">How-to Topics</span></span>](events-how-to-topics.md)
