---
title: 'Instrukcje: Konfigurowanie portu z certyfikatem SSL'
description: Dowiedz się, jak skonfigurować port za pomocą certyfikatu X. 509, który jest wymagany w przypadku samodzielnej usługi WCF z klasą WSHttpBinding za pomocą zabezpieczeń transportu.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SSL
- WCF, security mode
- WCF, security
ms.assetid: b8abcc8e-a5f5-4317-aca5-01e3c40ab24d
ms.openlocfilehash: 0eccdf916dae7b886cbc4e6563e6dfe17039c321
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247185"
---
# <a name="how-to-configure-a-port-with-an-ssl-certificate"></a><span data-ttu-id="a7261-103">Instrukcje: Konfigurowanie portu z certyfikatem SSL</span><span class="sxs-lookup"><span data-stu-id="a7261-103">How to: Configure a Port with an SSL Certificate</span></span>

<span data-ttu-id="a7261-104">Podczas tworzenia samohostowanej usługi Windows Communication Foundation (WCF) z <xref:System.ServiceModel.WSHttpBinding> klasą, która korzysta z zabezpieczeń transportu, należy również skonfigurować port za pomocą certyfikatu X. 509.</span><span class="sxs-lookup"><span data-stu-id="a7261-104">When creating a self-hosted Windows Communication Foundation (WCF) service with the <xref:System.ServiceModel.WSHttpBinding> class that uses transport security, you must also configure a port with an X.509 certificate.</span></span> <span data-ttu-id="a7261-105">Jeśli nie tworzysz usługi samodzielnej, możesz hostować usługę w Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="a7261-105">If you are not creating a self-hosted service, you can host your service on Internet Information Services (IIS).</span></span> <span data-ttu-id="a7261-106">Aby uzyskać więcej informacji, zobacz [zabezpieczenia transportu HTTP](http-transport-security.md).</span><span class="sxs-lookup"><span data-stu-id="a7261-106">For more information, see [HTTP Transport Security](http-transport-security.md).</span></span>  
  
 <span data-ttu-id="a7261-107">Aby skonfigurować port, używane narzędzie zależy od systemu operacyjnego działającego na komputerze.</span><span class="sxs-lookup"><span data-stu-id="a7261-107">To configure a port, the tool you use depends on the operating system that is running on your machine.</span></span>  
  
 <span data-ttu-id="a7261-108">Jeśli korzystasz z systemu Windows Server 2003, użyj narzędzia HttpCfg.exe.</span><span class="sxs-lookup"><span data-stu-id="a7261-108">If you are running Windows Server 2003, use the HttpCfg.exe tool.</span></span> <span data-ttu-id="a7261-109">W systemie Windows Server 2003 to narzędzie jest zainstalowane.</span><span class="sxs-lookup"><span data-stu-id="a7261-109">On Windows Server 2003, this tool is installed.</span></span> <span data-ttu-id="a7261-110">Aby uzyskać więcej informacji, zobacz [Httpcfg Overview (przegląd](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc787508(v=ws.10))).</span><span class="sxs-lookup"><span data-stu-id="a7261-110">For more information, see [Httpcfg Overview](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc787508(v=ws.10)).</span></span> <span data-ttu-id="a7261-111">[Dokumentacja narzędzi pomocy technicznej systemu Windows](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc781601(v=ws.10)) objaśnia składnię narzędzia Httpcfg.exe.</span><span class="sxs-lookup"><span data-stu-id="a7261-111">The [Windows Support Tools documentation](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc781601(v=ws.10)) explains the syntax for the Httpcfg.exe tool.</span></span>  
  
 <span data-ttu-id="a7261-112">Jeśli korzystasz z systemu Windows Vista, użyj narzędzia Netsh.exe, które jest już zainstalowane.</span><span class="sxs-lookup"><span data-stu-id="a7261-112">If you are running Windows Vista, use the Netsh.exe tool that is already installed.</span></span>
  
> [!NOTE]
> <span data-ttu-id="a7261-113">Modyfikowanie certyfikatów przechowywanych na komputerze wymaga uprawnień administracyjnych.</span><span class="sxs-lookup"><span data-stu-id="a7261-113">Modifying certificates stored on the computer requires administrative privileges.</span></span>  
  
## <a name="determine-how-ports-are-configured"></a><span data-ttu-id="a7261-114">Określanie sposobu konfiguracji portów</span><span class="sxs-lookup"><span data-stu-id="a7261-114">Determine how ports are configured</span></span>  
  
1. <span data-ttu-id="a7261-115">W systemie Windows Server 2003 lub Windows XP Użyj narzędzia HttpCfg.exe, aby wyświetlić bieżącą konfigurację portu przy użyciu **zapytań** i przełączników **SSL** , jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="a7261-115">In Windows Server 2003 or Windows XP, use the HttpCfg.exe tool to view the current port configuration, using the **query** and **ssl** switches, as shown in the following example.</span></span>  
  
    ```console
    httpcfg query ssl  
    ```  
  
2. <span data-ttu-id="a7261-116">W systemie Windows Vista Użyj narzędzia Netsh.exe, aby wyświetlić bieżącą konfigurację portu, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="a7261-116">In Windows Vista, use the Netsh.exe tool to view the current port configuration, as shown in the following example.</span></span>  
  
    ```console  
    netsh http show sslcert  
    ```  
  
## <a name="get-a-certificates-thumbprint"></a><span data-ttu-id="a7261-117">Pobieranie odcisku palca certyfikatu</span><span class="sxs-lookup"><span data-stu-id="a7261-117">Get a certificate's thumbprint</span></span>  
  
1. <span data-ttu-id="a7261-118">Za pomocą przystawki MMC Certyfikaty Znajdź certyfikat X. 509, który ma zamierzony cel uwierzytelniania klientów.</span><span class="sxs-lookup"><span data-stu-id="a7261-118">Use the Certificates MMC snap-in to find an X.509 certificate that has an intended purpose of client authentication.</span></span> <span data-ttu-id="a7261-119">Aby uzyskać więcej informacji, zobacz [How to: View Certificates za pomocą przystawki MMC](how-to-view-certificates-with-the-mmc-snap-in.md).</span><span class="sxs-lookup"><span data-stu-id="a7261-119">For more information, see [How to: View Certificates with the MMC Snap-in](how-to-view-certificates-with-the-mmc-snap-in.md).</span></span>  
  
2. <span data-ttu-id="a7261-120">Uzyskaj dostęp do odcisku palca certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="a7261-120">Access the certificate's thumbprint.</span></span> <span data-ttu-id="a7261-121">Aby uzyskać więcej informacji, zobacz [How to: Pobieranie odcisku palca certyfikatu](how-to-retrieve-the-thumbprint-of-a-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="a7261-121">For more information, see [How to: Retrieve the Thumbprint of a Certificate](how-to-retrieve-the-thumbprint-of-a-certificate.md).</span></span>  
  
3. <span data-ttu-id="a7261-122">Skopiuj odcisk palca certyfikatu do edytora tekstu, takiego jak Notatnik.</span><span class="sxs-lookup"><span data-stu-id="a7261-122">Copy the thumbprint of the certificate into a text editor, such as Notepad.</span></span>  
  
4. <span data-ttu-id="a7261-123">Usuń wszystkie spacje między znakami szesnastkowymi.</span><span class="sxs-lookup"><span data-stu-id="a7261-123">Remove all spaces between the hexadecimal characters.</span></span> <span data-ttu-id="a7261-124">Jednym ze sposobów osiągnięcia tego celu jest użycie funkcji znajdowania i zamieniania edytora tekstu oraz zastępowanie każdej spacji znakiem null.</span><span class="sxs-lookup"><span data-stu-id="a7261-124">One way to accomplish this is to use the text editor's find-and-replace feature and replace each space with a null character.</span></span>  
  
## <a name="bind-an-ssl-certificate-to-a-port-number"></a><span data-ttu-id="a7261-125">Powiąż certyfikat SSL z numerem portu</span><span class="sxs-lookup"><span data-stu-id="a7261-125">Bind an SSL certificate to a port number</span></span>  
  
1. <span data-ttu-id="a7261-126">W systemie Windows Server 2003 lub Windows XP Użyj narzędzia HttpCfg.exe w trybie "Set" w magazynie SSL (SSL), aby powiązać certyfikat z numerem portu.</span><span class="sxs-lookup"><span data-stu-id="a7261-126">In Windows Server 2003 or Windows XP, use the HttpCfg.exe tool in "set" mode on the Secure Sockets Layer (SSL) store to bind the certificate to a port number.</span></span> <span data-ttu-id="a7261-127">Narzędzie używa odcisku palca do identyfikowania certyfikatu, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="a7261-127">The tool uses the thumbprint to identify the certificate, as shown in the following example.</span></span>  
  
    ```console  
    httpcfg set ssl -i 0.0.0.0:8012 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6  
    ```  
  
    - <span data-ttu-id="a7261-128">Przełącznik **-i** ma składnię `IP` : `port` i instruuje narzędzie, aby ustawić certyfikat na port 8012 komputera.</span><span class="sxs-lookup"><span data-stu-id="a7261-128">The **-i** switch has the syntax of `IP`:`port` and instructs the tool to set the certificate to port 8012 of the computer.</span></span> <span data-ttu-id="a7261-129">Opcjonalnie cztery zera, które poprzedzają liczbę, można również zastąpić rzeczywistym adresem IP komputera.</span><span class="sxs-lookup"><span data-stu-id="a7261-129">Optionally, the four zeroes that precede the number can also be replaced by the actual IP address of the computer.</span></span>  
  
    - <span data-ttu-id="a7261-130">Przełącznik **-h** określa odcisk palca certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="a7261-130">The **-h** switch specifies the thumbprint of the certificate.</span></span>  
  
2. <span data-ttu-id="a7261-131">W systemie Windows Vista Użyj narzędzia Netsh.exe, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="a7261-131">In Windows Vista, use the Netsh.exe tool, as shown in the following example.</span></span>  
  
    ```console  
    netsh http add sslcert ipport=0.0.0.0:8000 certhash=0000000000003ed9cd0c315bbb6dc1c08da5e6 appid={00112233-4455-6677-8899-AABBCCDDEEFF}
    ```  
  
    - <span data-ttu-id="a7261-132">Parametr **certhash** określa odcisk palca certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="a7261-132">The **certhash** parameter specifies the thumbprint of the certificate.</span></span>  
  
    - <span data-ttu-id="a7261-133">Parametr **IPPORT** określa adres IP i port oraz działa podobnie jak w **przypadku przełącznika Httpcfg.exe opisanego w** opisie narzędzia.</span><span class="sxs-lookup"><span data-stu-id="a7261-133">The **ipport** parameter specifies the IP address and port, and functions just like the **-i** switch of the Httpcfg.exe tool described.</span></span>  
  
    - <span data-ttu-id="a7261-134">Identyfikator **AppID** jest identyfikatorem GUID, który może służyć do identyfikowania aplikacji będącej właścicielem.</span><span class="sxs-lookup"><span data-stu-id="a7261-134">The **appid** parameter is a GUID that can be used to identify the owning application.</span></span>  
  
## <a name="bind-an-ssl-certificate-to-a-port-number-and-support-client-certificates"></a><span data-ttu-id="a7261-135">Powiąż certyfikat SSL z numerem portu i obsługuj certyfikaty klienta</span><span class="sxs-lookup"><span data-stu-id="a7261-135">Bind an SSL certificate to a port number and support client certificates</span></span>  
  
1. <span data-ttu-id="a7261-136">W systemie Windows Server 2003 lub Windows XP w celu obsługi klientów uwierzytelnianych za pomocą certyfikatów X. 509 w warstwie transportowej Wykonaj poprzednią procedurę, ale Przekaż dodatkowy parametr wiersza polecenia do HttpCfg.exe, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="a7261-136">In Windows Server 2003 or Windows XP, to support clients that authenticate with X.509 certificates at the transport layer, follow the preceding procedure but pass an additional command-line parameter to HttpCfg.exe, as shown in the following example.</span></span>  
  
    ```console  
    httpcfg set ssl -i 0.0.0.0:8012 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6 -f 2  
    ```  
  
     <span data-ttu-id="a7261-137">Przełącznik **-f** ma składnię, `n` gdzie n jest liczbą z zakresu od 1 do 7.</span><span class="sxs-lookup"><span data-stu-id="a7261-137">The **-f** switch has the syntax of `n` where n is a number between 1 and 7.</span></span> <span data-ttu-id="a7261-138">Wartość 2, jak pokazano w powyższym przykładzie, umożliwia korzystanie z certyfikatów klienta w warstwie transportowej.</span><span class="sxs-lookup"><span data-stu-id="a7261-138">A value of 2, as shown in the preceding example, enables client certificates at the transport layer.</span></span> <span data-ttu-id="a7261-139">Wartość 3 włącza certyfikaty klienta i mapuje te certyfikaty na konto systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="a7261-139">A value of 3 enables client certificates and maps those certificates to a Windows account.</span></span> <span data-ttu-id="a7261-140">Zobacz HttpCfg.exe pomoc dotyczącą zachowania innych wartości.</span><span class="sxs-lookup"><span data-stu-id="a7261-140">See HttpCfg.exe Help for the behavior of other values.</span></span>  
  
2. <span data-ttu-id="a7261-141">W systemie Windows Vista w celu obsługi klientów uwierzytelnianych za pomocą certyfikatów X. 509 w warstwie transportowej Wykonaj poprzednią procedurę, ale z dodatkowym parametrem, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="a7261-141">In Windows Vista, to support clients that authenticate with X.509 certificates at the transport layer, follow the preceding procedure, but with an additional parameter, as shown in the following example.</span></span>  
  
    ```console  
    netsh http add sslcert ipport=0.0.0.0:8000 certhash=0000000000003ed9cd0c315bbb6dc1c08da5e6 appid={00112233-4455-6677-8899-AABBCCDDEEFF} clientcertnegotiation=enable  
    ```  
  
## <a name="delete-an-ssl-certificate-from-a-port-number"></a><span data-ttu-id="a7261-142">Usuwanie certyfikatu SSL z numeru portu</span><span class="sxs-lookup"><span data-stu-id="a7261-142">Delete an SSL certificate from a port number</span></span>  
  
1. <span data-ttu-id="a7261-143">Użyj narzędzia HttpCfg.exe lub Netsh.exe, aby zobaczyć porty i odciski palców wszystkich powiązań na komputerze.</span><span class="sxs-lookup"><span data-stu-id="a7261-143">Use the HttpCfg.exe or Netsh.exe tool to see the ports and thumbprints of all bindings on the computer.</span></span> <span data-ttu-id="a7261-144">Aby wydrukować informacje na dysku, użyj znaku przekierowania ">", jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="a7261-144">To print the information to disk, use the redirection character ">", as shown in the following example.</span></span>  
  
    ```console  
    httpcfg query ssl>myMachinePorts.txt  
    ```
  
2. <span data-ttu-id="a7261-145">W systemie Windows Server 2003 lub Windows XP Użyj narzędzia HttpCfg.exe ze słowami kluczowymi **delete** i **SSL** .</span><span class="sxs-lookup"><span data-stu-id="a7261-145">In Windows Server 2003 or Windows XP, use the HttpCfg.exe tool with the **delete** and **ssl** keywords.</span></span> <span data-ttu-id="a7261-146">Aby określić **-i** `IP` `port` odcisk palca, należy **użyć przełącznika** -i.</span><span class="sxs-lookup"><span data-stu-id="a7261-146">Use the **-i** switch to specify the `IP`:`port` number, and the **-h** switch to specify the thumbprint.</span></span>  
  
    ```console  
    httpcfg delete ssl -i 0.0.0.0:8005 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6  
    ```  
  
3. <span data-ttu-id="a7261-147">W systemie Windows Vista Użyj narzędzia Netsh.exe, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="a7261-147">In Windows Vista, use the Netsh.exe tool, as shown in the following example.</span></span>  
  
    ```console  
    Netsh http delete sslcert ipport=0.0.0.0:8005  
    ```  
  
## <a name="example"></a><span data-ttu-id="a7261-148">Przykład</span><span class="sxs-lookup"><span data-stu-id="a7261-148">Example</span></span>  

 <span data-ttu-id="a7261-149">Poniższy kod przedstawia sposób tworzenia usługi samodzielnej przy użyciu <xref:System.ServiceModel.WSHttpBinding> klasy ustawionej na zabezpieczenia transportu.</span><span class="sxs-lookup"><span data-stu-id="a7261-149">The following code shows how to create a self-hosted service using the <xref:System.ServiceModel.WSHttpBinding> class set to transport security.</span></span> <span data-ttu-id="a7261-150">Podczas tworzenia aplikacji należy określić numer portu w adresie.</span><span class="sxs-lookup"><span data-stu-id="a7261-150">When creating an application, specify the port number in the address.</span></span>  
  
 [!code-csharp[c_WsHttpService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wshttpservice/cs/source.cs#3)]
 [!code-vb[c_WsHttpService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wshttpservice/vb/source.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="a7261-151">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a7261-151">See also</span></span>

- [<span data-ttu-id="a7261-152">Zabezpieczenia transportu HTTP</span><span class="sxs-lookup"><span data-stu-id="a7261-152">HTTP Transport Security</span></span>](http-transport-security.md)
