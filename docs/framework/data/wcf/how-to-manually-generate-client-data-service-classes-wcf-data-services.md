---
title: "Porady: ręczne Generowanie klasy usługi danych klienta (usługi danych WCF)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF Data Services, configuring
- WCF Data Services, client library
ms.assetid: b98cb1d6-956a-4e50-add6-67e4f2587346
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f72f898b2a80d7d88a74deabe013e2eecc298bdd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-manually-generate-client-data-service-classes-wcf-data-services"></a><span data-ttu-id="1bd53-102">Porady: ręczne Generowanie klasy usługi danych klienta (usługi danych WCF)</span><span class="sxs-lookup"><span data-stu-id="1bd53-102">How to: Manually Generate Client Data Service Classes (WCF Data Services)</span></span>
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]<span data-ttu-id="1bd53-103">integruje się z programem Visual Studio umożliwiają automatyczne generowanie klasy usługi danych klienta, gdy używasz **Dodaj odwołanie do usługi** okno dialogowe, aby dodać odwołania do usługi danych w projekcie programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1bd53-103"> integrates with Visual Studio to enable you to automatically generate client data service classes when you use the **Add Service Reference** dialog box to add a reference to a data service in a Visual Studio project.</span></span> <span data-ttu-id="1bd53-104">Aby uzyskać więcej informacji, zobacz [porady: Dodawanie odwołania do danych usługi](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="1bd53-104">For more information, see [How to: Add a Data Service Reference](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md).</span></span> <span data-ttu-id="1bd53-105">Możesz też ręcznie wygenerować tej samej klasy usługi danych klienta przy użyciu narzędzia do generowania kodu, `DataSvcUtil.exe`.</span><span class="sxs-lookup"><span data-stu-id="1bd53-105">You can also manually generate the same client data service classes by using the code-generation tool, `DataSvcUtil.exe`.</span></span> <span data-ttu-id="1bd53-106">To narzędzie, który jest dołączony do [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], generuje klasy .NET Framework z definicji usługi danych.</span><span class="sxs-lookup"><span data-stu-id="1bd53-106">This tool, which is included with [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], generates .NET Framework classes from the data service definition.</span></span> <span data-ttu-id="1bd53-107">Można go również używane do generowania klasy usługi danych z pliku modelu koncepcyjnego (CSDL), a także od pliku edmx, który reprezentuje model narzędzia Entity Framework w projektu programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1bd53-107">It can also be used to generate data service classes from the conceptual model (.csdl) file and from the .edmx file that represents an Entity Framework model in a Visual Studio project.</span></span>  
  
 <span data-ttu-id="1bd53-108">W tym temacie tworzona klas usług danych klienta oparte na usługę Northwind przykładowych danych.</span><span class="sxs-lookup"><span data-stu-id="1bd53-108">The example in this topic creates client data service classes based on the Northwind sample data service.</span></span> <span data-ttu-id="1bd53-109">Ta usługa jest utworzone po zakończeniu [szybkiego startu usługi danych WCF](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="1bd53-109">This service is created when you complete the [WCF Data Services quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).</span></span> <span data-ttu-id="1bd53-110">Przykłady w tym temacie wymagają pliku modelu koncepcyjnego dla modelu Northwind.</span><span class="sxs-lookup"><span data-stu-id="1bd53-110">Some examples in this topic require the conceptual model file for the Northwind model.</span></span> <span data-ttu-id="1bd53-111">Aby uzyskać więcej informacji, zobacz [porady: EdmGen.exe używany do generowania modelu i mapowania plików](../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span><span class="sxs-lookup"><span data-stu-id="1bd53-111">For more information, see [How to: Use EdmGen.exe to Generate the Model and Mapping Files](../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span></span> <span data-ttu-id="1bd53-112">Przykłady w tym temacie wymagają pliku edmx modelu Northwind.</span><span class="sxs-lookup"><span data-stu-id="1bd53-112">Some examples in this topic require the .edmx file for the Northwind model.</span></span> <span data-ttu-id="1bd53-113">Aby uzyskać więcej informacji, zobacz [pliku Przegląd edmx](http://msdn.microsoft.com/en-us/f4c8e7ce-1db6-417e-9759-15f8b55155d4).</span><span class="sxs-lookup"><span data-stu-id="1bd53-113">For more information, see [.edmx File Overview](http://msdn.microsoft.com/en-us/f4c8e7ce-1db6-417e-9759-15f8b55155d4).</span></span>  
  
### <a name="to-generate-c-classes-that-support-data-binding"></a><span data-ttu-id="1bd53-114">Można wygenerować klas C#, które obsługuje powiązanie danych</span><span class="sxs-lookup"><span data-stu-id="1bd53-114">To generate C# classes that support data binding</span></span>  
  
-   <span data-ttu-id="1bd53-115">W wierszu polecenia Uruchom następujące polecenie bez podziałów wierszy:</span><span class="sxs-lookup"><span data-stu-id="1bd53-115">At the command prompt, execute the following command without line breaks:</span></span>  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v3.5\DataSvcUtil.exe" /dataservicecollection /version:2.0 /language:CSharp /out:Northwind.cs /uri:http://localhost:12345/Northwind.svc  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="1bd53-116">Należy zastąpić wartość dostarczona do `/uri:` parametru o identyfikatorze URI wystąpienia usługi Northwind przykładowych danych.</span><span class="sxs-lookup"><span data-stu-id="1bd53-116">You must replace the value supplied to the `/uri:` parameter with the URI of your instance of the Northwind sample data service.</span></span>  
  
### <a name="to-generate-visual-basic-classes-that-support-data-binding"></a><span data-ttu-id="1bd53-117">Można wygenerować klas języka Visual Basic, które obsługuje powiązanie danych</span><span class="sxs-lookup"><span data-stu-id="1bd53-117">To generate Visual Basic classes that support data binding</span></span>  
  
-   <span data-ttu-id="1bd53-118">W wierszu polecenia Uruchom następujące polecenie bez podziałów wierszy:</span><span class="sxs-lookup"><span data-stu-id="1bd53-118">At the command prompt, execute the following command without line breaks:</span></span>  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v3.5\DataSvcUtil.exe" /dataservicecollection /version:2.0 /language:VB /out:Northwind.vb /uri:http://localhost:12345/Northwind.svc  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="1bd53-119">Należy zastąpić wartość dostarczona do `/uri:` parametru o identyfikatorze URI wystąpienia usługi Northwind przykładowych danych.</span><span class="sxs-lookup"><span data-stu-id="1bd53-119">You must replace value supplied to the `/uri:` parameter with the URI of your instance of the Northwind sample data service.</span></span>  
  
### <a name="to-generate-c-classes-based-on-the-service-uri"></a><span data-ttu-id="1bd53-120">Aby wygenerować klas C# opartych na identyfikator URI usługi</span><span class="sxs-lookup"><span data-stu-id="1bd53-120">To generate C# classes based on the service URI</span></span>  
  
-   <span data-ttu-id="1bd53-121">W wierszu polecenia Uruchom następujące polecenie bez podziałów wierszy:</span><span class="sxs-lookup"><span data-stu-id="1bd53-121">At the command prompt, execute the following command without line breaks:</span></span>  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v3.5\DataSvcUtil.exe" /language:CSharp /out:northwind.cs /uri:http://localhost:12345/Northwind.svc  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="1bd53-122">Należy zastąpić wartość dostarczona do `/uri:` parametru o identyfikatorze URI wystąpienia usługi Northwind przykładowych danych.</span><span class="sxs-lookup"><span data-stu-id="1bd53-122">You must replace the value supplied to the `/uri:` parameter with the URI of your instance of the Northwind sample data service.</span></span>  
  
### <a name="to-generate-visual-basic-classes-based-on-the-service-uri"></a><span data-ttu-id="1bd53-123">Aby wygenerować klas języka Visual Basic opartych na identyfikator URI usługi</span><span class="sxs-lookup"><span data-stu-id="1bd53-123">To generate Visual Basic classes based on the service URI</span></span>  
  
-   <span data-ttu-id="1bd53-124">W wierszu polecenia Uruchom następujące polecenie bez podziałów wierszy:</span><span class="sxs-lookup"><span data-stu-id="1bd53-124">At the command prompt, execute the following command without line breaks:</span></span>  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:VB /out:Northwind.vb /uri:http://localhost:12345/Northwind.svc  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="1bd53-125">Należy zastąpić wartość dostarczona do `/uri:` parametru o identyfikatorze URI wystąpienia usługi Northwind przykładowych danych.</span><span class="sxs-lookup"><span data-stu-id="1bd53-125">You must replace value supplied to the `/uri:` parameter with the URI of your instance of the Northwind sample data service.</span></span>  
  
### <a name="to-generate-c-classes-based-on-the-conceptual-model-file-csdl"></a><span data-ttu-id="1bd53-126">Do generowania klasy C#, na podstawie pliku modelu koncepcyjnego (CSDL)</span><span class="sxs-lookup"><span data-stu-id="1bd53-126">To generate C# classes based on the conceptual model file (CSDL)</span></span>  
  
-   <span data-ttu-id="1bd53-127">W wierszu polecenia Uruchom następujące polecenie bez podziałów wierszy:</span><span class="sxs-lookup"><span data-stu-id="1bd53-127">At the command prompt, execute the following command without line breaks:</span></span>  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:CSharp /in:Northwind.csdl /out:Northwind.cs  
    ```  
  
### <a name="to-generate-visual-basic-classes-based-on-the-conceptual-model-file-csdl"></a><span data-ttu-id="1bd53-128">Można wygenerować klas języka Visual Basic na podstawie pliku modelu koncepcyjnego (CSDL)</span><span class="sxs-lookup"><span data-stu-id="1bd53-128">To generate Visual Basic classes based on the conceptual model file (CSDL)</span></span>  
  
-   <span data-ttu-id="1bd53-129">W wierszu polecenia Uruchom następujące polecenie bez podziałów wierszy:</span><span class="sxs-lookup"><span data-stu-id="1bd53-129">At the command prompt, execute the following command without line breaks:</span></span>  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:VB /in:Northwind.csdl /out:Northwind.vb  
    ```  
  
### <a name="to-generate-c-classes-based-on-the-edmx-file"></a><span data-ttu-id="1bd53-130">Aby wygenerować na podstawie pliku edmx klas C#</span><span class="sxs-lookup"><span data-stu-id="1bd53-130">To generate C# classes based on the .edmx file</span></span>  
  
-   <span data-ttu-id="1bd53-131">W wierszu polecenia Uruchom następujące polecenie bez podziałów wierszy:</span><span class="sxs-lookup"><span data-stu-id="1bd53-131">At the command prompt, execute the following command without line breaks:</span></span>  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:CSharp /in:Northwind.edmx /out:c:\northwind.cs   
    ```  
  
### <a name="to-generate-visual-basic-classes-based-on-the-edmx-file"></a><span data-ttu-id="1bd53-132">Aby wygenerować na podstawie pliku edmx klas języka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1bd53-132">To generate Visual Basic classes based on the .edmx file</span></span>  
  
-   <span data-ttu-id="1bd53-133">W wierszu polecenia Uruchom następujące polecenie bez podziałów wierszy:</span><span class="sxs-lookup"><span data-stu-id="1bd53-133">At the command prompt, execute the following command without line breaks:</span></span>  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:VB /in:Northwind.edmx /out:c:\northwind.vb   
    ```  
  
## <a name="see-also"></a><span data-ttu-id="1bd53-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1bd53-134">See Also</span></span>  
 [<span data-ttu-id="1bd53-135">Generowanie biblioteki klienta usługi danych</span><span class="sxs-lookup"><span data-stu-id="1bd53-135">Generating the Data Service Client Library</span></span>](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md)  
 [<span data-ttu-id="1bd53-136">Instrukcje: Dodawanie odwołania do usługi danych</span><span class="sxs-lookup"><span data-stu-id="1bd53-136">How to: Add a Data Service Reference</span></span>](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md)  
 [<span data-ttu-id="1bd53-137">Narzędzie klienta usługi danych WCF (DataSvcUtil.exe)</span><span class="sxs-lookup"><span data-stu-id="1bd53-137">WCF Data Service Client Utility (DataSvcUtil.exe)</span></span>](../../../../docs/framework/data/wcf/wcf-data-service-client-utility-datasvcutil-exe.md)
