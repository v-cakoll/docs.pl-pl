---
title: 'Instrukcje: Ręczne Generowanie klas usługi danych klienta (WCF Data Services)'
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, configuring
- WCF Data Services, client library
ms.assetid: b98cb1d6-956a-4e50-add6-67e4f2587346
ms.openlocfilehash: fbf3a3a2ee52df95780f715e1358a042eb7dd02c
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53128664"
---
# <a name="how-to-manually-generate-client-data-service-classes-wcf-data-services"></a><span data-ttu-id="fcb99-102">Instrukcje: Ręczne Generowanie klas usługi danych klienta (WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="fcb99-102">How to: Manually Generate Client Data Service Classes (WCF Data Services)</span></span>
<span data-ttu-id="fcb99-103">Usługi danych WCF integruje się z programem Visual Studio, aby umożliwić automatyczne generowanie klas usługi danych klienta, gdy używasz **Dodaj odwołanie do usługi** okno dialogowe, aby dodać odwołanie do usługi danych w projekcie programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="fcb99-103">WCF Data Services integrates with Visual Studio to enable you to automatically generate client data service classes when you use the **Add Service Reference** dialog box to add a reference to a data service in a Visual Studio project.</span></span> <span data-ttu-id="fcb99-104">Aby uzyskać więcej informacji, zobacz [jak: Dodaj odwołanie do usługi danych](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="fcb99-104">For more information, see [How to: Add a Data Service Reference](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md).</span></span> <span data-ttu-id="fcb99-105">Możesz również ręcznie wygenerować tych samych klas usługi danych klienta przy użyciu narzędzia do generowania kodu `DataSvcUtil.exe`.</span><span class="sxs-lookup"><span data-stu-id="fcb99-105">You can also manually generate the same client data service classes by using the code-generation tool, `DataSvcUtil.exe`.</span></span> <span data-ttu-id="fcb99-106">To narzędzie, który jest dołączony do usługi danych WCF, generuje klas .NET Framework na podstawie definicji usługi danych.</span><span class="sxs-lookup"><span data-stu-id="fcb99-106">This tool, which is included with WCF Data Services, generates .NET Framework classes from the data service definition.</span></span> <span data-ttu-id="fcb99-107">Może również służyć do Generowanie klas usługi danych z pliku modelu koncepcyjnego (.csdl), a także z pliku edmx, który reprezentuje model Entity Framework w projekcie programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="fcb99-107">It can also be used to generate data service classes from the conceptual model (.csdl) file and from the .edmx file that represents an Entity Framework model in a Visual Studio project.</span></span>

 <span data-ttu-id="fcb99-108">Ten przykład, w tym temacie tworzy klas usługi danych klienta oparte na usługę Northwind przykładowych danych.</span><span class="sxs-lookup"><span data-stu-id="fcb99-108">The example in this topic creates client data service classes based on the Northwind sample data service.</span></span> <span data-ttu-id="fcb99-109">Ta usługa zostanie utworzona po zakończeniu [Szybki Start usług danych WCF](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="fcb99-109">This service is created when you complete the [WCF Data Services quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).</span></span> <span data-ttu-id="fcb99-110">Przykłady w tym temacie wymagają pliku modelu koncepcyjnego dla modelu Northwind.</span><span class="sxs-lookup"><span data-stu-id="fcb99-110">Some examples in this topic require the conceptual model file for the Northwind model.</span></span> <span data-ttu-id="fcb99-111">Aby uzyskać więcej informacji, zobacz [jak: Generowanie modelu i mapowania plików za pomocą EdmGen.exe](../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span><span class="sxs-lookup"><span data-stu-id="fcb99-111">For more information, see [How to: Use EdmGen.exe to Generate the Model and Mapping Files](../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span></span> <span data-ttu-id="fcb99-112">Przykłady w tym temacie wymagają pliku edmx dla modelu Northwind.</span><span class="sxs-lookup"><span data-stu-id="fcb99-112">Some examples in this topic require the .edmx file for the Northwind model.</span></span> <span data-ttu-id="fcb99-113">Aby uzyskać więcej informacji, zobacz [Omówienie pliku edmx](https://msdn.microsoft.com/library/f4c8e7ce-1db6-417e-9759-15f8b55155d4).</span><span class="sxs-lookup"><span data-stu-id="fcb99-113">For more information, see [.edmx File Overview](https://msdn.microsoft.com/library/f4c8e7ce-1db6-417e-9759-15f8b55155d4).</span></span>

### <a name="to-generate-c-classes-that-support-data-binding"></a><span data-ttu-id="fcb99-114">Można wygenerować klas języka C#, które obsługuje powiązanie danych</span><span class="sxs-lookup"><span data-stu-id="fcb99-114">To generate C# classes that support data binding</span></span>

-   <span data-ttu-id="fcb99-115">W wierszu polecenia Uruchom następujące polecenie bez podziałów wiersza:</span><span class="sxs-lookup"><span data-stu-id="fcb99-115">At the command prompt, execute the following command without line breaks:</span></span>

    ```console
    "%windir%\Microsoft.NET\Framework\v3.5\DataSvcUtil.exe" /dataservicecollection /version:2.0 /language:CSharp /out:Northwind.cs /uri:http://localhost:12345/Northwind.svc
    ```

    > [!NOTE]
    >  <span data-ttu-id="fcb99-116">Należy zastąpić wartość dostarczona do `/uri:` parametru za pomocą identyfikatora URI wystąpienia usługi Northwind przykładowych danych.</span><span class="sxs-lookup"><span data-stu-id="fcb99-116">You must replace the value supplied to the `/uri:` parameter with the URI of your instance of the Northwind sample data service.</span></span>

### <a name="to-generate-visual-basic-classes-that-support-data-binding"></a><span data-ttu-id="fcb99-117">Do generowania klasy Visual Basic, które obsługuje powiązanie danych</span><span class="sxs-lookup"><span data-stu-id="fcb99-117">To generate Visual Basic classes that support data binding</span></span>

-   <span data-ttu-id="fcb99-118">W wierszu polecenia Uruchom następujące polecenie bez podziałów wiersza:</span><span class="sxs-lookup"><span data-stu-id="fcb99-118">At the command prompt, execute the following command without line breaks:</span></span>

    ```console
    "%windir%\Microsoft.NET\Framework\v3.5\DataSvcUtil.exe" /dataservicecollection /version:2.0 /language:VB /out:Northwind.vb /uri:http://localhost:12345/Northwind.svc
    ```

    > [!NOTE]
    >  <span data-ttu-id="fcb99-119">Należy zastąpić wartość dostarczona do `/uri:` parametru za pomocą identyfikatora URI wystąpienia usługi Northwind przykładowych danych.</span><span class="sxs-lookup"><span data-stu-id="fcb99-119">You must replace value supplied to the `/uri:` parameter with the URI of your instance of the Northwind sample data service.</span></span>

### <a name="to-generate-c-classes-based-on-the-service-uri"></a><span data-ttu-id="fcb99-120">Można wygenerować klas języka C# oparte na identyfikator URI usługi</span><span class="sxs-lookup"><span data-stu-id="fcb99-120">To generate C# classes based on the service URI</span></span>

-   <span data-ttu-id="fcb99-121">W wierszu polecenia Uruchom następujące polecenie bez podziałów wiersza:</span><span class="sxs-lookup"><span data-stu-id="fcb99-121">At the command prompt, execute the following command without line breaks:</span></span>

    ```
    "%windir%\Microsoft.NET\Framework\v3.5\DataSvcUtil.exe" /language:CSharp /out:northwind.cs /uri:http://localhost:12345/Northwind.svc
    ```

    > [!NOTE]
    >  <span data-ttu-id="fcb99-122">Należy zastąpić wartość dostarczona do `/uri:` parametru za pomocą identyfikatora URI wystąpienia usługi Northwind przykładowych danych.</span><span class="sxs-lookup"><span data-stu-id="fcb99-122">You must replace the value supplied to the `/uri:` parameter with the URI of your instance of the Northwind sample data service.</span></span>

### <a name="to-generate-visual-basic-classes-based-on-the-service-uri"></a><span data-ttu-id="fcb99-123">Do generowania klasy Visual Basic, w oparciu o identyfikator URI usługi</span><span class="sxs-lookup"><span data-stu-id="fcb99-123">To generate Visual Basic classes based on the service URI</span></span>

-   <span data-ttu-id="fcb99-124">W wierszu polecenia Uruchom następujące polecenie bez podziałów wiersza:</span><span class="sxs-lookup"><span data-stu-id="fcb99-124">At the command prompt, execute the following command without line breaks:</span></span>

    ```
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:VB /out:Northwind.vb /uri:http://localhost:12345/Northwind.svc
    ```

    > [!NOTE]
    >  <span data-ttu-id="fcb99-125">Należy zastąpić wartość dostarczona do `/uri:` parametru za pomocą identyfikatora URI wystąpienia usługi Northwind przykładowych danych.</span><span class="sxs-lookup"><span data-stu-id="fcb99-125">You must replace value supplied to the `/uri:` parameter with the URI of your instance of the Northwind sample data service.</span></span>

### <a name="to-generate-c-classes-based-on-the-conceptual-model-file-csdl"></a><span data-ttu-id="fcb99-126">Można wygenerować klas języka C# na podstawie pliku modelu koncepcyjnego (CSDL)</span><span class="sxs-lookup"><span data-stu-id="fcb99-126">To generate C# classes based on the conceptual model file (CSDL)</span></span>

-   <span data-ttu-id="fcb99-127">W wierszu polecenia Uruchom następujące polecenie bez podziałów wiersza:</span><span class="sxs-lookup"><span data-stu-id="fcb99-127">At the command prompt, execute the following command without line breaks:</span></span>

    ```
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:CSharp /in:Northwind.csdl /out:Northwind.cs
    ```

### <a name="to-generate-visual-basic-classes-based-on-the-conceptual-model-file-csdl"></a><span data-ttu-id="fcb99-128">Do generowania klasy Visual Basic na podstawie pliku modelu koncepcyjnego (CSDL)</span><span class="sxs-lookup"><span data-stu-id="fcb99-128">To generate Visual Basic classes based on the conceptual model file (CSDL)</span></span>

-   <span data-ttu-id="fcb99-129">W wierszu polecenia Uruchom następujące polecenie bez podziałów wiersza:</span><span class="sxs-lookup"><span data-stu-id="fcb99-129">At the command prompt, execute the following command without line breaks:</span></span>

    ```
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:VB /in:Northwind.csdl /out:Northwind.vb
    ```

### <a name="to-generate-c-classes-based-on-the-edmx-file"></a><span data-ttu-id="fcb99-130">Można wygenerować klas języka C# na podstawie pliku edmx</span><span class="sxs-lookup"><span data-stu-id="fcb99-130">To generate C# classes based on the .edmx file</span></span>

-   <span data-ttu-id="fcb99-131">W wierszu polecenia Uruchom następujące polecenie bez podziałów wiersza:</span><span class="sxs-lookup"><span data-stu-id="fcb99-131">At the command prompt, execute the following command without line breaks:</span></span>

    ```
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:CSharp /in:Northwind.edmx /out:c:\northwind.cs
    ```

### <a name="to-generate-visual-basic-classes-based-on-the-edmx-file"></a><span data-ttu-id="fcb99-132">Do generowania klasy Visual Basic na podstawie pliku edmx</span><span class="sxs-lookup"><span data-stu-id="fcb99-132">To generate Visual Basic classes based on the .edmx file</span></span>

-   <span data-ttu-id="fcb99-133">W wierszu polecenia Uruchom następujące polecenie bez podziałów wiersza:</span><span class="sxs-lookup"><span data-stu-id="fcb99-133">At the command prompt, execute the following command without line breaks:</span></span>

    ```
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:VB /in:Northwind.edmx /out:c:\northwind.vb
    ```

## <a name="see-also"></a><span data-ttu-id="fcb99-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fcb99-134">See Also</span></span>

- [<span data-ttu-id="fcb99-135">Generowanie biblioteki klienta usługi danych</span><span class="sxs-lookup"><span data-stu-id="fcb99-135">Generating the Data Service Client Library</span></span>](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md)
- [<span data-ttu-id="fcb99-136">Jak: Dodaj odwołanie do usługi danych</span><span class="sxs-lookup"><span data-stu-id="fcb99-136">How to: Add a Data Service Reference</span></span>](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md)
- [<span data-ttu-id="fcb99-137">Narzędzie klienta usługi danych WCF (DataSvcUtil.exe)</span><span class="sxs-lookup"><span data-stu-id="fcb99-137">WCF Data Service Client Utility (DataSvcUtil.exe)</span></span>](../../../../docs/framework/data/wcf/wcf-data-service-client-utility-datasvcutil-exe.md)