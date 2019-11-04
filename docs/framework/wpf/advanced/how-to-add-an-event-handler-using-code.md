---
title: Jak dodać obsługę zdarzeń z użyciem kodu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- event handlers [WPF], adding
- XAML [WPF], adding event handlers
ms.assetid: 269c61e0-6bd9-4291-9bed-1c5ee66da486
ms.openlocfilehash: 457b8cf5c68096b20df7fe39f1cc3f40358f34d0
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460438"
---
# <a name="how-to-add-an-event-handler-using-code"></a><span data-ttu-id="46480-102">Jak dodać obsługę zdarzeń z użyciem kodu</span><span class="sxs-lookup"><span data-stu-id="46480-102">How to: Add an Event Handler Using Code</span></span>
<span data-ttu-id="46480-103">Ten przykład pokazuje, jak dodać program obsługi zdarzeń do elementu przy użyciu kodu.</span><span class="sxs-lookup"><span data-stu-id="46480-103">This example shows how to add an event handler to an element by using code.</span></span>  
  
 <span data-ttu-id="46480-104">Jeśli chcesz dodać program obsługi zdarzeń do elementu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], a strona znaczników, która zawiera element, jest już załadowana, należy dodać program obsługi przy użyciu kodu.</span><span class="sxs-lookup"><span data-stu-id="46480-104">If you want to add an event handler to a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] element, and the markup page that contains the element has already been loaded, you must add the handler using code.</span></span> <span data-ttu-id="46480-105">Alternatywnie, jeśli tworzysz drzewo elementów dla aplikacji całkowicie przy użyciu kodu i nie deklaruje żadnych elementów przy użyciu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], można wywołać konkretne metody, aby dodać obsługę zdarzeń do drzewa skonstruowane elementy.</span><span class="sxs-lookup"><span data-stu-id="46480-105">Alternatively, if you are building up the element tree for an application entirely using code and not declaring any elements using [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], you can call specific methods to add event handlers to the constructed element tree.</span></span>  
  
## <a name="example"></a><span data-ttu-id="46480-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="46480-106">Example</span></span>  
 <span data-ttu-id="46480-107">Poniższy przykład dodaje nowe <xref:System.Windows.Controls.Button> do istniejącej strony, która jest początkowo zdefiniowana w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="46480-107">The following example adds a new <xref:System.Windows.Controls.Button> to an existing page that is initially defined in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span> <span data-ttu-id="46480-108">Plik związany z kodem implementuje metodę obsługi zdarzeń, a następnie dodaje tę metodę jako nowy program obsługi zdarzeń na <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="46480-108">A code-behind file implements an event handler method and then adds that method as a new event handler on the <xref:System.Windows.Controls.Button>.</span></span>  
  
 <span data-ttu-id="46480-109">W C# przykładzie używa operatora `+=`, aby przypisać procedurę obsługi do zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="46480-109">The C# example uses the `+=` operator to assign a handler to an event.</span></span> <span data-ttu-id="46480-110">Jest to ten sam operator, który jest używany do przypisania procedury obsługi w modelu obsługi zdarzeń środowiska uruchomieniowego języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="46480-110">This is the same operator that is used to assign a handler in the common language runtime (CLR) event handling model.</span></span> <span data-ttu-id="46480-111">Firma Microsoft Visual Basic nie obsługuje tego operatora jako metody dodawania obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="46480-111">Microsoft Visual Basic does not support this operator as a means of adding event handlers.</span></span> <span data-ttu-id="46480-112">Zamiast tego wymaga jednej z dwóch technik:</span><span class="sxs-lookup"><span data-stu-id="46480-112">It instead requires one of two techniques:</span></span>  
  
- <span data-ttu-id="46480-113">Użyj metody <xref:System.Windows.UIElement.AddHandler%2A> wraz z operatorem `AddressOf`, aby odwołać się do implementacji programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="46480-113">Use the <xref:System.Windows.UIElement.AddHandler%2A> method, together with an `AddressOf` operator, to reference the event handler implementation.</span></span>  
  
- <span data-ttu-id="46480-114">Użyj słowa kluczowego `Handles` jako części definicji programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="46480-114">Use the `Handles` keyword as part of the event handler definition.</span></span> <span data-ttu-id="46480-115">Ta technika nie jest tu pokazana. Zobacz [Visual Basic i obsługa zdarzeń WPF](visual-basic-and-wpf-event-handling.md).</span><span class="sxs-lookup"><span data-stu-id="46480-115">This technique is not shown here; see [Visual Basic and WPF Event Handling](visual-basic-and-wpf-event-handling.md).</span></span>  
  
 [!code-xaml[RoutedEventAddRemoveHandler#XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventAddRemoveHandler/CSharp/default.xaml#xaml)]  
  
 [!code-csharp[RoutedEventAddRemoveHandler#Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventAddRemoveHandler/CSharp/default.xaml.cs#handler)]
 [!code-vb[RoutedEventAddRemoveHandler#Handler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventAddRemoveHandler/VisualBasic/default.xaml.vb#handler)]  
  
> [!NOTE]
> <span data-ttu-id="46480-116">Dodawanie programu obsługi zdarzeń na pierwszej stronie przeanalizowanej [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] jest znacznie prostsze.</span><span class="sxs-lookup"><span data-stu-id="46480-116">Adding an event handler in the initially parsed [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] page is much simpler.</span></span> <span data-ttu-id="46480-117">W elemencie obiektu, do którego chcesz dodać procedurę obsługi zdarzeń, Dodaj atrybut, który pasuje do nazwy zdarzenia, które chcesz obsłużyć.</span><span class="sxs-lookup"><span data-stu-id="46480-117">Within the object element where you want to add the event handler, add an attribute that matches the name of the event that you want to handle.</span></span> <span data-ttu-id="46480-118">Następnie określ wartość tego atrybutu jako nazwę metody obsługi zdarzeń zdefiniowanej w pliku związanym z kodem na stronie [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="46480-118">Then specify the value of that attribute as the name of the event handler method that you defined in the code-behind file of the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] page.</span></span> <span data-ttu-id="46480-119">Aby uzyskać więcej informacji, zobacz [Omówienie języka XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md) lub [zdarzenia kierowane — Omówienie](routed-events-overview.md).</span><span class="sxs-lookup"><span data-stu-id="46480-119">For more information, see [XAML Overview (WPF)](../../../desktop-wpf/fundamentals/xaml.md) or [Routed Events Overview](routed-events-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46480-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="46480-120">See also</span></span>

- [<span data-ttu-id="46480-121">Przegląd zdarzeń trasowanych</span><span class="sxs-lookup"><span data-stu-id="46480-121">Routed Events Overview</span></span>](routed-events-overview.md)
- [<span data-ttu-id="46480-122">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="46480-122">How-to Topics</span></span>](events-how-to-topics.md)
