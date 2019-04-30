---
title: 'Instrukcje: migrowanie usług internetowych obsługujących technologię AJAX i opartych na platformie ASP.NET do programu WCF'
ms.date: 03/30/2017
ms.assetid: 1428df4d-b18f-4e6d-bd4d-79ab3dd5147c
ms.openlocfilehash: 6114fa90b10a5d0cacb60a7ad40f63fae776e174
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61683525"
---
# <a name="how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf"></a><span data-ttu-id="3779e-102">Instrukcje: migrowanie usług internetowych obsługujących technologię AJAX i opartych na platformie ASP.NET do programu WCF</span><span class="sxs-lookup"><span data-stu-id="3779e-102">How to: Migrate AJAX-Enabled ASP.NET Web Services to WCF</span></span>
<span data-ttu-id="3779e-103">W tym temacie opisano procedury migracji podstawowej usługi ASP.NET AJAX do równoważne usługi obsługujące technologie AJAX Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="3779e-103">This topic outlines procedures to migrate a basic ASP.NET AJAX service to an equivalent AJAX-enabled Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="3779e-104">Widoczny jest sposób utworzyć funkcjonalnie równoważne wersję usługi ASP.NET AJAX WCF.</span><span class="sxs-lookup"><span data-stu-id="3779e-104">It shows how to create a functionally equivalent WCF version of an ASP.NET AJAX service.</span></span> <span data-ttu-id="3779e-105">Te dwie usługi mogą następnie służyć obok siebie lub usługi WCF umożliwia zastąpienie usługi ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="3779e-105">The two services can then be used side by side, or the WCF service can be used to replace the ASP.NET AJAX service.</span></span>

 <span data-ttu-id="3779e-106">Migrowanie istniejących technologii ASP.NET AJAX Usługa do usługi WCF w technologii AJAX zapewnia następujące korzyści:</span><span class="sxs-lookup"><span data-stu-id="3779e-106">Migrating an existing ASP.NET AJAX service to a WCF AJAX service gives you the following benefits:</span></span>

- <span data-ttu-id="3779e-107">Usługa AJAX może narazić jako usługę protokołu SOAP z minimalną konfiguracją dodatkowe.</span><span class="sxs-lookup"><span data-stu-id="3779e-107">You can expose your AJAX service as a SOAP service with minimal extra configuration.</span></span>

- <span data-ttu-id="3779e-108">Korzystaj z funkcji usługi WCF, takie jak śledzenie i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="3779e-108">You can benefit from WCF features such as tracing, and so on.</span></span>

 <span data-ttu-id="3779e-109">W poniższych procedurach założono, że używasz programu Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="3779e-109">The following procedures assume that you are using Visual Studio 2012.</span></span>

 <span data-ttu-id="3779e-110">Kod, który jest wynikiem procedury opisane w tym temacie podano w przykładzie zamieszczonym procedur.</span><span class="sxs-lookup"><span data-stu-id="3779e-110">The code that results from the procedures outlined in this topic is provided in the example following the procedures.</span></span>

 <span data-ttu-id="3779e-111">Aby uzyskać więcej informacji na temat udostępniania usługi WCF, za pośrednictwem punktu końcowego z włączoną obsługą technologii AJAX, zobacz [jak: Dodawanie punktu końcowego AJAX ASP.NET przy użyciu konfiguracji](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md) tematu.</span><span class="sxs-lookup"><span data-stu-id="3779e-111">For more information about exposing a WCF service through an AJAX-enabled endpoint, see the [How to: Use Configuration to Add an ASP.NET AJAX Endpoint](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md) topic.</span></span>

### <a name="to-create-and-test-the-aspnet-web-service-application"></a><span data-ttu-id="3779e-112">Do tworzenia i testowania aplikacji usługi sieci Web platformy ASP.NET</span><span class="sxs-lookup"><span data-stu-id="3779e-112">To create and test the ASP.NET Web service application</span></span>

1. <span data-ttu-id="3779e-113">Open Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="3779e-113">Open Visual Studio 2012.</span></span>

2. <span data-ttu-id="3779e-114">Z **pliku** menu, wybierz opcję **nowy**, następnie **projektu**, następnie **Web**, a następnie wybierz pozycję **aplikacji usługi sieci Web platformy ASP.NET** .</span><span class="sxs-lookup"><span data-stu-id="3779e-114">From the **File** menu, select **New**, then **Project**, then **Web**, and then select **ASP.NET Web Service Application**.</span></span>

3. <span data-ttu-id="3779e-115">Nadaj projektowi nazwę `ASPHello` i kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="3779e-115">Name the project `ASPHello` and click **OK**.</span></span>

4. <span data-ttu-id="3779e-116">Usuń znaczniki komentarza w pliku Service1.asmx.cs, który zawiera `System.Web.Script.Services.ScriptService]` umożliwiające AJAX dla tej usługi.</span><span class="sxs-lookup"><span data-stu-id="3779e-116">Uncomment the line in the Service1.asmx.cs file that contains `System.Web.Script.Services.ScriptService]` to enable AJAX for this service.</span></span>

5. <span data-ttu-id="3779e-117">Z **kompilacji** menu, wybierz opcję **Kompiluj rozwiązanie**.</span><span class="sxs-lookup"><span data-stu-id="3779e-117">From the **Build** menu, select **Build Solution**.</span></span>

6. <span data-ttu-id="3779e-118">Z **debugowania** menu, wybierz opcję **Rozpocznij bez debugowania**.</span><span class="sxs-lookup"><span data-stu-id="3779e-118">From the **Debug** menu, select **Start Without Debugging**.</span></span>

7. <span data-ttu-id="3779e-119">Na stronie sieci Web, generowany wybierz `HelloWorld` operacji.</span><span class="sxs-lookup"><span data-stu-id="3779e-119">On the Web page generated, select the `HelloWorld` operation.</span></span>

8. <span data-ttu-id="3779e-120">Kliknij przycisk **Invoke** znajdujący się na `HelloWorld` strony testowej.</span><span class="sxs-lookup"><span data-stu-id="3779e-120">Click the **Invoke** button on the `HelloWorld` test page.</span></span> <span data-ttu-id="3779e-121">Powinny pojawić się następujące odpowiedzi XML.</span><span class="sxs-lookup"><span data-stu-id="3779e-121">You should receive the following XML response.</span></span>

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <string xmlns="http://tempuri.org/">Hello World</string>
    ```

9. <span data-ttu-id="3779e-122">Ta odpowiedź potwierdza, że teraz działa usługa ASP.NET AJAX i, w szczególności, że usługa ma teraz dostępne punktu końcowego w Service1.asmx/HelloWorld, który odpowiada na żądania HTTP POST żądania i zwraca XML.</span><span class="sxs-lookup"><span data-stu-id="3779e-122">This response confirms that you now have a functioning ASP.NET AJAX service and, in particular, that the service has now exposed an endpoint at Service1.asmx/HelloWorld that responds to HTTP POST requests and returns XML.</span></span>

     <span data-ttu-id="3779e-123">Teraz można przystąpić do przekonwertowania tej usługi do używania usługi WCF w technologii AJAX.</span><span class="sxs-lookup"><span data-stu-id="3779e-123">Now you are ready to convert this service to use a WCF AJAX service.</span></span>

### <a name="to-create-an-equivalent-wcf-ajax-service-application"></a><span data-ttu-id="3779e-124">Aby utworzyć aplikację usługi równoważne WCF AJAX</span><span class="sxs-lookup"><span data-stu-id="3779e-124">To create an equivalent WCF AJAX service application</span></span>

1. <span data-ttu-id="3779e-125">Kliknij prawym przyciskiem myszy **ASPHello** projektu, a następnie wybierz **Dodaj**, następnie **nowy element**, a następnie **usługi WCF z włączoną obsługą technologii AJAX**.</span><span class="sxs-lookup"><span data-stu-id="3779e-125">Right-click the **ASPHello** project and select **Add**, then **New Item**, and then **AJAX-enabled WCF Service**.</span></span>

2. <span data-ttu-id="3779e-126">Nazwij usługę `WCFHello` i kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="3779e-126">Name the service `WCFHello` and click **Add**.</span></span>

3. <span data-ttu-id="3779e-127">Otwórz plik WCFHello.svc.cs.</span><span class="sxs-lookup"><span data-stu-id="3779e-127">Open the WCFHello.svc.cs file.</span></span>

4. <span data-ttu-id="3779e-128">Service1.asmx.cs, skopiuj następującą implementacją z `HelloWorld` operacji.</span><span class="sxs-lookup"><span data-stu-id="3779e-128">From Service1.asmx.cs, copy the following implementation of the `HelloWorld` operation.</span></span>

    ```
    public string HelloWorld()
    {
         return "Hello World";
    }
    ```

5. <span data-ttu-id="3779e-129">Wklej skopiowany implementacji `HelloWorld` operacji na pliku WCFHello.svc.cs zamiast następujący kod.</span><span class="sxs-lookup"><span data-stu-id="3779e-129">Paste to copied implementation of the `HelloWorld` operation into the WCFHello.svc.cs file in place of the following code.</span></span>

    ```
    public void DoWork()
    {
          // Add your operation implementation here
          return;
    }
    ```

6. <span data-ttu-id="3779e-130">Określ `Namespace` atrybutu dla <xref:System.ServiceModel.ServiceContractAttribute> jako `WCFHello`.</span><span class="sxs-lookup"><span data-stu-id="3779e-130">Specify the `Namespace` attribute for <xref:System.ServiceModel.ServiceContractAttribute> as `WCFHello`.</span></span>

    ```
    [ServiceContract(Namespace="WCFHello")]
    [AspNetCompatibilityRequirements(RequirementsMode=AspNetCompatibilityRequirementsMode.Required)]
    public class WCFHello
    { … }
    ```

7. <span data-ttu-id="3779e-131">Dodaj <xref:System.ServiceModel.Web.WebInvokeAttribute> do `HelloWorld` operacji i ustaw <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A> właściwości do zwrócenia <xref:System.ServiceModel.Web.WebMessageFormat.Xml>.</span><span class="sxs-lookup"><span data-stu-id="3779e-131">Add the <xref:System.ServiceModel.Web.WebInvokeAttribute> to the `HelloWorld` operation and set the <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A> property to return <xref:System.ServiceModel.Web.WebMessageFormat.Xml>.</span></span> <span data-ttu-id="3779e-132">Należy pamiętać, że jeśli nie jest ustawiony domyślny typ zwracany jest <xref:System.ServiceModel.Web.WebMessageFormat.Json>.</span><span class="sxs-lookup"><span data-stu-id="3779e-132">Note that, if not set, the default return type is <xref:System.ServiceModel.Web.WebMessageFormat.Json>.</span></span>

    ```
    [OperationContract]
    [WebInvoke(ResponseFormat=WebMessageFormat.Xml)]
    public string HelloWorld()
    {
        return "Hello World";
    }
    ```

8. <span data-ttu-id="3779e-133">Z **kompilacji** menu, wybierz opcję **Kompiluj rozwiązanie**.</span><span class="sxs-lookup"><span data-stu-id="3779e-133">From the **Build** menu, select **Build Solution**.</span></span>

9. <span data-ttu-id="3779e-134">Otwórz plik WCFHello.svc i **debugowania** menu, wybierz opcję **Rozpocznij bez debugowania**.</span><span class="sxs-lookup"><span data-stu-id="3779e-134">Open the WCFHello.svc file and from the **Debug** menu, select **Start Without Debugging**.</span></span>

10. <span data-ttu-id="3779e-135">Usługa teraz udostępnia punkt końcowy w `WCFHello.svc/HelloWorld`, który odpowiada na żądania HTTP POST.</span><span class="sxs-lookup"><span data-stu-id="3779e-135">The service now exposes an endpoint at `WCFHello.svc/HelloWorld`, which responds to HTTP POST requests.</span></span> <span data-ttu-id="3779e-136">Nie można przetestować żądań POST protokołu HTTP z przeglądarki, ale XML następujące XML zwracany przez punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="3779e-136">HTTP POST requests cannot be tested from the browser, but the endpoint returns XML following XML.</span></span>

    ```xml
    <string xmlns="http://schemas.microsoft.com/2003/10/Serialization/">Hello World</string>
    ```

11. <span data-ttu-id="3779e-137">`WCFHello.svc/HelloWorld` i `Service1.aspx/HelloWorld` punktów końcowych, teraz są funkcjonalnie równoważne.</span><span class="sxs-lookup"><span data-stu-id="3779e-137">The `WCFHello.svc/HelloWorld` and the `Service1.aspx/HelloWorld` endpoints are now functionally equivalent.</span></span>

## <a name="example"></a><span data-ttu-id="3779e-138">Przykład</span><span class="sxs-lookup"><span data-stu-id="3779e-138">Example</span></span>
 <span data-ttu-id="3779e-139">Kod, który jest wynikiem procedury opisane w tym temacie znajduje się w następującym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="3779e-139">The code that results from the procedures outlined in this topic is provided in the following example.</span></span>

```csharp
//This is the ASP.NET code in the Service1.asmx.cs file.

using System;
using System.Collections;
using System.ComponentModel;
using System.Data;
using System.Linq;
using System.Web;
using System.Web.Services;
using System.Web.Services.Protocols;
using System.Xml.Linq;
using System.Web.Script.Services;

namespace ASPHello
{
    /// <summary>
    /// Summary description for Service1.
    /// </summary>
    [WebService(Namespace = "http://tempuri.org/")]
    [WebServiceBinding(ConformsTo = WsiProfiles.BasicProfile1_1)]
    [ToolboxItem(false)]
    // To allow this Web Service to be called from script, using ASP.NET AJAX, uncomment the following line.
    [System.Web.Script.Services.ScriptService]
    public class Service1 : System.Web.Services.WebService
    {

        [WebMethod]
        public string HelloWorld()
        {
            return "Hello World";
        }
    }
}

//This is the WCF code in the WCFHello.svc.cs file.
using System;
using System.Linq;
using System.Runtime.Serialization;
using System.ServiceModel;
using System.ServiceModel.Activation;
using System.ServiceModel.Web;

namespace ASPHello
{
    [ServiceContract(Namespace = "WCFHello")]
    [AspNetCompatibilityRequirements(RequirementsMode = AspNetCompatibilityRequirementsMode.Allowed)]
    public class WCFHello
    {
        // Add [WebInvoke] attribute to use HTTP GET.
        [OperationContract]
        [WebInvoke(ResponseFormat=WebMessageFormat.Xml)]
        public string HelloWorld()
        {
            return "Hello World";
        }

        // Add more operations here and mark them with [OperationContract].
    }
}
```

 <span data-ttu-id="3779e-140"><xref:System.Xml.XmlDocument> Typ nie jest obsługiwany przez <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> ponieważ nie jest możliwy do serializacji, <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="3779e-140">The <xref:System.Xml.XmlDocument> type is not supported by the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> because it is not serializable by the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="3779e-141">Można użyć dowolnego <xref:System.Xml.Linq.XDocument> wpisz lub serializacji <xref:System.Xml.XmlDocument.DocumentElement%2A> zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="3779e-141">You can use either an <xref:System.Xml.Linq.XDocument> type, or serialize the <xref:System.Xml.XmlDocument.DocumentElement%2A> instead.</span></span>

 <span data-ttu-id="3779e-142">Jeśli usługi sieci Web ASMX uaktualniania i migracji side-by-side do usług WCF, należy unikać mapowanie dwa typy do tej samej nazwie, na komputerze klienckim.</span><span class="sxs-lookup"><span data-stu-id="3779e-142">If ASMX Web services are being upgraded and migrated side-by-side to WCF services, avoid mapping two types to the same name on the client.</span></span> <span data-ttu-id="3779e-143">To powoduje, że wyjątek w serializatory w przypadku używania tego samego typu w <xref:System.Web.Services.WebMethodAttribute> i <xref:System.ServiceModel.ServiceContractAttribute>:</span><span class="sxs-lookup"><span data-stu-id="3779e-143">This causes an exception in serializers if the same type is used in a <xref:System.Web.Services.WebMethodAttribute> and a <xref:System.ServiceModel.ServiceContractAttribute>:</span></span>

- <span data-ttu-id="3779e-144">Jeśli usługa WCF jest dodawany jako pierwsze, wywołania metody usługi sieci Web ASMX powoduje wyjątek w <xref:System.Web.UI.ObjectConverter.ConvertValue%28System.Object%2CSystem.Type%2CSystem.String%29> ponieważ definicji stylu usług WCF zamówienia przez serwer proxy ma pierwszeństwo.</span><span class="sxs-lookup"><span data-stu-id="3779e-144">If WCF service is added first, invoking the method on ASMX Web Service causes exception in <xref:System.Web.UI.ObjectConverter.ConvertValue%28System.Object%2CSystem.Type%2CSystem.String%29> because the WCF style definition of the order in the proxy takes precedence.</span></span>

- <span data-ttu-id="3779e-145">Jeśli usługa sieci Web ASMX zostanie dodany jako pierwsze, wywołanie metody WCF usługi powoduje, że wyjątek w <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> ponieważ definicji stylu usług sieci Web zamówienia przez serwer proxy ma pierwszeństwo.</span><span class="sxs-lookup"><span data-stu-id="3779e-145">If ASMX Web Service is added first, invoking method on WCF service causes exception in <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> because the Web Service style definition of the order in the proxy takes precedence.</span></span>

 <span data-ttu-id="3779e-146">Istnieją między nimi istotne różnice w zachowaniu między <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> i ASP.NET AJAX <xref:System.Web.Script.Serialization.JavaScriptSerializer>.</span><span class="sxs-lookup"><span data-stu-id="3779e-146">There are significant differences in behavior between the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> and the ASP.NET AJAX <xref:System.Web.Script.Serialization.JavaScriptSerializer>.</span></span> <span data-ttu-id="3779e-147">Na przykład <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> reprezentuje słownik jako tablica par klucz wartość, natomiast ASP.NET AJAX <xref:System.Web.Script.Serialization.JavaScriptSerializer> reprezentuje słownik jako rzeczywistych obiektów JSON.</span><span class="sxs-lookup"><span data-stu-id="3779e-147">For example, the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> represents a dictionary as an array of key/value pairs, whereas the ASP.NET AJAX <xref:System.Web.Script.Serialization.JavaScriptSerializer> represents a dictionary as actual JSON objects.</span></span> <span data-ttu-id="3779e-148">Dlatego następujące słownika reprezentowane w technologii ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="3779e-148">So the following is the dictionary represented in ASP.NET AJAX.</span></span>

```
Dictionary<string, int> d = new Dictionary<string, int>();
d.Add("one", 1);
d.Add("two", 2);
```

 <span data-ttu-id="3779e-149">Tego słownika jest reprezentowana w obiekty JSON, jak pokazano na poniższej liście:</span><span class="sxs-lookup"><span data-stu-id="3779e-149">This dictionary is represented in JSON objects as shown in the following list:</span></span>

- <span data-ttu-id="3779e-150">[{"Key": "Jednego", "Value": 1}, {"Key": "Dwóch", "Value": 2}], <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer></span><span class="sxs-lookup"><span data-stu-id="3779e-150">[{"Key":"one","Value":1},{"Key":"two","Value":2}] by the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer></span></span>

- <span data-ttu-id="3779e-151">{"jeden": 1 "dwa": 2}, ASP.NET AJAX <xref:System.Web.Script.Serialization.JavaScriptSerializer></span><span class="sxs-lookup"><span data-stu-id="3779e-151">{"one":1,"two":2} by the ASP.NET AJAX <xref:System.Web.Script.Serialization.JavaScriptSerializer></span></span>

 <span data-ttu-id="3779e-152"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> Jest bardziej skuteczna, w tym sensie, że może obsługiwać słowników gdzie typ klucza nie jest ciągiem, gdy <xref:System.Web.Script.Serialization.JavaScriptSerializer> nie.</span><span class="sxs-lookup"><span data-stu-id="3779e-152">The <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> is more powerful in the sense that it can handle dictionaries where the key type is not string, while the <xref:System.Web.Script.Serialization.JavaScriptSerializer> cannot.</span></span> <span data-ttu-id="3779e-153">Ale nie jest bardziej przyjaznego dla formatu JSON.</span><span class="sxs-lookup"><span data-stu-id="3779e-153">But the latter is more JSON-friendly.</span></span>

 <span data-ttu-id="3779e-154">Znaczne różnice między tymi serializatory podsumowano w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="3779e-154">The significant differences between these serializers are summarized in the following table.</span></span>

|<span data-ttu-id="3779e-155">Kategoria różnice</span><span class="sxs-lookup"><span data-stu-id="3779e-155">Category of Differences</span></span>|<span data-ttu-id="3779e-156">DataContractJsonSerializer</span><span class="sxs-lookup"><span data-stu-id="3779e-156">DataContractJsonSerializer</span></span>|<span data-ttu-id="3779e-157">ASP.NET AJAX JavaScriptSerializer</span><span class="sxs-lookup"><span data-stu-id="3779e-157">ASP.NET AJAX JavaScriptSerializer</span></span>|
|-----------------------------|--------------------------------|---------------------------------------|
|<span data-ttu-id="3779e-158">Podczas deserializacji pusty bufor (nowe byte[0]) do <xref:System.Object> (lub <xref:System.Uri>, lub niektóre inne klasy).</span><span class="sxs-lookup"><span data-stu-id="3779e-158">Deserializing the empty buffer (new byte[0]) into <xref:System.Object> (or <xref:System.Uri>, or some other classes).</span></span>|<span data-ttu-id="3779e-159">SerializationException</span><span class="sxs-lookup"><span data-stu-id="3779e-159">SerializationException</span></span>|<span data-ttu-id="3779e-160">wartość null</span><span class="sxs-lookup"><span data-stu-id="3779e-160">null</span></span>|
|<span data-ttu-id="3779e-161">Serializacja <xref:System.DBNull.Value></span><span class="sxs-lookup"><span data-stu-id="3779e-161">Serialization of <xref:System.DBNull.Value></span></span>|<span data-ttu-id="3779e-162">{} (lub {"__type": "#System"})</span><span class="sxs-lookup"><span data-stu-id="3779e-162">{} (or {"__type":"#System"})</span></span>|<span data-ttu-id="3779e-163">Null</span><span class="sxs-lookup"><span data-stu-id="3779e-163">Null</span></span>|
|<span data-ttu-id="3779e-164">Serializacja prywatnych składowych typów [Serializable].</span><span class="sxs-lookup"><span data-stu-id="3779e-164">Serialization of the private members of [Serializable] types.</span></span>|<span data-ttu-id="3779e-165">serializacji</span><span class="sxs-lookup"><span data-stu-id="3779e-165">serialized</span></span>|<span data-ttu-id="3779e-166">nie serializacji</span><span class="sxs-lookup"><span data-stu-id="3779e-166">not serialized</span></span>|
|<span data-ttu-id="3779e-167">Serializacja publicznymi właściwościami <xref:System.Runtime.Serialization.ISerializable> typów.</span><span class="sxs-lookup"><span data-stu-id="3779e-167">Serialization of the public properties of <xref:System.Runtime.Serialization.ISerializable> types.</span></span>|<span data-ttu-id="3779e-168">nie serializacji</span><span class="sxs-lookup"><span data-stu-id="3779e-168">not serialized</span></span>|<span data-ttu-id="3779e-169">serializacji</span><span class="sxs-lookup"><span data-stu-id="3779e-169">serialized</span></span>|
|<span data-ttu-id="3779e-170">"Rozszerzenia" JSON</span><span class="sxs-lookup"><span data-stu-id="3779e-170">"Extensions" of JSON</span></span>|<span data-ttu-id="3779e-171">Jest zgodna ze specyfikacją formatu JSON, co wymaga cudzysłowów wokół nazwy elementów członkowskich obiektu ({"": "hello"}).</span><span class="sxs-lookup"><span data-stu-id="3779e-171">Adheres to the JSON specification, which requires quotes on object member names ({"a":"hello"}).</span></span>|<span data-ttu-id="3779e-172">Obsługuje nazwy elementów członkowskich obiektu, bez znaków cudzysłowu ({a: "hello"}).</span><span class="sxs-lookup"><span data-stu-id="3779e-172">Supports the names of object members without quotes ({a:"hello"}).</span></span>|
|<span data-ttu-id="3779e-173"><xref:System.DateTime> Uniwersalny czas koordynowany (UTC)</span><span class="sxs-lookup"><span data-stu-id="3779e-173"><xref:System.DateTime> Coordinated Universal Time (UTC)</span></span>|<span data-ttu-id="3779e-174">Nie obsługuje formatu "\\/Date(123456789U)\\/" lub "\\/Date\\(\d+ (U&#124;(\\+\\-[\d{4}]))?\\) \\\\/)".</span><span class="sxs-lookup"><span data-stu-id="3779e-174">Does not support format "\\/Date(123456789U)\\/" or "\\/Date\\(\d+(U&#124;(\\+\\-[\d{4}]))?\\)\\\\/)".</span></span>|<span data-ttu-id="3779e-175">Obsługuje format "\\/Date(123456789U)\\/" i "\\/Date\\(\d+ (U&#124;(\\+\\-[\d{4}]))?\\) \\ \\/) "jako wartości daty/godziny.</span><span class="sxs-lookup"><span data-stu-id="3779e-175">Supports format "\\/Date(123456789U)\\/" and "\\/Date\\(\d+(U&#124;(\\+\\-[\d{4}]))?\\)\\\\/)" as DateTime values.</span></span>|
|<span data-ttu-id="3779e-176">Reprezentacja słowników</span><span class="sxs-lookup"><span data-stu-id="3779e-176">Representation of dictionaries</span></span>|<span data-ttu-id="3779e-177">Tablica KeyValuePair\<K, V >, obsługuje typy kluczy, które nie są ciągami.</span><span class="sxs-lookup"><span data-stu-id="3779e-177">An array of KeyValuePair\<K,V>, handles key types that are not strings.</span></span>|<span data-ttu-id="3779e-178">Jako rzeczywistych obiektów JSON — ale jedyne typy kluczy uchwyty, które są ciągami.</span><span class="sxs-lookup"><span data-stu-id="3779e-178">As actual JSON objects - but only handles key types that are strings.</span></span>|
|<span data-ttu-id="3779e-179">Znaki ucieczki</span><span class="sxs-lookup"><span data-stu-id="3779e-179">Escaped characters</span></span>|<span data-ttu-id="3779e-180">Zawsze za pomocą ucieczki ukośnika (/); nigdy nie umożliwia niezmieniony nieprawidłowe znaki JSON, takich jak "\n".</span><span class="sxs-lookup"><span data-stu-id="3779e-180">Always with an escape forward slash (/); never allows un-escaped invalid JSON characters, such as "\n".</span></span>|<span data-ttu-id="3779e-181">Za pomocą ucieczki ukośnika (/) dla wartości daty/godziny.</span><span class="sxs-lookup"><span data-stu-id="3779e-181">With an escape forward slash (/) for DateTime values.</span></span>|

## <a name="see-also"></a><span data-ttu-id="3779e-182">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3779e-182">See also</span></span>

- [<span data-ttu-id="3779e-183">Instrukcje: Dodawanie punktu końcowego AJAX ASP.NET przy użyciu konfiguracji</span><span class="sxs-lookup"><span data-stu-id="3779e-183">How to: Use Configuration to Add an ASP.NET AJAX Endpoint</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md)
