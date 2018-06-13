---
title: Jak powiązać z usługą sieci Web
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- binding data [WPF], Web service
- Web service binding [WPF]
- data binding [WPF], Web service
ms.assetid: 77e2d373-69ba-4cbd-b6f5-2c83c38fc98b
ms.openlocfilehash: 75d9d5b6981f868c7a172edd7f23cf923fedd525
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33557293"
---
# <a name="how-to-bind-to-a-web-service"></a>Jak powiązać z usługą sieci Web
W tym przykładzie pokazano, jak można powiązać obiekty zwrócone przez wywołania metody usługi sieci Web.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto [usługi zawartość MSDN i TechNet systemu publikowania (MTPS)](http://go.microsoft.com/fwlink/?LinkId=95677) można pobrać listę języków obsługiwanych przez określony dokument.  
  
 Przed wywołaniem usługi sieci Web, należy utworzyć odwołanie do niej. Aby utworzyć odwołanie sieci Web przy użyciu usługi MTPS [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], wykonaj następujące kroki:  
  
1.  Otwórz projekt w [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)].  
  
2.  Z **projektu** menu, kliknij przycisk **Dodaj odwołanie sieci Web**.  
  
3.  W oknie dialogowym Ustaw **adres URL** do [ http://services.msdn.microsoft.com/contentservices/contentservice.asmx?wsdl ](http://services.msdn.microsoft.com/contentservices/contentservice.asmx?wsdl).  
  
4.  Naciśnij klawisz **Przejdź** , a następnie **Dodaj odwołanie**.  
  
 Następnie należy wywołać metody usługi sieci Web i ustaw <xref:System.Windows.FrameworkElement.DataContext%2A> właściwej opcji kontroli lub okna zwrócony obiekt. **GetContent** metoda usługi MTPS przyjmuje odwołanie do **getContentRequest** obiektu. W związku z tym w poniższym przykładzie najpierw ustawiono obiektu żądania:  
  
 [!code-csharp[BindToWebService#Namespace](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindToWebService/CSharp/Window1.xaml.cs#namespace)]
 [!code-vb[BindToWebService#Namespace](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BindToWebService/VisualBasic/Window1.xaml.vb#namespace)]  
[!code-csharp[BindToWebService#WebServiceCall](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindToWebService/CSharp/Window1.xaml.cs#webservicecall)]
[!code-vb[BindToWebService#WebServiceCall](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BindToWebService/VisualBasic/Window1.xaml.vb#webservicecall)]  
  
 Po <xref:System.Windows.FrameworkElement.DataContext%2A> skonfigurowano, można utworzyć powiązania z właściwości obiektu <xref:System.Windows.FrameworkElement.DataContext%2A> został ustawiony. W tym przykładzie <xref:System.Windows.FrameworkElement.DataContext%2A> ustawiono **getContentResponse** obiektu zwróconego przez **GetContent** metody. W poniższym przykładzie <xref:System.Windows.Controls.ItemsControl> wiąże i wyświetla **ustawień regionalnych** wartości **availableVersionsAndLocales** z **getContentResponse**.  
  
 [!code-xaml[BindToWebService#Binding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindToWebService/CSharp/Window1.xaml#binding)]  
  
 Aby uzyskać informacje dotyczące struktury **getContentResponse**, zobacz [usługi zawartość dokumentacji](http://services.msdn.microsoft.com/ContentServices/ContentService.asmx).  
  
## <a name="see-also"></a>Zobacz też  
 [Powiązanie danych — omówienie](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Wiązanie źródeł — omówienie](../../../../docs/framework/wpf/data/binding-sources-overview.md)  
 [Udostępnianie danych do powiązania w XAML](../../../../docs/framework/wpf/data/how-to-make-data-available-for-binding-in-xaml.md)
