---
title: "Jak dodać obsługę klasy dla zdarzenia trasowanego"
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
- routed events [WPF], class handlers
- task_core_add_class_handling_routed_properties [WPF]
- class handlers [WPF], routed events
ms.assetid: 15b7b06c-9112-4ee5-b30a-65d10c5c5df6
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: abbbdce0ca12c4d8bdd12f616bf49c3d6f66f441
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-add-class-handling-for-a-routed-event"></a><span data-ttu-id="0f9ad-102">Jak dodać obsługę klasy dla zdarzenia trasowanego</span><span class="sxs-lookup"><span data-stu-id="0f9ad-102">How to: Add Class Handling for a Routed Event</span></span>
<span data-ttu-id="0f9ad-103">Kierowane zdarzenia mogą być obsługiwane przez programy obsługi klasy lub wystąpienia obsługi na dowolny węzeł w trasie.</span><span class="sxs-lookup"><span data-stu-id="0f9ad-103">Routed events can be handled either by class handlers or instance handlers on any given node in the route.</span></span> <span data-ttu-id="0f9ad-104">Klasy obsługi są wywoływane najpierw i implementacji klasy można pominąć zdarzenia z obsługi wystąpienia lub wprowadzenie innych zachowań określonych zdarzeń na zdarzenia, które należą do klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="0f9ad-104">Class handlers are invoked first, and can be used by class implementations to suppress events from instance handling or introduce other event specific behaviors on events that are owned by base classes.</span></span> <span data-ttu-id="0f9ad-105">W tym przykładzie przedstawiono dwie metody ściśle związanych wykonawczych obsługę klas.</span><span class="sxs-lookup"><span data-stu-id="0f9ad-105">This example illustrates two closely related techniques for implementing class handlers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0f9ad-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="0f9ad-106">Example</span></span>  
 <span data-ttu-id="0f9ad-107">W tym przykładzie użyto niestandardowej klasy na podstawie <xref:System.Windows.Controls.Canvas> panelu.</span><span class="sxs-lookup"><span data-stu-id="0f9ad-107">This example uses a custom class based on the <xref:System.Windows.Controls.Canvas> panel.</span></span> <span data-ttu-id="0f9ad-108">Podstawowe lokalnych aplikacji jest, że niestandardowej klasy wprowadza zachowań na jego elementy podrzędne, w tym przechwytywaniu klikniętego dowolnego przycisku myszy po lewej stronie i oznaczania ich obsługę, zanim zostanie wywołany klasa elementu podrzędnego lub dowolnego obsługi wystąpienia na nim.</span><span class="sxs-lookup"><span data-stu-id="0f9ad-108">The basic premise of the application is that the custom class introduces behaviors on its child elements, including intercepting any left mouse button clicks and marking them handled, before the child element class or any instance handlers on it will be invoked.</span></span>  
  
 <span data-ttu-id="0f9ad-109"><xref:System.Windows.UIElement> Klasa opisuje metodę wirtualnego umożliwia klasy obsługi na <xref:System.Windows.UIElement.PreviewMouseLeftButtonDown> zdarzenia przez zastąpienie po prostu zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="0f9ad-109">The <xref:System.Windows.UIElement> class exposes a virtual method that enables class handling on the <xref:System.Windows.UIElement.PreviewMouseLeftButtonDown> event, by simply overriding the event.</span></span> <span data-ttu-id="0f9ad-110">Jest to najprostszy sposób do zaimplementowania klasy obsługi, jeśli metoda wirtualna jest dostępna w hierarchii swojej klasy.</span><span class="sxs-lookup"><span data-stu-id="0f9ad-110">This is the simplest way to implement class handling if such a virtual method is available somewhere in your class' hierarchy.</span></span> <span data-ttu-id="0f9ad-111">Poniższy kod przedstawia <xref:System.Windows.UIElement.OnPreviewMouseLeftButtonDown%2A> implementacja "MyEditContainer", która jest pochodną <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="0f9ad-111">The following code shows the <xref:System.Windows.UIElement.OnPreviewMouseLeftButtonDown%2A> implementation in the "MyEditContainer" that is derived from <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="0f9ad-112">Implementacja oznacza zdarzenia, jako obsługiwane w argumentach, a następnie dodanie kodu umożliwiają elementu źródła podstawowe widocznych zmian.</span><span class="sxs-lookup"><span data-stu-id="0f9ad-112">The implementation marks the event as handled in the arguments, and then adds some code to give the source element a basic visible change.</span></span>  
  
 [!code-csharp[ClassHandling#OnStarClassHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ClassHandling/CSharp/SDKSampleLibrary/class1.cs#onstarclasshandler)]
 [!code-vb[ClassHandling#OnStarClassHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ClassHandling/visualbasic/sdksamplelibrary/class1.vb#onstarclasshandler)]  
  
 <span data-ttu-id="0f9ad-113">Jeśli wirtualnego nie jest dostępne dla klas podstawowych lub dla określonej metody, klasy obsługi można dodać bezpośrednio za pomocą metody narzędzie <xref:System.Windows.EventManager> klasy <xref:System.Windows.EventManager.RegisterClassHandler%2A>.</span><span class="sxs-lookup"><span data-stu-id="0f9ad-113">If no virtual is available on base classes or for that particular method, class handling can be added directly using a utility method of the <xref:System.Windows.EventManager> class, <xref:System.Windows.EventManager.RegisterClassHandler%2A>.</span></span> <span data-ttu-id="0f9ad-114">Ta metoda powinna być wywoływana tylko w statyczne zainicjowanie klasy, które dodajesz klasy obsługi.</span><span class="sxs-lookup"><span data-stu-id="0f9ad-114">This method should only be called within the static initialization of classes that are adding class handling.</span></span> <span data-ttu-id="0f9ad-115">W tym przykładzie dodaje innego programu obsługi dla <xref:System.Windows.UIElement.PreviewMouseLeftButtonDown> , i w takim przypadku zarejestrowanych klasy niestandardowej klasy.</span><span class="sxs-lookup"><span data-stu-id="0f9ad-115">This example adds another handler for <xref:System.Windows.UIElement.PreviewMouseLeftButtonDown> , and in this case the registered class is the custom class.</span></span> <span data-ttu-id="0f9ad-116">Z kolei, korzystając z elementów wirtualnych, zarejestrowanych klasy to naprawdę <xref:System.Windows.UIElement> klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="0f9ad-116">In contrast, when using the virtuals, the registered class is really the <xref:System.Windows.UIElement> base class.</span></span> <span data-ttu-id="0f9ad-117">W przypadkach, gdy klasy podstawowe, jak i podklasy zarejestrować klasy obsługi najpierw są wywoływane programy obsługi podklasy.</span><span class="sxs-lookup"><span data-stu-id="0f9ad-117">In cases where base classes and subclass each register class handling, the subclass handlers are invoked first.</span></span> <span data-ttu-id="0f9ad-118">Zachowanie w aplikacji będą najpierw ten program obsługi może wyświetlić jego pola wiadomości, a następnie zostaną pokazane visual zmiany w obsłudze metody wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="0f9ad-118">The behavior in an application would be that first this handler would show its message box and then the visual change in the virtual method's handler would be shown.</span></span>  
  
 [!code-csharp[ClassHandling#StaticAndRegisterClassHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ClassHandling/CSharp/SDKSampleLibrary/class1.cs#staticandregisterclasshandler)]
 [!code-vb[ClassHandling#StaticAndRegisterClassHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ClassHandling/visualbasic/sdksamplelibrary/class1.vb#staticandregisterclasshandler)]  
  
## <a name="see-also"></a><span data-ttu-id="0f9ad-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0f9ad-119">See Also</span></span>  
 <xref:System.Windows.EventManager>  
 [<span data-ttu-id="0f9ad-120">Oznaczanie kierowane zdarzenia, ponieważ obsługiwane i klasy obsługi</span><span class="sxs-lookup"><span data-stu-id="0f9ad-120">Marking Routed Events as Handled, and Class Handling</span></span>](../../../../docs/framework/wpf/advanced/marking-routed-events-as-handled-and-class-handling.md)  
 [<span data-ttu-id="0f9ad-121">Dojście kierowanego zdarzenia</span><span class="sxs-lookup"><span data-stu-id="0f9ad-121">Handle a Routed Event</span></span>](../../../../docs/framework/wpf/advanced/how-to-handle-a-routed-event.md)  
 [<span data-ttu-id="0f9ad-122">Omówienie kierowane zdarzenia</span><span class="sxs-lookup"><span data-stu-id="0f9ad-122">Routed Events Overview</span></span>](../../../../docs/framework/wpf/advanced/routed-events-overview.md)
