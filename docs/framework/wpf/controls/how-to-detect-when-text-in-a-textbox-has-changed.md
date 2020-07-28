---
title: Jak wykryć kiedy tekst w TextBox uległ zmianie
description: Dowiedz się, jak używać zdarzenia textchanging do uruchamiania metody za każdym razem, gdy tekst w kontrolce TextBox zmieni się w aplikacji Windows Presentation Foundation.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TextBox control [WPF], detecting text change
- text change [WPF], detecting
- detecting text change [WPF]
ms.assetid: 1c39ee14-e37f-49fb-a0d1-a9824ca13584
ms.openlocfilehash: 1e054380a8c77d32e6bb4adbbcb032e531bbefd0
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166231"
---
# <a name="how-to-detect-when-text-in-a-textbox-has-changed"></a><span data-ttu-id="4c31c-103">Jak wykryć kiedy tekst w TextBox uległ zmianie</span><span class="sxs-lookup"><span data-stu-id="4c31c-103">How to: Detect When Text in a TextBox Has Changed</span></span>

<span data-ttu-id="4c31c-104">Ten przykład pokazuje jeden ze sposobów, aby użyć <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> zdarzenia do wykonania metody przy każdej zmianie tekstu w <xref:System.Windows.Controls.TextBox> kontrolce.</span><span class="sxs-lookup"><span data-stu-id="4c31c-104">This example shows one way to use the <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> event to execute a method whenever the text in a <xref:System.Windows.Controls.TextBox> control has changed.</span></span>

<span data-ttu-id="4c31c-105">W klasie związanej z kodem dla programu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] , która zawiera <xref:System.Windows.Controls.TextBox> kontrolkę, która ma być monitorowana pod kątem zmian, Wstaw metodę do wywołania za każdym razem, gdy zdarzenie zostanie wyzwolone <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> .</span><span class="sxs-lookup"><span data-stu-id="4c31c-105">In the code-behind class for the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] that contains the <xref:System.Windows.Controls.TextBox> control that you want to monitor for changes, insert a method to call whenever the <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> event fires.</span></span>  <span data-ttu-id="4c31c-106">Ta metoda musi mieć sygnaturę zgodną z oczekiwaną przez <xref:System.Windows.Controls.TextChangedEventHandler> delegata.</span><span class="sxs-lookup"><span data-stu-id="4c31c-106">This method must have a signature that matches what is expected by the <xref:System.Windows.Controls.TextChangedEventHandler> delegate.</span></span>

<span data-ttu-id="4c31c-107">Procedura obsługi zdarzeń jest wywoływana za każdym razem, gdy zawartość <xref:System.Windows.Controls.TextBox> kontrolki jest zmieniana przez użytkownika lub programowo.</span><span class="sxs-lookup"><span data-stu-id="4c31c-107">The event handler is called whenever the contents of the <xref:System.Windows.Controls.TextBox> control are changed, either by a user or programmatically.</span></span>

> [!NOTE]
> <span data-ttu-id="4c31c-108">To zdarzenie jest wyzwalane <xref:System.Windows.Controls.TextBox> , gdy kontrolka jest tworzona i początkowo wypełniana tekstem.</span><span class="sxs-lookup"><span data-stu-id="4c31c-108">This event fires when the <xref:System.Windows.Controls.TextBox> control is created and initially populated with text.</span></span>

## <a name="example"></a><span data-ttu-id="4c31c-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="4c31c-109">Example</span></span>

<span data-ttu-id="4c31c-110">W obszarze, [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] który definiuje <xref:System.Windows.Controls.TextBox> kontrolkę, należy określić <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> atrybut o wartości zgodnej z nazwą metody programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="4c31c-110">In the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] that defines your <xref:System.Windows.Controls.TextBox> control, specify the <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> attribute with a value that matches the event handler method name.</span></span>

[!code-xaml[TextBox_MiscCode#_TextChangedXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textchangedxaml)]

## <a name="example"></a><span data-ttu-id="4c31c-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="4c31c-111">Example</span></span>

<span data-ttu-id="4c31c-112">W klasie związanej z kodem dla programu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] , która zawiera <xref:System.Windows.Controls.TextBox> kontrolkę, która ma być monitorowana pod kątem zmian, Wstaw metodę do wywołania za każdym razem, gdy zdarzenie zostanie wyzwolone <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> .</span><span class="sxs-lookup"><span data-stu-id="4c31c-112">In the code-behind class for the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] that contains the <xref:System.Windows.Controls.TextBox> control that you want to monitor for changes, insert a method to call whenever the <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> event fires.</span></span>  <span data-ttu-id="4c31c-113">Ta metoda musi mieć sygnaturę zgodną z oczekiwaną przez <xref:System.Windows.Controls.TextChangedEventHandler> delegata.</span><span class="sxs-lookup"><span data-stu-id="4c31c-113">This method must have a signature that matches what is expected by the <xref:System.Windows.Controls.TextChangedEventHandler> delegate.</span></span>

[!code-csharp[TextBox_MiscCode#_TextChangedEventHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textchangedeventhandler)]
[!code-vb[TextBox_MiscCode#_TextChangedEventHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_textchangedeventhandler)]

<span data-ttu-id="4c31c-114">Procedura obsługi zdarzeń jest wywoływana za każdym razem, gdy zawartość <xref:System.Windows.Controls.TextBox> kontrolki jest zmieniana przez użytkownika lub programowo.</span><span class="sxs-lookup"><span data-stu-id="4c31c-114">The event handler is called whenever the contents of the <xref:System.Windows.Controls.TextBox> control are changed, either by a user or programmatically.</span></span>

> [!NOTE]
> <span data-ttu-id="4c31c-115">To zdarzenie jest wyzwalane <xref:System.Windows.Controls.TextBox> , gdy kontrolka jest tworzona i początkowo wypełniana tekstem.</span><span class="sxs-lookup"><span data-stu-id="4c31c-115">This event fires when the <xref:System.Windows.Controls.TextBox> control is created and initially populated with text.</span></span>

<span data-ttu-id="4c31c-116">Komentarze</span><span class="sxs-lookup"><span data-stu-id="4c31c-116">Comments</span></span>

## <a name="see-also"></a><span data-ttu-id="4c31c-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4c31c-117">See also</span></span>

- <xref:System.Windows.Controls.TextChangedEventArgs>
- [<span data-ttu-id="4c31c-118">TextBox — Przegląd</span><span class="sxs-lookup"><span data-stu-id="4c31c-118">TextBox Overview</span></span>](textbox-overview.md)
- [<span data-ttu-id="4c31c-119">RichTextBox — Przegląd</span><span class="sxs-lookup"><span data-stu-id="4c31c-119">RichTextBox Overview</span></span>](richtextbox-overview.md)
