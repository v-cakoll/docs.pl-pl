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
ms.openlocfilehash: 72638101b73e6b43fa225885b2e1f27d87b22826
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2019
ms.locfileid: "72920144"
---
# <a name="how-to-bind-to-a-web-service"></a><span data-ttu-id="ff549-102">Jak powiązać z usługą sieci Web</span><span class="sxs-lookup"><span data-stu-id="ff549-102">How to: Bind to a Web Service</span></span>
<span data-ttu-id="ff549-103">Ten przykład pokazuje, jak powiązać z obiektami zwracanymi przez wywołania metody usługi sieci Web.</span><span class="sxs-lookup"><span data-stu-id="ff549-103">This example shows how to bind to objects returned by Web service method calls.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ff549-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="ff549-104">Example</span></span>  
 <span data-ttu-id="ff549-105">Ten przykład używa [usługi zawartości MSDN/TechNet Publishing System (MTPS)](https://go.microsoft.com/fwlink/?LinkId=95677) w celu pobrania listy języków obsługiwanych przez określony dokument.</span><span class="sxs-lookup"><span data-stu-id="ff549-105">This example uses the [MSDN/TechNet Publishing System (MTPS) Content Service](https://go.microsoft.com/fwlink/?LinkId=95677) to retrieve the list of languages supported by a specified document.</span></span>  
  
 <span data-ttu-id="ff549-106">Przed wywołaniem usługi sieci Web należy utworzyć odwołanie do niej.</span><span class="sxs-lookup"><span data-stu-id="ff549-106">Before you call a Web service, you need to create a reference to it.</span></span> <span data-ttu-id="ff549-107">Aby utworzyć odwołanie sieci Web do usługi MTPS przy użyciu programu Visual Studio, wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="ff549-107">To create a Web reference to the MTPS service using Visual Studio, follow the following steps:</span></span>  
  
1. <span data-ttu-id="ff549-108">Otwórz projekt w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ff549-108">Open your project in Visual Studio.</span></span>  
  
2. <span data-ttu-id="ff549-109">W menu **projekt** kliknij polecenie **Dodaj odwołanie sieci Web**.</span><span class="sxs-lookup"><span data-stu-id="ff549-109">From the **Project** menu, click **Add Web Reference**.</span></span>  
  
3. <span data-ttu-id="ff549-110">W oknie dialogowym Ustaw **adres URL** na [http://services.msdn.microsoft.com/contentservices/contentservice.asmx?wsdl](https://services.msdn.microsoft.com/contentservices/contentservice.asmx?wsdl).</span><span class="sxs-lookup"><span data-stu-id="ff549-110">In the dialog box, set the **URL** to [http://services.msdn.microsoft.com/contentservices/contentservice.asmx?wsdl](https://services.msdn.microsoft.com/contentservices/contentservice.asmx?wsdl).</span></span>  
  
4. <span data-ttu-id="ff549-111">Naciśnij przycisk **Przejdź** , a następnie **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="ff549-111">Press **Go** and then **Add Reference**.</span></span>  
  
 <span data-ttu-id="ff549-112">Następnie należy wywołać metodę usługi sieci Web i ustawić <xref:System.Windows.FrameworkElement.DataContext%2A> odpowiedniej kontrolki lub okna do zwracanego obiektu.</span><span class="sxs-lookup"><span data-stu-id="ff549-112">Next, you call the Web service method and set the <xref:System.Windows.FrameworkElement.DataContext%2A> of the appropriate control or window to the returned object.</span></span> <span data-ttu-id="ff549-113">Metoda **getContent** usługi MTPS przyjmuje odwołanie do obiektu **getContentRequest** .</span><span class="sxs-lookup"><span data-stu-id="ff549-113">The **GetContent** method of the MTPS service takes a reference to the **getContentRequest** object.</span></span> <span data-ttu-id="ff549-114">W związku z tym Poniższy przykład najpierw konfiguruje obiekt żądania:</span><span class="sxs-lookup"><span data-stu-id="ff549-114">Therefore, the following example first sets up a request object:</span></span>  
  
 [!code-csharp[BindToWebService#Namespace](~/samples/snippets/csharp/VS_Snippets_Wpf/BindToWebService/CSharp/Window1.xaml.cs#namespace)]
 [!code-vb[BindToWebService#Namespace](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BindToWebService/VisualBasic/Window1.xaml.vb#namespace)]  
[!code-csharp[BindToWebService#WebServiceCall](~/samples/snippets/csharp/VS_Snippets_Wpf/BindToWebService/CSharp/Window1.xaml.cs#webservicecall)]
[!code-vb[BindToWebService#WebServiceCall](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BindToWebService/VisualBasic/Window1.xaml.vb#webservicecall)]  
  
 <span data-ttu-id="ff549-115">Po ustawieniu <xref:System.Windows.FrameworkElement.DataContext%2A> można utworzyć powiązania z właściwościami obiektu, do którego ustawiono <xref:System.Windows.FrameworkElement.DataContext%2A>.</span><span class="sxs-lookup"><span data-stu-id="ff549-115">After the <xref:System.Windows.FrameworkElement.DataContext%2A> has been set, you can create bindings to the properties of the object that the <xref:System.Windows.FrameworkElement.DataContext%2A> has been set to.</span></span> <span data-ttu-id="ff549-116">W tym przykładzie <xref:System.Windows.FrameworkElement.DataContext%2A> jest ustawiony na obiekt **getContentResponse** zwrócony przez metodę **getContent** .</span><span class="sxs-lookup"><span data-stu-id="ff549-116">In this example, the <xref:System.Windows.FrameworkElement.DataContext%2A> is set to the **getContentResponse** object returned by the **GetContent** method.</span></span> <span data-ttu-id="ff549-117">W poniższym przykładzie <xref:System.Windows.Controls.ItemsControl> tworzy powiązanie z i wyświetla wartości **ustawień regionalnych** **availableVersionsAndLocales** **getContentResponse**.</span><span class="sxs-lookup"><span data-stu-id="ff549-117">In the following example, the <xref:System.Windows.Controls.ItemsControl> binds to and displays the **locale** values of **availableVersionsAndLocales** of **getContentResponse**.</span></span>  
  
 [!code-xaml[BindToWebService#Binding](~/samples/snippets/csharp/VS_Snippets_Wpf/BindToWebService/CSharp/Window1.xaml#binding)]  
  
 <span data-ttu-id="ff549-118">Informacje o strukturze **getContentResponse**można znaleźć w [dokumentacji usługi zawartości](https://services.msdn.microsoft.com/ContentServices/ContentService.asmx).</span><span class="sxs-lookup"><span data-stu-id="ff549-118">For information about the structure of **getContentResponse**, see [Content Service documentation](https://services.msdn.microsoft.com/ContentServices/ContentService.asmx).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff549-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ff549-119">See also</span></span>

- [<span data-ttu-id="ff549-120">Powiązanie danych — omówienie</span><span class="sxs-lookup"><span data-stu-id="ff549-120">Data Binding Overview</span></span>](data-binding-overview.md)
- [<span data-ttu-id="ff549-121">Wiązanie źródeł — omówienie</span><span class="sxs-lookup"><span data-stu-id="ff549-121">Binding Sources Overview</span></span>](binding-sources-overview.md)
- [<span data-ttu-id="ff549-122">Udostępnianie danych do powiązania w XAML</span><span class="sxs-lookup"><span data-stu-id="ff549-122">Make Data Available for Binding in XAML</span></span>](how-to-make-data-available-for-binding-in-xaml.md)
