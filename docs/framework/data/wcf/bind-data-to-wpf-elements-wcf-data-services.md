---
title: "Porady: wiązanie danych do systemu Windows Presentation Foundation elementów (usługi danych WCF)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding, WCF Data Services
- WCF Data Services, data binding
ms.assetid: d6538ab0-0abe-426a-b9d9-e6f3a5ca2016
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 0f0ff1bed93d534dea3a407f4923e13856d761d1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-bind-data-to-windows-presentation-foundation-elements-wcf-data-services"></a>Porady: wiązanie danych do systemu Windows Presentation Foundation elementów (usługi danych WCF)
Z [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], można powiązać Windows Presentation Foundation (WPF) elementów, takich jak <xref:System.Windows.Controls.ListBox>"lub <xref:System.Windows.Controls.ComboBox> na wystąpienie <xref:System.Data.Services.Client.DataServiceCollection%601>, który obsługuje zdarzenia wygenerowane przez formanty, aby zachować <xref:System.Data.Services.Client.DataServiceContext> zsynchronizowany ze zmianami wprowadzone dane w formantach. Aby uzyskać więcej informacji, zobacz [wiązanie danych do kontrolek](../../../../docs/framework/data/wcf/binding-data-to-controls-wcf-data-services.md).  
  
 Przykład, w tym temacie korzysta z Northwind przykładowych danych wygenerowany automatycznie i usługi klienta danych usługi klas. Ta usługa i klas danych klienta są tworzone po ukończeniu [szybkiego startu usługi danych WCF](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pochodzi ze strony CodeBehind dla strony Extensible Application Markup Language (XAML), który definiuje `SalesOrders` okna na platformie WPF. Po załadowaniu okna <xref:System.Data.Services.Client.DataServiceCollection%601> jest tworzony na podstawie wyniku zapytania, które zwraca klientów filtrowane według kraju. Wszystkie strony tego wyniku stronicowanych zostały załadowane oraz powiązane zamówienia i są powiązane z <xref:System.Windows.FrameworkElement.DataContext%2A> właściwość <xref:System.Windows.Controls.StackPanel> czyli formant układu głównego okna WPF. Aby uzyskać więcej informacji, zobacz [ładowanie odłożone zawartości](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md).  
  
 [!code-csharp[Astoria Northwind Client#BindPagedData](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/customerorderswpf3.xaml.cs#bindpageddata)]
 [!code-vb[Astoria Northwind Client#BindPagedData](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerorderswpf3.xaml.vb#bindpageddata)]  
  
## <a name="example"></a>Przykład  
 Definiuje następujące XAML `SalesOrders` okna na platformie WPF w poprzednim przykładzie.  
  
 [!code-xaml[Astoria Northwind Client#BindPagedDataXaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerorderswpf3.xaml#bindpageddataxaml)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pochodzi ze strony CodeBehind dla strony Extensible Application Markup Language (XAML), który definiuje `SalesOrders` okna na platformie WPF. Po załadowaniu okna <xref:System.Data.Services.Client.DataServiceCollection%601> jest tworzony na podstawie wyniku zapytania, które zwraca klientów z powiązane obiekty filtrowane według kraju. Ten wynik jest powiązany z <xref:System.Windows.FrameworkElement.DataContext%2A> właściwość <xref:System.Windows.Controls.StackPanel> czyli formant układu głównego okna WPF.  
  
 [!code-csharp[Astoria Northwind Client#WpfDataBinding](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/customerorderswpf.xaml.cs#wpfdatabinding)]
 [!code-vb[Astoria Northwind Client#WpfDataBinding](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerorderswpf.xaml.vb#wpfdatabinding)]  
  
## <a name="example"></a>Przykład  
 Definiuje następujące XAML `SalesOrders` okna na platformie WPF w poprzednim przykładzie.  
  
 [!code-xaml[Astoria Northwind Client#WpfDataBindingXaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerorderswpf.xaml#wpfdatabindingxaml)]
