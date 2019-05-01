---
title: 'Instrukcje: konfigurowanie portu z certyfikatem SSL'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SSL
- WCF, security mode
- WCF, security
ms.assetid: b8abcc8e-a5f5-4317-aca5-01e3c40ab24d
ms.openlocfilehash: d709123895f361c1d2268a218b4163c8d195e1b4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62047969"
---
# <a name="how-to-configure-a-port-with-an-ssl-certificate"></a><span data-ttu-id="c782e-102">Instrukcje: konfigurowanie portu z certyfikatem SSL</span><span class="sxs-lookup"><span data-stu-id="c782e-102">How to: Configure a Port with an SSL Certificate</span></span>
<span data-ttu-id="c782e-103">Podczas tworzenia własnego usługi Windows Communication Foundation (WCF) z <xref:System.ServiceModel.WSHttpBinding> zabezpieczenia transportu używa klasy, należy również skonfigurować port, za pomocą certyfikatu X.509.</span><span class="sxs-lookup"><span data-stu-id="c782e-103">When creating a self-hosted Windows Communication Foundation (WCF) service with the <xref:System.ServiceModel.WSHttpBinding> class that uses transport security, you must also configure a port with an X.509 certificate.</span></span> <span data-ttu-id="c782e-104">Jeśli nie tworzysz własne usługi, możesz hostować usługi w Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="c782e-104">If you are not creating a self-hosted service, you can host your service on Internet Information Services (IIS).</span></span> <span data-ttu-id="c782e-105">Aby uzyskać więcej informacji, zobacz [zabezpieczenia transportu HTTP](../../../../docs/framework/wcf/feature-details/http-transport-security.md).</span><span class="sxs-lookup"><span data-stu-id="c782e-105">For more information, see [HTTP Transport Security](../../../../docs/framework/wcf/feature-details/http-transport-security.md).</span></span>  
  
 <span data-ttu-id="c782e-106">Aby skonfigurować port, użyte narzędzie zależy od systemu operacyjnego, który jest uruchomiony na Twoim komputerze.</span><span class="sxs-lookup"><span data-stu-id="c782e-106">To configure a port, the tool you use depends on the operating system that is running on your machine.</span></span>  
  
 <span data-ttu-id="c782e-107">Jeśli używasz [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] lub [!INCLUDE[wxp](../../../../includes/wxp-md.md)], użyj narzędzia HttpCfg.exe.</span><span class="sxs-lookup"><span data-stu-id="c782e-107">If you are running [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] or [!INCLUDE[wxp](../../../../includes/wxp-md.md)], use the HttpCfg.exe tool.</span></span> <span data-ttu-id="c782e-108">Za pomocą [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] to narzędzie jest instalowane.</span><span class="sxs-lookup"><span data-stu-id="c782e-108">With [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] this tool is installed.</span></span> <span data-ttu-id="c782e-109">Za pomocą [!INCLUDE[wxp](../../../../includes/wxp-md.md)], możesz pobrać narzędzia z [narzędzia obsługi systemu Windows XP Service Pack 2](https://go.microsoft.com/fwlink/?LinkId=88606).</span><span class="sxs-lookup"><span data-stu-id="c782e-109">With [!INCLUDE[wxp](../../../../includes/wxp-md.md)], you can download the tool at [Windows XP Service Pack 2 Support Tools](https://go.microsoft.com/fwlink/?LinkId=88606).</span></span> <span data-ttu-id="c782e-110">Aby uzyskać więcej informacji, zobacz [Przegląd tak](https://go.microsoft.com/fwlink/?LinkId=88605).</span><span class="sxs-lookup"><span data-stu-id="c782e-110">For more information, see [Httpcfg Overview](https://go.microsoft.com/fwlink/?LinkId=88605).</span></span> <span data-ttu-id="c782e-111">[Dokumentację Windows Support Tools](https://go.microsoft.com/fwlink/?LinkId=94840) opisano składnię narzędzia Httpcfg.exe.</span><span class="sxs-lookup"><span data-stu-id="c782e-111">The [Windows Support Tools documentation](https://go.microsoft.com/fwlink/?LinkId=94840) explains the syntax for the Httpcfg.exe tool.</span></span>  
  
 <span data-ttu-id="c782e-112">Jeśli używasz [!INCLUDE[wv](../../../../includes/wv-md.md)], użyj narzędzia Netsh.exe, która jest już zainstalowana.</span><span class="sxs-lookup"><span data-stu-id="c782e-112">If you are running [!INCLUDE[wv](../../../../includes/wv-md.md)], use the Netsh.exe tool that is already installed.</span></span>  
  
 <span data-ttu-id="c782e-113">W tym temacie opisano sposób wykonania kilku procedur:</span><span class="sxs-lookup"><span data-stu-id="c782e-113">This topic describes how to accomplish several procedures:</span></span>  
  
- <span data-ttu-id="c782e-114">Określanie konfiguracji portu z bieżącego komputera.</span><span class="sxs-lookup"><span data-stu-id="c782e-114">Determining a computer's current port configuration.</span></span>  
  
- <span data-ttu-id="c782e-115">Pobieranie odcisku palca certyfikatu (wymagane dla dwóch poniższych procedur).</span><span class="sxs-lookup"><span data-stu-id="c782e-115">Getting a certificate's thumbprint (necessary for the following two procedures).</span></span>  
  
- <span data-ttu-id="c782e-116">Powiązanie certyfikatu SSL z konfiguracji portów.</span><span class="sxs-lookup"><span data-stu-id="c782e-116">Binding an SSL certificate to a port configuration.</span></span>  
  
- <span data-ttu-id="c782e-117">Powiązanie certyfikatu SSL z konfiguracji portów i obsługi certyfikatów klienta.</span><span class="sxs-lookup"><span data-stu-id="c782e-117">Binding an SSL certificate to a port configuration and supporting client certificates.</span></span>  
  
- <span data-ttu-id="c782e-118">Usuwanie certyfikatu SSL z numeru portu.</span><span class="sxs-lookup"><span data-stu-id="c782e-118">Deleting an SSL certificate from a port number.</span></span>  
  
 <span data-ttu-id="c782e-119">Należy pamiętać, że modyfikowanie certyfikaty przechowywane na komputerze wymaga uprawnień administracyjnych.</span><span class="sxs-lookup"><span data-stu-id="c782e-119">Note that modifying certificates stored on the computer requires administrative privileges.</span></span>  
  
### <a name="to-determine-how-ports-are-configured"></a><span data-ttu-id="c782e-120">Aby określić, jak porty są skonfigurowane.</span><span class="sxs-lookup"><span data-stu-id="c782e-120">To determine how ports are configured</span></span>  
  
1. <span data-ttu-id="c782e-121">W [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] lub [!INCLUDE[wxp](../../../../includes/wxp-md.md)], użyj narzędzia HttpCfg.exe do wyświetlenia bieżącej konfiguracji portów przy użyciu **zapytania** i **ssl** przełączy się, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="c782e-121">In [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] or [!INCLUDE[wxp](../../../../includes/wxp-md.md)], use the HttpCfg.exe tool to view the current port configuration, using the **query** and **ssl** switches, as shown in the following example.</span></span>  
  
    ```  
    httpcfg query ssl  
    ```  
  
2. <span data-ttu-id="c782e-122">W [!INCLUDE[wv](../../../../includes/wv-md.md)], należy użyć narzędzia Netsh.exe do wyświetlenia bieżącej konfiguracji portów, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="c782e-122">In [!INCLUDE[wv](../../../../includes/wv-md.md)], use the Netsh.exe tool to view the current port configuration, as shown in the following example.</span></span>  
  
    ```  
    netsh http show sslcert  
    ```  
  
### <a name="to-get-a-certificates-thumbprint"></a><span data-ttu-id="c782e-123">Aby uzyskać odcisk palca certyfikatu</span><span class="sxs-lookup"><span data-stu-id="c782e-123">To get a certificate's thumbprint</span></span>  
  
1. <span data-ttu-id="c782e-124">Użyj przystawki MMC certyfikatów, aby znaleźć certyfikat X.509, który ma zamierzony cel Uwierzytelnianie klienta.</span><span class="sxs-lookup"><span data-stu-id="c782e-124">Use the Certificates MMC snap-in to find an X.509 certificate that has an intended purpose of client authentication.</span></span> <span data-ttu-id="c782e-125">Aby uzyskać więcej informacji, zobacz [jak: Wyświetlanie certyfikatów za pomocą przystawki programu MMC](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).</span><span class="sxs-lookup"><span data-stu-id="c782e-125">For more information, see [How to: View Certificates with the MMC Snap-in](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).</span></span>  
  
2. <span data-ttu-id="c782e-126">Dostęp do odcisk palca certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="c782e-126">Access the certificate's thumbprint.</span></span> <span data-ttu-id="c782e-127">Aby uzyskać więcej informacji, zobacz [jak: Pobieranie odcisku palca certyfikatu](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="c782e-127">For more information, see [How to: Retrieve the Thumbprint of a Certificate](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).</span></span>  
  
3. <span data-ttu-id="c782e-128">Skopiuj odcisk palca certyfikatu do edytora tekstów, takiego jak Notatnik.</span><span class="sxs-lookup"><span data-stu-id="c782e-128">Copy the thumbprint of the certificate into a text editor, such as Notepad.</span></span>  
  
4. <span data-ttu-id="c782e-129">Usuń wszystkie spacje między znaków szesnastkowych.</span><span class="sxs-lookup"><span data-stu-id="c782e-129">Remove all spaces between the hexadecimal characters.</span></span> <span data-ttu-id="c782e-130">Jednym ze sposobów osiągnięcia tego jest korzystać z funkcji znajdowania i zamieniania w edytorze tekstów i Zastąp każdą spację znakiem null.</span><span class="sxs-lookup"><span data-stu-id="c782e-130">One way to accomplish this is to use the text editor's find-and-replace feature and replace each space with a null character.</span></span>  
  
### <a name="to-bind-an-ssl-certificate-to-a-port-number"></a><span data-ttu-id="c782e-131">Aby powiązać certyfikatu SSL do numeru portu</span><span class="sxs-lookup"><span data-stu-id="c782e-131">To bind an SSL certificate to a port number</span></span>  
  
1. <span data-ttu-id="c782e-132">W [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] lub [!INCLUDE[wxp](../../../../includes/wxp-md.md)], użyj narzędzia HttpCfg.exe w trybie "set" w sklepie Secure Sockets Layer (SSL), aby powiązać certyfikat numeru portu.</span><span class="sxs-lookup"><span data-stu-id="c782e-132">In [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] or [!INCLUDE[wxp](../../../../includes/wxp-md.md)], use the HttpCfg.exe tool in "set" mode on the Secure Sockets Layer (SSL) store to bind the certificate to a port number.</span></span> <span data-ttu-id="c782e-133">Narzędzie używana odcisk palca certyfikatu, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="c782e-133">The tool uses the thumbprint to identify the certificate, as shown in the following example.</span></span>  
  
    ```  
    httpcfg set ssl -i 0.0.0.0:8012 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6  
    ```  
  
    - <span data-ttu-id="c782e-134">**-I** przełącznik ma składnię `IP`:`port` i powoduje, że narzędzie, aby ustawić certyfikat z portem 8012 komputera.</span><span class="sxs-lookup"><span data-stu-id="c782e-134">The **-i** switch has the syntax of `IP`:`port` and instructs the tool to set the certificate to port 8012 of the computer.</span></span> <span data-ttu-id="c782e-135">Opcjonalnie cztery zera, które poprzedzają numer można również zastąpić rzeczywistego adresu IP komputera.</span><span class="sxs-lookup"><span data-stu-id="c782e-135">Optionally, the four zeroes that precede the number can also be replaced by the actual IP address of the computer.</span></span>  
  
    - <span data-ttu-id="c782e-136">**-H** przełącznik określa odcisk palca certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="c782e-136">The **-h** switch specifies the thumbprint of the certificate.</span></span>  
  
2. <span data-ttu-id="c782e-137">W [!INCLUDE[wv](../../../../includes/wv-md.md)], użyj narzędzia Netsh.exe, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="c782e-137">In [!INCLUDE[wv](../../../../includes/wv-md.md)], use the Netsh.exe tool, as shown in the following example.</span></span>  
  
    ```  
    netsh http add sslcert ipport=0.0.0.0:8000 certhash=0000000000003ed9cd0c315bbb6dc1c08da5e6 appid={00112233-4455-6677-8899-AABBCCDDEEFF}   
    ```  
  
    - <span data-ttu-id="c782e-138">**Certhash** parametr określa odcisk palca certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="c782e-138">The **certhash** parameter specifies the thumbprint of the certificate.</span></span>  
  
    - <span data-ttu-id="c782e-139">**Ipport** parametr określa adres IP i port, a funkcje podobnie jak **-i** przełącznika narzędzia Httpcfg.exe opisem.</span><span class="sxs-lookup"><span data-stu-id="c782e-139">The **ipport** parameter specifies the IP address and port, and functions just like the **-i** switch of the Httpcfg.exe tool described.</span></span>  
  
    - <span data-ttu-id="c782e-140">**Appid** parametru jest identyfikatorem GUID, który może służyć do identyfikowania będąca właścicielem aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c782e-140">The **appid** parameter is a GUID that can be used to identify the owning application.</span></span>  
  
### <a name="to-bind-an-ssl-certificate-to-a-port-number-and-support-client-certificates"></a><span data-ttu-id="c782e-141">Powiąż certyfikat SSL na numer portu i obsługują certyfikaty klientów</span><span class="sxs-lookup"><span data-stu-id="c782e-141">To bind an SSL certificate to a port number and support client certificates</span></span>  
  
1. <span data-ttu-id="c782e-142">W [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] lub [!INCLUDE[wxp](../../../../includes/wxp-md.md)], które obsługują klientów, którzy uwierzytelniania za pomocą certyfikatów X.509 w warstwie transportowej, wykonaj poprzednią procedurę, ale należy przekazać dodatkowy parametr wiersza polecenia do HttpCfg.exe, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="c782e-142">In [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] or [!INCLUDE[wxp](../../../../includes/wxp-md.md)], to support clients that authenticate with X.509 certificates at the transport layer, follow the preceding procedure but pass an additional command-line parameter to HttpCfg.exe, as shown in the following example.</span></span>  
  
    ```  
    httpcfg set ssl -i 0.0.0.0:8012 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6 -f 2  
    ```  
  
     <span data-ttu-id="c782e-143">**-F** przełącznik ma składnię `n` gdzie n to liczba od 1 do 7.</span><span class="sxs-lookup"><span data-stu-id="c782e-143">The **-f** switch has the syntax of `n` where n is a number between 1 and 7.</span></span> <span data-ttu-id="c782e-144">Wartość 2, jak pokazano w powyższym przykładzie umożliwia certyfikaty klienta w warstwie transportowej.</span><span class="sxs-lookup"><span data-stu-id="c782e-144">A value of 2, as shown in the preceding example, enables client certificates at the transport layer.</span></span> <span data-ttu-id="c782e-145">Wartość 3 umożliwia certyfikaty klienta i mapuje te certyfikaty do konta Windows.</span><span class="sxs-lookup"><span data-stu-id="c782e-145">A value of 3 enables client certificates and maps those certificates to a Windows account.</span></span> <span data-ttu-id="c782e-146">Zapoznaj się z pomocą HttpCfg.exe zachowania inne wartości.</span><span class="sxs-lookup"><span data-stu-id="c782e-146">See HttpCfg.exe Help for the behavior of other values.</span></span>  
  
2. <span data-ttu-id="c782e-147">W [!INCLUDE[wv](../../../../includes/wv-md.md)], dla klientów pomocy technicznej, którzy uwierzytelniać za pomocą certyfikatów X.509 w warstwie transportowej, wykonaj poprzednią procedurę, ale o dodatkowy parametr, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="c782e-147">In [!INCLUDE[wv](../../../../includes/wv-md.md)], to support clients that authenticate with X.509 certificates at the transport layer, follow the preceding procedure, but with an additional parameter, as shown in the following example.</span></span>  
  
    ```  
    netsh http add sslcert ipport=0.0.0.0:8000 certhash=0000000000003ed9cd0c315bbb6dc1c08da5e6 appid={00112233-4455-6677-8899-AABBCCDDEEFF} clientcertnegotiation=enable  
    ```  
  
### <a name="to-delete-an-ssl-certificate-from-a-port-number"></a><span data-ttu-id="c782e-148">Aby usunąć certyfikat SSL z numeru portu</span><span class="sxs-lookup"><span data-stu-id="c782e-148">To delete an SSL certificate from a port number</span></span>  
  
1. <span data-ttu-id="c782e-149">Użyj narzędzia HttpCfg.exe lub Netsh.exe, aby zobaczyć porty i odciski palca wszystkie powiązania na komputerze.</span><span class="sxs-lookup"><span data-stu-id="c782e-149">Use the HttpCfg.exe or Netsh.exe tool to see the ports and thumbprints of all bindings on the computer.</span></span> <span data-ttu-id="c782e-150">Aby wydrukować dane na dysku, użyj znaku przekierowania ">", jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="c782e-150">To print the information to disk, use the redirection character ">", as shown in the following example.</span></span>  
  
    ```  
    httpcfg query ssl>myMachinePorts.txt  
    ```  
  
2. <span data-ttu-id="c782e-151">W [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] lub [!INCLUDE[wxp](../../../../includes/wxp-md.md)], użyj narzędzia HttpCfg.exe z **Usuń** i **ssl** słów kluczowych.</span><span class="sxs-lookup"><span data-stu-id="c782e-151">In [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] or [!INCLUDE[wxp](../../../../includes/wxp-md.md)], use the HttpCfg.exe tool with the **delete** and **ssl** keywords.</span></span> <span data-ttu-id="c782e-152">Użyj **-i** przełącznika `IP`:`port` cyfrą i **-h** Przełącz się do określania odcisku palca.</span><span class="sxs-lookup"><span data-stu-id="c782e-152">Use the **-i** switch to specify the `IP`:`port` number, and the **-h** switch to specify the thumbprint.</span></span>  
  
    ```  
    httpcfg delete ssl -i 0.0.0.0:8005 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6  
    ```  
  
3. <span data-ttu-id="c782e-153">W [!INCLUDE[wv](../../../../includes/wv-md.md)], użyj narzędzia Netsh.exe, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="c782e-153">In [!INCLUDE[wv](../../../../includes/wv-md.md)], use the Netsh.exe tool, as shown in the following example.</span></span>  
  
    ```  
    Netsh http delete sslcert ipport=0.0.0.0:8005  
    ```  
  
## <a name="example"></a><span data-ttu-id="c782e-154">Przykład</span><span class="sxs-lookup"><span data-stu-id="c782e-154">Example</span></span>  
 <span data-ttu-id="c782e-155">Poniższy kod pokazuje, jak utworzyć samodzielnie hostowanej usługi za pomocą <xref:System.ServiceModel.WSHttpBinding> klasy ustawienie zabezpieczeń transportu.</span><span class="sxs-lookup"><span data-stu-id="c782e-155">The following code shows how to create a self-hosted service using the <xref:System.ServiceModel.WSHttpBinding> class set to transport security.</span></span> <span data-ttu-id="c782e-156">Podczas tworzenia aplikacji, należy określić numer portu w adresie.</span><span class="sxs-lookup"><span data-stu-id="c782e-156">When creating an application, specify the port number in the address.</span></span>  
  
 [!code-csharp[c_WsHttpService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wshttpservice/cs/source.cs#3)]
 [!code-vb[c_WsHttpService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wshttpservice/vb/source.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="c782e-157">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c782e-157">See also</span></span>

- [<span data-ttu-id="c782e-158">Zabezpieczenia transportu HTTP</span><span class="sxs-lookup"><span data-stu-id="c782e-158">HTTP Transport Security</span></span>](../../../../docs/framework/wcf/feature-details/http-transport-security.md)
