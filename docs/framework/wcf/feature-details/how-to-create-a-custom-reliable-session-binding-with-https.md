---
title: 'Instrukcje: tworzenie niestandardowych wiązań niezawodnej sesji za pomocą protokołu HTTPS'
ms.date: 03/30/2017
ms.assetid: fa772232-da1f-4c66-8c94-e36c0584b549
ms.openlocfilehash: 70f8f4f33626ab0d1705e03750bfd9baa324e60a
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598999"
---
# <a name="how-to-create-a-custom-reliable-session-binding-with-https"></a><span data-ttu-id="e3710-102">Instrukcje: tworzenie niestandardowych wiązań niezawodnej sesji za pomocą protokołu HTTPS</span><span class="sxs-lookup"><span data-stu-id="e3710-102">How to: Create a Custom Reliable Session Binding with HTTPS</span></span>

<span data-ttu-id="e3710-103">W tym temacie przedstawiono sposób korzystania z zabezpieczeń transportu SSL (SSL) z niezawodnymi sesjami.</span><span class="sxs-lookup"><span data-stu-id="e3710-103">This topic demonstrates the use of Secure Sockets Layer (SSL) transport security with reliable sessions.</span></span> <span data-ttu-id="e3710-104">Aby używać niezawodnej sesji za pośrednictwem protokołu HTTPS, należy utworzyć niestandardowe powiązanie, które korzysta z niezawodnej sesji i transportu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="e3710-104">To use a reliable session over HTTPS, you must create a custom binding that uses a reliable session and the HTTPS transport.</span></span> <span data-ttu-id="e3710-105">Niezawodne sesje można wykonać samodzielnie za pomocą kodu lub deklaratywnie w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="e3710-105">You enable the reliable session either imperatively by using code or declaratively in the configuration file.</span></span> <span data-ttu-id="e3710-106">Ta procedura powoduje użycie plików konfiguracji klienta i usługi w celu włączenia niezawodnej sesji i [**\<httpsTransport>**](../../configure-apps/file-schema/wcf/httpstransport.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="e3710-106">This procedure uses the client and service configuration files to enable the reliable session and the [**\<httpsTransport>**](../../configure-apps/file-schema/wcf/httpstransport.md) element.</span></span>

<span data-ttu-id="e3710-107">Kluczową częścią tej procedury jest to, że **\<endpoint>** element Configuration zawiera `bindingConfiguration` atrybut odwołujący się do konfiguracji niestandardowego powiązania o nazwie `reliableSessionOverHttps` .</span><span class="sxs-lookup"><span data-stu-id="e3710-107">The key part of this procedure is that the **\<endpoint>** configuration element contain a `bindingConfiguration` attribute that references a custom binding configuration named `reliableSessionOverHttps`.</span></span> <span data-ttu-id="e3710-108">[**\<binding>**](../../configure-apps/file-schema/wcf/bindings.md)Element konfiguracji odwołuje się do tej nazwy, aby określić, że Niezawodna sesja i transport HTTPS są używane przez włączenie **\<reliableSession>** **\<httpsTransport>** elementów i.</span><span class="sxs-lookup"><span data-stu-id="e3710-108">The [**\<binding>**](../../configure-apps/file-schema/wcf/bindings.md) configuration element references this name to specify that a reliable session and the HTTPS transport are used by including **\<reliableSession>** and **\<httpsTransport>** elements.</span></span>

<span data-ttu-id="e3710-109">Aby uzyskać kopię źródła tego przykładu, zobacz [niestandardowe powiązania niezawodnej sesji za pośrednictwem protokołu HTTPS](../samples/custom-binding-reliable-session-over-https.md).</span><span class="sxs-lookup"><span data-stu-id="e3710-109">For the source copy of this example, see [Custom Binding Reliable Session over HTTPS](../samples/custom-binding-reliable-session-over-https.md).</span></span>

### <a name="configure-the-service-with-a-custombinding-to-use-a-reliable-session-with-https"></a><span data-ttu-id="e3710-110">Konfigurowanie usługi z niestandardową do korzystania z niezawodnej sesji z protokołem HTTPS</span><span class="sxs-lookup"><span data-stu-id="e3710-110">Configure the service with a CustomBinding to use a reliable session with HTTPS</span></span>

1. <span data-ttu-id="e3710-111">Zdefiniuj kontrakt usługi dla typu usługi.</span><span class="sxs-lookup"><span data-stu-id="e3710-111">Define a service contract for the type of service.</span></span>

   [!code-csharp[c_HowTo_CreateReliableSessionHTTPS#1121](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/service.cs#1121)]

1. <span data-ttu-id="e3710-112">Zaimplementuj kontrakt usługi w klasie usługi.</span><span class="sxs-lookup"><span data-stu-id="e3710-112">Implement the service contract in a service class.</span></span> <span data-ttu-id="e3710-113">Należy zauważyć, że adres lub informacje o powiązaniu nie są określone w implementacji usługi.</span><span class="sxs-lookup"><span data-stu-id="e3710-113">Note that the address or binding information isn't specified inside the implementation of the service.</span></span> <span data-ttu-id="e3710-114">Nie trzeba pisać kodu w celu pobrania adresu lub informacji o powiązaniu z pliku konfiguracyjnego.</span><span class="sxs-lookup"><span data-stu-id="e3710-114">You aren't required to write code to retrieve the address or binding information from the configuration file.</span></span>

   [!code-csharp[c_HowTo_CreateReliableSessionHTTPS#1122](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/service.cs#1122)]

1. <span data-ttu-id="e3710-115">Utwórz plik *Web. config* w celu skonfigurowania punktu końcowego dla `CalculatorService` niestandardowego powiązania o nazwie `reliableSessionOverHttps` , który używa niezawodnej sesji i transportu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="e3710-115">Create a *Web.config* file to configure an endpoint for the `CalculatorService` with a custom binding named `reliableSessionOverHttps` that uses a reliable session and the HTTPS transport.</span></span>

   [!code-xml[c_HowTo_CreateReliableSessionHTTPS#2111](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/common/web.config#2111)]

1. <span data-ttu-id="e3710-116">Utwórz plik *usługi SVC* , który zawiera wiersz:</span><span class="sxs-lookup"><span data-stu-id="e3710-116">Create a *Service.svc* file that contains the line:</span></span>

   `<%@ServiceHost language=c# Service="CalculatorService" %>`

1. <span data-ttu-id="e3710-117">Umieść plik *Service. svc* w katalogu wirtualnym Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="e3710-117">Place the *Service.svc* file in your Internet Information Services (IIS) virtual directory.</span></span>

### <a name="configure-the-client-with-a-custombinding-to-use-a-reliable-session-with-https"></a><span data-ttu-id="e3710-118">Konfigurowanie klienta z niestandardową do korzystania z niezawodnej sesji z protokołem HTTPS</span><span class="sxs-lookup"><span data-stu-id="e3710-118">Configure the client with a CustomBinding to use a reliable session with HTTPS</span></span>

1. <span data-ttu-id="e3710-119">Użyj [Narzędzia metadanych ServiceModel (*Svcutil. exe*)](../servicemodel-metadata-utility-tool-svcutil-exe.md) z wiersza polecenia, aby wygenerować kod na podstawie metadanych usługi.</span><span class="sxs-lookup"><span data-stu-id="e3710-119">Use the [ServiceModel Metadata Utility Tool (*Svcutil.exe*)](../servicemodel-metadata-utility-tool-svcutil-exe.md) from the command line to generate code from service metadata.</span></span>

   ```console
   Svcutil.exe <Metadata Exchange (MEX) address or HTTP GET address>
   ```

1. <span data-ttu-id="e3710-120">Wygenerowany klient zawiera `ICalculator` interfejs, który definiuje kontrakt usługi, który musi spełniać implementacja klienta.</span><span class="sxs-lookup"><span data-stu-id="e3710-120">The client that's generated contains the `ICalculator` interface that defines the service contract that the client implementation must satisfy.</span></span>

   [!code-csharp[C_HowTo_CreateReliableSessionHTTPS#1221](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/client.cs#1221)]

1. <span data-ttu-id="e3710-121">Wygenerowana aplikacja kliencka zawiera również implementację programu `ClientCalculator` .</span><span class="sxs-lookup"><span data-stu-id="e3710-121">The generated client application also contains the implementation of the `ClientCalculator`.</span></span> <span data-ttu-id="e3710-122">Należy zauważyć, że adres i informacje o powiązaniu nie są określone w implementacji usługi.</span><span class="sxs-lookup"><span data-stu-id="e3710-122">Note that the address and binding information isn't specified inside the implementation of the service.</span></span> <span data-ttu-id="e3710-123">Nie trzeba pisać kodu w celu pobrania informacji o adresie i powiązaniu z pliku konfiguracyjnego.</span><span class="sxs-lookup"><span data-stu-id="e3710-123">You aren't required to write code to retrieve the address and binding information from the configuration file.</span></span>

   [!code-csharp[C_HowTo_CreateReliableSessionHTTPS#1222](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/client.cs#1222)]

1. <span data-ttu-id="e3710-124">Skonfiguruj niestandardowe powiązanie o nazwie `reliableSessionOverHttps` do korzystania z transportu HTTPS i sesji niezawodnych.</span><span class="sxs-lookup"><span data-stu-id="e3710-124">Configure a custom binding named `reliableSessionOverHttps` to use the HTTPS transport and reliable sessions.</span></span>

   [!code-xml[C_HowTo_CreateReliableSessionHTTPS#2211](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/common/app.config#2211)]

1. <span data-ttu-id="e3710-125">Utwórz wystąpienie elementu `ClientCalculator` w aplikacji, a następnie Wywołaj operacje usługi.</span><span class="sxs-lookup"><span data-stu-id="e3710-125">Create an instance of the `ClientCalculator` in an application and then call the service operations.</span></span>

   [!code-csharp[C_HowTo_CreateReliableSessionHTTPS#1223](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/client.cs#1223)]

1. <span data-ttu-id="e3710-126">Kompiluj i uruchom klienta.</span><span class="sxs-lookup"><span data-stu-id="e3710-126">Compile and run the client.</span></span>  

## <a name="net-framework-security"></a><span data-ttu-id="e3710-127">zabezpieczenia .NET Framework</span><span class="sxs-lookup"><span data-stu-id="e3710-127">.NET Framework security</span></span>

<span data-ttu-id="e3710-128">Ponieważ certyfikat używany w tym przykładzie jest certyfikatem testowym utworzonym za pomocą *Makecert. exe*, podczas próby uzyskania dostępu do adresu https, takiego jak `https://localhost/servicemodelsamples/service.svc` , z przeglądarki, pojawia się Alert zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="e3710-128">Because the certificate used in this sample is a test certificate created with *Makecert.exe*, a security alert appears when you try to access an HTTPS address, such as `https://localhost/servicemodelsamples/service.svc`, from your browser.</span></span>

## <a name="see-also"></a><span data-ttu-id="e3710-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e3710-129">See also</span></span>

- [<span data-ttu-id="e3710-130">Niezawodne sesje</span><span class="sxs-lookup"><span data-stu-id="e3710-130">Reliable Sessions</span></span>](reliable-sessions.md)
