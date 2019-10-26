---
title: Jak implementować powiązaną walidację
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- validation of binding [WPF]
- data binding [WPF], validation of binding
- binding [WPF], validation of
ms.assetid: eb98b33d-9866-49ae-b981-bc5ff20d607a
ms.openlocfilehash: 7a1a8df78a785066992472c7de37f958ae3467f1
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2019
ms.locfileid: "72920155"
---
# <a name="how-to-implement-binding-validation"></a>Jak implementować powiązaną walidację

Ten przykład pokazuje, jak używać <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> i wyzwalacza stylu, aby zapewnić wizualną opinię informującą użytkownika o wprowadzeniu nieprawidłowej wartości na podstawie niestandardowej reguły walidacji.

## <a name="example"></a>Przykład

Zawartość tekstowa <xref:System.Windows.Controls.TextBox> w poniższym przykładzie jest powiązana z właściwością `Age` (typu int) obiektu źródłowego powiązania o nazwie `ods`. Powiązanie jest skonfigurowane tak, aby korzystało z reguły walidacji o nazwie `AgeRangeRule`, tak że jeśli użytkownik wpisze znaki niebędące cyframi lub wartość, która jest mniejsza niż 21 lub większa niż 130, obok pola tekstowego pojawia się czerwony wykrzyknik i zostanie wyświetlona etykietka narzędzia z komunikatem o błędzie, gdy  użytkownik przesuwa wskaźnik myszy nad polem tekstowym.

[!code-xaml[BindValidation#2](~/samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml#2)]

Poniższy przykład pokazuje implementację `AgeRangeRule`, która dziedziczy po <xref:System.Windows.Controls.ValidationRule> i zastępuje metodę <xref:System.Windows.Controls.ValidationRule.Validate%2A>. Metoda `Int32.Parse` jest wywoływana na wartości, aby upewnić się, że nie zawiera żadnych nieprawidłowych znaków. Metoda <xref:System.Windows.Controls.ValidationRule.Validate%2A> zwraca <xref:System.Windows.Controls.ValidationResult>, który wskazuje, czy wartość jest poprawna w zależności od tego, czy wyjątek jest przechwytywany podczas analizowania i czy wartość wieku znajduje się poza dolną i górną granicą.

[!code-csharp[BindValidation#3](~/samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/AgeRangeRule.cs#3)]
[!code-vb[BindValidation#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BindValidation/VisualBasic/AgeRangeRule.vb#3)]

W poniższym przykładzie przedstawiono niestandardowy `validationTemplate` <xref:System.Windows.Controls.ControlTemplate>, który tworzy czerwony wykrzyknik, aby powiadomić użytkownika o błędzie walidacji. Szablony kontrolek służą do ponownego definiowania wyglądu kontrolki.

[!code-xaml[BindValidation#4](~/samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml#4)]

Jak pokazano w poniższym przykładzie, <xref:System.Windows.Controls.ToolTip>, który wyświetla komunikat o błędzie jest tworzony przy użyciu stylu o nazwie `textBoxInError`. Jeśli wartość <xref:System.Windows.Controls.Validation.HasError%2A> jest `true`, wyzwalacz ustawi etykietkę narzędzia bieżącego <xref:System.Windows.Controls.TextBox> do pierwszego błędu walidacji. <xref:System.Windows.Data.Binding.RelativeSource%2A> jest ustawiona na <xref:System.Windows.Data.RelativeSourceMode.Self>, odwołująca się do bieżącego elementu.

[!code-xaml[BindValidation#5](~/samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml#5)]

Aby zapoznać się z kompletnym przykładem, zobacz [Sample Validation rebind](https://github.com/Microsoft/WPF-Samples/tree/master/Data%20Binding/BindValidation).
  
Należy pamiętać, że jeśli nie podasz niestandardowego <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> domyślny szablon błędu zostanie wyświetlony, aby przekazać użytkownikowi informacje zwrotne, gdy wystąpi błąd walidacji. Aby uzyskać więcej informacji, zobacz "Sprawdzanie poprawności danych" w temacie [powiązanie danych](data-binding-overview.md) . Ponadto [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zapewnia wbudowaną regułę walidacji, która przechwytuje wyjątki, które są zgłaszane podczas aktualizacji właściwości źródła powiązania. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Controls.ExceptionValidationRule>.

## <a name="see-also"></a>Zobacz także

- [Powiązanie danych — omówienie](data-binding-overview.md)
- [Tematy z instrukcjami](data-binding-how-to-topics.md)
