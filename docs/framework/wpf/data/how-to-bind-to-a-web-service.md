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
ms.openlocfilehash: d752f4815de16daa466302881116e80aceec6edf
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040908"
---
# <a name="how-to-bind-to-a-web-service"></a>Jak powiązać z usługą sieci Web
Ten przykład pokazuje, jak powiązać z obiektami zwracanymi przez wywołania metody usługi sieci Web.  
  
## <a name="example"></a>Przykład  
 Ten przykład używa [usługi zawartości MSDN/TechNet Publishing System (MTPS)](https://go.microsoft.com/fwlink/?LinkId=95677) w celu pobrania listy języków obsługiwanych przez określony dokument.  
  
 Przed wywołaniem usługi sieci Web należy utworzyć odwołanie do niej. Aby utworzyć odwołanie sieci Web do usługi MTPS przy użyciu programu Visual Studio, wykonaj następujące czynności:  
  
1. Otwórz projekt w programie Visual Studio.  
  
2. W menu **projekt** kliknij polecenie **Dodaj odwołanie sieci Web**.  
  
3. W oknie dialogowym Ustaw **adres URL** na [http://services.msdn.microsoft.com/contentservices/contentservice.asmx?wsdl](https://services.msdn.microsoft.com/contentservices/contentservice.asmx?wsdl).  
  
4. Naciśnij przycisk **Przejdź** , a następnie **Dodaj odwołanie**.  
  
 Następnie należy wywołać metodę usługi sieci Web i ustawić <xref:System.Windows.FrameworkElement.DataContext%2A> odpowiedniej kontrolki lub okna do zwracanego obiektu. Metoda `GetContent` usługi MTPS przyjmuje odwołanie do obiektu `getContentRequest`. W związku z tym Poniższy przykład najpierw konfiguruje obiekt żądania:  
  
 [!code-csharp[BindToWebService#Namespace](~/samples/snippets/csharp/VS_Snippets_Wpf/BindToWebService/CSharp/Window1.xaml.cs#namespace)]
 [!code-vb[BindToWebService#Namespace](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BindToWebService/VisualBasic/Window1.xaml.vb#namespace)]  
[!code-csharp[BindToWebService#WebServiceCall](~/samples/snippets/csharp/VS_Snippets_Wpf/BindToWebService/CSharp/Window1.xaml.cs#webservicecall)]
[!code-vb[BindToWebService#WebServiceCall](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BindToWebService/VisualBasic/Window1.xaml.vb#webservicecall)]  
  
 Po ustawieniu <xref:System.Windows.FrameworkElement.DataContext%2A> można utworzyć powiązania z właściwościami obiektu, do którego ustawiono <xref:System.Windows.FrameworkElement.DataContext%2A>. W tym przykładzie <xref:System.Windows.FrameworkElement.DataContext%2A> jest ustawiony na obiekt `getContentResponse` zwracany przez metodę `GetContent`. W poniższym przykładzie <xref:System.Windows.Controls.ItemsControl> tworzy powiązanie z i wyświetla `locale` wartości `availableVersionsAndLocales` `getContentResponse`.  
  
 [!code-xaml[BindToWebService#Binding](~/samples/snippets/csharp/VS_Snippets_Wpf/BindToWebService/CSharp/Window1.xaml#binding)]  
  
 Aby uzyskać informacje na temat struktury `getContentResponse`, zobacz [dokumentację usługi zawartości](https://services.msdn.microsoft.com/ContentServices/ContentService.asmx).  
  
## <a name="see-also"></a>Zobacz także

- [Powiązanie danych — omówienie](data-binding-overview.md)
- [Wiązanie źródeł — omówienie](binding-sources-overview.md)
- [Udostępnianie danych do powiązania w XAML](how-to-make-data-available-for-binding-in-xaml.md)
