---
title: Jak implementować powiązaną walidację
description: Dowiedz się, jak za pomocą walidacji powiązania zapewnić wizualną opinię użytkownikowi po wprowadzeniu nieprawidłowej wartości w Windows Presentation Foundation (WPF).
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- validation of binding [WPF]
- data binding [WPF], validation of binding
- binding [WPF], validation of
ms.assetid: eb98b33d-9866-49ae-b981-bc5ff20d607a
ms.openlocfilehash: 0813be9f79a83a9dae26db1dadb58b5e973339fd
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617885"
---
# <a name="how-to-implement-binding-validation"></a><span data-ttu-id="a8527-103">Jak implementować powiązaną walidację</span><span class="sxs-lookup"><span data-stu-id="a8527-103">How to: Implement Binding Validation</span></span>

<span data-ttu-id="a8527-104">W tym przykładzie pokazano, jak za pomocą <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> i wyzwalacza stylu zapewnić wizualną opinię, aby poinformować użytkownika o wprowadzeniu nieprawidłowej wartości na podstawie niestandardowej reguły walidacji.</span><span class="sxs-lookup"><span data-stu-id="a8527-104">This example shows how to use an <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> and a style trigger to provide visual feedback to inform the user when an invalid value is entered, based on a custom validation rule.</span></span>

## <a name="example"></a><span data-ttu-id="a8527-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="a8527-105">Example</span></span>

<span data-ttu-id="a8527-106">Zawartość tekstowa <xref:System.Windows.Controls.TextBox> w poniższym przykładzie jest powiązana z `Age` właściwością (typu int) obiektu źródłowego powiązania o nazwie `ods` .</span><span class="sxs-lookup"><span data-stu-id="a8527-106">The text content of the <xref:System.Windows.Controls.TextBox> in the following example is bound to the `Age` property (of type int) of a binding source object named `ods`.</span></span> <span data-ttu-id="a8527-107">Powiązanie jest skonfigurowane tak, aby korzystało z reguły walidacji o nazwie, `AgeRangeRule` tak że jeśli użytkownik wpisze znaki niebędące cyframi lub wartość, która jest mniejsza niż 21 lub większa niż 130, obok pola tekstowego pojawia się czerwony wykrzyknik, a w polu tekstowym pojawia się etykietka narzędzia z komunikatem o błędzie.</span><span class="sxs-lookup"><span data-stu-id="a8527-107">The binding is set up to use a validation rule named `AgeRangeRule` so that if the user enters non-numeric characters or a value that is smaller than 21 or greater than 130, a red exclamation mark appears next to the text box and a tool tip with the error message appears when the user moves the mouse over the text box.</span></span>

[!code-xaml[BindValidation#2](~/samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml#2)]

<span data-ttu-id="a8527-108">Poniższy przykład pokazuje implementację `AgeRangeRule` , która dziedziczy z <xref:System.Windows.Controls.ValidationRule> i zastępuje <xref:System.Windows.Controls.ValidationRule.Validate%2A> metodę.</span><span class="sxs-lookup"><span data-stu-id="a8527-108">The following example shows the implementation of `AgeRangeRule`, which inherits from <xref:System.Windows.Controls.ValidationRule> and overrides the <xref:System.Windows.Controls.ValidationRule.Validate%2A> method.</span></span> <span data-ttu-id="a8527-109">`Int32.Parse`Metoda jest wywoływana dla wartości, aby upewnić się, że nie zawiera żadnych nieprawidłowych znaków.</span><span class="sxs-lookup"><span data-stu-id="a8527-109">The `Int32.Parse` method is called on the value to make sure that it does not contain any invalid characters.</span></span> <span data-ttu-id="a8527-110"><xref:System.Windows.Controls.ValidationRule.Validate%2A>Metoda zwraca <xref:System.Windows.Controls.ValidationResult> , która wskazuje, czy wartość jest prawidłowa w zależności od tego, czy wyjątek jest przechwytywany podczas analizowania i czy wartość wieku znajduje się poza dolną i górną granicą.</span><span class="sxs-lookup"><span data-stu-id="a8527-110">The <xref:System.Windows.Controls.ValidationRule.Validate%2A> method returns a <xref:System.Windows.Controls.ValidationResult> that indicates if the value is valid based on whether an exception is caught during the parsing and whether the age value is outside of the lower and upper bounds.</span></span>

[!code-csharp[BindValidation#3](~/samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/AgeRangeRule.cs#3)]
[!code-vb[BindValidation#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BindValidation/VisualBasic/AgeRangeRule.vb#3)]

<span data-ttu-id="a8527-111">Poniższy przykład pokazuje niestandardowy <xref:System.Windows.Controls.ControlTemplate> `validationTemplate` , który tworzy czerwony wykrzyknik, aby powiadomić użytkownika o błędzie walidacji.</span><span class="sxs-lookup"><span data-stu-id="a8527-111">The following example shows the custom <xref:System.Windows.Controls.ControlTemplate> `validationTemplate` that creates a red exclamation mark to notify the user of a validation error.</span></span> <span data-ttu-id="a8527-112">Szablony kontrolek służą do ponownego definiowania wyglądu kontrolki.</span><span class="sxs-lookup"><span data-stu-id="a8527-112">Control templates are used to redefine the appearance of a control.</span></span>

[!code-xaml[BindValidation#4](~/samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml#4)]

<span data-ttu-id="a8527-113">Jak pokazano w poniższym przykładzie, <xref:System.Windows.Controls.ToolTip> pokazuje komunikat o błędzie jest tworzony przy użyciu stylu o nazwie `textBoxInError` .</span><span class="sxs-lookup"><span data-stu-id="a8527-113">As shown in the following example, the <xref:System.Windows.Controls.ToolTip> that shows the error message is created using the style named `textBoxInError`.</span></span> <span data-ttu-id="a8527-114">Jeśli wartość <xref:System.Windows.Controls.Validation.HasError%2A> jest `true` , wyzwalacz ustawia etykietka narzędzia bieżącego <xref:System.Windows.Controls.TextBox> do pierwszego błędu walidacji.</span><span class="sxs-lookup"><span data-stu-id="a8527-114">If the value of <xref:System.Windows.Controls.Validation.HasError%2A> is `true`, the trigger sets the tool tip of the current <xref:System.Windows.Controls.TextBox> to its first validation error.</span></span> <span data-ttu-id="a8527-115">Wartość <xref:System.Windows.Data.Binding.RelativeSource%2A> jest ustawiona na <xref:System.Windows.Data.RelativeSourceMode.Self> , odwołująca się do bieżącego elementu.</span><span class="sxs-lookup"><span data-stu-id="a8527-115">The <xref:System.Windows.Data.Binding.RelativeSource%2A> is set to <xref:System.Windows.Data.RelativeSourceMode.Self>, referring to the current element.</span></span>

[!code-xaml[BindValidation#5](~/samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml#5)]

<span data-ttu-id="a8527-116">Aby zapoznać się z kompletnym przykładem, zobacz [Sample Validation rebind](https://github.com/Microsoft/WPF-Samples/tree/master/Data%20Binding/BindValidation).</span><span class="sxs-lookup"><span data-stu-id="a8527-116">For the complete example, see [Bind Validation sample](https://github.com/Microsoft/WPF-Samples/tree/master/Data%20Binding/BindValidation).</span></span>
  
<span data-ttu-id="a8527-117">Należy pamiętać, że jeśli nie podasz niestandardowego <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> domyślnego szablonu błędu, pojawi się informacja o tym, że w przypadku błędu sprawdzania poprawności zostanie wyświetlona wizualna opinia dla użytkownika.</span><span class="sxs-lookup"><span data-stu-id="a8527-117">Note that if you do not provide a custom <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> the default error template appears to provide visual feedback to the user when there is a validation error.</span></span> <span data-ttu-id="a8527-118">Aby uzyskać więcej informacji, zobacz "Sprawdzanie poprawności danych" w temacie [powiązanie danych](../../../desktop-wpf/data/data-binding-overview.md) .</span><span class="sxs-lookup"><span data-stu-id="a8527-118">See "Data Validation" in [Data Binding Overview](../../../desktop-wpf/data/data-binding-overview.md) for more information.</span></span> <span data-ttu-id="a8527-119">Ponadto program [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] udostępnia wbudowaną regułę walidacji, która przechwytuje wyjątki, które są zgłaszane podczas aktualizacji właściwości źródła powiązania.</span><span class="sxs-lookup"><span data-stu-id="a8527-119">Also, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] provides a built-in validation rule that catches exceptions that are thrown during the update of the binding source property.</span></span> <span data-ttu-id="a8527-120">Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Controls.ExceptionValidationRule>.</span><span class="sxs-lookup"><span data-stu-id="a8527-120">For more information, see <xref:System.Windows.Controls.ExceptionValidationRule>.</span></span>

## <a name="see-also"></a><span data-ttu-id="a8527-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a8527-121">See also</span></span>

- [<span data-ttu-id="a8527-122">Przegląd powiązań danych</span><span class="sxs-lookup"><span data-stu-id="a8527-122">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="a8527-123">— Tematy porad</span><span class="sxs-lookup"><span data-stu-id="a8527-123">How-to Topics</span></span>](data-binding-how-to-topics.md)
