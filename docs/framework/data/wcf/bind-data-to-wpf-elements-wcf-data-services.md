---
title: 'Instrukcje: Powiąż dane z Windows Presentation Foundation elementów (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding, WCF Data Services
- WCF Data Services, data binding
ms.assetid: d6538ab0-0abe-426a-b9d9-e6f3a5ca2016
ms.openlocfilehash: cecfa42035d4c09eade708417c338ef04ab09ad9
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/31/2019
ms.locfileid: "66423828"
---
# <a name="how-to-bind-data-to-windows-presentation-foundation-elements-wcf-data-services"></a>Instrukcje: Powiąż dane z Windows Presentation Foundation elementów (WCF Data Services)
Za pomocą [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], można powiązać elementy Windows Presentation Foundation (WPF), takie jak <xref:System.Windows.Controls.ListBox> lub <xref:System.Windows.Controls.ComboBox> do wystąpienia <xref:System.Data.Services.Client.DataServiceCollection%601>, który obsługuje zdarzenia wygenerowane przez formanty, aby zachować <xref:System.Data.Services.Client.DataServiceContext> synchronizowane ze zmianami wprowadzonymi wprowadzone do danych w kontrolkach. Aby uzyskać więcej informacji, zobacz [powiązanie danych z kontrolkami](../../../../docs/framework/data/wcf/binding-data-to-controls-wcf-data-services.md).  
  
 W przykładzie w tym temacie użyto Northwind przykładowe dane usługi i automatycznie wygenerowany klas usługi danych klienta. Ta usługa i klas danych klienta, są tworzone po ukończeniu [Szybki Start usług danych WCF](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pochodzi z osobna strona kodu strony Extensible Application Markup Language (XAML), który definiuje `SalesOrders` okna w WPF. Po załadowaniu okna <xref:System.Data.Services.Client.DataServiceCollection%601> powstaje w oparciu o wyniku zapytania, które zwraca klientów, przefiltrowane według kraju/regionu. Wszystkie strony tego wyniku stronicowane są ładowane, wraz z powiązane zamówienia i są powiązane z <xref:System.Windows.FrameworkElement.DataContext%2A> właściwość <xref:System.Windows.Controls.StackPanel> oznacza to formant układu głównego okna WPF. Aby uzyskać więcej informacji, zobacz [ładowanie zawartości odroczone](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md).  
  
 [!code-csharp[Astoria Northwind Client#BindPagedData](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorderswpf3.xaml.cs#bindpageddata)]
 [!code-vb[Astoria Northwind Client#BindPagedData](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderswpf3.xaml.vb#bindpageddata)]  
  
## <a name="example"></a>Przykład  
 Definiuje następujące XAML `SalesOrders` okna w WPF w poprzednim przykładzie.  
  
 [!code-xaml[Astoria Northwind Client#BindPagedDataXaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderswpf3.xaml#bindpageddataxaml)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pochodzi z osobna strona kodu strony Extensible Application Markup Language (XAML), który definiuje `SalesOrders` okna w WPF. Po załadowaniu okna <xref:System.Data.Services.Client.DataServiceCollection%601> powstaje w oparciu o wyniku zapytania, które zwraca klienci z powiązanymi obiektami, przefiltrowane według kraju/regionu. Ten wynik jest powiązany z <xref:System.Windows.FrameworkElement.DataContext%2A> właściwość <xref:System.Windows.Controls.StackPanel> oznacza to formant układu głównego okna WPF.  
  
 [!code-csharp[Astoria Northwind Client#WpfDataBinding](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorderswpf.xaml.cs#wpfdatabinding)]
 [!code-vb[Astoria Northwind Client#WpfDataBinding](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderswpf.xaml.vb#wpfdatabinding)]  
  
## <a name="example"></a>Przykład  
 Definiuje następujące XAML `SalesOrders` okna w WPF w poprzednim przykładzie.  
  
 [!code-xaml[Astoria Northwind Client#WpfDataBindingXaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderswpf.xaml#wpfdatabindingxaml)]
