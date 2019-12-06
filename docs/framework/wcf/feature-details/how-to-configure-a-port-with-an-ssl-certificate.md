---
title: 'Instrukcje: Konfigurowanie portu z certyfikatem SSL'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SSL
- WCF, security mode
- WCF, security
ms.assetid: b8abcc8e-a5f5-4317-aca5-01e3c40ab24d
ms.openlocfilehash: d2fe9a73f79408db08ef48d380940fcf6bb831c0
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/05/2019
ms.locfileid: "74838003"
---
# <a name="how-to-configure-a-port-with-an-ssl-certificate"></a><span data-ttu-id="54c26-102">Instrukcje: Konfigurowanie portu z certyfikatem SSL</span><span class="sxs-lookup"><span data-stu-id="54c26-102">How to: Configure a Port with an SSL Certificate</span></span>
<span data-ttu-id="54c26-103">Podczas tworzenia samohostowanej usługi Windows Communication Foundation (WCF) z klasą <xref:System.ServiceModel.WSHttpBinding>, która korzysta z zabezpieczeń transportu, należy również skonfigurować port za pomocą certyfikatu X. 509.</span><span class="sxs-lookup"><span data-stu-id="54c26-103">When creating a self-hosted Windows Communication Foundation (WCF) service with the <xref:System.ServiceModel.WSHttpBinding> class that uses transport security, you must also configure a port with an X.509 certificate.</span></span> <span data-ttu-id="54c26-104">Jeśli nie tworzysz usługi samodzielnej, możesz hostować usługę w Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="54c26-104">If you are not creating a self-hosted service, you can host your service on Internet Information Services (IIS).</span></span> <span data-ttu-id="54c26-105">Aby uzyskać więcej informacji, zobacz [zabezpieczenia transportu HTTP](../../../../docs/framework/wcf/feature-details/http-transport-security.md).</span><span class="sxs-lookup"><span data-stu-id="54c26-105">For more information, see [HTTP Transport Security](../../../../docs/framework/wcf/feature-details/http-transport-security.md).</span></span>  
  
 <span data-ttu-id="54c26-106">Aby skonfigurować port, używane narzędzie zależy od systemu operacyjnego działającego na komputerze.</span><span class="sxs-lookup"><span data-stu-id="54c26-106">To configure a port, the tool you use depends on the operating system that is running on your machine.</span></span>  
  
 <span data-ttu-id="54c26-107">Jeśli używasz programu [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] lub [!INCLUDE[wxp](../../../../includes/wxp-md.md)], użyj narzędzia HttpCfg. exe.</span><span class="sxs-lookup"><span data-stu-id="54c26-107">If you are running [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] or [!INCLUDE[wxp](../../../../includes/wxp-md.md)], use the HttpCfg.exe tool.</span></span> <span data-ttu-id="54c26-108">Za pomocą [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] to narzędzie jest zainstalowane.</span><span class="sxs-lookup"><span data-stu-id="54c26-108">With [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] this tool is installed.</span></span> <span data-ttu-id="54c26-109">Za pomocą [!INCLUDE[wxp](../../../../includes/wxp-md.md)]można pobrać narzędzie w [systemie Windows XP z dodatkiem Service Pack 2](https://go.microsoft.com/fwlink/?LinkId=88606).</span><span class="sxs-lookup"><span data-stu-id="54c26-109">With [!INCLUDE[wxp](../../../../includes/wxp-md.md)], you can download the tool at [Windows XP Service Pack 2 Support Tools](https://go.microsoft.com/fwlink/?LinkId=88606).</span></span> <span data-ttu-id="54c26-110">Aby uzyskać więcej informacji, zobacz [Httpcfg Overview (przegląd](https://go.microsoft.com/fwlink/?LinkId=88605)).</span><span class="sxs-lookup"><span data-stu-id="54c26-110">For more information, see [Httpcfg Overview](https://go.microsoft.com/fwlink/?LinkId=88605).</span></span> <span data-ttu-id="54c26-111">[Dokumentacja narzędzi pomocy technicznej systemu Windows](https://go.microsoft.com/fwlink/?LinkId=94840) objaśnia składnię dla narzędzia HttpCfg. exe.</span><span class="sxs-lookup"><span data-stu-id="54c26-111">The [Windows Support Tools documentation](https://go.microsoft.com/fwlink/?LinkId=94840) explains the syntax for the Httpcfg.exe tool.</span></span>  
  
 <span data-ttu-id="54c26-112">Jeśli korzystasz z systemu Windows Vista, użyj narzędzia Netsh. exe, które jest już zainstalowane.</span><span class="sxs-lookup"><span data-stu-id="54c26-112">If you are running Windows Vista, use the Netsh.exe tool that is already installed.</span></span>  
  
 <span data-ttu-id="54c26-113">W tym temacie opisano sposób wykonywania kilku procedur:</span><span class="sxs-lookup"><span data-stu-id="54c26-113">This topic describes how to accomplish several procedures:</span></span>  
  
- <span data-ttu-id="54c26-114">Określanie bieżącej konfiguracji komputera.</span><span class="sxs-lookup"><span data-stu-id="54c26-114">Determining a computer's current port configuration.</span></span>  
  
- <span data-ttu-id="54c26-115">Pobieranie odcisku palca certyfikatu (wymagane w przypadku poniższych dwóch procedur).</span><span class="sxs-lookup"><span data-stu-id="54c26-115">Getting a certificate's thumbprint (necessary for the following two procedures).</span></span>  
  
- <span data-ttu-id="54c26-116">Powiązanie certyfikatu SSL z konfiguracją portu.</span><span class="sxs-lookup"><span data-stu-id="54c26-116">Binding an SSL certificate to a port configuration.</span></span>  
  
- <span data-ttu-id="54c26-117">Powiązanie certyfikatu SSL z konfiguracją portu i obsługą certyfikatów klienta.</span><span class="sxs-lookup"><span data-stu-id="54c26-117">Binding an SSL certificate to a port configuration and supporting client certificates.</span></span>  
  
- <span data-ttu-id="54c26-118">Usuwanie certyfikatu SSL z numeru portu.</span><span class="sxs-lookup"><span data-stu-id="54c26-118">Deleting an SSL certificate from a port number.</span></span>  
  
 <span data-ttu-id="54c26-119">Należy zauważyć, że modyfikowanie certyfikatów przechowywanych na komputerze wymaga uprawnień administracyjnych.</span><span class="sxs-lookup"><span data-stu-id="54c26-119">Note that modifying certificates stored on the computer requires administrative privileges.</span></span>  
  
### <a name="to-determine-how-ports-are-configured"></a><span data-ttu-id="54c26-120">Aby określić sposób konfiguracji portów</span><span class="sxs-lookup"><span data-stu-id="54c26-120">To determine how ports are configured</span></span>  
  
1. <span data-ttu-id="54c26-121">W [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] lub [!INCLUDE[wxp](../../../../includes/wxp-md.md)]Użyj narzędzia HttpCfg. exe, aby wyświetlić bieżącą konfigurację portu przy użyciu **zapytań** i przełączników **SSL** , jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="54c26-121">In [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] or [!INCLUDE[wxp](../../../../includes/wxp-md.md)], use the HttpCfg.exe tool to view the current port configuration, using the **query** and **ssl** switches, as shown in the following example.</span></span>  
  
    ```console
    httpcfg query ssl  
    ```  
  
2. <span data-ttu-id="54c26-122">W systemie Windows Vista Użyj narzędzia Netsh. exe, aby wyświetlić bieżącą konfigurację portu, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="54c26-122">In Windows Vista, use the Netsh.exe tool to view the current port configuration, as shown in the following example.</span></span>  
  
    ```console  
    netsh http show sslcert  
    ```  
  
### <a name="to-get-a-certificates-thumbprint"></a><span data-ttu-id="54c26-123">Aby uzyskać odcisk palca certyfikatu</span><span class="sxs-lookup"><span data-stu-id="54c26-123">To get a certificate's thumbprint</span></span>  
  
1. <span data-ttu-id="54c26-124">Za pomocą przystawki MMC Certyfikaty Znajdź certyfikat X. 509, który ma zamierzony cel uwierzytelniania klientów.</span><span class="sxs-lookup"><span data-stu-id="54c26-124">Use the Certificates MMC snap-in to find an X.509 certificate that has an intended purpose of client authentication.</span></span> <span data-ttu-id="54c26-125">Aby uzyskać więcej informacji, zobacz [How to: View Certificates za pomocą przystawki MMC](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).</span><span class="sxs-lookup"><span data-stu-id="54c26-125">For more information, see [How to: View Certificates with the MMC Snap-in](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).</span></span>  
  
2. <span data-ttu-id="54c26-126">Uzyskaj dostęp do odcisku palca certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="54c26-126">Access the certificate's thumbprint.</span></span> <span data-ttu-id="54c26-127">Aby uzyskać więcej informacji, zobacz [Instrukcje: Pobieranie odcisku palca certyfikatu](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="54c26-127">For more information, see [How to: Retrieve the Thumbprint of a Certificate](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).</span></span>  
  
3. <span data-ttu-id="54c26-128">Skopiuj odcisk palca certyfikatu do edytora tekstu, takiego jak Notatnik.</span><span class="sxs-lookup"><span data-stu-id="54c26-128">Copy the thumbprint of the certificate into a text editor, such as Notepad.</span></span>  
  
4. <span data-ttu-id="54c26-129">Usuń wszystkie spacje między znakami szesnastkowymi.</span><span class="sxs-lookup"><span data-stu-id="54c26-129">Remove all spaces between the hexadecimal characters.</span></span> <span data-ttu-id="54c26-130">Jednym ze sposobów osiągnięcia tego celu jest użycie funkcji znajdowania i zamieniania edytora tekstu oraz zastępowanie każdej spacji znakiem null.</span><span class="sxs-lookup"><span data-stu-id="54c26-130">One way to accomplish this is to use the text editor's find-and-replace feature and replace each space with a null character.</span></span>  
  
### <a name="to-bind-an-ssl-certificate-to-a-port-number"></a><span data-ttu-id="54c26-131">Aby powiązać certyfikat protokołu SSL z numerem portu</span><span class="sxs-lookup"><span data-stu-id="54c26-131">To bind an SSL certificate to a port number</span></span>  
  
1. <span data-ttu-id="54c26-132">W [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] lub [!INCLUDE[wxp](../../../../includes/wxp-md.md)]Użyj narzędzia HttpCfg. exe w trybie "Set" w magazynie SSL (SSL), aby powiązać certyfikat z numerem portu.</span><span class="sxs-lookup"><span data-stu-id="54c26-132">In [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] or [!INCLUDE[wxp](../../../../includes/wxp-md.md)], use the HttpCfg.exe tool in "set" mode on the Secure Sockets Layer (SSL) store to bind the certificate to a port number.</span></span> <span data-ttu-id="54c26-133">Narzędzie używa odcisku palca do identyfikowania certyfikatu, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="54c26-133">The tool uses the thumbprint to identify the certificate, as shown in the following example.</span></span>  
  
    ```console  
    httpcfg set ssl -i 0.0.0.0:8012 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6  
    ```  
  
    - <span data-ttu-id="54c26-134">Przełącznik **-i** ma składnię `IP`:`port` i instruuje narzędzie, aby ustawił certyfikat na port 8012 na komputerze.</span><span class="sxs-lookup"><span data-stu-id="54c26-134">The **-i** switch has the syntax of `IP`:`port` and instructs the tool to set the certificate to port 8012 of the computer.</span></span> <span data-ttu-id="54c26-135">Opcjonalnie cztery zera, które poprzedzają liczbę, można również zastąpić rzeczywistym adresem IP komputera.</span><span class="sxs-lookup"><span data-stu-id="54c26-135">Optionally, the four zeroes that precede the number can also be replaced by the actual IP address of the computer.</span></span>  
  
    - <span data-ttu-id="54c26-136">Przełącznik **-h** określa odcisk palca certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="54c26-136">The **-h** switch specifies the thumbprint of the certificate.</span></span>  
  
2. <span data-ttu-id="54c26-137">W systemie Windows Vista Użyj narzędzia Netsh. exe, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="54c26-137">In Windows Vista, use the Netsh.exe tool, as shown in the following example.</span></span>  
  
    ```console  
    netsh http add sslcert ipport=0.0.0.0:8000 certhash=0000000000003ed9cd0c315bbb6dc1c08da5e6 appid={00112233-4455-6677-8899-AABBCCDDEEFF}   
    ```  
  
    - <span data-ttu-id="54c26-138">Parametr **certhash** określa odcisk palca certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="54c26-138">The **certhash** parameter specifies the thumbprint of the certificate.</span></span>  
  
    - <span data-ttu-id="54c26-139">Parametr **IPPORT** określa adres IP i port oraz działa podobnie jak w **przypadku przełącznika Httpcfg** . exe opisanego w opisie.</span><span class="sxs-lookup"><span data-stu-id="54c26-139">The **ipport** parameter specifies the IP address and port, and functions just like the **-i** switch of the Httpcfg.exe tool described.</span></span>  
  
    - <span data-ttu-id="54c26-140">Identyfikator **AppID** jest identyfikatorem GUID, który może służyć do identyfikowania aplikacji będącej właścicielem.</span><span class="sxs-lookup"><span data-stu-id="54c26-140">The **appid** parameter is a GUID that can be used to identify the owning application.</span></span>  
  
### <a name="to-bind-an-ssl-certificate-to-a-port-number-and-support-client-certificates"></a><span data-ttu-id="54c26-141">Aby powiązać certyfikat protokołu SSL z numerem portu i obsługiwać certyfikaty klienta</span><span class="sxs-lookup"><span data-stu-id="54c26-141">To bind an SSL certificate to a port number and support client certificates</span></span>  
  
1. <span data-ttu-id="54c26-142">W [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] lub [!INCLUDE[wxp](../../../../includes/wxp-md.md)], aby obsługiwać klientów uwierzytelnianych za pomocą certyfikatów X. 509 w warstwie transportowej, wykonaj poprzednią procedurę, ale Przekaż dodatkowy parametr wiersza polecenia do HttpCfg. exe, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="54c26-142">In [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] or [!INCLUDE[wxp](../../../../includes/wxp-md.md)], to support clients that authenticate with X.509 certificates at the transport layer, follow the preceding procedure but pass an additional command-line parameter to HttpCfg.exe, as shown in the following example.</span></span>  
  
    ```console  
    httpcfg set ssl -i 0.0.0.0:8012 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6 -f 2  
    ```  
  
     <span data-ttu-id="54c26-143">Przełącznik **-f** ma składnię `n` gdzie n jest liczbą z zakresu od 1 do 7.</span><span class="sxs-lookup"><span data-stu-id="54c26-143">The **-f** switch has the syntax of `n` where n is a number between 1 and 7.</span></span> <span data-ttu-id="54c26-144">Wartość 2, jak pokazano w powyższym przykładzie, umożliwia korzystanie z certyfikatów klienta w warstwie transportowej.</span><span class="sxs-lookup"><span data-stu-id="54c26-144">A value of 2, as shown in the preceding example, enables client certificates at the transport layer.</span></span> <span data-ttu-id="54c26-145">Wartość 3 włącza certyfikaty klienta i mapuje te certyfikaty na konto systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="54c26-145">A value of 3 enables client certificates and maps those certificates to a Windows account.</span></span> <span data-ttu-id="54c26-146">Zapoznaj się z tematem zachowanie innych wartości w pomocy programu HttpCfg. exe.</span><span class="sxs-lookup"><span data-stu-id="54c26-146">See HttpCfg.exe Help for the behavior of other values.</span></span>  
  
2. <span data-ttu-id="54c26-147">W systemie Windows Vista w celu obsługi klientów uwierzytelnianych za pomocą certyfikatów X. 509 w warstwie transportowej Wykonaj poprzednią procedurę, ale z dodatkowym parametrem, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="54c26-147">In Windows Vista, to support clients that authenticate with X.509 certificates at the transport layer, follow the preceding procedure, but with an additional parameter, as shown in the following example.</span></span>  
  
    ```console  
    netsh http add sslcert ipport=0.0.0.0:8000 certhash=0000000000003ed9cd0c315bbb6dc1c08da5e6 appid={00112233-4455-6677-8899-AABBCCDDEEFF} clientcertnegotiation=enable  
    ```  
  
### <a name="to-delete-an-ssl-certificate-from-a-port-number"></a><span data-ttu-id="54c26-148">Aby usunąć certyfikat SSL z numeru portu</span><span class="sxs-lookup"><span data-stu-id="54c26-148">To delete an SSL certificate from a port number</span></span>  
  
1. <span data-ttu-id="54c26-149">Użyj narzędzia HttpCfg. exe lub netsh. exe, aby zobaczyć porty i odciski palców wszystkich powiązań na komputerze.</span><span class="sxs-lookup"><span data-stu-id="54c26-149">Use the HttpCfg.exe or Netsh.exe tool to see the ports and thumbprints of all bindings on the computer.</span></span> <span data-ttu-id="54c26-150">Aby wydrukować informacje na dysku, użyj znaku przekierowania ">", jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="54c26-150">To print the information to disk, use the redirection character ">", as shown in the following example.</span></span>  
  
    ```console  
    httpcfg query ssl>myMachinePorts.txt  
    ```
  
2. <span data-ttu-id="54c26-151">W [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] lub [!INCLUDE[wxp](../../../../includes/wxp-md.md)]Użyj narzędzia HttpCfg. exe ze słowami kluczowymi **delete** i **SSL** .</span><span class="sxs-lookup"><span data-stu-id="54c26-151">In [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] or [!INCLUDE[wxp](../../../../includes/wxp-md.md)], use the HttpCfg.exe tool with the **delete** and **ssl** keywords.</span></span> <span data-ttu-id="54c26-152">Użyj przełącznika **-i** , aby określić `IP`: numer`port` i przełącznik **-h** , aby określić odcisk palca.</span><span class="sxs-lookup"><span data-stu-id="54c26-152">Use the **-i** switch to specify the `IP`:`port` number, and the **-h** switch to specify the thumbprint.</span></span>  
  
    ```console  
    httpcfg delete ssl -i 0.0.0.0:8005 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6  
    ```  
  
3. <span data-ttu-id="54c26-153">W systemie Windows Vista Użyj narzędzia Netsh. exe, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="54c26-153">In Windows Vista, use the Netsh.exe tool, as shown in the following example.</span></span>  
  
    ```console  
    Netsh http delete sslcert ipport=0.0.0.0:8005  
    ```  
  
## <a name="example"></a><span data-ttu-id="54c26-154">Przykład</span><span class="sxs-lookup"><span data-stu-id="54c26-154">Example</span></span>  
 <span data-ttu-id="54c26-155">Poniższy kod przedstawia sposób tworzenia usługi samodzielnej przy użyciu klasy <xref:System.ServiceModel.WSHttpBinding> ustawionej na zabezpieczenia transportu.</span><span class="sxs-lookup"><span data-stu-id="54c26-155">The following code shows how to create a self-hosted service using the <xref:System.ServiceModel.WSHttpBinding> class set to transport security.</span></span> <span data-ttu-id="54c26-156">Podczas tworzenia aplikacji należy określić numer portu w adresie.</span><span class="sxs-lookup"><span data-stu-id="54c26-156">When creating an application, specify the port number in the address.</span></span>  
  
 [!code-csharp[c_WsHttpService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wshttpservice/cs/source.cs#3)]
 [!code-vb[c_WsHttpService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wshttpservice/vb/source.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="54c26-157">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="54c26-157">See also</span></span>

- [<span data-ttu-id="54c26-158">Zabezpieczenia transportu HTTP</span><span class="sxs-lookup"><span data-stu-id="54c26-158">HTTP Transport Security</span></span>](../../../../docs/framework/wcf/feature-details/http-transport-security.md)
