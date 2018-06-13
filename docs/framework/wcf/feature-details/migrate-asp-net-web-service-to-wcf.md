---
title: 'Porady: Migrowanie kodu usługi sieci Web ASP.NET do programu Windows Communication Foundation'
ms.date: 03/30/2017
ms.assetid: e528c64f-c027-4f2e-ada6-d8f3994cf8d6
ms.openlocfilehash: 90a6109a56299ec1bcaff4a35141abc194484772
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33496702"
---
# <a name="how-to-migrate-aspnet-web-service-code-to-the-windows-communication-foundation"></a><span data-ttu-id="d42af-102">Porady: Migrowanie kodu usługi sieci Web ASP.NET do programu Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="d42af-102">How to: Migrate ASP.NET Web Service Code to the Windows Communication Foundation</span></span>
<span data-ttu-id="d42af-103">Poniższa procedura zawiera opis sposobu migracji usługi sieci Web ASP.NET do programu Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="d42af-103">The following procedure describes how to migrate an ASP.NET Web Service to Windows Communication Foundation (WCF).</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="d42af-104">Procedura</span><span class="sxs-lookup"><span data-stu-id="d42af-104">Procedure</span></span>  
  
#### <a name="to-migrate-aspnet-web-service-code-to-wcf"></a><span data-ttu-id="d42af-105">Aby przeprowadzić migrację kodu usługi sieci Web ASP.NET do programu WCF</span><span class="sxs-lookup"><span data-stu-id="d42af-105">To migrate ASP.NET Web service code to WCF</span></span>  
  
1.  <span data-ttu-id="d42af-106">Upewnij się, że o zaawansowany zestaw testów istnieje dla usługi.</span><span class="sxs-lookup"><span data-stu-id="d42af-106">Ensure that a comprehensive set of tests exist for the service.</span></span>  
  
2.  <span data-ttu-id="d42af-107">Generowanie języka WSDL, usługi i Zapisz kopię w tym samym folderze co plik .asmx usługi.</span><span class="sxs-lookup"><span data-stu-id="d42af-107">Generate the WSDL for the service and save a copy in the same folder as the service’s .asmx file.</span></span>  
  
3.  <span data-ttu-id="d42af-108">Uaktualnij usługę sieci Web ASP.NET do korzystania z .NET 2.0.</span><span class="sxs-lookup"><span data-stu-id="d42af-108">Upgrade the ASP.NET Web service to use .NET 2.0.</span></span> <span data-ttu-id="d42af-109">Najpierw wdrożyć programu .NET Framework 2.0 do aplikacji w usługach IIS, a następnie użyj programu Visual Studio 2005 można zautomatyzować proces konwersji kodu, zgodnie z opisem w [przewodnik krok po kroku do konwertowania projektów sieci Web z programu Visual Studio .NET 2002/2003 do programu Visual Studio 2005](http://go.microsoft.com/fwlink/?LinkId=96492).</span><span class="sxs-lookup"><span data-stu-id="d42af-109">First deploy the .NET Framework 2.0 to the application in IIS, and then use Visual Studio 2005 to automate the code conversion process, as documented in [Step-By-Step Guide to Converting Web Projects from Visual Studio .NET 2002/2003 to Visual Studio 2005](http://go.microsoft.com/fwlink/?LinkId=96492).</span></span> <span data-ttu-id="d42af-110">Uruchom zestaw testów.</span><span class="sxs-lookup"><span data-stu-id="d42af-110">Run the set of tests.</span></span>  
  
4.  <span data-ttu-id="d42af-111">Podaj wartości jawne `Namespace` i `Name` parametry <xref:System.Web.Services.WebService> atrybuty, jeśli nie są już udostępniane.</span><span class="sxs-lookup"><span data-stu-id="d42af-111">Provide explicit values for the `Namespace` and `Name` parameters of the <xref:System.Web.Services.WebService> attributes if they are not provided already.</span></span> <span data-ttu-id="d42af-112">Tym samym `MessageName` parametr <xref:System.Web.Services.WebMethodAttribute>.</span><span class="sxs-lookup"><span data-stu-id="d42af-112">Do the same for the `MessageName` parameter of the <xref:System.Web.Services.WebMethodAttribute>.</span></span> <span data-ttu-id="d42af-113">Jeśli jawne wartości nie są już podany nagłówki SOAPAction HTTP, przez które żądania są kierowane do metod, a następnie jawnie określić wartość domyślną `Action` parametr <xref:System.Web.Services.Protocols.SoapDocumentMethodAttribute>.</span><span class="sxs-lookup"><span data-stu-id="d42af-113">If explicit values are not already provided for the SOAPAction HTTP headers by which requests are routed to methods, then explicitly specify the default value of the `Action` parameter with a <xref:System.Web.Services.Protocols.SoapDocumentMethodAttribute>.</span></span>  
  
    ```  
    [WebService(Namespace = "http://tempuri.org/", Name = "Adder")]  
    public class Adder  
    {  
         [WebMethod(MessageName = "Add")]  
         [SoapDocumentMethod(Action = "http://tempuri.org/Add")]  
         public double Add(SumInput input)  
         {  
              double sum = 0.00;  
              foreach (double inputValue in input.Input)  
              {  
                  sum += inputValue;  
              }  
          return sum;  
         }  
    }  
    ```  
  
5.  <span data-ttu-id="d42af-114">Testowanie zmian.</span><span class="sxs-lookup"><span data-stu-id="d42af-114">Test the change.</span></span>  
  
6.  <span data-ttu-id="d42af-115">Przenieś wszystkie merytorycznych kod w treści metod klasy do osobnej klasy zgłaszającego oryginalnej klasy do użycia.</span><span class="sxs-lookup"><span data-stu-id="d42af-115">Move any substantive code in the bodies of the methods of the class to a separate class that the original class is made to use.</span></span>  
  
    ```  
    [WebService(Namespace = "http://tempuri.org/", Name = "Adder")]  
    public class Adder  
    {  
         [WebMethod(MessageName = "Add")]  
         [SoapDocumentMethod(Action = "http://tempuri.org/Add")]  
         public double Add(SumInput input)  
         {  
              return new ActualAdder().Add(input);  
         }  
    }  
  
    internal class ActualAdder  
    {  
         internal double Add(SumInput input)  
         {  
              double sum = 0.00;  
              foreach (double inputValue in input.Input)  
              {  
                  sum += inputValue;  
              }  
          return sum;  
         }  
    }  
    ```  
  
7.  <span data-ttu-id="d42af-116">Testowanie zmian.</span><span class="sxs-lookup"><span data-stu-id="d42af-116">Test the change.</span></span>  
  
8.  <span data-ttu-id="d42af-117">Dodaj odwołania do zestawów WCF System.ServiceModel i System.Runtime.Serialization do projektu usługi sieci Web ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="d42af-117">Add references to WCF assemblies System.ServiceModel and System.Runtime.Serialization to the ASP.NET Web service project.</span></span>  
  
9. <span data-ttu-id="d42af-118">Uruchom [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) do generowania klasy klienta WCF z WSDL.</span><span class="sxs-lookup"><span data-stu-id="d42af-118">Run [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to generate a WCF client class from the WSDL.</span></span> <span data-ttu-id="d42af-119">Dodaj moduł wygenerowanej klasy do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="d42af-119">Add the generated class module to the solution.</span></span>  
  
10. <span data-ttu-id="d42af-120">Moduł klasy generowane w poprzednim kroku zawiera definicję interfejsu.</span><span class="sxs-lookup"><span data-stu-id="d42af-120">The class module generated in the preceding step contains the definition of an interface.</span></span>  
  
    ```  
    [System.ServiceModel.ServiceContractAttribute()]  
    public interface AdderSoap  
    {  
         [System.ServiceModel.OperationContractAttribute(  
          Action="http://tempuri.org/Add",   
          ReplyAction="http://tempuri.org/Add")]  
         AddResponse Add(AddRequest request);  
    }  
    ```  
  
     <span data-ttu-id="d42af-121">Dlatego, że klasa jest zdefiniowana jako implementacja interfejsu, jak pokazano w poniższym kodzie próbki, należy zmodyfikować definicję klasy usługi sieci Web ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="d42af-121">Modify the definition of the ASP.NET Web service class so that the class is defined as implementing that interface, as shown in the following sample code.</span></span>  
  
    ```  
    [WebService(Namespace = "http://tempuri.org/", Name = "Adder")]  
    public class Adder: AdderSoap  
    {  
         [WebMethod(MessageName = "Add")]  
         [SoapDocumentMethod(Action = "http://tempuri.org/Add")]  
         public double Add(SumInput input)  
         {  
              return new ActualAdder().Add(input);  
         }  
  
         public AddResponse Add(AddRequest request)  
         {  
            return new AddResponse(  
            new AddResponseBody(  
            this.Add(request.Body.input)));  
         }  
    }  
    ```  
  
11. <span data-ttu-id="d42af-122">Skompiluj projekt.</span><span class="sxs-lookup"><span data-stu-id="d42af-122">Compile the project.</span></span> <span data-ttu-id="d42af-123">Może to być błędy z powodu kod wygenerowany w kroku 9, który zduplikowany niektórych definicji typu.</span><span class="sxs-lookup"><span data-stu-id="d42af-123">There may be some errors due to the code generated in step nine that duplicated some type definitions.</span></span> <span data-ttu-id="d42af-124">Zwykle naprawić te błędy, usuwając istniejące definicje typów.</span><span class="sxs-lookup"><span data-stu-id="d42af-124">Repair those errors, usually by deleting the pre-existing definitions of the types.</span></span> <span data-ttu-id="d42af-125">Testowanie zmian.</span><span class="sxs-lookup"><span data-stu-id="d42af-125">Test the change.</span></span>  
  
12. <span data-ttu-id="d42af-126">Usuń atrybuty specyficzne dla platformy ASP.NET, takich jak <xref:System.Web.Services.WebService>, <xref:System.Web.Services.WebMethodAttribute> i <xref:System.Web.Services.Protocols.SoapDocumentMethodAttribute>.</span><span class="sxs-lookup"><span data-stu-id="d42af-126">Remove the ASP.NET-specific attributes, such as the <xref:System.Web.Services.WebService>, <xref:System.Web.Services.WebMethodAttribute> and <xref:System.Web.Services.Protocols.SoapDocumentMethodAttribute>.</span></span>  
  
    ```  
    public class Adder: AdderSoap  
    {  
         public double Add(SumInput input)  
         {  
              return new ActualAdder().Add(input);  
         }  
  
         public AddResponse Add(AddRequest request)  
         {  
              return new AddResponse(  
             new AddResponseBody(  
            this.Add(request.Body.input)));  
         }  
    }  
    ```  
  
13. <span data-ttu-id="d42af-127">Konfigurowanie klasy, która jest teraz typ usługi WCF, aby wymagać tryb zgodności WCF ASP.NET, jeśli usługa sieci Web ASP.NET polegać na jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="d42af-127">Configure the class, which is now a WCF service type, to require WCF ASP.NET compatibility mode if the ASP.NET Web service relied on any of the following:</span></span>  
  
    -   <span data-ttu-id="d42af-128"><xref:System.Web.HttpContext> Klasy.</span><span class="sxs-lookup"><span data-stu-id="d42af-128">The <xref:System.Web.HttpContext> class.</span></span>  
  
    -   <span data-ttu-id="d42af-129">Profile platformy ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="d42af-129">The ASP.NET Profiles.</span></span>  
  
    -   <span data-ttu-id="d42af-130">Listy ACL plików .asmx.</span><span class="sxs-lookup"><span data-stu-id="d42af-130">ACLs on .asmx files.</span></span>  
  
    -   <span data-ttu-id="d42af-131">Opcje uwierzytelniania usług IIS.</span><span class="sxs-lookup"><span data-stu-id="d42af-131">IIS authentication options.</span></span>  
  
    -   <span data-ttu-id="d42af-132">Opcje personifikacji platformy ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="d42af-132">ASP.NET impersonation options.</span></span>  
  
    -   <span data-ttu-id="d42af-133">Globalizacja platformy ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="d42af-133">ASP.NET globalization.</span></span>  
  
    ```  
    [System.ServiceModel.AspNetCompatibilityRequirements(  
      RequirementsMode=AspNetCompatbilityRequirementsMode.Required)]  
    public class Adder: AdderSoap  
    ```  
  
14. <span data-ttu-id="d42af-134">Nazwy oryginalnego pliku .asmx. asmx.old.</span><span class="sxs-lookup"><span data-stu-id="d42af-134">Rename the original .asmx file to .asmx.old.</span></span>  
  
15. <span data-ttu-id="d42af-135">Tworzenie pliku usługi WCF dla usługi, nadaj mu rozszerzenie, .asmx i zapisz go w katalogu głównym aplikacji w usługach IIS.</span><span class="sxs-lookup"><span data-stu-id="d42af-135">Create a WCF service file for the service, give it the extension, .asmx, and save it into the application root in IIS.</span></span>  
  
    ```xml  
    <%@Service Class="MyOrganization.Adder" %>  
    <%@Assembly Name="MyServiceAssembly" %>   
    ```  
  
16. <span data-ttu-id="d42af-136">Dodaj konfigurację usługi WCF do jego pliku Web.config.</span><span class="sxs-lookup"><span data-stu-id="d42af-136">Add a WCF configuration for the service to its Web.config file.</span></span> <span data-ttu-id="d42af-137">Konfigurowanie usługi do [ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md), używanie usługi pliku z rozszerzeniem .asmx utworzone w poprzednich krokach i aby nie generować WSDL dla siebie, ale umożliwia WSDL z kroku 2.</span><span class="sxs-lookup"><span data-stu-id="d42af-137">Configure the service to use the [\<basicHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md), to use the service file with the .asmx extension created in the preceding steps, and to not generate WSDL for itself, but to use the WSDL from step two.</span></span> <span data-ttu-id="d42af-138">Również jest skonfigurowana do używania trybu zgodności ASP.NET, w razie potrzeby.</span><span class="sxs-lookup"><span data-stu-id="d42af-138">Also configure it to use ASP.NET compatibility mode if necessary.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
     <system.web>  
      <compilation>  
      <buildProviders>  
       <remove extension=".asmx" />  
       <add extension=".asmx"   
        type=  
        "System.ServiceModel.Activation.ServiceBuildProvider,  
        T:System.ServiceModel, Version=2.0.0.0,   
       Culture=neutral,   
       PublicKeyToken=b77a5c561934e089" />  
      </buildProviders>  
      </compilation>  
     </system.web>  
     <system.serviceModel>  
      <services>  
      <service name="MyOrganization.Adder "  
        behaviorConfiguration="AdderBehavior">  
       <endpoint   
        address=""  
        binding="basicHttpBinding"  
        contract="AdderSoap "/>  
       </service>  
      </services>  
      <behaviors>  
      <behavior name="AdderBehavior">  
       <metadataPublishing   
        enableMetadataExchange="true"   
        enableGetWsdl="true"   
        enableHelpPage="true"   
        metadataLocation=  
        "http://MyHost.com/AdderService/Service.WSDL"/>  
      </behavior>  
      </behaviors>  
      <serviceHostingEnvironment   
       aspNetCompatibilityEnabled ="true"/>  
     </system.serviceModel>  
    </configuration>  
    ```  
  
17. <span data-ttu-id="d42af-139">Zapisz konfigurację.</span><span class="sxs-lookup"><span data-stu-id="d42af-139">Save the configuration.</span></span>  
  
18. <span data-ttu-id="d42af-140">Skompiluj projekt.</span><span class="sxs-lookup"><span data-stu-id="d42af-140">Compile the project.</span></span>  
  
19. <span data-ttu-id="d42af-141">Uruchom zestaw testów, upewnij się, że wszystkie zmiany są prawidłowe.</span><span class="sxs-lookup"><span data-stu-id="d42af-141">Run the set of tests to make sure all the changes work.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d42af-142">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d42af-142">See Also</span></span>  
 [<span data-ttu-id="d42af-143">Instrukcje: migrowanie kodu klienta usługi internetowej na platformie ASP.NET do programu Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="d42af-143">How to: Migrate ASP.NET Web Service Client Code to the Windows Communication Foundation</span></span>](../../../../docs/framework/wcf/feature-details/migrate-asp-net-web-service-client-to-wcf.md)
