---
title: Jak dodać obsługę zdarzeń z użyciem kodu
description: Użyj tego przykładu, aby dowiedzieć się, jak dodać program obsługi zdarzeń do elementu w Windows Presentation Foundation przy użyciu kodu, zamiast deklarowania go przy użyciu języka XAML.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- event handlers [WPF], adding
- XAML [WPF], adding event handlers
ms.assetid: 269c61e0-6bd9-4291-9bed-1c5ee66da486
ms.openlocfilehash: b36969f7a65ccbf6c9d03b22767d9eacdc177ad1
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166368"
---
# <a name="how-to-add-an-event-handler-using-code"></a><span data-ttu-id="a871a-103">Jak dodać obsługę zdarzeń z użyciem kodu</span><span class="sxs-lookup"><span data-stu-id="a871a-103">How to: Add an Event Handler Using Code</span></span>
<span data-ttu-id="a871a-104">Ten przykład pokazuje, jak dodać program obsługi zdarzeń do elementu przy użyciu kodu.</span><span class="sxs-lookup"><span data-stu-id="a871a-104">This example shows how to add an event handler to an element by using code.</span></span>  
  
 <span data-ttu-id="a871a-105">Jeśli chcesz dodać program obsługi zdarzeń do [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] elementu, a strona znaczników, która zawiera element, jest już załadowana, należy dodać procedurę obsługi przy użyciu kodu.</span><span class="sxs-lookup"><span data-stu-id="a871a-105">If you want to add an event handler to a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] element, and the markup page that contains the element has already been loaded, you must add the handler using code.</span></span> <span data-ttu-id="a871a-106">Alternatywnie, jeśli tworzysz drzewo elementów dla aplikacji całkowicie przy użyciu kodu i nie deklaruje żadnych elementów przy użyciu, można [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] wywołać konkretne metody, aby dodać obsługę zdarzeń do drzewa skonstruowane elementy.</span><span class="sxs-lookup"><span data-stu-id="a871a-106">Alternatively, if you are building up the element tree for an application entirely using code and not declaring any elements using [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], you can call specific methods to add event handlers to the constructed element tree.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a871a-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="a871a-107">Example</span></span>  
 <span data-ttu-id="a871a-108">Poniższy przykład dodaje nową <xref:System.Windows.Controls.Button> do istniejącej strony, która jest początkowo zdefiniowana w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="a871a-108">The following example adds a new <xref:System.Windows.Controls.Button> to an existing page that is initially defined in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span> <span data-ttu-id="a871a-109">Plik związany z kodem implementuje metodę obsługi zdarzeń, a następnie dodaje tę metodę jako nowy program obsługi zdarzeń na <xref:System.Windows.Controls.Button> .</span><span class="sxs-lookup"><span data-stu-id="a871a-109">A code-behind file implements an event handler method and then adds that method as a new event handler on the <xref:System.Windows.Controls.Button>.</span></span>  
  
 <span data-ttu-id="a871a-110">W przykładzie w języku C# `+=` za pomocą operatora można przypisać do zdarzenia procedurę obsługi.</span><span class="sxs-lookup"><span data-stu-id="a871a-110">The C# example uses the `+=` operator to assign a handler to an event.</span></span> <span data-ttu-id="a871a-111">Jest to ten sam operator, który jest używany do przypisania procedury obsługi w modelu obsługi zdarzeń środowiska uruchomieniowego języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="a871a-111">This is the same operator that is used to assign a handler in the common language runtime (CLR) event handling model.</span></span> <span data-ttu-id="a871a-112">Firma Microsoft Visual Basic nie obsługuje tego operatora jako metody dodawania obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="a871a-112">Microsoft Visual Basic does not support this operator as a means of adding event handlers.</span></span> <span data-ttu-id="a871a-113">Zamiast tego wymaga jednej z dwóch technik:</span><span class="sxs-lookup"><span data-stu-id="a871a-113">It instead requires one of two techniques:</span></span>  
  
- <span data-ttu-id="a871a-114">Użyj <xref:System.Windows.UIElement.AddHandler%2A> metody wraz z `AddressOf` operatorem, aby odwołać się do implementacji programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="a871a-114">Use the <xref:System.Windows.UIElement.AddHandler%2A> method, together with an `AddressOf` operator, to reference the event handler implementation.</span></span>  
  
- <span data-ttu-id="a871a-115">Użyj `Handles` słowa kluczowego jako części definicji programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="a871a-115">Use the `Handles` keyword as part of the event handler definition.</span></span> <span data-ttu-id="a871a-116">Ta technika nie jest tu pokazana. Zobacz [Visual Basic i obsługa zdarzeń WPF](visual-basic-and-wpf-event-handling.md).</span><span class="sxs-lookup"><span data-stu-id="a871a-116">This technique is not shown here; see [Visual Basic and WPF Event Handling](visual-basic-and-wpf-event-handling.md).</span></span>  
  
 [!code-xaml[RoutedEventAddRemoveHandler#XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventAddRemoveHandler/CSharp/default.xaml#xaml)]  
  
 [!code-csharp[RoutedEventAddRemoveHandler#Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventAddRemoveHandler/CSharp/default.xaml.cs#handler)]
 [!code-vb[RoutedEventAddRemoveHandler#Handler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventAddRemoveHandler/VisualBasic/default.xaml.vb#handler)]  
  
> [!NOTE]
> <span data-ttu-id="a871a-117">Dodawanie programu obsługi zdarzeń na pierwszej przeanalizowanej [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] stronie jest znacznie prostsze.</span><span class="sxs-lookup"><span data-stu-id="a871a-117">Adding an event handler in the initially parsed [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] page is much simpler.</span></span> <span data-ttu-id="a871a-118">W elemencie obiektu, do którego chcesz dodać procedurę obsługi zdarzeń, Dodaj atrybut, który pasuje do nazwy zdarzenia, które chcesz obsłużyć.</span><span class="sxs-lookup"><span data-stu-id="a871a-118">Within the object element where you want to add the event handler, add an attribute that matches the name of the event that you want to handle.</span></span> <span data-ttu-id="a871a-119">Następnie określ wartość tego atrybutu jako nazwę metody obsługi zdarzeń zdefiniowanej w pliku związanym z kodem na [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] stronie.</span><span class="sxs-lookup"><span data-stu-id="a871a-119">Then specify the value of that attribute as the name of the event handler method that you defined in the code-behind file of the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] page.</span></span> <span data-ttu-id="a871a-120">Aby uzyskać więcej informacji, zobacz [Omówienie języka XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md) lub [zdarzenia kierowane — Omówienie](routed-events-overview.md).</span><span class="sxs-lookup"><span data-stu-id="a871a-120">For more information, see [XAML Overview (WPF)](../../../desktop-wpf/fundamentals/xaml.md) or [Routed Events Overview](routed-events-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a871a-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a871a-121">See also</span></span>

- [<span data-ttu-id="a871a-122">Przegląd Zdarzenia trasowane</span><span class="sxs-lookup"><span data-stu-id="a871a-122">Routed Events Overview</span></span>](routed-events-overview.md)
- [<span data-ttu-id="a871a-123">— Tematy porad</span><span class="sxs-lookup"><span data-stu-id="a871a-123">How-to Topics</span></span>](events-how-to-topics.md)
