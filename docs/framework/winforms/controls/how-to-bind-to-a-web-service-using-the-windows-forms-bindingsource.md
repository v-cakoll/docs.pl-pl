---
title: 'Instrukcje: Powiązanie z usługą sieci Web przy użyciu kontrolki BindingSource formularzy Windows Forms'
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
ms.openlocfilehash: 597ffbfb44430379e1ca3709aa88e25fc2f22d46
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57722623"
---
# <a name="how-to-bind-to-a-web-service-using-the-windows-forms-bindingsource"></a><span data-ttu-id="782a9-102">Instrukcje: Powiązanie z usługą sieci Web przy użyciu kontrolki BindingSource formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="782a9-102">How to: Bind to a Web Service Using the Windows Forms BindingSource</span></span>
<span data-ttu-id="782a9-103">Jeśli chcesz powiązać kontrolkę formularza Windows wyniki uzyskane z wywołaniem usługi sieci Web XML, możesz użyć <xref:System.Windows.Forms.BindingSource> składnika.</span><span class="sxs-lookup"><span data-stu-id="782a9-103">If you want to bind a Windows Form control to the results obtained from calling an XML Web service, you can use a <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="782a9-104">Ta procedura jest podobna do powiązania <xref:System.Windows.Forms.BindingSource> składnik do typu.</span><span class="sxs-lookup"><span data-stu-id="782a9-104">This procedure is similar to binding a <xref:System.Windows.Forms.BindingSource> component to a type.</span></span> <span data-ttu-id="782a9-105">Należy utworzyć serwer proxy po stronie klienta, który zawiera metody i typy udostępnianych przez usługę sieci Web.</span><span class="sxs-lookup"><span data-stu-id="782a9-105">You must create a client-side proxy that contains the methods and types exposed by the Web service.</span></span> <span data-ttu-id="782a9-106">Możesz wygenerować, serwer proxy po stronie klienta z usługi sieci Web (.asmx), samego lub plik sieci Web Services Description Language (WSDL).</span><span class="sxs-lookup"><span data-stu-id="782a9-106">You generate a client-side proxy from the Web service (.asmx) itself, or its Web Services Description Language (WSDL) file.</span></span> <span data-ttu-id="782a9-107">Ponadto serwer proxy po stronie klienta, należy ujawnić pola złożone typy używane przez usługę sieci Web jako właściwości publiczne.</span><span class="sxs-lookup"><span data-stu-id="782a9-107">Additionally, your client-side proxy must expose the fields of complex types used by the Web service as public properties.</span></span> <span data-ttu-id="782a9-108">Następnie Powiąż <xref:System.Windows.Forms.BindingSource> do jednego z typów ujawnione w sieci Web usługi serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="782a9-108">You then bind the <xref:System.Windows.Forms.BindingSource> to one of the types exposed in the Web service proxy.</span></span>  
  
### <a name="to-create-and-bind-to-a-client-side-proxy"></a><span data-ttu-id="782a9-109">Aby utworzyć i powiązać serwer proxy po stronie klienta</span><span class="sxs-lookup"><span data-stu-id="782a9-109">To create and bind to a client-side proxy</span></span>  
  
1.  <span data-ttu-id="782a9-110">Tworzenie formularza Windows w katalogu, co pozwala przy użyciu odpowiedniego obszaru nazw.</span><span class="sxs-lookup"><span data-stu-id="782a9-110">Create a Windows Form in the directory of your choice, with an appropriate namespace.</span></span>  
  
2.  <span data-ttu-id="782a9-111">Dodaj <xref:System.Windows.Forms.BindingSource> składnika do formularza.</span><span class="sxs-lookup"><span data-stu-id="782a9-111">Add a <xref:System.Windows.Forms.BindingSource> component to the form.</span></span>  
  
3.  <span data-ttu-id="782a9-112">Otwórz [!INCLUDE[winsdklong](../../../../includes/winsdklong-md.md)] wiersz polecenia i przejdź do formularza znajdujący się w katalogu.</span><span class="sxs-lookup"><span data-stu-id="782a9-112">Open the [!INCLUDE[winsdklong](../../../../includes/winsdklong-md.md)] command prompt, and navigate to the same directory that your form is located in.</span></span>  
  
4.  <span data-ttu-id="782a9-113">Za pomocą narzędzia WSDL wprowadź `wsdl` adres URL .asmx lub pliku WSDL usługi sieci Web, a następnie przestrzeni nazw aplikacji i opcjonalnie język, w którym pracujesz.</span><span class="sxs-lookup"><span data-stu-id="782a9-113">Using the WSDL tool, enter `wsdl` and the URL for the .asmx or WSDL file for the Web service, followed by the namespace of your application, and optionally the language you are working in.</span></span>  
  
     <span data-ttu-id="782a9-114">Poniższy przykład kodu wykorzystuje usługę sieci Web, znajduje się w `http://webservices.eraserver.net/zipcoderesolver/zipcoderesolver.asmx`.</span><span class="sxs-lookup"><span data-stu-id="782a9-114">The following code example uses the Web service located at `http://webservices.eraserver.net/zipcoderesolver/zipcoderesolver.asmx`.</span></span> <span data-ttu-id="782a9-115">Na przykład typ C# `wsdl http://webservices.eraserver.net.zipcoderesolver/zipcoderesolver.asmx /n:BindToWebService`, lub dla języka Visual Basic typu `wsdl http://webservices.eraserver.net.zipcoderesolver/zipcoderesolver.asmx /n:BindToWebService /language:VB`.</span><span class="sxs-lookup"><span data-stu-id="782a9-115">For example, for C# type `wsdl http://webservices.eraserver.net.zipcoderesolver/zipcoderesolver.asmx /n:BindToWebService`, or for Visual Basic type `wsdl http://webservices.eraserver.net.zipcoderesolver/zipcoderesolver.asmx /n:BindToWebService /language:VB`.</span></span> <span data-ttu-id="782a9-116">Przekazanie ścieżki jako argument do języka WSDL narzędzie wygeneruje serwer proxy po stronie klienta w tym samym katalogu i przestrzeni nazw jako aplikację w wybranym języku.</span><span class="sxs-lookup"><span data-stu-id="782a9-116">Passing the path as an argument to the WSDL tool will generate a client-side proxy in the same directory and namespace as your application, in the specified language.</span></span> <span data-ttu-id="782a9-117">Jeśli używasz programu Visual Studio, należy dodać plik do projektu.</span><span class="sxs-lookup"><span data-stu-id="782a9-117">If you are using Visual Studio, add the file to your project.</span></span>  
  
5.  <span data-ttu-id="782a9-118">Wybierz typ serwera proxy po stronie klienta, aby powiązać.</span><span class="sxs-lookup"><span data-stu-id="782a9-118">Select a type in the client-side proxy to bind to.</span></span>  
  
     <span data-ttu-id="782a9-119">Zazwyczaj jest to typ zwracany przez metodę, oferowane przez usługę sieci Web.</span><span class="sxs-lookup"><span data-stu-id="782a9-119">This is typically a type returned by a method offered by the Web service.</span></span> <span data-ttu-id="782a9-120">Pola wybranego typu muszą być widoczne jako właściwości publiczne dla powiązania celów.</span><span class="sxs-lookup"><span data-stu-id="782a9-120">The fields of the chosen type must be exposed as public properties for binding purposes.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataConnectorWebService#4](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CPP/form1.cpp#4)]
     [!code-csharp[System.Windows.Forms.DataConnectorWebService#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CS/form1.cs#4)]
     [!code-vb[System.Windows.Forms.DataConnectorWebService#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/VB/form1.vb#4)]  
  
6.  <span data-ttu-id="782a9-121">Ustaw <xref:System.Windows.Forms.BindingSource.DataSource%2A> właściwość <xref:System.Windows.Forms.BindingSource> do typu, to znaczy ma zawarte w serwer proxy po stronie klienta dla usługi sieci Web.</span><span class="sxs-lookup"><span data-stu-id="782a9-121">Set the <xref:System.Windows.Forms.BindingSource.DataSource%2A> property of the <xref:System.Windows.Forms.BindingSource> to the type you want that is contained in the Web service client-side proxy.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataConnectorWebService#2](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CPP/form1.cpp#2)]
     [!code-csharp[System.Windows.Forms.DataConnectorWebService#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CS/form1.cs#2)]
     [!code-vb[System.Windows.Forms.DataConnectorWebService#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/VB/form1.vb#2)]  
  
### <a name="to-bind-controls-to-the-bindingsource-that-is-bound-to-a-web-service"></a><span data-ttu-id="782a9-122">Aby powiązać formanty z BindingSource, który jest powiązany z usługą sieci Web</span><span class="sxs-lookup"><span data-stu-id="782a9-122">To bind controls to the BindingSource that is bound to a Web service</span></span>  
  
-   <span data-ttu-id="782a9-123">Powiązywanie kontrolek do <xref:System.Windows.Forms.BindingSource>, przekazując właściwość publiczna typu usługi sieci Web, która ma jako parametr.</span><span class="sxs-lookup"><span data-stu-id="782a9-123">Bind controls to the <xref:System.Windows.Forms.BindingSource>, passing the public property of the Web service type that you want as a parameter.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataConnectorWebService#3](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CPP/form1.cpp#3)]
     [!code-csharp[System.Windows.Forms.DataConnectorWebService#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CS/form1.cs#3)]
     [!code-vb[System.Windows.Forms.DataConnectorWebService#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/VB/form1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="782a9-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="782a9-124">Example</span></span>  
 <span data-ttu-id="782a9-125">Poniższy przykład kodu pokazuje, jak powiązać <xref:System.Windows.Forms.BindingSource> składnik usługi sieci Web, a następnie powiązać pole tekstowe do <xref:System.Windows.Forms.BindingSource> składnika.</span><span class="sxs-lookup"><span data-stu-id="782a9-125">The following code example demonstrates how to bind a <xref:System.Windows.Forms.BindingSource> component to a Web service, and then how to bind a text box to the <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="782a9-126">Po kliknięciu przycisku, wywoływana jest metoda usługi sieci Web i wyniki pojawią się w `textbox1`.</span><span class="sxs-lookup"><span data-stu-id="782a9-126">When you click the button, a Web service method is called and the results will appear in `textbox1`.</span></span>  
  
 [!code-cpp[System.Windows.Forms.DataConnectorWebService#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnectorWebService#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnectorWebService#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="782a9-127">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="782a9-127">Compiling the Code</span></span>  
 <span data-ttu-id="782a9-128">Jest to kompletny przykład, który zawiera `Main` metoda i skróconą wersję kodu serwera proxy po stronie klienta.</span><span class="sxs-lookup"><span data-stu-id="782a9-128">This is a complete example that includes a `Main` method, and a shortened version of client-side proxy code.</span></span>  
  
 <span data-ttu-id="782a9-129">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="782a9-129">This example requires:</span></span>  
  
-   <span data-ttu-id="782a9-130">Odwołania do zestawów systemu, System.Drawing, System.Web.Services, przestrzeń nazw System.Windows.Forms i System.Xml.</span><span class="sxs-lookup"><span data-stu-id="782a9-130">References to the System, System.Drawing, System.Web.Services, System.Windows.Forms and System.Xml assemblies.</span></span>  
  
 <span data-ttu-id="782a9-131">Aby dowiedzieć się, jak tworzyć aplikacje w tym przykładzie z wiersza polecenia dla języka Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [wiersza polecenia tworzenia przy użyciu csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="782a9-131">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="782a9-132">Można także utworzyć tego przykładu w programie Visual Studio, wklejając kod do nowego projektu.</span><span class="sxs-lookup"><span data-stu-id="782a9-132">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="782a9-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="782a9-133">See also</span></span>
- [<span data-ttu-id="782a9-134">BindingSource, składnik</span><span class="sxs-lookup"><span data-stu-id="782a9-134">BindingSource Component</span></span>](bindingsource-component.md)
- [<span data-ttu-id="782a9-135">Instrukcje: Powiązanie z typem formantu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="782a9-135">How to: Bind a Windows Forms Control to a Type</span></span>](how-to-bind-a-windows-forms-control-to-a-type.md)
