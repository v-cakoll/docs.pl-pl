---
title: Powiąż z usługą sieci Web przy użyciu źródła BindingSource
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Web services [Windows Forms], binding controls
- BindingSource component [Windows Forms], binding to a Web service
- examples [Windows Forms], BindingSource component
- controls [Windows Forms], binding to Web service
- BindingSource component [Windows Forms], examples
ms.assetid: ee261207-4573-4cb9-a8cb-5185037e0fba
ms.openlocfilehash: 0680c73e578577cf40158761f6c635fe30ff9f4d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746678"
---
# <a name="how-to-bind-to-a-web-service-using-the-windows-forms-bindingsource"></a><span data-ttu-id="d795e-102">Porady: powiązanie z usługą sieci Web za pomocą kontrolki BindingSource formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="d795e-102">How to: Bind to a Web Service Using the Windows Forms BindingSource</span></span>
<span data-ttu-id="d795e-103">Jeśli chcesz powiązać formant formularza systemu Windows z wynikami uzyskanymi z wywołania usługi sieci Web XML, możesz użyć składnika <xref:System.Windows.Forms.BindingSource>.</span><span class="sxs-lookup"><span data-stu-id="d795e-103">If you want to bind a Windows Form control to the results obtained from calling an XML Web service, you can use a <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="d795e-104">Ta procedura jest podobna do powiązania składnika <xref:System.Windows.Forms.BindingSource> z typem.</span><span class="sxs-lookup"><span data-stu-id="d795e-104">This procedure is similar to binding a <xref:System.Windows.Forms.BindingSource> component to a type.</span></span> <span data-ttu-id="d795e-105">Należy utworzyć serwer proxy po stronie klienta zawierający metody i typy udostępniane przez usługę sieci Web.</span><span class="sxs-lookup"><span data-stu-id="d795e-105">You must create a client-side proxy that contains the methods and types exposed by the Web service.</span></span> <span data-ttu-id="d795e-106">Serwer proxy po stronie klienta jest generowany na podstawie samej usługi sieci Web (. asmx) lub pliku Web Services Description Language (WSDL).</span><span class="sxs-lookup"><span data-stu-id="d795e-106">You generate a client-side proxy from the Web service (.asmx) itself, or its Web Services Description Language (WSDL) file.</span></span> <span data-ttu-id="d795e-107">Ponadto serwer proxy po stronie klienta musi ujawniać pola typów złożonych używanych przez usługę sieci Web jako właściwości publiczne.</span><span class="sxs-lookup"><span data-stu-id="d795e-107">Additionally, your client-side proxy must expose the fields of complex types used by the Web service as public properties.</span></span> <span data-ttu-id="d795e-108">Następnie można powiązać <xref:System.Windows.Forms.BindingSource> z jednym z typów uwidocznionych w serwerze proxy usługi sieci Web.</span><span class="sxs-lookup"><span data-stu-id="d795e-108">You then bind the <xref:System.Windows.Forms.BindingSource> to one of the types exposed in the Web service proxy.</span></span>  
  
### <a name="to-create-and-bind-to-a-client-side-proxy"></a><span data-ttu-id="d795e-109">Aby utworzyć i powiązać serwer proxy po stronie klienta</span><span class="sxs-lookup"><span data-stu-id="d795e-109">To create and bind to a client-side proxy</span></span>  
  
1. <span data-ttu-id="d795e-110">Utwórz w wybranym katalogu formularz systemu Windows z odpowiednią przestrzenią nazw.</span><span class="sxs-lookup"><span data-stu-id="d795e-110">Create a Windows Form in the directory of your choice, with an appropriate namespace.</span></span>  
  
2. <span data-ttu-id="d795e-111">Dodaj składnik <xref:System.Windows.Forms.BindingSource> do formularza.</span><span class="sxs-lookup"><span data-stu-id="d795e-111">Add a <xref:System.Windows.Forms.BindingSource> component to the form.</span></span>  
  
3. <span data-ttu-id="d795e-112">Otwórz wiersz polecenia zestawu Windows Software Development Kit (SDK) i przejdź do tego samego katalogu, w którym znajduje się formularz.</span><span class="sxs-lookup"><span data-stu-id="d795e-112">Open the Windows Software Development Kit (SDK) command prompt, and navigate to the same directory that your form is located in.</span></span>  
  
4. <span data-ttu-id="d795e-113">Za pomocą narzędzia WSDL wprowadź `wsdl` i adres URL pliku. asmx lub WSDL dla usługi sieci Web, a następnie przestrzeń nazw aplikacji i opcjonalnie język, w którym pracujesz.</span><span class="sxs-lookup"><span data-stu-id="d795e-113">Using the WSDL tool, enter `wsdl` and the URL for the .asmx or WSDL file for the Web service, followed by the namespace of your application, and optionally the language you are working in.</span></span>  
  
     <span data-ttu-id="d795e-114">Poniższy przykład kodu używa usługi sieci Web znajdującej się w `http://webservices.eraserver.net/zipcoderesolver/zipcoderesolver.asmx`.</span><span class="sxs-lookup"><span data-stu-id="d795e-114">The following code example uses the Web service located at `http://webservices.eraserver.net/zipcoderesolver/zipcoderesolver.asmx`.</span></span> <span data-ttu-id="d795e-115">Na przykład dla C# typu `wsdl http://webservices.eraserver.net.zipcoderesolver/zipcoderesolver.asmx /n:BindToWebService`lub Visual Basic `wsdl http://webservices.eraserver.net.zipcoderesolver/zipcoderesolver.asmx /n:BindToWebService /language:VB`.</span><span class="sxs-lookup"><span data-stu-id="d795e-115">For example, for C# type `wsdl http://webservices.eraserver.net.zipcoderesolver/zipcoderesolver.asmx /n:BindToWebService`, or for Visual Basic type `wsdl http://webservices.eraserver.net.zipcoderesolver/zipcoderesolver.asmx /n:BindToWebService /language:VB`.</span></span> <span data-ttu-id="d795e-116">Przekazanie ścieżki jako argumentu narzędzia WSDL spowoduje wygenerowanie serwera proxy po stronie klienta w tym samym katalogu i przestrzeni nazw, w którym znajduje się aplikacja, w określonym języku.</span><span class="sxs-lookup"><span data-stu-id="d795e-116">Passing the path as an argument to the WSDL tool will generate a client-side proxy in the same directory and namespace as your application, in the specified language.</span></span> <span data-ttu-id="d795e-117">Jeśli używasz programu Visual Studio, Dodaj plik do projektu.</span><span class="sxs-lookup"><span data-stu-id="d795e-117">If you are using Visual Studio, add the file to your project.</span></span>  
  
5. <span data-ttu-id="d795e-118">Wybierz typ w serwerze proxy po stronie klienta, z którym ma zostać utworzone powiązanie.</span><span class="sxs-lookup"><span data-stu-id="d795e-118">Select a type in the client-side proxy to bind to.</span></span>  
  
     <span data-ttu-id="d795e-119">Zwykle jest to typ zwracany przez metodę oferowaną przez usługę sieci Web.</span><span class="sxs-lookup"><span data-stu-id="d795e-119">This is typically a type returned by a method offered by the Web service.</span></span> <span data-ttu-id="d795e-120">Pola wybranego typu muszą być uwidocznione jako właściwości publiczne na potrzeby tworzenia powiązań.</span><span class="sxs-lookup"><span data-stu-id="d795e-120">The fields of the chosen type must be exposed as public properties for binding purposes.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataConnectorWebService#4](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CPP/form1.cpp#4)]
     [!code-csharp[System.Windows.Forms.DataConnectorWebService#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CS/form1.cs#4)]
     [!code-vb[System.Windows.Forms.DataConnectorWebService#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/VB/form1.vb#4)]  
  
6. <span data-ttu-id="d795e-121">Ustaw właściwość <xref:System.Windows.Forms.BindingSource.DataSource%2A> <xref:System.Windows.Forms.BindingSource> na typ, który ma być zawarty w serwerze proxy po stronie klienta usługi sieci Web.</span><span class="sxs-lookup"><span data-stu-id="d795e-121">Set the <xref:System.Windows.Forms.BindingSource.DataSource%2A> property of the <xref:System.Windows.Forms.BindingSource> to the type you want that is contained in the Web service client-side proxy.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataConnectorWebService#2](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CPP/form1.cpp#2)]
     [!code-csharp[System.Windows.Forms.DataConnectorWebService#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CS/form1.cs#2)]
     [!code-vb[System.Windows.Forms.DataConnectorWebService#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/VB/form1.vb#2)]  
  
### <a name="to-bind-controls-to-the-bindingsource-that-is-bound-to-a-web-service"></a><span data-ttu-id="d795e-122">Aby powiązać kontrolki ze źródłem BindingSource, które jest powiązane z usługą sieci Web</span><span class="sxs-lookup"><span data-stu-id="d795e-122">To bind controls to the BindingSource that is bound to a Web service</span></span>  
  
- <span data-ttu-id="d795e-123">Powiązywanie kontrolek z <xref:System.Windows.Forms.BindingSource>, przekazując Właściwość publiczną typu usługi sieci Web, która ma być parametrem.</span><span class="sxs-lookup"><span data-stu-id="d795e-123">Bind controls to the <xref:System.Windows.Forms.BindingSource>, passing the public property of the Web service type that you want as a parameter.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataConnectorWebService#3](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CPP/form1.cpp#3)]
     [!code-csharp[System.Windows.Forms.DataConnectorWebService#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CS/form1.cs#3)]
     [!code-vb[System.Windows.Forms.DataConnectorWebService#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/VB/form1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="d795e-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="d795e-124">Example</span></span>  
 <span data-ttu-id="d795e-125">Poniższy przykład kodu demonstruje sposób powiązania składnika <xref:System.Windows.Forms.BindingSource> z usługą sieci Web, a następnie powiązania pola tekstowego ze składnikiem <xref:System.Windows.Forms.BindingSource>.</span><span class="sxs-lookup"><span data-stu-id="d795e-125">The following code example demonstrates how to bind a <xref:System.Windows.Forms.BindingSource> component to a Web service, and then how to bind a text box to the <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="d795e-126">Po kliknięciu przycisku zostanie wywołana metoda usługi sieci Web, a wyniki pojawią się w `textbox1`.</span><span class="sxs-lookup"><span data-stu-id="d795e-126">When you click the button, a Web service method is called and the results will appear in `textbox1`.</span></span>  
  
 [!code-cpp[System.Windows.Forms.DataConnectorWebService#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnectorWebService#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnectorWebService#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d795e-127">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="d795e-127">Compiling the Code</span></span>  
 <span data-ttu-id="d795e-128">Jest to kompletny przykład, który obejmuje metodę `Main` i skróconą wersję kodu serwera proxy po stronie klienta.</span><span class="sxs-lookup"><span data-stu-id="d795e-128">This is a complete example that includes a `Main` method, and a shortened version of client-side proxy code.</span></span>  
  
 <span data-ttu-id="d795e-129">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="d795e-129">This example requires:</span></span>  
  
- <span data-ttu-id="d795e-130">Odwołania do zestawów system, system. Drawing, system. Web. Services, system. Windows. Forms i system. XML.</span><span class="sxs-lookup"><span data-stu-id="d795e-130">References to the System, System.Drawing, System.Web.Services, System.Windows.Forms and System.Xml assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d795e-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d795e-131">See also</span></span>

- [<span data-ttu-id="d795e-132">BindingSource, składnik</span><span class="sxs-lookup"><span data-stu-id="d795e-132">BindingSource Component</span></span>](bindingsource-component.md)
- [<span data-ttu-id="d795e-133">Instrukcje: powiązanie kontrolki Windows Forms z typem</span><span class="sxs-lookup"><span data-stu-id="d795e-133">How to: Bind a Windows Forms Control to a Type</span></span>](how-to-bind-a-windows-forms-control-to-a-type.md)
