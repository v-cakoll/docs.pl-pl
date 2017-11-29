---
title: "Jak implementować powiązaną walidację"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- validation of binding [WPF]
- data binding [WPF], validation of binding
- binding [WPF], validation of
ms.assetid: eb98b33d-9866-49ae-b981-bc5ff20d607a
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ec860cc9cc58febd98d8642c98a50ec296592d02
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-implement-binding-validation"></a>Jak implementować powiązaną walidację
Ten przykład przedstawia sposób użycia <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> i wyzwalacz style wizualne, aby poinformować użytkownika, gdy wprowadzono nieprawidłową wartość oparte na niestandardowej reguły walidacji.  
  
## <a name="example"></a>Przykład  
 Zawartość tekstu <xref:System.Windows.Controls.TextBox> w poniższym przykładzie jest powiązany z `Age` właściwości (typ int) obiektu źródła powiązanie o nazwie `ods`. Powiązanie jest skonfigurowany do użycia reguły sprawdzania poprawności, o nazwie `AgeRangeRule` tak, aby po wprowadzeniu znaków nienumerycznych lub wartość, która jest mniejsza niż 21 lub większa niż 130, czerwony wykrzyknik jest wyświetlany obok pola tekstowego, a podpowiedzi z komunikatem o błędzie gdzie n użytkownik przesuwa wskaźnik myszy nad pole tekstowe.  
  
 [!code-xaml[BindValidation#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml#2)]  
  
 Poniższy przykład przedstawia implementację `AgeRangeRule`, który dziedziczy z <xref:System.Windows.Controls.ValidationRule> i zastępuje <xref:System.Windows.Controls.ValidationRule.Validate%2A> metody. Metoda Int32.Parse() jest wywoływana na wartość, aby upewnić się, że nie zawiera nieprawidłowych znaków. <xref:System.Windows.Controls.ValidationRule.Validate%2A> Metoda zwraca <xref:System.Windows.Controls.ValidationResult> wskazujące, że jeśli wartość jest prawidłowa na podstawie tego, czy zostanie przechwycony wyjątek podczas analizowania i określa, czy wartość wieku znajduje się poza dolną i górną granicę.  
  
 [!code-csharp[BindValidation#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/AgeRangeRule.cs#3)]  
  
 W poniższym przykładzie przedstawiono niestandardowego <xref:System.Windows.Controls.ControlTemplate> `validationTemplate` tworzącą czerwony wykrzyknik w celu powiadomienia użytkownika Błąd sprawdzania poprawności. Formant szablony są używane do ponownego zdefiniowania wyglądu formantu.  
  
 [!code-xaml[BindValidation#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml#4)]  
  
 Jak pokazano w poniższym przykładzie <xref:System.Windows.Controls.ToolTip> który zawiera komunikat o błędzie jest tworzony przy użyciu style o nazwie `textBoxInError`. Jeśli wartość <xref:System.Windows.Controls.Validation.HasError%2A> jest `true`, wyzwalacz ustawia podpowiedzi bieżącego <xref:System.Windows.Controls.TextBox> do jego pierwszego błędu sprawdzania poprawności. <xref:System.Windows.Data.Binding.RelativeSource%2A> Ustawiono <xref:System.Windows.Data.RelativeSourceMode.Self>odwołujący się do bieżącego elementu.  
  
 [!code-xaml[BindValidation#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml#5)]  
  
 Aby uzyskać pełny przykład, zobacz [powiązania przykładowych weryfikacji](http://go.microsoft.com/fwlink/?LinkID=159972).  
  
 Należy pamiętać, że jeśli nie podasz niestandardowego <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> domyślny szablon błąd powinien zapewniać wizualne użytkownikowi, gdy występuje błąd weryfikacji. Zobacz "Sprawdzanie poprawności danych" w [omówienie powiązania danych](../../../../docs/framework/wpf/data/data-binding-overview.md) Aby uzyskać więcej informacji. Ponadto [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawiera reguły poprawności wbudowanych przechwytuje wyjątków, które są generowane podczas aktualizacji powiązania właściwości source. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Controls.ExceptionValidationRule>.  
  
## <a name="see-also"></a>Zobacz też  
 [Omówienie powiązania danych](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Tematy porad](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
