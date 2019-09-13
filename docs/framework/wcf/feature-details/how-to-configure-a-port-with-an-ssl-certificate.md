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
ms.openlocfilehash: 6e21311802b0a3ce4e415b14686b101d31f18035
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/11/2019
ms.locfileid: "70893313"
---
# <a name="how-to-configure-a-port-with-an-ssl-certificate"></a><span data-ttu-id="8ec96-102">Instrukcje: konfigurowanie portu z certyfikatem SSL</span><span class="sxs-lookup"><span data-stu-id="8ec96-102">How to: Configure a Port with an SSL Certificate</span></span>
<span data-ttu-id="8ec96-103">Podczas tworzenia samohostowanej usługi Windows Communication Foundation (WCF) z <xref:System.ServiceModel.WSHttpBinding> klasą, która korzysta z zabezpieczeń transportu, należy również skonfigurować port za pomocą certyfikatu X. 509.</span><span class="sxs-lookup"><span data-stu-id="8ec96-103">When creating a self-hosted Windows Communication Foundation (WCF) service with the <xref:System.ServiceModel.WSHttpBinding> class that uses transport security, you must also configure a port with an X.509 certificate.</span></span> <span data-ttu-id="8ec96-104">Jeśli nie tworzysz usługi samodzielnej, możesz hostować usługę w Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="8ec96-104">If you are not creating a self-hosted service, you can host your service on Internet Information Services (IIS).</span></span> <span data-ttu-id="8ec96-105">Aby uzyskać więcej informacji, zobacz [zabezpieczenia transportu HTTP](../../../../docs/framework/wcf/feature-details/http-transport-security.md).</span><span class="sxs-lookup"><span data-stu-id="8ec96-105">For more information, see [HTTP Transport Security](../../../../docs/framework/wcf/feature-details/http-transport-security.md).</span></span>  
  
 <span data-ttu-id="8ec96-106">Aby skonfigurować port, używane narzędzie zależy od systemu operacyjnego działającego na komputerze.</span><span class="sxs-lookup"><span data-stu-id="8ec96-106">To configure a port, the tool you use depends on the operating system that is running on your machine.</span></span>  
  
 <span data-ttu-id="8ec96-107">Jeśli używasz programu [!INCLUDE[wxp](../../../../includes/wxp-md.md)]lub,Użyj narzędzia HttpCfg. exe. [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8ec96-107">If you are running [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] or [!INCLUDE[wxp](../../../../includes/wxp-md.md)], use the HttpCfg.exe tool.</span></span> <span data-ttu-id="8ec96-108">Po [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] zainstalowaniu tego narzędzia.</span><span class="sxs-lookup"><span data-stu-id="8ec96-108">With [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] this tool is installed.</span></span> <span data-ttu-id="8ec96-109">Za [!INCLUDE[wxp](../../../../includes/wxp-md.md)]pomocą narzędzia można pobrać narzędzie w [systemie Windows XP z dodatkiem Service Pack 2](https://go.microsoft.com/fwlink/?LinkId=88606).</span><span class="sxs-lookup"><span data-stu-id="8ec96-109">With [!INCLUDE[wxp](../../../../includes/wxp-md.md)], you can download the tool at [Windows XP Service Pack 2 Support Tools](https://go.microsoft.com/fwlink/?LinkId=88606).</span></span> <span data-ttu-id="8ec96-110">Aby uzyskać więcej informacji, zobacz [Httpcfg Overview (przegląd](https://go.microsoft.com/fwlink/?LinkId=88605)).</span><span class="sxs-lookup"><span data-stu-id="8ec96-110">For more information, see [Httpcfg Overview](https://go.microsoft.com/fwlink/?LinkId=88605).</span></span> <span data-ttu-id="8ec96-111">[Dokumentacja narzędzi pomocy technicznej systemu Windows](https://go.microsoft.com/fwlink/?LinkId=94840) objaśnia składnię dla narzędzia HttpCfg. exe.</span><span class="sxs-lookup"><span data-stu-id="8ec96-111">The [Windows Support Tools documentation](https://go.microsoft.com/fwlink/?LinkId=94840) explains the syntax for the Httpcfg.exe tool.</span></span>  
  
 <span data-ttu-id="8ec96-112">Jeśli używasz programu, użyj narzędzia Netsh. exe, które jest już zainstalowane. [!INCLUDE[wv](../../../../includes/wv-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8ec96-112">If you are running [!INCLUDE[wv](../../../../includes/wv-md.md)], use the Netsh.exe tool that is already installed.</span></span>  
  
 <span data-ttu-id="8ec96-113">W tym temacie opisano sposób wykonywania kilku procedur:</span><span class="sxs-lookup"><span data-stu-id="8ec96-113">This topic describes how to accomplish several procedures:</span></span>  
  
- <span data-ttu-id="8ec96-114">Określanie bieżącej konfiguracji komputera.</span><span class="sxs-lookup"><span data-stu-id="8ec96-114">Determining a computer's current port configuration.</span></span>  
  
- <span data-ttu-id="8ec96-115">Pobieranie odcisku palca certyfikatu (wymagane w przypadku poniższych dwóch procedur).</span><span class="sxs-lookup"><span data-stu-id="8ec96-115">Getting a certificate's thumbprint (necessary for the following two procedures).</span></span>  
  
- <span data-ttu-id="8ec96-116">Powiązanie certyfikatu SSL z konfiguracją portu.</span><span class="sxs-lookup"><span data-stu-id="8ec96-116">Binding an SSL certificate to a port configuration.</span></span>  
  
- <span data-ttu-id="8ec96-117">Powiązanie certyfikatu SSL z konfiguracją portu i obsługą certyfikatów klienta.</span><span class="sxs-lookup"><span data-stu-id="8ec96-117">Binding an SSL certificate to a port configuration and supporting client certificates.</span></span>  
  
- <span data-ttu-id="8ec96-118">Usuwanie certyfikatu SSL z numeru portu.</span><span class="sxs-lookup"><span data-stu-id="8ec96-118">Deleting an SSL certificate from a port number.</span></span>  
  
 <span data-ttu-id="8ec96-119">Należy zauważyć, że modyfikowanie certyfikatów przechowywanych na komputerze wymaga uprawnień administracyjnych.</span><span class="sxs-lookup"><span data-stu-id="8ec96-119">Note that modifying certificates stored on the computer requires administrative privileges.</span></span>  
  
### <a name="to-determine-how-ports-are-configured"></a><span data-ttu-id="8ec96-120">Aby określić sposób konfiguracji portów</span><span class="sxs-lookup"><span data-stu-id="8ec96-120">To determine how ports are configured</span></span>  
  
1. <span data-ttu-id="8ec96-121">W [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] programie [!INCLUDE[wxp](../../../../includes/wxp-md.md)]lub użyj narzędzia HttpCfg. exe, aby wyświetlić bieżącą konfigurację portu przy użyciu **zapytań** i przełączników **SSL** , jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="8ec96-121">In [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] or [!INCLUDE[wxp](../../../../includes/wxp-md.md)], use the HttpCfg.exe tool to view the current port configuration, using the **query** and **ssl** switches, as shown in the following example.</span></span>  
  
    ```console
    httpcfg query ssl  
    ```  
  
2. <span data-ttu-id="8ec96-122">W [!INCLUDE[wv](../../../../includes/wv-md.md)]programie Użyj narzędzia Netsh. exe, aby wyświetlić bieżącą konfigurację portu, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="8ec96-122">In [!INCLUDE[wv](../../../../includes/wv-md.md)], use the Netsh.exe tool to view the current port configuration, as shown in the following example.</span></span>  
  
    ```console  
    netsh http show sslcert  
    ```  
  
### <a name="to-get-a-certificates-thumbprint"></a><span data-ttu-id="8ec96-123">Aby uzyskać odcisk palca certyfikatu</span><span class="sxs-lookup"><span data-stu-id="8ec96-123">To get a certificate's thumbprint</span></span>  
  
1. <span data-ttu-id="8ec96-124">Za pomocą przystawki MMC Certyfikaty Znajdź certyfikat X. 509, który ma zamierzony cel uwierzytelniania klientów.</span><span class="sxs-lookup"><span data-stu-id="8ec96-124">Use the Certificates MMC snap-in to find an X.509 certificate that has an intended purpose of client authentication.</span></span> <span data-ttu-id="8ec96-125">Aby uzyskać więcej informacji, zobacz [jak: Wyświetlanie certyfikatów z przystawką](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md)programu MMC.</span><span class="sxs-lookup"><span data-stu-id="8ec96-125">For more information, see [How to: View Certificates with the MMC Snap-in](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).</span></span>  
  
2. <span data-ttu-id="8ec96-126">Uzyskaj dostęp do odcisku palca certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="8ec96-126">Access the certificate's thumbprint.</span></span> <span data-ttu-id="8ec96-127">Aby uzyskać więcej informacji, zobacz [jak: Pobieranie odcisku palca certyfikatu](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="8ec96-127">For more information, see [How to: Retrieve the Thumbprint of a Certificate](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).</span></span>  
  
3. <span data-ttu-id="8ec96-128">Skopiuj odcisk palca certyfikatu do edytora tekstu, takiego jak Notatnik.</span><span class="sxs-lookup"><span data-stu-id="8ec96-128">Copy the thumbprint of the certificate into a text editor, such as Notepad.</span></span>  
  
4. <span data-ttu-id="8ec96-129">Usuń wszystkie spacje między znakami szesnastkowymi.</span><span class="sxs-lookup"><span data-stu-id="8ec96-129">Remove all spaces between the hexadecimal characters.</span></span> <span data-ttu-id="8ec96-130">Jednym ze sposobów osiągnięcia tego celu jest użycie funkcji znajdowania i zamieniania edytora tekstu oraz zastępowanie każdej spacji znakiem null.</span><span class="sxs-lookup"><span data-stu-id="8ec96-130">One way to accomplish this is to use the text editor's find-and-replace feature and replace each space with a null character.</span></span>  
  
### <a name="to-bind-an-ssl-certificate-to-a-port-number"></a><span data-ttu-id="8ec96-131">Aby powiązać certyfikat protokołu SSL z numerem portu</span><span class="sxs-lookup"><span data-stu-id="8ec96-131">To bind an SSL certificate to a port number</span></span>  
  
1. <span data-ttu-id="8ec96-132">W [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] systemie [!INCLUDE[wxp](../../../../includes/wxp-md.md)]lub użyj narzędzia HttpCfg. exe w trybie "Set" w magazynie SSL (SSL), aby powiązać certyfikat z numerem portu.</span><span class="sxs-lookup"><span data-stu-id="8ec96-132">In [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] or [!INCLUDE[wxp](../../../../includes/wxp-md.md)], use the HttpCfg.exe tool in "set" mode on the Secure Sockets Layer (SSL) store to bind the certificate to a port number.</span></span> <span data-ttu-id="8ec96-133">Narzędzie używa odcisku palca do identyfikowania certyfikatu, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="8ec96-133">The tool uses the thumbprint to identify the certificate, as shown in the following example.</span></span>  
  
    ```console  
    httpcfg set ssl -i 0.0.0.0:8012 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6  
    ```  
  
    - <span data-ttu-id="8ec96-134">Przełącznik **-i** ma składnię `IP`:`port` i instruuje narzędzie, aby ustawić certyfikat na port 8012 komputera.</span><span class="sxs-lookup"><span data-stu-id="8ec96-134">The **-i** switch has the syntax of `IP`:`port` and instructs the tool to set the certificate to port 8012 of the computer.</span></span> <span data-ttu-id="8ec96-135">Opcjonalnie cztery zera, które poprzedzają liczbę, można również zastąpić rzeczywistym adresem IP komputera.</span><span class="sxs-lookup"><span data-stu-id="8ec96-135">Optionally, the four zeroes that precede the number can also be replaced by the actual IP address of the computer.</span></span>  
  
    - <span data-ttu-id="8ec96-136">Przełącznik **-h** określa odcisk palca certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="8ec96-136">The **-h** switch specifies the thumbprint of the certificate.</span></span>  
  
2. <span data-ttu-id="8ec96-137">W [!INCLUDE[wv](../../../../includes/wv-md.md)]programie Użyj narzędzia Netsh. exe, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="8ec96-137">In [!INCLUDE[wv](../../../../includes/wv-md.md)], use the Netsh.exe tool, as shown in the following example.</span></span>  
  
    ```console  
    netsh http add sslcert ipport=0.0.0.0:8000 certhash=0000000000003ed9cd0c315bbb6dc1c08da5e6 appid={00112233-4455-6677-8899-AABBCCDDEEFF}   
    ```  
  
    - <span data-ttu-id="8ec96-138">Parametr **certhash** określa odcisk palca certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="8ec96-138">The **certhash** parameter specifies the thumbprint of the certificate.</span></span>  
  
    - <span data-ttu-id="8ec96-139">Parametr **IPPORT** określa adres IP i port oraz działa podobnie jak w **przypadku przełącznika Httpcfg** . exe opisanego w opisie.</span><span class="sxs-lookup"><span data-stu-id="8ec96-139">The **ipport** parameter specifies the IP address and port, and functions just like the **-i** switch of the Httpcfg.exe tool described.</span></span>  
  
    - <span data-ttu-id="8ec96-140">Identyfikator **AppID** jest identyfikatorem GUID, który może służyć do identyfikowania aplikacji będącej właścicielem.</span><span class="sxs-lookup"><span data-stu-id="8ec96-140">The **appid** parameter is a GUID that can be used to identify the owning application.</span></span>  
  
### <a name="to-bind-an-ssl-certificate-to-a-port-number-and-support-client-certificates"></a><span data-ttu-id="8ec96-141">Aby powiązać certyfikat protokołu SSL z numerem portu i obsługiwać certyfikaty klienta</span><span class="sxs-lookup"><span data-stu-id="8ec96-141">To bind an SSL certificate to a port number and support client certificates</span></span>  
  
1. <span data-ttu-id="8ec96-142">W [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] programie [!INCLUDE[wxp](../../../../includes/wxp-md.md)]lub, aby obsługiwać klientów, którzy uwierzytelniają się za pomocą certyfikatów X. 509 w warstwie transportowej, postępuj zgodnie z powyższą procedurą, ale Przekaż dodatkowy parametr wiersza polecenia do HttpCfg. exe, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="8ec96-142">In [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] or [!INCLUDE[wxp](../../../../includes/wxp-md.md)], to support clients that authenticate with X.509 certificates at the transport layer, follow the preceding procedure but pass an additional command-line parameter to HttpCfg.exe, as shown in the following example.</span></span>  
  
    ```console  
    httpcfg set ssl -i 0.0.0.0:8012 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6 -f 2  
    ```  
  
     <span data-ttu-id="8ec96-143">Przełącznik **-f** ma składnię, gdzie `n` n jest liczbą z zakresu od 1 do 7.</span><span class="sxs-lookup"><span data-stu-id="8ec96-143">The **-f** switch has the syntax of `n` where n is a number between 1 and 7.</span></span> <span data-ttu-id="8ec96-144">Wartość 2, jak pokazano w powyższym przykładzie, umożliwia korzystanie z certyfikatów klienta w warstwie transportowej.</span><span class="sxs-lookup"><span data-stu-id="8ec96-144">A value of 2, as shown in the preceding example, enables client certificates at the transport layer.</span></span> <span data-ttu-id="8ec96-145">Wartość 3 włącza certyfikaty klienta i mapuje te certyfikaty na konto systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="8ec96-145">A value of 3 enables client certificates and maps those certificates to a Windows account.</span></span> <span data-ttu-id="8ec96-146">Zapoznaj się z tematem zachowanie innych wartości w pomocy programu HttpCfg. exe.</span><span class="sxs-lookup"><span data-stu-id="8ec96-146">See HttpCfg.exe Help for the behavior of other values.</span></span>  
  
2. <span data-ttu-id="8ec96-147">W [!INCLUDE[wv](../../../../includes/wv-md.md)]programie w celu obsługi klientów uwierzytelnianych za pomocą certyfikatów X. 509 w warstwie transportowej postępuj zgodnie z poprzednią procedurą, ale z dodatkowym parametrem, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="8ec96-147">In [!INCLUDE[wv](../../../../includes/wv-md.md)], to support clients that authenticate with X.509 certificates at the transport layer, follow the preceding procedure, but with an additional parameter, as shown in the following example.</span></span>  
  
    ```console  
    netsh http add sslcert ipport=0.0.0.0:8000 certhash=0000000000003ed9cd0c315bbb6dc1c08da5e6 appid={00112233-4455-6677-8899-AABBCCDDEEFF} clientcertnegotiation=enable  
    ```  
  
### <a name="to-delete-an-ssl-certificate-from-a-port-number"></a><span data-ttu-id="8ec96-148">Aby usunąć certyfikat SSL z numeru portu</span><span class="sxs-lookup"><span data-stu-id="8ec96-148">To delete an SSL certificate from a port number</span></span>  
  
1. <span data-ttu-id="8ec96-149">Użyj narzędzia HttpCfg. exe lub netsh. exe, aby zobaczyć porty i odciski palców wszystkich powiązań na komputerze.</span><span class="sxs-lookup"><span data-stu-id="8ec96-149">Use the HttpCfg.exe or Netsh.exe tool to see the ports and thumbprints of all bindings on the computer.</span></span> <span data-ttu-id="8ec96-150">Aby wydrukować informacje na dysku, użyj znaku przekierowania ">", jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="8ec96-150">To print the information to disk, use the redirection character ">", as shown in the following example.</span></span>  
  
    ```console  
    httpcfg query ssl>myMachinePorts.txt  
    ```
  
2. <span data-ttu-id="8ec96-151">W [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] programie [!INCLUDE[wxp](../../../../includes/wxp-md.md)]lub użyj narzędzia HttpCfg. exe ze słowami kluczowymi **delete** i **SSL** .</span><span class="sxs-lookup"><span data-stu-id="8ec96-151">In [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] or [!INCLUDE[wxp](../../../../includes/wxp-md.md)], use the HttpCfg.exe tool with the **delete** and **ssl** keywords.</span></span> <span data-ttu-id="8ec96-152">Aby`IP`określićodciskpalca, należy **użyć przełącznika** **-i.** `port`</span><span class="sxs-lookup"><span data-stu-id="8ec96-152">Use the **-i** switch to specify the `IP`:`port` number, and the **-h** switch to specify the thumbprint.</span></span>  
  
    ```console  
    httpcfg delete ssl -i 0.0.0.0:8005 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6  
    ```  
  
3. <span data-ttu-id="8ec96-153">W [!INCLUDE[wv](../../../../includes/wv-md.md)]programie Użyj narzędzia Netsh. exe, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="8ec96-153">In [!INCLUDE[wv](../../../../includes/wv-md.md)], use the Netsh.exe tool, as shown in the following example.</span></span>  
  
    ```console  
    Netsh http delete sslcert ipport=0.0.0.0:8005  
    ```  
  
## <a name="example"></a><span data-ttu-id="8ec96-154">Przykład</span><span class="sxs-lookup"><span data-stu-id="8ec96-154">Example</span></span>  
 <span data-ttu-id="8ec96-155">Poniższy kod przedstawia sposób tworzenia usługi samodzielnej przy użyciu <xref:System.ServiceModel.WSHttpBinding> klasy ustawionej na zabezpieczenia transportu.</span><span class="sxs-lookup"><span data-stu-id="8ec96-155">The following code shows how to create a self-hosted service using the <xref:System.ServiceModel.WSHttpBinding> class set to transport security.</span></span> <span data-ttu-id="8ec96-156">Podczas tworzenia aplikacji należy określić numer portu w adresie.</span><span class="sxs-lookup"><span data-stu-id="8ec96-156">When creating an application, specify the port number in the address.</span></span>  
  
 [!code-csharp[c_WsHttpService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wshttpservice/cs/source.cs#3)]
 [!code-vb[c_WsHttpService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wshttpservice/vb/source.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="8ec96-157">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8ec96-157">See also</span></span>

- [<span data-ttu-id="8ec96-158">Zabezpieczenia transportu HTTP</span><span class="sxs-lookup"><span data-stu-id="8ec96-158">HTTP Transport Security</span></span>](../../../../docs/framework/wcf/feature-details/http-transport-security.md)
