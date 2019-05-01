---
title: 'Instrukcje: Implementowanie weryfikacji wiązania'
ms.date: 03/30/2017
helpviewer_keywords:
- validation of binding [WPF]
- data binding [WPF], validation of binding
- binding [WPF], validation of
ms.assetid: eb98b33d-9866-49ae-b981-bc5ff20d607a
ms.openlocfilehash: 3950df8b6f4b48a035c6ebf37d8d65c18cb82e1e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62010335"
---
# <a name="how-to-implement-binding-validation"></a>Instrukcje: Implementowanie weryfikacji wiązania
W tym przykładzie pokazano, jak używać <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> i wyzwalacz stylu, aby przekazać wizualną opinię, aby poinformować użytkownika, gdy wprowadzono nieprawidłową wartość oparte na niestandardowej reguły walidacji.  
  
## <a name="example"></a>Przykład  
 Zawartość tekstu <xref:System.Windows.Controls.TextBox> w poniższym przykładzie jest powiązany z `Age` własności (typu int) obiektu źródłowego powiązania o nazwie `ods`. Powiązanie jest ustawiane, aby zastosować regułę sprawdzania poprawności, o nazwie `AgeRangeRule` tak, aby po użytkownik wprowadzi znaki nienumeryczne lub wartość, która jest mniejsza niż 21 lub większa niż 130, czerwony wykrzyknik pojawia się obok pola tekstowego i podpowiedzi z komunikatem o błędzie gdzie n użytkownik przesunie wskaźnik myszy nad polem tekstowym.  
  
 [!code-xaml[BindValidation#2](~/samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml#2)]  
  
 W poniższym przykładzie pokazano implementację `AgeRangeRule`, który dziedziczy z <xref:System.Windows.Controls.ValidationRule> i zastępuje <xref:System.Windows.Controls.ValidationRule.Validate%2A> metody. Metoda Int32.Parse() jest wywoływana na wartości, aby upewnić się, że nie zawiera nieprawidłowych znaków. <xref:System.Windows.Controls.ValidationRule.Validate%2A> Metoda zwraca <xref:System.Windows.Controls.ValidationResult> oznacza to, jeśli wartość jest prawidłowa na podstawie tego, czy wyjątek zostaje przechwycony podczas analizowania i tego, czy wartość wieku znajduje się poza dolną i górną granicę.  
  
 [!code-csharp[BindValidation#3](~/samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/AgeRangeRule.cs#3)]  
  
 Poniższy przykład pokazuje niestandardowy <xref:System.Windows.Controls.ControlTemplate> `validationTemplate` tworząca czerwony wykrzyknik, aby powiadomić użytkownika o błąd sprawdzania poprawności. Szablony kontrolek są używane do przedefiniowania wyglądu formantu.  
  
 [!code-xaml[BindValidation#4](~/samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml#4)]  
  
 Jak pokazano w poniższym przykładzie <xref:System.Windows.Controls.ToolTip> pokazujący, że komunikat o błędzie jest tworzony przy użyciu stylu o nazwie `textBoxInError`. Jeśli wartość <xref:System.Windows.Controls.Validation.HasError%2A> jest `true`, wyzwalacz ustawia podpowiedzi bieżącego <xref:System.Windows.Controls.TextBox> do jej pierwszego błędu walidacji. <xref:System.Windows.Data.Binding.RelativeSource%2A> Ustawiono <xref:System.Windows.Data.RelativeSourceMode.Self>odwołujący się do bieżącego elementu.  
  
 [!code-xaml[BindValidation#5](~/samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml#5)]  
  
 Aby uzyskać kompletny przykład, zobacz [powiązania przykładowych weryfikacji](https://go.microsoft.com/fwlink/?LinkID=159972).  
  
 Należy pamiętać, że jeśli nie podasz niestandardowe <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> domyślnego szablonu błąd wydaje się przekazać wizualną opinię do użytkownika, gdy występuje błąd weryfikacji. Zobacz "Sprawdzanie poprawności danych" w [Przegląd wiązanie danych](data-binding-overview.md) Aby uzyskać więcej informacji. Ponadto [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] udostępnia wbudowane walidację, który przechwytuje wyjątki, które są generowane podczas aktualizacji właściwości źródła powiązania. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Controls.ExceptionValidationRule>.  
  
## <a name="see-also"></a>Zobacz także

- [Powiązanie danych — omówienie](data-binding-overview.md)
- [Tematy z instrukcjami](data-binding-how-to-topics.md)
