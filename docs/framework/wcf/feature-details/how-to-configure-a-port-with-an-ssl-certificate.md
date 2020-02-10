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
ms.openlocfilehash: 99a08c9714e8f8cef0c1c96ac7f890d163324b44
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2020
ms.locfileid: "77095024"
---
# <a name="how-to-configure-a-port-with-an-ssl-certificate"></a><span data-ttu-id="5c22b-102">Instrukcje: Konfigurowanie portu z certyfikatem SSL</span><span class="sxs-lookup"><span data-stu-id="5c22b-102">How to: Configure a Port with an SSL Certificate</span></span>

<span data-ttu-id="5c22b-103">Podczas tworzenia samohostowanej usługi Windows Communication Foundation (WCF) z klasą <xref:System.ServiceModel.WSHttpBinding>, która korzysta z zabezpieczeń transportu, należy również skonfigurować port za pomocą certyfikatu X. 509.</span><span class="sxs-lookup"><span data-stu-id="5c22b-103">When creating a self-hosted Windows Communication Foundation (WCF) service with the <xref:System.ServiceModel.WSHttpBinding> class that uses transport security, you must also configure a port with an X.509 certificate.</span></span> <span data-ttu-id="5c22b-104">Jeśli nie tworzysz usługi samodzielnej, możesz hostować usługę w Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="5c22b-104">If you are not creating a self-hosted service, you can host your service on Internet Information Services (IIS).</span></span> <span data-ttu-id="5c22b-105">Aby uzyskać więcej informacji, zobacz [zabezpieczenia transportu HTTP](../../../../docs/framework/wcf/feature-details/http-transport-security.md).</span><span class="sxs-lookup"><span data-stu-id="5c22b-105">For more information, see [HTTP Transport Security](../../../../docs/framework/wcf/feature-details/http-transport-security.md).</span></span>  
  
 <span data-ttu-id="5c22b-106">Aby skonfigurować port, używane narzędzie zależy od systemu operacyjnego działającego na komputerze.</span><span class="sxs-lookup"><span data-stu-id="5c22b-106">To configure a port, the tool you use depends on the operating system that is running on your machine.</span></span>  
  
 <span data-ttu-id="5c22b-107">Jeśli korzystasz z systemu Windows Server 2003, użyj narzędzia HttpCfg. exe.</span><span class="sxs-lookup"><span data-stu-id="5c22b-107">If you are running Windows Server 2003, use the HttpCfg.exe tool.</span></span> <span data-ttu-id="5c22b-108">W systemie Windows Server 2003 to narzędzie jest zainstalowane.</span><span class="sxs-lookup"><span data-stu-id="5c22b-108">On Windows Server 2003, this tool is installed.</span></span> <span data-ttu-id="5c22b-109">Aby uzyskać więcej informacji, zobacz [Httpcfg Overview (przegląd](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc787508(v=ws.10))).</span><span class="sxs-lookup"><span data-stu-id="5c22b-109">For more information, see [Httpcfg Overview](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc787508(v=ws.10)).</span></span> <span data-ttu-id="5c22b-110">[Dokumentacja narzędzi pomocy technicznej systemu Windows](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc781601(v=ws.10)) objaśnia składnię dla narzędzia HttpCfg. exe.</span><span class="sxs-lookup"><span data-stu-id="5c22b-110">The [Windows Support Tools documentation](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc781601(v=ws.10)) explains the syntax for the Httpcfg.exe tool.</span></span>  
  
 <span data-ttu-id="5c22b-111">Jeśli korzystasz z systemu Windows Vista, użyj narzędzia Netsh. exe, które jest już zainstalowane.</span><span class="sxs-lookup"><span data-stu-id="5c22b-111">If you are running Windows Vista, use the Netsh.exe tool that is already installed.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="5c22b-112">Modyfikowanie certyfikatów przechowywanych na komputerze wymaga uprawnień administracyjnych.</span><span class="sxs-lookup"><span data-stu-id="5c22b-112">Modifying certificates stored on the computer requires administrative privileges.</span></span>  
  
## <a name="determine-how-ports-are-configured"></a><span data-ttu-id="5c22b-113">Określanie sposobu konfiguracji portów</span><span class="sxs-lookup"><span data-stu-id="5c22b-113">Determine how ports are configured</span></span>  
  
1. <span data-ttu-id="5c22b-114">W systemie Windows Server 2003 lub Windows XP Użyj narzędzia HttpCfg. exe, aby wyświetlić bieżącą konfigurację portu przy użyciu **zapytań** i przełączników **SSL** , jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="5c22b-114">In Windows Server 2003 or Windows XP, use the HttpCfg.exe tool to view the current port configuration, using the **query** and **ssl** switches, as shown in the following example.</span></span>  
  
    ```console
    httpcfg query ssl  
    ```  
  
2. <span data-ttu-id="5c22b-115">W systemie Windows Vista Użyj narzędzia Netsh. exe, aby wyświetlić bieżącą konfigurację portu, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="5c22b-115">In Windows Vista, use the Netsh.exe tool to view the current port configuration, as shown in the following example.</span></span>  
  
    ```console  
    netsh http show sslcert  
    ```  
  
## <a name="get-a-certificates-thumbprint"></a><span data-ttu-id="5c22b-116">Pobieranie odcisku palca certyfikatu</span><span class="sxs-lookup"><span data-stu-id="5c22b-116">Get a certificate's thumbprint</span></span>  
  
1. <span data-ttu-id="5c22b-117">Za pomocą przystawki MMC Certyfikaty Znajdź certyfikat X. 509, który ma zamierzony cel uwierzytelniania klientów.</span><span class="sxs-lookup"><span data-stu-id="5c22b-117">Use the Certificates MMC snap-in to find an X.509 certificate that has an intended purpose of client authentication.</span></span> <span data-ttu-id="5c22b-118">Aby uzyskać więcej informacji, zobacz [How to: View Certificates za pomocą przystawki MMC](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).</span><span class="sxs-lookup"><span data-stu-id="5c22b-118">For more information, see [How to: View Certificates with the MMC Snap-in](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).</span></span>  
  
2. <span data-ttu-id="5c22b-119">Uzyskaj dostęp do odcisku palca certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="5c22b-119">Access the certificate's thumbprint.</span></span> <span data-ttu-id="5c22b-120">Aby uzyskać więcej informacji, zobacz [Instrukcje: Pobieranie odcisku palca certyfikatu](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="5c22b-120">For more information, see [How to: Retrieve the Thumbprint of a Certificate](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).</span></span>  
  
3. <span data-ttu-id="5c22b-121">Skopiuj odcisk palca certyfikatu do edytora tekstu, takiego jak Notatnik.</span><span class="sxs-lookup"><span data-stu-id="5c22b-121">Copy the thumbprint of the certificate into a text editor, such as Notepad.</span></span>  
  
4. <span data-ttu-id="5c22b-122">Usuń wszystkie spacje między znakami szesnastkowymi.</span><span class="sxs-lookup"><span data-stu-id="5c22b-122">Remove all spaces between the hexadecimal characters.</span></span> <span data-ttu-id="5c22b-123">Jednym ze sposobów osiągnięcia tego celu jest użycie funkcji znajdowania i zamieniania edytora tekstu oraz zastępowanie każdej spacji znakiem null.</span><span class="sxs-lookup"><span data-stu-id="5c22b-123">One way to accomplish this is to use the text editor's find-and-replace feature and replace each space with a null character.</span></span>  
  
## <a name="bind-an-ssl-certificate-to-a-port-number"></a><span data-ttu-id="5c22b-124">Powiąż certyfikat SSL z numerem portu</span><span class="sxs-lookup"><span data-stu-id="5c22b-124">Bind an SSL certificate to a port number</span></span>  
  
1. <span data-ttu-id="5c22b-125">W systemie Windows Server 2003 lub Windows XP Użyj narzędzia HttpCfg. exe w trybie "Set" w magazynie SSL (SSL), aby powiązać certyfikat z numerem portu.</span><span class="sxs-lookup"><span data-stu-id="5c22b-125">In Windows Server 2003 or Windows XP, use the HttpCfg.exe tool in "set" mode on the Secure Sockets Layer (SSL) store to bind the certificate to a port number.</span></span> <span data-ttu-id="5c22b-126">Narzędzie używa odcisku palca do identyfikowania certyfikatu, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="5c22b-126">The tool uses the thumbprint to identify the certificate, as shown in the following example.</span></span>  
  
    ```console  
    httpcfg set ssl -i 0.0.0.0:8012 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6  
    ```  
  
    - <span data-ttu-id="5c22b-127">Przełącznik **-i** ma składnię `IP`:`port` i instruuje narzędzie, aby ustawił certyfikat na port 8012 na komputerze.</span><span class="sxs-lookup"><span data-stu-id="5c22b-127">The **-i** switch has the syntax of `IP`:`port` and instructs the tool to set the certificate to port 8012 of the computer.</span></span> <span data-ttu-id="5c22b-128">Opcjonalnie cztery zera, które poprzedzają liczbę, można również zastąpić rzeczywistym adresem IP komputera.</span><span class="sxs-lookup"><span data-stu-id="5c22b-128">Optionally, the four zeroes that precede the number can also be replaced by the actual IP address of the computer.</span></span>  
  
    - <span data-ttu-id="5c22b-129">Przełącznik **-h** określa odcisk palca certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="5c22b-129">The **-h** switch specifies the thumbprint of the certificate.</span></span>  
  
2. <span data-ttu-id="5c22b-130">W systemie Windows Vista Użyj narzędzia Netsh. exe, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="5c22b-130">In Windows Vista, use the Netsh.exe tool, as shown in the following example.</span></span>  
  
    ```console  
    netsh http add sslcert ipport=0.0.0.0:8000 certhash=0000000000003ed9cd0c315bbb6dc1c08da5e6 appid={00112233-4455-6677-8899-AABBCCDDEEFF}   
    ```  
  
    - <span data-ttu-id="5c22b-131">Parametr **certhash** określa odcisk palca certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="5c22b-131">The **certhash** parameter specifies the thumbprint of the certificate.</span></span>  
  
    - <span data-ttu-id="5c22b-132">Parametr **IPPORT** określa adres IP i port oraz działa podobnie jak w **przypadku przełącznika Httpcfg** . exe opisanego w opisie.</span><span class="sxs-lookup"><span data-stu-id="5c22b-132">The **ipport** parameter specifies the IP address and port, and functions just like the **-i** switch of the Httpcfg.exe tool described.</span></span>  
  
    - <span data-ttu-id="5c22b-133">Identyfikator **AppID** jest identyfikatorem GUID, który może służyć do identyfikowania aplikacji będącej właścicielem.</span><span class="sxs-lookup"><span data-stu-id="5c22b-133">The **appid** parameter is a GUID that can be used to identify the owning application.</span></span>  
  
## <a name="bind-an-ssl-certificate-to-a-port-number-and-support-client-certificates"></a><span data-ttu-id="5c22b-134">Powiąż certyfikat SSL z numerem portu i obsługuj certyfikaty klienta</span><span class="sxs-lookup"><span data-stu-id="5c22b-134">Bind an SSL certificate to a port number and support client certificates</span></span>  
  
1. <span data-ttu-id="5c22b-135">W systemie Windows Server 2003 lub Windows XP do obsługi klientów uwierzytelnianych za pomocą certyfikatów X. 509 w warstwie transportowej wykonaj powyższą procedurę, ale Przekaż dodatkowy parametr wiersza polecenia do HttpCfg. exe, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="5c22b-135">In Windows Server 2003 or Windows XP, to support clients that authenticate with X.509 certificates at the transport layer, follow the preceding procedure but pass an additional command-line parameter to HttpCfg.exe, as shown in the following example.</span></span>  
  
    ```console  
    httpcfg set ssl -i 0.0.0.0:8012 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6 -f 2  
    ```  
  
     <span data-ttu-id="5c22b-136">Przełącznik **-f** ma składnię `n` gdzie n jest liczbą z zakresu od 1 do 7.</span><span class="sxs-lookup"><span data-stu-id="5c22b-136">The **-f** switch has the syntax of `n` where n is a number between 1 and 7.</span></span> <span data-ttu-id="5c22b-137">Wartość 2, jak pokazano w powyższym przykładzie, umożliwia korzystanie z certyfikatów klienta w warstwie transportowej.</span><span class="sxs-lookup"><span data-stu-id="5c22b-137">A value of 2, as shown in the preceding example, enables client certificates at the transport layer.</span></span> <span data-ttu-id="5c22b-138">Wartość 3 włącza certyfikaty klienta i mapuje te certyfikaty na konto systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="5c22b-138">A value of 3 enables client certificates and maps those certificates to a Windows account.</span></span> <span data-ttu-id="5c22b-139">Zapoznaj się z tematem zachowanie innych wartości w pomocy programu HttpCfg. exe.</span><span class="sxs-lookup"><span data-stu-id="5c22b-139">See HttpCfg.exe Help for the behavior of other values.</span></span>  
  
2. <span data-ttu-id="5c22b-140">W systemie Windows Vista w celu obsługi klientów uwierzytelnianych za pomocą certyfikatów X. 509 w warstwie transportowej Wykonaj poprzednią procedurę, ale z dodatkowym parametrem, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="5c22b-140">In Windows Vista, to support clients that authenticate with X.509 certificates at the transport layer, follow the preceding procedure, but with an additional parameter, as shown in the following example.</span></span>  
  
    ```console  
    netsh http add sslcert ipport=0.0.0.0:8000 certhash=0000000000003ed9cd0c315bbb6dc1c08da5e6 appid={00112233-4455-6677-8899-AABBCCDDEEFF} clientcertnegotiation=enable  
    ```  
  
## <a name="delete-an-ssl-certificate-from-a-port-number"></a><span data-ttu-id="5c22b-141">Usuwanie certyfikatu SSL z numeru portu</span><span class="sxs-lookup"><span data-stu-id="5c22b-141">Delete an SSL certificate from a port number</span></span>  
  
1. <span data-ttu-id="5c22b-142">Użyj narzędzia HttpCfg. exe lub netsh. exe, aby zobaczyć porty i odciski palców wszystkich powiązań na komputerze.</span><span class="sxs-lookup"><span data-stu-id="5c22b-142">Use the HttpCfg.exe or Netsh.exe tool to see the ports and thumbprints of all bindings on the computer.</span></span> <span data-ttu-id="5c22b-143">Aby wydrukować informacje na dysku, użyj znaku przekierowania ">", jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="5c22b-143">To print the information to disk, use the redirection character ">", as shown in the following example.</span></span>  
  
    ```console  
    httpcfg query ssl>myMachinePorts.txt  
    ```
  
2. <span data-ttu-id="5c22b-144">W systemie Windows Server 2003 lub Windows XP Użyj narzędzia HttpCfg. exe ze słowami kluczowymi **delete** i **SSL** .</span><span class="sxs-lookup"><span data-stu-id="5c22b-144">In Windows Server 2003 or Windows XP, use the HttpCfg.exe tool with the **delete** and **ssl** keywords.</span></span> <span data-ttu-id="5c22b-145">Użyj przełącznika **-i** , aby określić `IP`: numer`port` i przełącznik **-h** , aby określić odcisk palca.</span><span class="sxs-lookup"><span data-stu-id="5c22b-145">Use the **-i** switch to specify the `IP`:`port` number, and the **-h** switch to specify the thumbprint.</span></span>  
  
    ```console  
    httpcfg delete ssl -i 0.0.0.0:8005 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6  
    ```  
  
3. <span data-ttu-id="5c22b-146">W systemie Windows Vista Użyj narzędzia Netsh. exe, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="5c22b-146">In Windows Vista, use the Netsh.exe tool, as shown in the following example.</span></span>  
  
    ```console  
    Netsh http delete sslcert ipport=0.0.0.0:8005  
    ```  
  
## <a name="example"></a><span data-ttu-id="5c22b-147">Przykład</span><span class="sxs-lookup"><span data-stu-id="5c22b-147">Example</span></span>  

 <span data-ttu-id="5c22b-148">Poniższy kod przedstawia sposób tworzenia usługi samodzielnej przy użyciu klasy <xref:System.ServiceModel.WSHttpBinding> ustawionej na zabezpieczenia transportu.</span><span class="sxs-lookup"><span data-stu-id="5c22b-148">The following code shows how to create a self-hosted service using the <xref:System.ServiceModel.WSHttpBinding> class set to transport security.</span></span> <span data-ttu-id="5c22b-149">Podczas tworzenia aplikacji należy określić numer portu w adresie.</span><span class="sxs-lookup"><span data-stu-id="5c22b-149">When creating an application, specify the port number in the address.</span></span>  
  
 [!code-csharp[c_WsHttpService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wshttpservice/cs/source.cs#3)]
 [!code-vb[c_WsHttpService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wshttpservice/vb/source.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="5c22b-150">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5c22b-150">See also</span></span>

- [<span data-ttu-id="5c22b-151">Zabezpieczenia transportu HTTP</span><span class="sxs-lookup"><span data-stu-id="5c22b-151">HTTP Transport Security</span></span>](../../../../docs/framework/wcf/feature-details/http-transport-security.md)
