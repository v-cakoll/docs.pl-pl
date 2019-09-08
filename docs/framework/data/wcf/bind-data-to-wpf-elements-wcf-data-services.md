---
title: 'Instrukcje: Powiąż dane z elementami Windows Presentation Foundation (Usługi danych programu WCF)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding, WCF Data Services
- WCF Data Services, data binding
ms.assetid: d6538ab0-0abe-426a-b9d9-e6f3a5ca2016
ms.openlocfilehash: 44f3361aa56d9f15e62852000accd0b4d4d8eb43
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70791130"
---
# <a name="how-to-bind-data-to-windows-presentation-foundation-elements-wcf-data-services"></a>Instrukcje: Powiąż dane z elementami Windows Presentation Foundation (Usługi danych programu WCF)
Za [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]pomocą, można powiązać elementy Windows Presentation Foundation (WPF) <xref:System.Data.Services.Client.DataServiceCollection%601>, takie <xref:System.Windows.Controls.ListBox> jak lub <xref:System.Windows.Controls.ComboBox> do wystąpienia, <xref:System.Data.Services.Client.DataServiceContext> które obsługuje zdarzenia wywoływane przez kontrolki, aby zachować synchronizację ze zmianami wprowadzone do danych w kontrolkach. Aby uzyskać więcej informacji, zobacz [Powiązywanie danych z kontrolkami](binding-data-to-controls-wcf-data-services.md).  
  
 W przykładzie w tym temacie jest stosowana usługa danych przykładowych Northwind i klasy usługi danych klientów. Ta usługa i klasy danych klienta są tworzone po zakończeniu [usługi danych programu WCF szybkiego startu](quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pochodzi ze strony `SalesOrders` powiązanej z kodem dla strony Extensible Application Markup Language (XAML), która definiuje okno w WPF. Po załadowaniu <xref:System.Data.Services.Client.DataServiceCollection%601> okna jest tworzone na podstawie wyniku zapytania, które zwraca klientów, filtrowane według kraju/regionu. Wszystkie strony tego wyniku stronicowanego są wczytywane wraz z powiązanymi zamówieniami i są powiązane z <xref:System.Windows.FrameworkElement.DataContext%2A> właściwością <xref:System.Windows.Controls.StackPanel> , która jest głównym formantem układu dla okna WPF. Aby uzyskać więcej informacji, zobacz [ładowanie odroczonej zawartości](loading-deferred-content-wcf-data-services.md).  
  
 [!code-csharp[Astoria Northwind Client#BindPagedData](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorderswpf3.xaml.cs#bindpageddata)]
 [!code-vb[Astoria Northwind Client#BindPagedData](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderswpf3.xaml.vb#bindpageddata)]  
  
## <a name="example"></a>Przykład  
 Poniższy kod XAML definiuje `SalesOrders` okno w WPF dla poprzedniego przykładu.  
  
 [!code-xaml[Astoria Northwind Client#BindPagedDataXaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderswpf3.xaml#bindpageddataxaml)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pochodzi ze strony `SalesOrders` powiązanej z kodem dla strony Extensible Application Markup Language (XAML), która definiuje okno w WPF. Po załadowaniu <xref:System.Data.Services.Client.DataServiceCollection%601> okna jest tworzone na podstawie wyniku zapytania, które zwraca klientów z powiązanymi obiektami, filtrowane według kraju/regionu. Ten wynik jest powiązany z <xref:System.Windows.FrameworkElement.DataContext%2A> właściwością <xref:System.Windows.Controls.StackPanel> będącą głównym formantem układu okna WPF.  
  
 [!code-csharp[Astoria Northwind Client#WpfDataBinding](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorderswpf.xaml.cs#wpfdatabinding)]
 [!code-vb[Astoria Northwind Client#WpfDataBinding](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderswpf.xaml.vb#wpfdatabinding)]  
  
## <a name="example"></a>Przykład  
 Poniższy kod XAML definiuje `SalesOrders` okno w WPF dla poprzedniego przykładu.  
  
 [!code-xaml[Astoria Northwind Client#WpfDataBindingXaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderswpf.xaml#wpfdatabindingxaml)]
