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
ms.openlocfilehash: 3a3f6edc974448ddab9fe30e97bdc1130d3b97dc
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2020
ms.locfileid: "77449975"
---
# <a name="how-to-bind-to-a-web-service"></a><span data-ttu-id="8efed-102">Jak powiązać z usługą sieci Web</span><span class="sxs-lookup"><span data-stu-id="8efed-102">How to: Bind to a Web Service</span></span>
<span data-ttu-id="8efed-103">Ten przykład pokazuje, jak powiązać z obiektami zwracanymi przez wywołania metody usługi sieci Web.</span><span class="sxs-lookup"><span data-stu-id="8efed-103">This example shows how to bind to objects returned by Web service method calls.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8efed-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="8efed-104">Example</span></span>  
 <span data-ttu-id="8efed-105">Ten przykład używa usługi zawartości MSDN/TechNet Publishing System (MTPS) w celu pobrania listy języków obsługiwanych przez określony dokument.</span><span class="sxs-lookup"><span data-stu-id="8efed-105">This example uses the MSDN/TechNet Publishing System (MTPS) Content Service to retrieve the list of languages supported by a specified document.</span></span>  
  
 <span data-ttu-id="8efed-106">Przed wywołaniem usługi sieci Web należy utworzyć odwołanie do niej.</span><span class="sxs-lookup"><span data-stu-id="8efed-106">Before you call a Web service, you need to create a reference to it.</span></span> <span data-ttu-id="8efed-107">Aby utworzyć odwołanie sieci Web do usługi MTPS przy użyciu programu Visual Studio, wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="8efed-107">To create a Web reference to the MTPS service using Visual Studio, follow the following steps:</span></span>  
  
1. <span data-ttu-id="8efed-108">Otwórz projekt w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8efed-108">Open your project in Visual Studio.</span></span>  
  
2. <span data-ttu-id="8efed-109">W menu **projekt** kliknij polecenie **Dodaj odwołanie sieci Web**.</span><span class="sxs-lookup"><span data-stu-id="8efed-109">From the **Project** menu, click **Add Web Reference**.</span></span>  
  
3. <span data-ttu-id="8efed-110">W oknie dialogowym Ustaw **adres URL** na [http://services.msdn.microsoft.com/contentservices/contentservice.asmx?wsdl](https://services.msdn.microsoft.com/contentservices/contentservice.asmx?wsdl).</span><span class="sxs-lookup"><span data-stu-id="8efed-110">In the dialog box, set the **URL** to [http://services.msdn.microsoft.com/contentservices/contentservice.asmx?wsdl](https://services.msdn.microsoft.com/contentservices/contentservice.asmx?wsdl).</span></span>  
  
4. <span data-ttu-id="8efed-111">Naciśnij przycisk **Przejdź** , a następnie **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="8efed-111">Press **Go** and then **Add Reference**.</span></span>  
  
 <span data-ttu-id="8efed-112">Następnie należy wywołać metodę usługi sieci Web i ustawić <xref:System.Windows.FrameworkElement.DataContext%2A> odpowiedniej kontrolki lub okna do zwracanego obiektu.</span><span class="sxs-lookup"><span data-stu-id="8efed-112">Next, you call the Web service method and set the <xref:System.Windows.FrameworkElement.DataContext%2A> of the appropriate control or window to the returned object.</span></span> <span data-ttu-id="8efed-113">Metoda `GetContent` usługi MTPS przyjmuje odwołanie do obiektu `getContentRequest`.</span><span class="sxs-lookup"><span data-stu-id="8efed-113">The `GetContent` method of the MTPS service takes a reference to the `getContentRequest` object.</span></span> <span data-ttu-id="8efed-114">W związku z tym Poniższy przykład najpierw konfiguruje obiekt żądania:</span><span class="sxs-lookup"><span data-stu-id="8efed-114">Therefore, the following example first sets up a request object:</span></span>  
  
 [!code-csharp[BindToWebService#Namespace](~/samples/snippets/csharp/VS_Snippets_Wpf/BindToWebService/CSharp/Window1.xaml.cs#namespace)]
 [!code-vb[BindToWebService#Namespace](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BindToWebService/VisualBasic/Window1.xaml.vb#namespace)]  
[!code-csharp[BindToWebService#WebServiceCall](~/samples/snippets/csharp/VS_Snippets_Wpf/BindToWebService/CSharp/Window1.xaml.cs#webservicecall)]
[!code-vb[BindToWebService#WebServiceCall](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BindToWebService/VisualBasic/Window1.xaml.vb#webservicecall)]  
  
 <span data-ttu-id="8efed-115">Po ustawieniu <xref:System.Windows.FrameworkElement.DataContext%2A> można utworzyć powiązania z właściwościami obiektu, do którego ustawiono <xref:System.Windows.FrameworkElement.DataContext%2A>.</span><span class="sxs-lookup"><span data-stu-id="8efed-115">After the <xref:System.Windows.FrameworkElement.DataContext%2A> has been set, you can create bindings to the properties of the object that the <xref:System.Windows.FrameworkElement.DataContext%2A> has been set to.</span></span> <span data-ttu-id="8efed-116">W tym przykładzie <xref:System.Windows.FrameworkElement.DataContext%2A> jest ustawiony na obiekt `getContentResponse` zwracany przez metodę `GetContent`.</span><span class="sxs-lookup"><span data-stu-id="8efed-116">In this example, the <xref:System.Windows.FrameworkElement.DataContext%2A> is set to the `getContentResponse` object returned by the `GetContent` method.</span></span> <span data-ttu-id="8efed-117">W poniższym przykładzie <xref:System.Windows.Controls.ItemsControl> tworzy powiązanie z i wyświetla `locale` wartości `availableVersionsAndLocales` `getContentResponse`.</span><span class="sxs-lookup"><span data-stu-id="8efed-117">In the following example, the <xref:System.Windows.Controls.ItemsControl> binds to and displays the `locale` values of `availableVersionsAndLocales` of `getContentResponse`.</span></span>  
  
 [!code-xaml[BindToWebService#Binding](~/samples/snippets/csharp/VS_Snippets_Wpf/BindToWebService/CSharp/Window1.xaml#binding)]  
  
 <span data-ttu-id="8efed-118">Aby uzyskać informacje na temat struktury `getContentResponse`, zobacz [dokumentację usługi zawartości](https://services.msdn.microsoft.com/ContentServices/ContentService.asmx).</span><span class="sxs-lookup"><span data-stu-id="8efed-118">For information about the structure of `getContentResponse`, see [Content Service documentation](https://services.msdn.microsoft.com/ContentServices/ContentService.asmx).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8efed-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8efed-119">See also</span></span>

- [<span data-ttu-id="8efed-120">Powiązanie danych — omówienie</span><span class="sxs-lookup"><span data-stu-id="8efed-120">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="8efed-121">Wiązanie źródeł — omówienie</span><span class="sxs-lookup"><span data-stu-id="8efed-121">Binding Sources Overview</span></span>](binding-sources-overview.md)
- [<span data-ttu-id="8efed-122">Udostępnianie danych do powiązania w XAML</span><span class="sxs-lookup"><span data-stu-id="8efed-122">Make Data Available for Binding in XAML</span></span>](how-to-make-data-available-for-binding-in-xaml.md)
