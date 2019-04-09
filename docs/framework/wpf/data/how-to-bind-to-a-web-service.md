---
title: 'Instrukcje: Wiązanie z usługą internetową'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- binding data [WPF], Web service
- Web service binding [WPF]
- data binding [WPF], Web service
ms.assetid: 77e2d373-69ba-4cbd-b6f5-2c83c38fc98b
ms.openlocfilehash: 66e91190e68d9610dd95d677edb276e117ec6abb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59098583"
---
# <a name="how-to-bind-to-a-web-service"></a>Instrukcje: Wiązanie z usługą internetową
W tym przykładzie pokazano, jak powiązać obiekty zwrócone przez wywołania metody usługi sieci Web.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto [usługi zawartości MSDN/TechNet Publishing System (MTPS)](https://go.microsoft.com/fwlink/?LinkId=95677) można pobrać listę języków obsługiwanych przez określony dokument.  
  
 Przed wywołaniem usługi sieci Web, należy utworzyć odwołanie do niej. Aby utworzyć odwołanie sieci Web za pomocą usługi MTPS [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], wykonaj następujące kroki:  
  
1.  Otwórz projekt w programie [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)].  
  
2.  Z **projektu** menu, kliknij przycisk **Dodaj odwołanie sieci Web**.  
  
3.  W oknie dialogowym Ustaw **adresu URL** do [ http://services.msdn.microsoft.com/contentservices/contentservice.asmx?wsdl ](https://services.msdn.microsoft.com/contentservices/contentservice.asmx?wsdl).  
  
4.  Naciśnij klawisz **Przejdź** i następnie **Dodaj odwołanie**.  
  
 Następnie należy wywołać metody usługi sieci Web i ustaw <xref:System.Windows.FrameworkElement.DataContext%2A> właściwej opcji kontroli lub okna, aby zwracany obiekt. **Getcontent elementu** metoda usługi MTPS przyjmuje odwołanie do **getContentRequest** obiektu. W związku z tym w poniższym przykładzie najpierw ustawiono obiektu żądania:  
  
 [!code-csharp[BindToWebService#Namespace](~/samples/snippets/csharp/VS_Snippets_Wpf/BindToWebService/CSharp/Window1.xaml.cs#namespace)]
 [!code-vb[BindToWebService#Namespace](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BindToWebService/VisualBasic/Window1.xaml.vb#namespace)]  
[!code-csharp[BindToWebService#WebServiceCall](~/samples/snippets/csharp/VS_Snippets_Wpf/BindToWebService/CSharp/Window1.xaml.cs#webservicecall)]
[!code-vb[BindToWebService#WebServiceCall](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BindToWebService/VisualBasic/Window1.xaml.vb#webservicecall)]  
  
 Po <xref:System.Windows.FrameworkElement.DataContext%2A> skonfigurowano, można utworzyć powiązania z właściwości obiektu <xref:System.Windows.FrameworkElement.DataContext%2A> została ustawiona. W tym przykładzie <xref:System.Windows.FrameworkElement.DataContext%2A> ustawiono **getContentResponse** obiektu zwróconego przez **getcontent elementu** metody. W poniższym przykładzie <xref:System.Windows.Controls.ItemsControl> wiąże się i wyświetla **ustawień regionalnych** wartości **availableVersionsAndLocales** z **getContentResponse**.  
  
 [!code-xaml[BindToWebService#Binding](~/samples/snippets/csharp/VS_Snippets_Wpf/BindToWebService/CSharp/Window1.xaml#binding)]  
  
 Aby uzyskać informacje na temat struktury **getContentResponse**, zobacz [dokumentacji usługi zawartości](https://services.msdn.microsoft.com/ContentServices/ContentService.asmx).  
  
## <a name="see-also"></a>Zobacz także

- [Przegląd Wiązanie danych](data-binding-overview.md)
- [Przegląd Wiązanie źródeł](binding-sources-overview.md)
- [Udostępnianie danych do powiązania w XAML](how-to-make-data-available-for-binding-in-xaml.md)
