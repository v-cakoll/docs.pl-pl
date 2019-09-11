---
title: 'Instrukcje: Wykrywanie momentu zmiany tekstu w kontrolce TextBox'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TextBox control [WPF], detecting text change
- text change [WPF], detecting
- detecting text change [WPF]
ms.assetid: 1c39ee14-e37f-49fb-a0d1-a9824ca13584
ms.openlocfilehash: 8c7744e9e61b8ba796802e54435c0bf9fdbee50e
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855624"
---
# <a name="how-to-detect-when-text-in-a-textbox-has-changed"></a><span data-ttu-id="a5179-102">Instrukcje: Wykrywanie momentu zmiany tekstu w kontrolce TextBox</span><span class="sxs-lookup"><span data-stu-id="a5179-102">How to: Detect When Text in a TextBox Has Changed</span></span>

<span data-ttu-id="a5179-103">Ten przykład pokazuje jeden ze sposobów, <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> aby użyć zdarzenia do wykonania metody przy każdej zmianie tekstu <xref:System.Windows.Controls.TextBox> w kontrolce.</span><span class="sxs-lookup"><span data-stu-id="a5179-103">This example shows one way to use the <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> event to execute a method whenever the text in a <xref:System.Windows.Controls.TextBox> control has changed.</span></span>

<span data-ttu-id="a5179-104">W klasie związanej z kodem dla programu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] , która <xref:System.Windows.Controls.TextBox> zawiera kontrolkę, która ma być monitorowana pod kątem zmian, Wstaw <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> metodę do wywołania za każdym razem, gdy zdarzenie zostanie wyzwolone.</span><span class="sxs-lookup"><span data-stu-id="a5179-104">In the code-behind class for the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] that contains the <xref:System.Windows.Controls.TextBox> control that you want to monitor for changes, insert a method to call whenever the <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> event fires.</span></span>  <span data-ttu-id="a5179-105">Ta metoda musi mieć sygnaturę zgodną z oczekiwaną przez <xref:System.Windows.Controls.TextChangedEventHandler> delegata.</span><span class="sxs-lookup"><span data-stu-id="a5179-105">This method must have a signature that matches what is expected by the <xref:System.Windows.Controls.TextChangedEventHandler> delegate.</span></span>

<span data-ttu-id="a5179-106">Procedura obsługi zdarzeń jest wywoływana za każdym razem, gdy <xref:System.Windows.Controls.TextBox> zawartość kontrolki jest zmieniana przez użytkownika lub programowo.</span><span class="sxs-lookup"><span data-stu-id="a5179-106">The event handler is called whenever the contents of the <xref:System.Windows.Controls.TextBox> control are changed, either by a user or programmatically.</span></span>

> [!NOTE]
> <span data-ttu-id="a5179-107">To zdarzenie jest wyzwalane <xref:System.Windows.Controls.TextBox> , gdy kontrolka jest tworzona i początkowo wypełniana tekstem.</span><span class="sxs-lookup"><span data-stu-id="a5179-107">This event fires when the <xref:System.Windows.Controls.TextBox> control is created and initially populated with text.</span></span>

## <a name="example"></a><span data-ttu-id="a5179-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="a5179-108">Example</span></span>

<span data-ttu-id="a5179-109">W obszarze [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] , który <xref:System.Windows.Controls.TextBox> definiuje kontrolkę, należy <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> określić atrybut o wartości zgodnej z nazwą metody programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="a5179-109">In the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] that defines your <xref:System.Windows.Controls.TextBox> control, specify the <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> attribute with a value that matches the event handler method name.</span></span>

[!code-xaml[TextBox_MiscCode#_TextChangedXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textchangedxaml)]

## <a name="example"></a><span data-ttu-id="a5179-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="a5179-110">Example</span></span>

<span data-ttu-id="a5179-111">W klasie związanej z kodem dla programu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] , która <xref:System.Windows.Controls.TextBox> zawiera kontrolkę, która ma być monitorowana pod kątem zmian, Wstaw <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> metodę do wywołania za każdym razem, gdy zdarzenie zostanie wyzwolone.</span><span class="sxs-lookup"><span data-stu-id="a5179-111">In the code-behind class for the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] that contains the <xref:System.Windows.Controls.TextBox> control that you want to monitor for changes, insert a method to call whenever the <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> event fires.</span></span>  <span data-ttu-id="a5179-112">Ta metoda musi mieć sygnaturę zgodną z oczekiwaną przez <xref:System.Windows.Controls.TextChangedEventHandler> delegata.</span><span class="sxs-lookup"><span data-stu-id="a5179-112">This method must have a signature that matches what is expected by the <xref:System.Windows.Controls.TextChangedEventHandler> delegate.</span></span>

[!code-csharp[TextBox_MiscCode#_TextChangedEventHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textchangedeventhandler)]
[!code-vb[TextBox_MiscCode#_TextChangedEventHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_textchangedeventhandler)]

<span data-ttu-id="a5179-113">Procedura obsługi zdarzeń jest wywoływana za każdym razem, gdy <xref:System.Windows.Controls.TextBox> zawartość kontrolki jest zmieniana przez użytkownika lub programowo.</span><span class="sxs-lookup"><span data-stu-id="a5179-113">The event handler is called whenever the contents of the <xref:System.Windows.Controls.TextBox> control are changed, either by a user or programmatically.</span></span>

> [!NOTE]
> <span data-ttu-id="a5179-114">To zdarzenie jest wyzwalane <xref:System.Windows.Controls.TextBox> , gdy kontrolka jest tworzona i początkowo wypełniana tekstem.</span><span class="sxs-lookup"><span data-stu-id="a5179-114">This event fires when the <xref:System.Windows.Controls.TextBox> control is created and initially populated with text.</span></span>

<span data-ttu-id="a5179-115">Komentarze</span><span class="sxs-lookup"><span data-stu-id="a5179-115">Comments</span></span>

## <a name="see-also"></a><span data-ttu-id="a5179-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a5179-116">See also</span></span>

- <xref:System.Windows.Controls.TextChangedEventArgs>
- [<span data-ttu-id="a5179-117">TextBox — omówienie</span><span class="sxs-lookup"><span data-stu-id="a5179-117">TextBox Overview</span></span>](textbox-overview.md)
- [<span data-ttu-id="a5179-118">RichTextBox — omówienie</span><span class="sxs-lookup"><span data-stu-id="a5179-118">RichTextBox Overview</span></span>](richtextbox-overview.md)
