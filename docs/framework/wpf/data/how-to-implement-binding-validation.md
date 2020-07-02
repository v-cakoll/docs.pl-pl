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
# <a name="how-to-implement-binding-validation"></a>Jak implementować powiązaną walidację

W tym przykładzie pokazano, jak za pomocą <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> i wyzwalacza stylu zapewnić wizualną opinię, aby poinformować użytkownika o wprowadzeniu nieprawidłowej wartości na podstawie niestandardowej reguły walidacji.

## <a name="example"></a>Przykład

Zawartość tekstowa <xref:System.Windows.Controls.TextBox> w poniższym przykładzie jest powiązana z `Age` właściwością (typu int) obiektu źródłowego powiązania o nazwie `ods` . Powiązanie jest skonfigurowane tak, aby korzystało z reguły walidacji o nazwie, `AgeRangeRule` tak że jeśli użytkownik wpisze znaki niebędące cyframi lub wartość, która jest mniejsza niż 21 lub większa niż 130, obok pola tekstowego pojawia się czerwony wykrzyknik, a w polu tekstowym pojawia się etykietka narzędzia z komunikatem o błędzie.

[!code-xaml[BindValidation#2](~/samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml#2)]

Poniższy przykład pokazuje implementację `AgeRangeRule` , która dziedziczy z <xref:System.Windows.Controls.ValidationRule> i zastępuje <xref:System.Windows.Controls.ValidationRule.Validate%2A> metodę. `Int32.Parse`Metoda jest wywoływana dla wartości, aby upewnić się, że nie zawiera żadnych nieprawidłowych znaków. <xref:System.Windows.Controls.ValidationRule.Validate%2A>Metoda zwraca <xref:System.Windows.Controls.ValidationResult> , która wskazuje, czy wartość jest prawidłowa w zależności od tego, czy wyjątek jest przechwytywany podczas analizowania i czy wartość wieku znajduje się poza dolną i górną granicą.

[!code-csharp[BindValidation#3](~/samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/AgeRangeRule.cs#3)]
[!code-vb[BindValidation#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BindValidation/VisualBasic/AgeRangeRule.vb#3)]

Poniższy przykład pokazuje niestandardowy <xref:System.Windows.Controls.ControlTemplate> `validationTemplate` , który tworzy czerwony wykrzyknik, aby powiadomić użytkownika o błędzie walidacji. Szablony kontrolek służą do ponownego definiowania wyglądu kontrolki.

[!code-xaml[BindValidation#4](~/samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml#4)]

Jak pokazano w poniższym przykładzie, <xref:System.Windows.Controls.ToolTip> pokazuje komunikat o błędzie jest tworzony przy użyciu stylu o nazwie `textBoxInError` . Jeśli wartość <xref:System.Windows.Controls.Validation.HasError%2A> jest `true` , wyzwalacz ustawia etykietka narzędzia bieżącego <xref:System.Windows.Controls.TextBox> do pierwszego błędu walidacji. Wartość <xref:System.Windows.Data.Binding.RelativeSource%2A> jest ustawiona na <xref:System.Windows.Data.RelativeSourceMode.Self> , odwołująca się do bieżącego elementu.

[!code-xaml[BindValidation#5](~/samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml#5)]

Aby zapoznać się z kompletnym przykładem, zobacz [Sample Validation rebind](https://github.com/Microsoft/WPF-Samples/tree/master/Data%20Binding/BindValidation).
  
Należy pamiętać, że jeśli nie podasz niestandardowego <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> domyślnego szablonu błędu, pojawi się informacja o tym, że w przypadku błędu sprawdzania poprawności zostanie wyświetlona wizualna opinia dla użytkownika. Aby uzyskać więcej informacji, zobacz "Sprawdzanie poprawności danych" w temacie [powiązanie danych](../../../desktop-wpf/data/data-binding-overview.md) . Ponadto program [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] udostępnia wbudowaną regułę walidacji, która przechwytuje wyjątki, które są zgłaszane podczas aktualizacji właściwości źródła powiązania. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Controls.ExceptionValidationRule>.

## <a name="see-also"></a>Zobacz także

- [Przegląd powiązań danych](../../../desktop-wpf/data/data-binding-overview.md)
- [— Tematy porad](data-binding-how-to-topics.md)
