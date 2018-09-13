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
ms.openlocfilehash: 84c5aee8d2bc7d31ebcfee98930d9a0847c527d5
ms.sourcegitcommit: ba5c189bf44d44204a3e8838e59ec378a62d82f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2018
ms.locfileid: "44704803"
---
# <a name="how-to-bind-to-a-web-service"></a><span data-ttu-id="15769-102">Jak powiązać z usługą sieci Web</span><span class="sxs-lookup"><span data-stu-id="15769-102">How to: Bind to a Web Service</span></span>
<span data-ttu-id="15769-103">W tym przykładzie pokazano, jak powiązać obiekty zwrócone przez wywołania metody usługi sieci Web.</span><span class="sxs-lookup"><span data-stu-id="15769-103">This example shows how to bind to objects returned by Web service method calls.</span></span>  
  
## <a name="example"></a><span data-ttu-id="15769-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="15769-104">Example</span></span>  
 <span data-ttu-id="15769-105">W tym przykładzie użyto [usługi zawartości MSDN/TechNet Publishing System (MTPS)](https://go.microsoft.com/fwlink/?LinkId=95677) można pobrać listę języków obsługiwanych przez określony dokument.</span><span class="sxs-lookup"><span data-stu-id="15769-105">This example uses the [MSDN/TechNet Publishing System (MTPS) Content Service](https://go.microsoft.com/fwlink/?LinkId=95677) to retrieve the list of languages supported by a specified document.</span></span>  
  
 <span data-ttu-id="15769-106">Przed wywołaniem usługi sieci Web, należy utworzyć odwołanie do niej.</span><span class="sxs-lookup"><span data-stu-id="15769-106">Before you call a Web service, you need to create a reference to it.</span></span> <span data-ttu-id="15769-107">Aby utworzyć odwołanie sieci Web za pomocą usługi MTPS [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="15769-107">To create a Web reference to the MTPS service using [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], follow the following steps:</span></span>  
  
1.  <span data-ttu-id="15769-108">Otwórz projekt w programie [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)].</span><span class="sxs-lookup"><span data-stu-id="15769-108">Open your project in [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)].</span></span>  
  
2.  <span data-ttu-id="15769-109">Z **projektu** menu, kliknij przycisk **Dodaj odwołanie sieci Web**.</span><span class="sxs-lookup"><span data-stu-id="15769-109">From the **Project** menu, click **Add Web Reference**.</span></span>  
  
3.  <span data-ttu-id="15769-110">W oknie dialogowym Ustaw **adresu URL** do [ http://services.msdn.microsoft.com/contentservices/contentservice.asmx?wsdl ](https://services.msdn.microsoft.com/contentservices/contentservice.asmx?wsdl).</span><span class="sxs-lookup"><span data-stu-id="15769-110">In the dialog box, set the **URL** to [http://services.msdn.microsoft.com/contentservices/contentservice.asmx?wsdl](https://services.msdn.microsoft.com/contentservices/contentservice.asmx?wsdl).</span></span>  
  
4.  <span data-ttu-id="15769-111">Naciśnij klawisz **Przejdź** i następnie **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="15769-111">Press **Go** and then **Add Reference**.</span></span>  
  
 <span data-ttu-id="15769-112">Następnie należy wywołać metody usługi sieci Web i ustaw <xref:System.Windows.FrameworkElement.DataContext%2A> właściwej opcji kontroli lub okna, aby zwracany obiekt.</span><span class="sxs-lookup"><span data-stu-id="15769-112">Next, you call the Web service method and set the <xref:System.Windows.FrameworkElement.DataContext%2A> of the appropriate control or window to the returned object.</span></span> <span data-ttu-id="15769-113">**Getcontent elementu** metoda usługi MTPS przyjmuje odwołanie do **getContentRequest** obiektu.</span><span class="sxs-lookup"><span data-stu-id="15769-113">The **GetContent** method of the MTPS service takes a reference to the **getContentRequest** object.</span></span> <span data-ttu-id="15769-114">W związku z tym w poniższym przykładzie najpierw ustawiono obiektu żądania:</span><span class="sxs-lookup"><span data-stu-id="15769-114">Therefore, the following example first sets up a request object:</span></span>  
  
 [!code-csharp[BindToWebService#Namespace](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindToWebService/CSharp/Window1.xaml.cs#namespace)]
 [!code-vb[BindToWebService#Namespace](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BindToWebService/VisualBasic/Window1.xaml.vb#namespace)]  
[!code-csharp[BindToWebService#WebServiceCall](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindToWebService/CSharp/Window1.xaml.cs#webservicecall)]
[!code-vb[BindToWebService#WebServiceCall](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BindToWebService/VisualBasic/Window1.xaml.vb#webservicecall)]  
  
 <span data-ttu-id="15769-115">Po <xref:System.Windows.FrameworkElement.DataContext%2A> skonfigurowano, można utworzyć powiązania z właściwości obiektu <xref:System.Windows.FrameworkElement.DataContext%2A> została ustawiona.</span><span class="sxs-lookup"><span data-stu-id="15769-115">After the <xref:System.Windows.FrameworkElement.DataContext%2A> has been set, you can create bindings to the properties of the object that the <xref:System.Windows.FrameworkElement.DataContext%2A> has been set to.</span></span> <span data-ttu-id="15769-116">W tym przykładzie <xref:System.Windows.FrameworkElement.DataContext%2A> ustawiono **getContentResponse** obiektu zwróconego przez **getcontent elementu** metody.</span><span class="sxs-lookup"><span data-stu-id="15769-116">In this example, the <xref:System.Windows.FrameworkElement.DataContext%2A> is set to the **getContentResponse** object returned by the **GetContent** method.</span></span> <span data-ttu-id="15769-117">W poniższym przykładzie <xref:System.Windows.Controls.ItemsControl> wiąże się i wyświetla **ustawień regionalnych** wartości **availableVersionsAndLocales** z **getContentResponse**.</span><span class="sxs-lookup"><span data-stu-id="15769-117">In the following example, the <xref:System.Windows.Controls.ItemsControl> binds to and displays the **locale** values of **availableVersionsAndLocales** of **getContentResponse**.</span></span>  
  
 [!code-xaml[BindToWebService#Binding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindToWebService/CSharp/Window1.xaml#binding)]  
  
 <span data-ttu-id="15769-118">Aby uzyskać informacje na temat struktury **getContentResponse**, zobacz [dokumentacji usługi zawartości](https://services.msdn.microsoft.com/ContentServices/ContentService.asmx).</span><span class="sxs-lookup"><span data-stu-id="15769-118">For information about the structure of **getContentResponse**, see [Content Service documentation](https://services.msdn.microsoft.com/ContentServices/ContentService.asmx).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15769-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="15769-119">See Also</span></span>  
 [<span data-ttu-id="15769-120">Powiązanie danych — omówienie</span><span class="sxs-lookup"><span data-stu-id="15769-120">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="15769-121">Wiązanie źródeł — omówienie</span><span class="sxs-lookup"><span data-stu-id="15769-121">Binding Sources Overview</span></span>](../../../../docs/framework/wpf/data/binding-sources-overview.md)  
 [<span data-ttu-id="15769-122">Udostępnianie danych do powiązania w XAML</span><span class="sxs-lookup"><span data-stu-id="15769-122">Make Data Available for Binding in XAML</span></span>](../../../../docs/framework/wpf/data/how-to-make-data-available-for-binding-in-xaml.md)
