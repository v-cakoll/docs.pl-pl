---
title: 'Instrukcje: Migrowanie usług sieci Web obsługujących technologię AJAX i opartych na platformie ASP.NET do programu WCF'
ms.date: 03/30/2017
ms.assetid: 1428df4d-b18f-4e6d-bd4d-79ab3dd5147c
ms.openlocfilehash: 60e3088b9075464176c328af1f52676a69c4990f
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976141"
---
# <a name="how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf"></a><span data-ttu-id="05829-102">Instrukcje: Migrowanie usług sieci Web obsługujących technologię AJAX i opartych na platformie ASP.NET do programu WCF</span><span class="sxs-lookup"><span data-stu-id="05829-102">How to: Migrate AJAX-Enabled ASP.NET Web Services to WCF</span></span>
<span data-ttu-id="05829-103">Ten temat zawiera opis procedur migrowania podstawowej usługi ASP.NET AJAX do odpowiedniej usługi Windows Communication Foundation (WCF) z obsługą technologii AJAX.</span><span class="sxs-lookup"><span data-stu-id="05829-103">This topic outlines procedures to migrate a basic ASP.NET AJAX service to an equivalent AJAX-enabled Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="05829-104">Pokazano, jak utworzyć funkcjonalnie odpowiednikową wersję programu WCF usługi ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="05829-104">It shows how to create a functionally equivalent WCF version of an ASP.NET AJAX service.</span></span> <span data-ttu-id="05829-105">Te dwie usługi mogą być następnie używane obok siebie lub można użyć usługi WCF w celu zastąpienia usługi ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="05829-105">The two services can then be used side by side, or the WCF service can be used to replace the ASP.NET AJAX service.</span></span>

 <span data-ttu-id="05829-106">Migrowanie istniejącej usługi ASP.NET AJAX do usługi WCF AJAX zapewnia następujące korzyści:</span><span class="sxs-lookup"><span data-stu-id="05829-106">Migrating an existing ASP.NET AJAX service to a WCF AJAX service gives you the following benefits:</span></span>

- <span data-ttu-id="05829-107">Usługę AJAX można uwidocznić jako usługę SOAP przy minimalnej dodatkowej konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="05829-107">You can expose your AJAX service as a SOAP service with minimal extra configuration.</span></span>

- <span data-ttu-id="05829-108">Można korzystać z funkcji WCF, takich jak śledzenie i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="05829-108">You can benefit from WCF features such as tracing, and so on.</span></span>

 <span data-ttu-id="05829-109">W poniższych procedurach założono, że używasz programu Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="05829-109">The following procedures assume that you are using Visual Studio 2012.</span></span>

 <span data-ttu-id="05829-110">Kod, który wynika z procedur przedstawionych w tym temacie, znajduje się w przykładzie poniżej procedur.</span><span class="sxs-lookup"><span data-stu-id="05829-110">The code that results from the procedures outlined in this topic is provided in the example following the procedures.</span></span>

 <span data-ttu-id="05829-111">Więcej informacji o udostępnianiu usługi WCF za pomocą punktu końcowego z obsługą technologii AJAX można znaleźć w temacie [How to: use Configuration to Add a ASP.NET AJAX Endpoint](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md) .</span><span class="sxs-lookup"><span data-stu-id="05829-111">For more information about exposing a WCF service through an AJAX-enabled endpoint, see the [How to: Use Configuration to Add an ASP.NET AJAX Endpoint](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md) topic.</span></span>

### <a name="to-create-and-test-the-aspnet-web-service-application"></a><span data-ttu-id="05829-112">Aby utworzyć i przetestować aplikację usługi sieci Web ASP.NET</span><span class="sxs-lookup"><span data-stu-id="05829-112">To create and test the ASP.NET Web service application</span></span>

1. <span data-ttu-id="05829-113">Otwórz program Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="05829-113">Open Visual Studio 2012.</span></span>

2. <span data-ttu-id="05829-114">Z menu **plik** wybierz pozycję **Nowy**, a następnie pozycję **projekt**, **a następnie kliknij**pozycję **aplikacja usługi sieci Web ASP.NET**.</span><span class="sxs-lookup"><span data-stu-id="05829-114">From the **File** menu, select **New**, then **Project**, then **Web**, and then select **ASP.NET Web Service Application**.</span></span>

3. <span data-ttu-id="05829-115">Nazwij projekt `ASPHello` a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="05829-115">Name the project `ASPHello` and click **OK**.</span></span>

4. <span data-ttu-id="05829-116">Usuń komentarz z wiersza w pliku Service1.asmx.cs, który zawiera `System.Web.Script.Services.ScriptService]`, aby włączyć technologię AJAX dla tej usługi.</span><span class="sxs-lookup"><span data-stu-id="05829-116">Uncomment the line in the Service1.asmx.cs file that contains `System.Web.Script.Services.ScriptService]` to enable AJAX for this service.</span></span>

5. <span data-ttu-id="05829-117">Z menu **kompilacja** wybierz opcję **Kompiluj rozwiązanie**.</span><span class="sxs-lookup"><span data-stu-id="05829-117">From the **Build** menu, select **Build Solution**.</span></span>

6. <span data-ttu-id="05829-118">Z menu **Debuguj** wybierz polecenie **Uruchom bez debugowania**.</span><span class="sxs-lookup"><span data-stu-id="05829-118">From the **Debug** menu, select **Start Without Debugging**.</span></span>

7. <span data-ttu-id="05829-119">Na wygenerowanej stronie sieci Web Wybierz operację `HelloWorld`.</span><span class="sxs-lookup"><span data-stu-id="05829-119">On the Web page generated, select the `HelloWorld` operation.</span></span>

8. <span data-ttu-id="05829-120">Kliknij przycisk **Wywołaj** na stronie test `HelloWorld`.</span><span class="sxs-lookup"><span data-stu-id="05829-120">Click the **Invoke** button on the `HelloWorld` test page.</span></span> <span data-ttu-id="05829-121">Powinna zostać wyświetlona następująca odpowiedź XML.</span><span class="sxs-lookup"><span data-stu-id="05829-121">You should receive the following XML response.</span></span>

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <string xmlns="http://tempuri.org/">Hello World</string>
    ```

9. <span data-ttu-id="05829-122">Ta odpowiedź potwierdza, że masz już działającą usługę ASP.NET AJAX i, w szczególności, że usługa została teraz uwidoczniona jako punkt końcowy w Service1. asmx/HelloWorld, który reaguje na żądania HTTP POST i zwraca kod XML.</span><span class="sxs-lookup"><span data-stu-id="05829-122">This response confirms that you now have a functioning ASP.NET AJAX service and, in particular, that the service has now exposed an endpoint at Service1.asmx/HelloWorld that responds to HTTP POST requests and returns XML.</span></span>

     <span data-ttu-id="05829-123">Teraz możesz przystąpić do konwersji tej usługi w taki sposób, aby korzystała z usługi WCF AJAX.</span><span class="sxs-lookup"><span data-stu-id="05829-123">Now you are ready to convert this service to use a WCF AJAX service.</span></span>

### <a name="to-create-an-equivalent-wcf-ajax-service-application"></a><span data-ttu-id="05829-124">Aby utworzyć równoważną aplikację usługi WCF AJAX</span><span class="sxs-lookup"><span data-stu-id="05829-124">To create an equivalent WCF AJAX service application</span></span>

1. <span data-ttu-id="05829-125">Kliknij prawym przyciskiem myszy projekt **ASPHello** i wybierz polecenie **Dodaj**, a następnie pozycję **nowy element**, a następnie **usługi WCF z włączoną obsługą technologii AJAX**.</span><span class="sxs-lookup"><span data-stu-id="05829-125">Right-click the **ASPHello** project and select **Add**, then **New Item**, and then **AJAX-enabled WCF Service**.</span></span>

2. <span data-ttu-id="05829-126">Nazwij usługę `WCFHello` a następnie kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="05829-126">Name the service `WCFHello` and click **Add**.</span></span>

3. <span data-ttu-id="05829-127">Otwórz plik WCFHello.svc.cs.</span><span class="sxs-lookup"><span data-stu-id="05829-127">Open the WCFHello.svc.cs file.</span></span>

4. <span data-ttu-id="05829-128">Z Service1.asmx.cs Skopiuj następującą implementację operacji `HelloWorld`.</span><span class="sxs-lookup"><span data-stu-id="05829-128">From Service1.asmx.cs, copy the following implementation of the `HelloWorld` operation.</span></span>

    ```csharp
    public string HelloWorld()
    {
        return "Hello World";
    }
    ```

5. <span data-ttu-id="05829-129">Wklej do skopiowanej implementacji operacji `HelloWorld` do pliku WCFHello.svc.cs zamiast poniższego kodu.</span><span class="sxs-lookup"><span data-stu-id="05829-129">Paste to copied implementation of the `HelloWorld` operation into the WCFHello.svc.cs file in place of the following code.</span></span>

    ```csharp
    public void DoWork()
    {
          // Add your operation implementation here
          return;
    }
    ```

6. <span data-ttu-id="05829-130">Określ `Namespace` atrybut <xref:System.ServiceModel.ServiceContractAttribute> jako `WCFHello`.</span><span class="sxs-lookup"><span data-stu-id="05829-130">Specify the `Namespace` attribute for <xref:System.ServiceModel.ServiceContractAttribute> as `WCFHello`.</span></span>

    ```csharp
    [ServiceContract(Namespace="WCFHello")]
    [AspNetCompatibilityRequirements(RequirementsMode=AspNetCompatibilityRequirementsMode.Required)]
    public class WCFHello
    { … }
    ```

7. <span data-ttu-id="05829-131">Dodaj <xref:System.ServiceModel.Web.WebInvokeAttribute> do operacji `HelloWorld` i ustaw właściwość <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A>, aby zwracała <xref:System.ServiceModel.Web.WebMessageFormat.Xml>.</span><span class="sxs-lookup"><span data-stu-id="05829-131">Add the <xref:System.ServiceModel.Web.WebInvokeAttribute> to the `HelloWorld` operation and set the <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A> property to return <xref:System.ServiceModel.Web.WebMessageFormat.Xml>.</span></span> <span data-ttu-id="05829-132">Należy pamiętać, że jeśli nie zostanie ustawiona, domyślnym typem zwracanym jest <xref:System.ServiceModel.Web.WebMessageFormat.Json>.</span><span class="sxs-lookup"><span data-stu-id="05829-132">Note that, if not set, the default return type is <xref:System.ServiceModel.Web.WebMessageFormat.Json>.</span></span>

    ```csharp
    [OperationContract]
    [WebInvoke(ResponseFormat=WebMessageFormat.Xml)]
    public string HelloWorld()
    {
        return "Hello World";
    }
    ```

8. <span data-ttu-id="05829-133">Z menu **kompilacja** wybierz opcję **Kompiluj rozwiązanie**.</span><span class="sxs-lookup"><span data-stu-id="05829-133">From the **Build** menu, select **Build Solution**.</span></span>

9. <span data-ttu-id="05829-134">Otwórz plik WCFHello. svc i z menu **Debuguj** wybierz polecenie **Start bez debugowania**.</span><span class="sxs-lookup"><span data-stu-id="05829-134">Open the WCFHello.svc file and from the **Debug** menu, select **Start Without Debugging**.</span></span>

10. <span data-ttu-id="05829-135">Usługa udostępnia teraz punkt końcowy o `WCFHello.svc/HelloWorld`, który reaguje na żądania HTTP POST.</span><span class="sxs-lookup"><span data-stu-id="05829-135">The service now exposes an endpoint at `WCFHello.svc/HelloWorld`, which responds to HTTP POST requests.</span></span> <span data-ttu-id="05829-136">Nie można przetestować żądań POST protokołu HTTP z przeglądarki, ale punkt końcowy zwraca kod XML po kodzie XML.</span><span class="sxs-lookup"><span data-stu-id="05829-136">HTTP POST requests cannot be tested from the browser, but the endpoint returns XML following XML.</span></span>

    ```xml
    <string xmlns="http://schemas.microsoft.com/2003/10/Serialization/">Hello World</string>
    ```

11. <span data-ttu-id="05829-137">`WCFHello.svc/HelloWorld` i punkty końcowe `Service1.aspx/HelloWorld` są teraz równoważne funkcjonalnie.</span><span class="sxs-lookup"><span data-stu-id="05829-137">The `WCFHello.svc/HelloWorld` and the `Service1.aspx/HelloWorld` endpoints are now functionally equivalent.</span></span>

## <a name="example"></a><span data-ttu-id="05829-138">Przykład</span><span class="sxs-lookup"><span data-stu-id="05829-138">Example</span></span>
 <span data-ttu-id="05829-139">Kod, który wynika z procedur przedstawionych w tym temacie, znajduje się w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="05829-139">The code that results from the procedures outlined in this topic is provided in the following example.</span></span>

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

 <span data-ttu-id="05829-140">Typ <xref:System.Xml.XmlDocument> nie jest obsługiwany przez <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, ponieważ nie można go serializować przez <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="05829-140">The <xref:System.Xml.XmlDocument> type is not supported by the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> because it is not serializable by the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="05829-141">Zamiast tego można użyć typu <xref:System.Xml.Linq.XDocument> lub serializować <xref:System.Xml.XmlDocument.DocumentElement%2A>.</span><span class="sxs-lookup"><span data-stu-id="05829-141">You can use either an <xref:System.Xml.Linq.XDocument> type, or serialize the <xref:System.Xml.XmlDocument.DocumentElement%2A> instead.</span></span>

 <span data-ttu-id="05829-142">Jeśli usługi sieci Web ASMX są uaktualniane i migrowane obok usług WCF, należy unikać mapowania dwóch typów na taką samą nazwę na kliencie.</span><span class="sxs-lookup"><span data-stu-id="05829-142">If ASMX Web services are being upgraded and migrated side-by-side to WCF services, avoid mapping two types to the same name on the client.</span></span> <span data-ttu-id="05829-143">Powoduje to wyjątek w serializatorach, jeśli ten sam typ jest używany w <xref:System.Web.Services.WebMethodAttribute> i <xref:System.ServiceModel.ServiceContractAttribute>:</span><span class="sxs-lookup"><span data-stu-id="05829-143">This causes an exception in serializers if the same type is used in a <xref:System.Web.Services.WebMethodAttribute> and a <xref:System.ServiceModel.ServiceContractAttribute>:</span></span>

- <span data-ttu-id="05829-144">Jeśli po raz pierwszy zostanie dodana usługa WCF, wywołanie metody w usłudze sieci Web ASMX powoduje wyjątek w <xref:System.Web.UI.ObjectConverter.ConvertValue%28System.Object%2CSystem.Type%2CSystem.String%29>, ponieważ definicja stylu WCF zamówienia na serwerze proxy ma pierwszeństwo.</span><span class="sxs-lookup"><span data-stu-id="05829-144">If WCF service is added first, invoking the method on ASMX Web Service causes exception in <xref:System.Web.UI.ObjectConverter.ConvertValue%28System.Object%2CSystem.Type%2CSystem.String%29> because the WCF style definition of the order in the proxy takes precedence.</span></span>

- <span data-ttu-id="05829-145">Jeśli najpierw zostanie dodana usługa sieci Web ASMX, Metoda wywoływania w usłudze WCF powoduje wyjątek w <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, ponieważ definicja stylu usługi sieci Web zamówienia na serwerze proxy ma pierwszeństwo.</span><span class="sxs-lookup"><span data-stu-id="05829-145">If ASMX Web Service is added first, invoking method on WCF service causes exception in <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> because the Web Service style definition of the order in the proxy takes precedence.</span></span>

 <span data-ttu-id="05829-146">Istnieją znaczne różnice w zachowaniu między <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> i <xref:System.Web.Script.Serialization.JavaScriptSerializer>AJAX ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="05829-146">There are significant differences in behavior between the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> and the ASP.NET AJAX <xref:System.Web.Script.Serialization.JavaScriptSerializer>.</span></span> <span data-ttu-id="05829-147">Na przykład <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> reprezentuje słownik jako tablicę par klucz/wartość, natomiast ASP.NET AJAX <xref:System.Web.Script.Serialization.JavaScriptSerializer> reprezentuje słownik jako rzeczywiste obiekty JSON.</span><span class="sxs-lookup"><span data-stu-id="05829-147">For example, the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> represents a dictionary as an array of key/value pairs, whereas the ASP.NET AJAX <xref:System.Web.Script.Serialization.JavaScriptSerializer> represents a dictionary as actual JSON objects.</span></span> <span data-ttu-id="05829-148">Poniżej znajduje się słownik przedstawiony w ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="05829-148">So the following is the dictionary represented in ASP.NET AJAX.</span></span>

```csharp
Dictionary<string, int> d = new Dictionary<string, int>();
d.Add("one", 1);
d.Add("two", 2);
```

 <span data-ttu-id="05829-149">Ten słownik jest reprezentowany w obiektach JSON, jak pokazano na poniższej liście:</span><span class="sxs-lookup"><span data-stu-id="05829-149">This dictionary is represented in JSON objects as shown in the following list:</span></span>

- <span data-ttu-id="05829-150">[{"Key": "jeden", "value": 1}, {"Key": "dwa", "value": 2}] przez <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer></span><span class="sxs-lookup"><span data-stu-id="05829-150">[{"Key":"one","Value":1},{"Key":"two","Value":2}] by the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer></span></span>

- <span data-ttu-id="05829-151">{"jeden": 1, "dwa": 2} przez ASP.NET AJAX <xref:System.Web.Script.Serialization.JavaScriptSerializer></span><span class="sxs-lookup"><span data-stu-id="05829-151">{"one":1,"two":2} by the ASP.NET AJAX <xref:System.Web.Script.Serialization.JavaScriptSerializer></span></span>

 <span data-ttu-id="05829-152"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> jest bardziej wydajny w sensie, że może obsługiwać słowniki, w których typ klucza nie jest ciągiem, podczas gdy <xref:System.Web.Script.Serialization.JavaScriptSerializer> nie może.</span><span class="sxs-lookup"><span data-stu-id="05829-152">The <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> is more powerful in the sense that it can handle dictionaries where the key type is not string, while the <xref:System.Web.Script.Serialization.JavaScriptSerializer> cannot.</span></span> <span data-ttu-id="05829-153">Jednak ten drugi jest bardziej przyjazny dla kodu JSON.</span><span class="sxs-lookup"><span data-stu-id="05829-153">But the latter is more JSON-friendly.</span></span>

 <span data-ttu-id="05829-154">Znaczące różnice między tymi serializatorami zostały podsumowane w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="05829-154">The significant differences between these serializers are summarized in the following table.</span></span>

|<span data-ttu-id="05829-155">Kategoria różnic</span><span class="sxs-lookup"><span data-stu-id="05829-155">Category of Differences</span></span>|<span data-ttu-id="05829-156">Klasa DataContractJsonSerializer</span><span class="sxs-lookup"><span data-stu-id="05829-156">DataContractJsonSerializer</span></span>|<span data-ttu-id="05829-157">ASP.NET AJAX klasy JavaScriptSerializer</span><span class="sxs-lookup"><span data-stu-id="05829-157">ASP.NET AJAX JavaScriptSerializer</span></span>|
|-----------------------------|--------------------------------|---------------------------------------|
|<span data-ttu-id="05829-158">Deserializacja pustego buforu (nowy bajt [0]) do <xref:System.Object> (lub <xref:System.Uri>lub innych klas).</span><span class="sxs-lookup"><span data-stu-id="05829-158">Deserializing the empty buffer (new byte[0]) into <xref:System.Object> (or <xref:System.Uri>, or some other classes).</span></span>|<span data-ttu-id="05829-159">SerializationException</span><span class="sxs-lookup"><span data-stu-id="05829-159">SerializationException</span></span>|<span data-ttu-id="05829-160">wartość null</span><span class="sxs-lookup"><span data-stu-id="05829-160">null</span></span>|
|<span data-ttu-id="05829-161">Serializacja <xref:System.DBNull.Value></span><span class="sxs-lookup"><span data-stu-id="05829-161">Serialization of <xref:System.DBNull.Value></span></span>|<span data-ttu-id="05829-162">{} (lub {"__type": "#System"})</span><span class="sxs-lookup"><span data-stu-id="05829-162">{} (or {"__type":"#System"})</span></span>|<span data-ttu-id="05829-163">Null</span><span class="sxs-lookup"><span data-stu-id="05829-163">Null</span></span>|
|<span data-ttu-id="05829-164">Serializacja prywatnych składowych typów [Serializable].</span><span class="sxs-lookup"><span data-stu-id="05829-164">Serialization of the private members of [Serializable] types.</span></span>|<span data-ttu-id="05829-165">serializowana</span><span class="sxs-lookup"><span data-stu-id="05829-165">serialized</span></span>|<span data-ttu-id="05829-166">nie Zserializowano</span><span class="sxs-lookup"><span data-stu-id="05829-166">not serialized</span></span>|
|<span data-ttu-id="05829-167">Serializacja właściwości publicznych typów <xref:System.Runtime.Serialization.ISerializable>.</span><span class="sxs-lookup"><span data-stu-id="05829-167">Serialization of the public properties of <xref:System.Runtime.Serialization.ISerializable> types.</span></span>|<span data-ttu-id="05829-168">nie Zserializowano</span><span class="sxs-lookup"><span data-stu-id="05829-168">not serialized</span></span>|<span data-ttu-id="05829-169">serializowana</span><span class="sxs-lookup"><span data-stu-id="05829-169">serialized</span></span>|
|<span data-ttu-id="05829-170">"Rozszerzenia" JSON</span><span class="sxs-lookup"><span data-stu-id="05829-170">"Extensions" of JSON</span></span>|<span data-ttu-id="05829-171">Jest zgodna ze specyfikacją JSON, która wymaga cudzysłowów w nazwach elementów członkowskich obiektu ({"a": "Hello"}).</span><span class="sxs-lookup"><span data-stu-id="05829-171">Adheres to the JSON specification, which requires quotes on object member names ({"a":"hello"}).</span></span>|<span data-ttu-id="05829-172">Obsługuje nazwy elementów członkowskich obiektów bez cudzysłowów ({a: "Hello"}).</span><span class="sxs-lookup"><span data-stu-id="05829-172">Supports the names of object members without quotes ({a:"hello"}).</span></span>|
|<span data-ttu-id="05829-173">Uniwersalny czas koordynowany <xref:System.DateTime> (UTC)</span><span class="sxs-lookup"><span data-stu-id="05829-173"><xref:System.DateTime> Coordinated Universal Time (UTC)</span></span>|<span data-ttu-id="05829-174">Program nie obsługuje formatu "\\/Date (123456789U)\\/" lub "\\/Date\\(\d + (U&#124;(\\+\\-[\d{4}]))?\\)\\\\/) ".</span><span class="sxs-lookup"><span data-stu-id="05829-174">Does not support format "\\/Date(123456789U)\\/" or "\\/Date\\(\d+(U&#124;(\\+\\-[\d{4}]))?\\)\\\\/)".</span></span>|<span data-ttu-id="05829-175">Obsługuje format "\\/Date (123456789U)\\/" i "\\/Date\\(\d + (U&#124;(\\+\\-[\d{4}]))?\\)\\\\/) "jako wartości DateTime.</span><span class="sxs-lookup"><span data-stu-id="05829-175">Supports format "\\/Date(123456789U)\\/" and "\\/Date\\(\d+(U&#124;(\\+\\-[\d{4}]))?\\)\\\\/)" as DateTime values.</span></span>|
|<span data-ttu-id="05829-176">Reprezentacja słowników</span><span class="sxs-lookup"><span data-stu-id="05829-176">Representation of dictionaries</span></span>|<span data-ttu-id="05829-177">Tablica KeyValuePair\<K, V >, obsługuje typy kluczy, które nie są ciągami.</span><span class="sxs-lookup"><span data-stu-id="05829-177">An array of KeyValuePair\<K,V>, handles key types that are not strings.</span></span>|<span data-ttu-id="05829-178">Jako rzeczywiste obiekty JSON — ale obsługuje tylko typy kluczy, które są ciągami.</span><span class="sxs-lookup"><span data-stu-id="05829-178">As actual JSON objects - but only handles key types that are strings.</span></span>|
|<span data-ttu-id="05829-179">Znaki ucieczki</span><span class="sxs-lookup"><span data-stu-id="05829-179">Escaped characters</span></span>|<span data-ttu-id="05829-180">Zawsze z ukośnikiem ucieczki (/); nigdy nie zezwala na anulowanie ucieczki nieprawidłowych znaków JSON, takich jak "\n".</span><span class="sxs-lookup"><span data-stu-id="05829-180">Always with an escape forward slash (/); never allows un-escaped invalid JSON characters, such as "\n".</span></span>|<span data-ttu-id="05829-181">Za pomocą znaku ucieczki (/) dla wartości typu DateTime.</span><span class="sxs-lookup"><span data-stu-id="05829-181">With an escape forward slash (/) for DateTime values.</span></span>|

## <a name="see-also"></a><span data-ttu-id="05829-182">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="05829-182">See also</span></span>

- [<span data-ttu-id="05829-183">Instrukcje: dodawanie punktu końcowego AJAX ASP.NET przy użyciu konfiguracji</span><span class="sxs-lookup"><span data-stu-id="05829-183">How to: Use Configuration to Add an ASP.NET AJAX Endpoint</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md)
