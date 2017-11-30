---
title: "Porady: Migrowanie kodu usługi sieci Web ASP.NET do programu Windows Communication Foundation"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e528c64f-c027-4f2e-ada6-d8f3994cf8d6
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 94d6cc499caddc8b3cbbf8ba7845e4de5441165c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-migrate-aspnet-web-service-code-to-the-windows-communication-foundation"></a>Porady: Migrowanie kodu usługi sieci Web ASP.NET do programu Windows Communication Foundation
W poniższej procedurze opisano sposób migracji usługi sieci Web ASP.NET do [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].  
  
## <a name="procedure"></a>Procedura  
  
#### <a name="to-migrate-aspnet-web-service-code-to-wcf"></a>Aby przeprowadzić migrację kodu usługi sieci Web ASP.NET do programu WCF  
  
1.  Upewnij się, że o zaawansowany zestaw testów istnieje dla usługi.  
  
2.  Generowanie języka WSDL, usługi i Zapisz kopię w tym samym folderze co plik .asmx usługi.  
  
3.  Uaktualnij usługę sieci Web ASP.NET do korzystania z .NET 2.0. Najpierw wdrożyć programu .NET Framework 2.0 do aplikacji w usługach IIS, a następnie użyj programu Visual Studio 2005 można zautomatyzować proces konwersji kodu, zgodnie z opisem w [przewodnik krok po kroku do konwertowania projektów sieci Web z programu Visual Studio .NET 2002/2003 do programu Visual Studio 2005](http://go.microsoft.com/fwlink/?LinkId=96492). Uruchom zestaw testów.  
  
4.  Podaj wartości jawne `Namespace` i `Name` parametry <xref:System.Web.Services.WebService> atrybuty, jeśli nie są już udostępniane. Tym samym `MessageName` parametr <xref:System.Web.Services.WebMethodAttribute>. Jeśli jawne wartości nie są już podany nagłówki SOAPAction HTTP, przez które żądania są kierowane do metod, a następnie jawnie określić wartość domyślną `Action` parametr <xref:System.Web.Services.Protocols.SoapDocumentMethodAttribute>.  
  
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
  
5.  Testowanie zmian.  
  
6.  Przenieś wszystkie merytorycznych kod w treści metod klasy do osobnej klasy zgłaszającego oryginalnej klasy do użycia.  
  
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
  
7.  Testowanie zmian.  
  
8.  Dodaj odwołania do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zestawów System.ServiceModel i System.Runtime.Serialization do projektu usługi sieci Web ASP.NET.  
  
9. Uruchom [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) do generowania [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klasy klienta w formacie WSDL. Dodaj moduł wygenerowanej klasy do rozwiązania.  
  
10. Moduł klasy generowane w poprzednim kroku zawiera definicję interfejsu.  
  
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
  
     Dlatego, że klasa jest zdefiniowana jako implementacja interfejsu, jak pokazano w poniższym kodzie próbki, należy zmodyfikować definicję klasy usługi sieci Web ASP.NET.  
  
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
  
11. Skompiluj projekt. Może to być błędy z powodu kod wygenerowany w kroku 9, który zduplikowany niektórych definicji typu. Zwykle naprawić te błędy, usuwając istniejące definicje typów. Testowanie zmian.  
  
12. Usuń atrybuty specyficzne dla platformy ASP.NET, takich jak <xref:System.Web.Services.WebService>, <xref:System.Web.Services.WebMethodAttribute> i <xref:System.Web.Services.Protocols.SoapDocumentMethodAttribute>.  
  
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
  
13. Konfigurowanie klasy, która jest teraz [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] typ, aby wymagać usługi [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] tryb zgodności ASP.NET, jeśli usługa sieci Web ASP.NET zależał od następujących:  
  
    -   <xref:System.Web.HttpContext> Klasy.  
  
    -   Profile platformy ASP.NET.  
  
    -   Listy ACL plików .asmx.  
  
    -   Opcje uwierzytelniania usług IIS.  
  
    -   Opcje personifikacji platformy ASP.NET.  
  
    -   Globalizacja platformy ASP.NET.  
  
    ```  
    [System.ServiceModel.AspNetCompatibilityRequirements(  
      RequirementsMode=AspNetCompatbilityRequirementsMode.Required)]  
    public class Adder: AdderSoap  
    ```  
  
14. Nazwy oryginalnego pliku .asmx. asmx.old.  
  
15. Utwórz [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi plików dla usługi, nadaj mu rozszerzenie, .asmx i zapisz go w katalogu głównym aplikacji w usługach IIS.  
  
    ```xml  
    <%@Service Class="MyOrganization.Adder" %>  
    <%@Assembly Name="MyServiceAssembly" %>   
    ```  
  
16. Dodaj [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] konfiguracji dla usługi do jego pliku Web.config. Konfigurowanie usługi do [ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md), używanie usługi pliku z rozszerzeniem .asmx utworzone w poprzednich krokach i aby nie generować WSDL dla siebie, ale umożliwia WSDL z kroku 2. Również jest skonfigurowana do używania trybu zgodności ASP.NET, w razie potrzeby.  
  
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
  
17. Zapisz konfigurację.  
  
18. Skompiluj projekt.  
  
19. Uruchom zestaw testów, upewnij się, że wszystkie zmiany są prawidłowe.  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: Migrowanie kodu klienta usługi sieci Web ASP.NET do programu Windows Communication Foundation](../../../../docs/framework/wcf/feature-details/migrate-asp-net-web-service-client-to-wcf.md)
