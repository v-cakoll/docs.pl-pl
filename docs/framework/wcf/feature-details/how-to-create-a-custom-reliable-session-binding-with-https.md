---
title: 'Porady: tworzenie powiązania niestandardowego niezawodnej sesji z protokołu HTTPS'
ms.date: 03/30/2017
ms.assetid: fa772232-da1f-4c66-8c94-e36c0584b549
ms.openlocfilehash: b3699593f783fff1227ec51194956e0cc8577dd8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33492765"
---
# <a name="how-to-create-a-custom-reliable-session-binding-with-https"></a><span data-ttu-id="6129e-102">Porady: tworzenie powiązania niestandardowego niezawodnej sesji z protokołu HTTPS</span><span class="sxs-lookup"><span data-stu-id="6129e-102">How to: Create a Custom Reliable Session Binding with HTTPS</span></span>

<span data-ttu-id="6129e-103">W tym temacie przedstawiono użycie zabezpieczeń transportu Secure Sockets Layer (SSL) z sesji niezawodnej.</span><span class="sxs-lookup"><span data-stu-id="6129e-103">This topic demonstrates the use of Secure Sockets Layer (SSL) transport security with reliable sessions.</span></span> <span data-ttu-id="6129e-104">Aby użyć niezawodnej sesji przez protokół HTTPS, należy utworzyć niestandardowego powiązania, który używa niezawodnej sesji i transportu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="6129e-104">To use a reliable session over HTTPS, you must create a custom binding that uses a reliable session and the HTTPS transport.</span></span> <span data-ttu-id="6129e-105">Możesz włączyć niezawodnej sesji imperatively przy użyciu kodu lub deklaratywnie w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="6129e-105">You enable the reliable session either imperatively by using code or declaratively in the configuration file.</span></span> <span data-ttu-id="6129e-106">Ta procedura używa plików konfiguracji klienta i usługi, aby umożliwić niezawodnej sesji i [  **\<httpsTransport >** ](../../../../docs/framework/configure-apps/file-schema/wcf/httpstransport.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="6129e-106">This procedure uses the client and service configuration files to enable the reliable session and the [**\<httpsTransport>**](../../../../docs/framework/configure-apps/file-schema/wcf/httpstransport.md) element.</span></span>

<span data-ttu-id="6129e-107">Część klucza tej procedury jest to, że  **\<punktu końcowego >** element konfiguracji zawiera `bindingConfiguration` atrybut, który odwołuje się do konfiguracji niestandardowego powiązania o nazwie `reliableSessionOverHttps`.</span><span class="sxs-lookup"><span data-stu-id="6129e-107">The key part of this procedure is that the **\<endpoint>** configuration element contain a `bindingConfiguration` attribute that references a custom binding configuration named `reliableSessionOverHttps`.</span></span> <span data-ttu-id="6129e-108">[  **\<Powiązania >** ](../../../../docs/framework/misc/binding.md) element konfiguracji odwołuje się do tej nazwy, aby określić, że niezawodnej sesji i transportu HTTPS są używane przez dołączenie  **\< reliableSession >** i  **\<httpsTransport >** elementów.</span><span class="sxs-lookup"><span data-stu-id="6129e-108">The [**\<binding>**](../../../../docs/framework/misc/binding.md) configuration element references this name to specify that a reliable session and the HTTPS transport are used by including **\<reliableSession>** and **\<httpsTransport>** elements.</span></span>

<span data-ttu-id="6129e-109">Dla źródła kopię w tym przykładzie [niestandardowe powiązanie niezawodnej sesji przez protokół HTTPS](../../../../docs/framework/wcf/samples/custom-binding-reliable-session-over-https.md).</span><span class="sxs-lookup"><span data-stu-id="6129e-109">For the source copy of this example, see [Custom Binding Reliable Session over HTTPS](../../../../docs/framework/wcf/samples/custom-binding-reliable-session-over-https.md).</span></span>

### <a name="configure-the-service-with-a-custombinding-to-use-a-reliable-session-with-https"></a><span data-ttu-id="6129e-110">Skonfiguruj usługę z CustomBinding do niezawodnej sesji za pomocą protokołu HTTPS</span><span class="sxs-lookup"><span data-stu-id="6129e-110">Configure the service with a CustomBinding to use a reliable session with HTTPS</span></span>

1. <span data-ttu-id="6129e-111">Definiowanie kontraktu usługi dla typu usługi.</span><span class="sxs-lookup"><span data-stu-id="6129e-111">Define a service contract for the type of service.</span></span>

   [!code-csharp[c_HowTo_CreateReliableSessionHTTPS#1121](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/service.cs#1121)]

1. <span data-ttu-id="6129e-112">Implementowanie kontraktu usługi w klasie usługi.</span><span class="sxs-lookup"><span data-stu-id="6129e-112">Implement the service contract in a service class.</span></span> <span data-ttu-id="6129e-113">Należy pamiętać, że informacje powiązania lub adres nie jest określona wewnątrz implementacji usługi.</span><span class="sxs-lookup"><span data-stu-id="6129e-113">Note that the address or binding information isn't specified inside the implementation of the service.</span></span> <span data-ttu-id="6129e-114">Nie są wymagane do pisania kodu, które można pobrać informacji o adresie lub powiązanie z pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="6129e-114">You aren't required to write code to retrieve the address or binding information from the configuration file.</span></span>

   [!code-csharp[c_HowTo_CreateReliableSessionHTTPS#1122](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/service.cs#1122)]

1. <span data-ttu-id="6129e-115">Utwórz *Web.config* pliku do konfigurowania punktu końcowego dla `CalculatorService` z niestandardowego powiązania o nazwie `reliableSessionOverHttps` używającą transportu HTTPS i niezawodnej sesji.</span><span class="sxs-lookup"><span data-stu-id="6129e-115">Create a *Web.config* file to configure an endpoint for the `CalculatorService` with a custom binding named `reliableSessionOverHttps` that uses a reliable session and the HTTPS transport.</span></span>

   [!code-xml[c_HowTo_CreateReliableSessionHTTPS#2111](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/common/web.config#2111)]

1. <span data-ttu-id="6129e-116">Utwórz *Service.svc* pliku, który zawiera wiersz:</span><span class="sxs-lookup"><span data-stu-id="6129e-116">Create a *Service.svc* file that contains the line:</span></span>

   ```
   <%@ServiceHost language=c# Service="CalculatorService" %>
   ```

1. <span data-ttu-id="6129e-117">Miejsce *Service.svc* pliku w katalogu wirtualnym programu Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="6129e-117">Place the *Service.svc* file in your Internet Information Services (IIS) virtual directory.</span></span>

### <a name="configure-the-client-with-a-custombinding-to-use-a-reliable-session-with-https"></a><span data-ttu-id="6129e-118">Konfigurowanie klienta z CustomBinding do niezawodnej sesji za pomocą protokołu HTTPS</span><span class="sxs-lookup"><span data-stu-id="6129e-118">Configure the client with a CustomBinding to use a reliable session with HTTPS</span></span>

1. <span data-ttu-id="6129e-119">Użyj [narzędzie do obsługi metadanych elementu ServiceModel (*Svcutil.exe*)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) z poziomu wiersza polecenia, aby wygenerować kod na podstawie metadanych usługi.</span><span class="sxs-lookup"><span data-stu-id="6129e-119">Use the [ServiceModel Metadata Utility Tool (*Svcutil.exe*)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) from the command line to generate code from service metadata.</span></span>

   ```console
   Svcutil.exe <Metadata Exchange (MEX) address or HTTP GET address>
   ```

1. <span data-ttu-id="6129e-120">Klient, który jest generowany zawiera `ICalculator` Interfejs definiujący kontrakt usługi, które muszą spełniać implementacja klienta.</span><span class="sxs-lookup"><span data-stu-id="6129e-120">The client that's generated contains the `ICalculator` interface that defines the service contract that the client implementation must satisfy.</span></span>

   [!code-csharp[C_HowTo_CreateReliableSessionHTTPS#1221](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/client.cs#1221)]

1. <span data-ttu-id="6129e-121">Aplikacja wygenerowanego klienta zawiera również implementacja `ClientCalculator`.</span><span class="sxs-lookup"><span data-stu-id="6129e-121">The generated client application also contains the implementation of the `ClientCalculator`.</span></span> <span data-ttu-id="6129e-122">Należy pamiętać, że informacje adres i powiązanie nie jest określona wewnątrz implementacji usługi.</span><span class="sxs-lookup"><span data-stu-id="6129e-122">Note that the address and binding information isn't specified inside the implementation of the service.</span></span> <span data-ttu-id="6129e-123">Nie są wymagane do pisania kodu, aby pobrać informacje adres i powiązanie z pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="6129e-123">You aren't required to write code to retrieve the address and binding information from the configuration file.</span></span>

   [!code-csharp[C_HowTo_CreateReliableSessionHTTPS#1222](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/client.cs#1222)]

1. <span data-ttu-id="6129e-124">Konfigurowanie niestandardowego powiązania o nazwie `reliableSessionOverHttps` korzystać z transportu HTTPS i niezawodnej sesji.</span><span class="sxs-lookup"><span data-stu-id="6129e-124">Configure a custom binding named `reliableSessionOverHttps` to use the HTTPS transport and reliable sessions.</span></span>

   [!code-xml[C_HowTo_CreateReliableSessionHTTPS#2211](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/common/app.config#2211)]

1. <span data-ttu-id="6129e-125">Utwórz wystąpienie `ClientCalculator` w aplikacji, a następnie wywołać operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="6129e-125">Create an instance of the `ClientCalculator` in an application and then call the service operations.</span></span>

   [!code-csharp[C_HowTo_CreateReliableSessionHTTPS#1223](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/client.cs#1223)]

1. <span data-ttu-id="6129e-126">Kompilowanie i uruchamianie klienta.</span><span class="sxs-lookup"><span data-stu-id="6129e-126">Compile and run the client.</span></span>  

## <a name="net-framework-security"></a><span data-ttu-id="6129e-127">zabezpieczenia .NET Framework</span><span class="sxs-lookup"><span data-stu-id="6129e-127">.NET Framework security</span></span>

<span data-ttu-id="6129e-128">Ponieważ certyfikat użyty w tym przykładzie jest utworzone za pomocą certyfikatu testowego *Makecert.exe*, alert zabezpieczeń zostanie wyświetlony podczas próby dostępu adres HTTPS, takich jak `https://localhost/servicemodelsamples/service.svc`, w przeglądarce.</span><span class="sxs-lookup"><span data-stu-id="6129e-128">Because the certificate used in this sample is a test certificate created with *Makecert.exe*, a security alert appears when you try to access an HTTPS address, such as `https://localhost/servicemodelsamples/service.svc`, from your browser.</span></span>

## <a name="see-also"></a><span data-ttu-id="6129e-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6129e-129">See also</span></span>

[<span data-ttu-id="6129e-130">Niezawodne sesje</span><span class="sxs-lookup"><span data-stu-id="6129e-130">Reliable Sessions</span></span>](../../../../docs/framework/wcf/feature-details/reliable-sessions.md)
