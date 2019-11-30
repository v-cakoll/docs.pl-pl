---
title: 'Instrukcje: powiązywanie danych z Windows Presentation Foundation elementami (Usługi danych programu WCF)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding, WCF Data Services
- WCF Data Services, data binding
ms.assetid: d6538ab0-0abe-426a-b9d9-e6f3a5ca2016
ms.openlocfilehash: b623dc10bfe1b723c62b2861b4142a138904e64a
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/28/2019
ms.locfileid: "74569340"
---
# <a name="how-to-bind-data-to-windows-presentation-foundation-elements-wcf-data-services"></a>Instrukcje: powiązywanie danych z Windows Presentation Foundation elementami (Usługi danych programu WCF)
Za pomocą Usługi danych programu WCF można powiązać elementy Windows Presentation Foundation (WPF), takie jak <xref:System.Windows.Controls.ListBox> lub <xref:System.Windows.Controls.ComboBox>, z wystąpieniem <xref:System.Data.Services.Client.DataServiceCollection%601>, które obsługuje zdarzenia wywoływane przez kontrolki, aby zachować <xref:System.Data.Services.Client.DataServiceContext> zsynchronizowane ze zmianami wprowadzonymi w danych w kontrolkach. Aby uzyskać więcej informacji, zobacz [Powiązywanie danych z kontrolkami](binding-data-to-controls-wcf-data-services.md).  
  
 W przykładzie w tym temacie jest stosowana usługa danych przykładowych Northwind i klasy usługi danych klientów. Ta usługa i klasy danych klienta są tworzone po zakończeniu [usługi danych programu WCF szybkiego startu](quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pochodzi ze strony powiązanej z kodem dla strony Extensible Application Markup Language (XAML), która definiuje okno `SalesOrders` w WPF. Po załadowaniu okna <xref:System.Data.Services.Client.DataServiceCollection%601> jest tworzony na podstawie wyniku zapytania, które zwraca klientów, filtrowane według kraju/regionu. Wszystkie strony tego wyniku stronicowanego są ładowane wraz z powiązanymi zamówieniami i są powiązane z właściwością <xref:System.Windows.FrameworkElement.DataContext%2A> <xref:System.Windows.Controls.StackPanel>, który jest głównym formantem układu dla okna WPF. Aby uzyskać więcej informacji, zobacz [ładowanie odroczonej zawartości](loading-deferred-content-wcf-data-services.md).  
  
 [!code-csharp[Astoria Northwind Client#BindPagedData](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorderswpf3.xaml.cs#bindpageddata)]
 [!code-vb[Astoria Northwind Client#BindPagedData](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderswpf3.xaml.vb#bindpageddata)]  
  
## <a name="example"></a>Przykład  
 Poniższy kod XAML definiuje okno `SalesOrders` w WPF dla poprzedniego przykładu.  
  
 [!code-xaml[Astoria Northwind Client#BindPagedDataXaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderswpf3.xaml#bindpageddataxaml)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pochodzi ze strony powiązanej z kodem dla strony Extensible Application Markup Language (XAML), która definiuje okno `SalesOrders` w WPF. Po załadowaniu okna <xref:System.Data.Services.Client.DataServiceCollection%601> jest tworzony na podstawie wyniku zapytania, które zwraca klientów z powiązanymi obiektami, filtrowane według kraju/regionu. Ten wynik jest powiązany z właściwością <xref:System.Windows.FrameworkElement.DataContext%2A> <xref:System.Windows.Controls.StackPanel>, która jest głównym formantem układu dla okna WPF.  
  
 [!code-csharp[Astoria Northwind Client#WpfDataBinding](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorderswpf.xaml.cs#wpfdatabinding)]
 [!code-vb[Astoria Northwind Client#WpfDataBinding](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderswpf.xaml.vb#wpfdatabinding)]  
  
## <a name="example"></a>Przykład  
 Poniższy kod XAML definiuje okno `SalesOrders` w WPF dla poprzedniego przykładu.  
  
 [!code-xaml[Astoria Northwind Client#WpfDataBindingXaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderswpf.xaml#wpfdatabindingxaml)]
