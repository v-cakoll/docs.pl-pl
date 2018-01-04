---
title: "Jak dodać obsługę zdarzeń z użyciem kodu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- event handlers [WPF], adding
- XAML [WPF], adding event handlers
ms.assetid: 269c61e0-6bd9-4291-9bed-1c5ee66da486
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3abcd441219e58df2e5a0d4b66447e255c6aabd4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-an-event-handler-using-code"></a><span data-ttu-id="6aa63-102">Jak dodać obsługę zdarzeń z użyciem kodu</span><span class="sxs-lookup"><span data-stu-id="6aa63-102">How to: Add an Event Handler Using Code</span></span>
<span data-ttu-id="6aa63-103">W tym przykładzie przedstawiono sposób dodawania obsługi zdarzeń do elementu przy użyciu kodu.</span><span class="sxs-lookup"><span data-stu-id="6aa63-103">This example shows how to add an event handler to an element by using code.</span></span>  
  
 <span data-ttu-id="6aa63-104">Jeśli chcesz dodać program obsługi zdarzeń do [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] elementu i stronie znaczników, który zawiera element został już załadowany, należy dodać program obsługi przy użyciu kodu.</span><span class="sxs-lookup"><span data-stu-id="6aa63-104">If you want to add an event handler to a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] element, and the markup page that contains the element has already been loaded, you must add the handler using code.</span></span> <span data-ttu-id="6aa63-105">Alternatywnie Jeśli tworzysz górę drzewa element aplikacji całkowicie przy użyciu kodu i typ deklarujący nie elementów przy użyciu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], należy wywołać określonej metody dodawania obsługi zdarzeń do skonstruowanego element drzewa.</span><span class="sxs-lookup"><span data-stu-id="6aa63-105">Alternatively, if you are building up the element tree for an application entirely using code and not declaring any elements using [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], you can call specific methods to add event handlers to the constructed element tree.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6aa63-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="6aa63-106">Example</span></span>  
 <span data-ttu-id="6aa63-107">Poniższy przykład umożliwia dodanie nowego <xref:System.Windows.Controls.Button> do istniejącej strony wstępnie zdefiniowanego w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6aa63-107">The following example adds a new <xref:System.Windows.Controls.Button> to an existing page that is initially defined in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span> <span data-ttu-id="6aa63-108">Plik CodeBehind implementuje metoda obsługi zdarzeń, a następnie dodaje tej metody jako nowy program obsługi zdarzeń, na <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="6aa63-108">A code-behind file implements an event handler method and then adds that method as a new event handler on the <xref:System.Windows.Controls.Button>.</span></span>  
  
 <span data-ttu-id="6aa63-109">[!INCLUDE[TLA2#tla_cshrp](../../../../includes/tla2sharptla-cshrp-md.md)] Przykładzie użyto `+=` operatora, aby przypisać program obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="6aa63-109">The [!INCLUDE[TLA2#tla_cshrp](../../../../includes/tla2sharptla-cshrp-md.md)] example uses the `+=` operator to assign a handler to an event.</span></span> <span data-ttu-id="6aa63-110">To jest tym samym operator, który jest używany do przypisywania obsługi w [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] model obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="6aa63-110">This is the same operator that is used to assign a handler in the [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] event handling model.</span></span> [!INCLUDE[TLA#tla_visualb](../../../../includes/tlasharptla-visualb-md.md)]<span data-ttu-id="6aa63-111">nie obsługuje tego operatora jako środek Dodawanie programów obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="6aa63-111"> does not support this operator as a means of adding event handlers.</span></span> <span data-ttu-id="6aa63-112">Zamiast tego wymaga jednego z dwóch metod:</span><span class="sxs-lookup"><span data-stu-id="6aa63-112">It instead requires one of two techniques:</span></span>  
  
-   <span data-ttu-id="6aa63-113">Użyj <xref:System.Windows.UIElement.AddHandler%2A> metody, wraz z `AddressOf` operatora, aby odwołać implementację programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="6aa63-113">Use the <xref:System.Windows.UIElement.AddHandler%2A> method, together with an `AddressOf` operator, to reference the event handler implementation.</span></span>  
  
-   <span data-ttu-id="6aa63-114">Użyj `Handles` słowa kluczowego jako część definicji programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="6aa63-114">Use the `Handles` keyword as part of the event handler definition.</span></span> <span data-ttu-id="6aa63-115">Ta metoda nie jest wyświetlany w tym miejscu; zobacz [Visual Basic i obsługi zdarzeń WPF](../../../../docs/framework/wpf/advanced/visual-basic-and-wpf-event-handling.md).</span><span class="sxs-lookup"><span data-stu-id="6aa63-115">This technique is not shown here; see [Visual Basic and WPF Event Handling](../../../../docs/framework/wpf/advanced/visual-basic-and-wpf-event-handling.md).</span></span>  
  
 [!code-xaml[RoutedEventAddRemoveHandler#XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventAddRemoveHandler/CSharp/default.xaml#xaml)]  
  
 [!code-csharp[RoutedEventAddRemoveHandler#Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventAddRemoveHandler/CSharp/default.xaml.cs#handler)]
 [!code-vb[RoutedEventAddRemoveHandler#Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventAddRemoveHandler/VisualBasic/default.xaml.vb#handler)]  
  
> [!NOTE]
>  <span data-ttu-id="6aa63-116">Dodawanie obsługi zdarzeń w początkowo przeanalizowany [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] strony jest znacznie prostsze.</span><span class="sxs-lookup"><span data-stu-id="6aa63-116">Adding an event handler in the initially parsed [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] page is much simpler.</span></span> <span data-ttu-id="6aa63-117">W elemencie obiektu, której chcesz dodać procedury obsługi zdarzeń Dodaj atrybut, który odpowiada nazwie zdarzenia, które mają być obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="6aa63-117">Within the object element where you want to add the event handler, add an attribute that matches the name of the event that you want to handle.</span></span> <span data-ttu-id="6aa63-118">Następnie określ wartość atrybutu z nazwą metody obsługi zdarzeń, zdefiniowanego w pliku CodeBehind [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] strony.</span><span class="sxs-lookup"><span data-stu-id="6aa63-118">Then specify the value of that attribute as the name of the event handler method that you defined in the code-behind file of the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] page.</span></span> <span data-ttu-id="6aa63-119">Aby uzyskać więcej informacji, zobacz [omówienie XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md) lub [kierowane Przegląd zdarzeń](../../../../docs/framework/wpf/advanced/routed-events-overview.md).</span><span class="sxs-lookup"><span data-stu-id="6aa63-119">For more information, see [XAML Overview (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md) or [Routed Events Overview](../../../../docs/framework/wpf/advanced/routed-events-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6aa63-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6aa63-120">See Also</span></span>  
 [<span data-ttu-id="6aa63-121">Przegląd zdarzeń trasowanych</span><span class="sxs-lookup"><span data-stu-id="6aa63-121">Routed Events Overview</span></span>](../../../../docs/framework/wpf/advanced/routed-events-overview.md)  
 [<span data-ttu-id="6aa63-122">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="6aa63-122">How-to Topics</span></span>](../../../../docs/framework/wpf/advanced/events-how-to-topics.md)
