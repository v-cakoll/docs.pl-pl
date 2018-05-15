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
---
# <a name="how-to-bind-to-a-web-service"></a><span data-ttu-id="e71fb-102">Jak powiązać z usługą sieci Web</span><span class="sxs-lookup"><span data-stu-id="e71fb-102">How to: Bind to a Web Service</span></span>
<span data-ttu-id="e71fb-103">W tym przykładzie pokazano, jak można powiązać obiekty zwrócone przez wywołania metody usługi sieci Web.</span><span class="sxs-lookup"><span data-stu-id="e71fb-103">This example shows how to bind to objects returned by Web service method calls.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e71fb-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="e71fb-104">Example</span></span>  
 <span data-ttu-id="e71fb-105">W tym przykładzie użyto [usługi zawartość MSDN i TechNet systemu publikowania (MTPS)](http://go.microsoft.com/fwlink/?LinkId=95677) można pobrać listę języków obsługiwanych przez określony dokument.</span><span class="sxs-lookup"><span data-stu-id="e71fb-105">This example uses the [MSDN/TechNet Publishing System (MTPS) Content Service](http://go.microsoft.com/fwlink/?LinkId=95677) to retrieve the list of languages supported by a specified document.</span></span>  
  
 <span data-ttu-id="e71fb-106">Przed wywołaniem usługi sieci Web, należy utworzyć odwołanie do niej.</span><span class="sxs-lookup"><span data-stu-id="e71fb-106">Before you call a Web service, you need to create a reference to it.</span></span> <span data-ttu-id="e71fb-107">Aby utworzyć odwołanie sieci Web przy użyciu usługi MTPS [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="e71fb-107">To create a Web reference to the MTPS service using [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], follow the following steps:</span></span>  
  
1.  <span data-ttu-id="e71fb-108">Otwórz projekt w [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e71fb-108">Open your project in [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)].</span></span>  
  
2.  <span data-ttu-id="e71fb-109">Z **projektu** menu, kliknij przycisk **Dodaj odwołanie sieci Web**.</span><span class="sxs-lookup"><span data-stu-id="e71fb-109">From the **Project** menu, click **Add Web Reference**.</span></span>  
  
3.  <span data-ttu-id="e71fb-110">W oknie dialogowym Ustaw **adres URL** do [ http://services.msdn.microsoft.com/contentservices/contentservice.asmx?wsdl ](http://services.msdn.microsoft.com/contentservices/contentservice.asmx?wsdl).</span><span class="sxs-lookup"><span data-stu-id="e71fb-110">In the dialog box, set the **URL** to [http://services.msdn.microsoft.com/contentservices/contentservice.asmx?wsdl](http://services.msdn.microsoft.com/contentservices/contentservice.asmx?wsdl).</span></span>  
  
4.  <span data-ttu-id="e71fb-111">Naciśnij klawisz **Przejdź** , a następnie **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="e71fb-111">Press **Go** and then **Add Reference**.</span></span>  
  
 <span data-ttu-id="e71fb-112">Następnie należy wywołać metody usługi sieci Web i ustaw <xref:System.Windows.FrameworkElement.DataContext%2A> właściwej opcji kontroli lub okna zwrócony obiekt.</span><span class="sxs-lookup"><span data-stu-id="e71fb-112">Next, you call the Web service method and set the <xref:System.Windows.FrameworkElement.DataContext%2A> of the appropriate control or window to the returned object.</span></span> <span data-ttu-id="e71fb-113">**GetContent** metoda usługi MTPS przyjmuje odwołanie do **getContentRequest** obiektu.</span><span class="sxs-lookup"><span data-stu-id="e71fb-113">The **GetContent** method of the MTPS service takes a reference to the **getContentRequest** object.</span></span> <span data-ttu-id="e71fb-114">W związku z tym w poniższym przykładzie najpierw ustawiono obiektu żądania:</span><span class="sxs-lookup"><span data-stu-id="e71fb-114">Therefore, the following example first sets up a request object:</span></span>  
  
 [!code-csharp[BindToWebService#Namespace](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindToWebService/CSharp/Window1.xaml.cs#namespace)]
 [!code-vb[BindToWebService#Namespace](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BindToWebService/VisualBasic/Window1.xaml.vb#namespace)]  
[!code-csharp[BindToWebService#WebServiceCall](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindToWebService/CSharp/Window1.xaml.cs#webservicecall)]
[!code-vb[BindToWebService#WebServiceCall](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BindToWebService/VisualBasic/Window1.xaml.vb#webservicecall)]  
  
 <span data-ttu-id="e71fb-115">Po <xref:System.Windows.FrameworkElement.DataContext%2A> skonfigurowano, można utworzyć powiązania z właściwości obiektu <xref:System.Windows.FrameworkElement.DataContext%2A> został ustawiony.</span><span class="sxs-lookup"><span data-stu-id="e71fb-115">After the <xref:System.Windows.FrameworkElement.DataContext%2A> has been set, you can create bindings to the properties of the object that the <xref:System.Windows.FrameworkElement.DataContext%2A> has been set to.</span></span> <span data-ttu-id="e71fb-116">W tym przykładzie <xref:System.Windows.FrameworkElement.DataContext%2A> ustawiono **getContentResponse** obiektu zwróconego przez **GetContent** metody.</span><span class="sxs-lookup"><span data-stu-id="e71fb-116">In this example, the <xref:System.Windows.FrameworkElement.DataContext%2A> is set to the **getContentResponse** object returned by the **GetContent** method.</span></span> <span data-ttu-id="e71fb-117">W poniższym przykładzie <xref:System.Windows.Controls.ItemsControl> wiąże i wyświetla **ustawień regionalnych** wartości **availableVersionsAndLocales** z **getContentResponse**.</span><span class="sxs-lookup"><span data-stu-id="e71fb-117">In the following example, the <xref:System.Windows.Controls.ItemsControl> binds to and displays the **locale** values of **availableVersionsAndLocales** of **getContentResponse**.</span></span>  
  
 [!code-xaml[BindToWebService#Binding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindToWebService/CSharp/Window1.xaml#binding)]  
  
 <span data-ttu-id="e71fb-118">Aby uzyskać informacje dotyczące struktury **getContentResponse**, zobacz [usługi zawartość dokumentacji](http://services.msdn.microsoft.com/ContentServices/ContentService.asmx).</span><span class="sxs-lookup"><span data-stu-id="e71fb-118">For information about the structure of **getContentResponse**, see [Content Service documentation](http://services.msdn.microsoft.com/ContentServices/ContentService.asmx).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e71fb-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e71fb-119">See Also</span></span>  
 [<span data-ttu-id="e71fb-120">Powiązanie danych — omówienie</span><span class="sxs-lookup"><span data-stu-id="e71fb-120">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="e71fb-121">Wiązanie źródeł — omówienie</span><span class="sxs-lookup"><span data-stu-id="e71fb-121">Binding Sources Overview</span></span>](../../../../docs/framework/wpf/data/binding-sources-overview.md)  
 [<span data-ttu-id="e71fb-122">Udostępnianie danych do powiązania w XAML</span><span class="sxs-lookup"><span data-stu-id="e71fb-122">Make Data Available for Binding in XAML</span></span>](../../../../docs/framework/wpf/data/how-to-make-data-available-for-binding-in-xaml.md)
