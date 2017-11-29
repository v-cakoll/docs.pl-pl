---
title: 'Porady: Pobieranie odcisku palca certyfikatu'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: certificates [WCF], retrieving thumbprint
ms.assetid: da3101aa-78cd-4c34-9652-d1f24777eeab
caps.latest.revision: "15"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4719be3d4e98407062bd246df4f14b9cbf452c74
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-retrieve-the-thumbprint-of-a-certificate"></a><span data-ttu-id="1305d-102">Porady: Pobieranie odcisku palca certyfikatu</span><span class="sxs-lookup"><span data-stu-id="1305d-102">How to: Retrieve the Thumbprint of a Certificate</span></span>
<span data-ttu-id="1305d-103">Podczas zapisywania [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] aplikacji, która używa certyfikatu X.509 do uwierzytelniania, często jest niezbędne do określenia oświadczenia, znalezione w certyfikacie.</span><span class="sxs-lookup"><span data-stu-id="1305d-103">When writing a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] application that uses an X.509 certificate for authentication, it is often necessary to specify claims found in the certificate.</span></span> <span data-ttu-id="1305d-104">Na przykład, należy podać oświadczenie odcisk palca podczas przy użyciu <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindByThumbprint> wyliczanie w <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="1305d-104">For example, you must supply a thumbprint claim when using the <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindByThumbprint> enumeration in the <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> method.</span></span> <span data-ttu-id="1305d-105">Znajdowanie wartość oświadczenia wymaga wykonania dwóch kroków.</span><span class="sxs-lookup"><span data-stu-id="1305d-105">Finding the claim value requires two steps.</span></span> <span data-ttu-id="1305d-106">Po pierwsze Otwórz przystawkę Microsoft Management Console (MMC) dla certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="1305d-106">First, open the Microsoft Management Console (MMC) snap-in for certificates.</span></span> <span data-ttu-id="1305d-107">(Zobacz [porady: wyświetlanie certyfikatów w przystawce programu MMC](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).) Po drugie zgodnie z opisem w tym miejscu, Znajdź odpowiedni certyfikat i skopiuj jego odcisk palca (lub inne wartości oświadczenia).</span><span class="sxs-lookup"><span data-stu-id="1305d-107">(See [How to: View Certificates with the MMC Snap-in](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).) Second, as described here, find an appropriate certificate and copy its thumbprint (or other claim values).</span></span>  
  
 <span data-ttu-id="1305d-108">Jeśli używasz certyfikatu dla usługi uwierzytelniania, ważne jest, aby Zanotuj wartość ustawienia **wystawiony** kolumny (pierwszej kolumny w konsoli).</span><span class="sxs-lookup"><span data-stu-id="1305d-108">If you are using a certificate for service authentication, it is important to note the value of the **Issued To** column (the first column in the console).</span></span> <span data-ttu-id="1305d-109">Gdy przy użyciu protokołu Secure Sockets Layer (SSL), zgodnie z zabezpieczeń transportu, jeden najpierw sprawdza, czy wykonywane jest porównanie bazie adres URI Uniform Resource Identifier () do usługi **wystawiony** wartość.</span><span class="sxs-lookup"><span data-stu-id="1305d-109">When using Secure Sockets Layer (SSL) as a transport security, one of the first checks done is to compare the base address Uniform Resource Identifier (URI) of a service to the **Issued To** value.</span></span> <span data-ttu-id="1305d-110">Wartości muszą być zgodne, lub proces uwierzytelniania jest zatrzymany.</span><span class="sxs-lookup"><span data-stu-id="1305d-110">The values must match or the authentication process is halted.</span></span>  
  
 <span data-ttu-id="1305d-111">Można także użyć narzędzia Makecert.exe z [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] zestawu SDK do tworzenia certyfikatów tymczasowych do użytku tylko podczas programowania.</span><span class="sxs-lookup"><span data-stu-id="1305d-111">You can also use the Makecert.exe tool from the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] SDK to create temporary certificates for use only during development.</span></span> <span data-ttu-id="1305d-112">Domyślnie jednak taki certyfikat nie jest wystawiany przez urząd certyfikacji, a nie nadaje się do celów produkcyjnych.</span><span class="sxs-lookup"><span data-stu-id="1305d-112">By default, however, such a certificate is not issued by a certification authority, and is unusable for production purposes.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="1305d-113">[Porady: Tworzenie certyfikatów tymczasowych do użycia podczas tworzenia](../../../../docs/framework/wcf/feature-details/how-to-create-temporary-certificates-for-use-during-development.md).</span><span class="sxs-lookup"><span data-stu-id="1305d-113"> [How to: Create Temporary Certificates for Use During Development](../../../../docs/framework/wcf/feature-details/how-to-create-temporary-certificates-for-use-during-development.md).</span></span>  
  
### <a name="to-retrieve-a-certificates-thumbprint"></a><span data-ttu-id="1305d-114">Aby pobrać odcisk palca certyfikatu</span><span class="sxs-lookup"><span data-stu-id="1305d-114">To retrieve a certificate's thumbprint</span></span>  
  
1.  <span data-ttu-id="1305d-115">Otwórz przystawkę Microsoft Management Console (MMC) dla certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="1305d-115">Open the Microsoft Management Console (MMC) snap-in for certificates.</span></span> <span data-ttu-id="1305d-116">(Zobacz [porady: wyświetlanie certyfikatów w przystawce programu MMC](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).)</span><span class="sxs-lookup"><span data-stu-id="1305d-116">(See [How to: View Certificates with the MMC Snap-in](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).)</span></span>  
  
2.  <span data-ttu-id="1305d-117">W **katalog główny konsoli** okna na lewe okienko, kliknij przycisk **certyfikaty (komputer lokalny)**.</span><span class="sxs-lookup"><span data-stu-id="1305d-117">In the **Console Root** window's left pane, click **Certificates (Local Computer)**.</span></span>  
  
3.  <span data-ttu-id="1305d-118">Kliknij przycisk **osobistych** folderu, aby go rozwinąć.</span><span class="sxs-lookup"><span data-stu-id="1305d-118">Click the **Personal** folder to expand it.</span></span>  
  
4.  <span data-ttu-id="1305d-119">Kliknij przycisk **certyfikaty** folderu, aby go rozwinąć.</span><span class="sxs-lookup"><span data-stu-id="1305d-119">Click the **Certificates** folder to expand it.</span></span>  
  
5.  <span data-ttu-id="1305d-120">Lista certyfikatów, zanotuj **zamierzone cele** nagłówka.</span><span class="sxs-lookup"><span data-stu-id="1305d-120">In the list of certificates, note the **Intended Purposes** heading.</span></span> <span data-ttu-id="1305d-121">Znalezienie certyfikatu, który zawiera listę **uwierzytelnianie klienta** jako przeznaczenie.</span><span class="sxs-lookup"><span data-stu-id="1305d-121">Find a certificate that lists **Client Authentication** as an intended purpose.</span></span>  
  
6.  <span data-ttu-id="1305d-122">Kliknij dwukrotnie certyfikat.</span><span class="sxs-lookup"><span data-stu-id="1305d-122">Double-click the certificate.</span></span>  
  
7.  <span data-ttu-id="1305d-123">W **certyfikatu** okno dialogowe, kliknij przycisk **szczegóły** kartę.</span><span class="sxs-lookup"><span data-stu-id="1305d-123">In the **Certificate** dialog box, click the **Details** tab.</span></span>  
  
8.  <span data-ttu-id="1305d-124">Przewiń listę pól, a następnie kliknij przycisk **odcisk palca**.</span><span class="sxs-lookup"><span data-stu-id="1305d-124">Scroll through the list of fields and click **Thumbprint**.</span></span>  
  
9. <span data-ttu-id="1305d-125">Kopiowanie znaków szesnastkowych, w polu.</span><span class="sxs-lookup"><span data-stu-id="1305d-125">Copy the hexadecimal characters from the box.</span></span> <span data-ttu-id="1305d-126">Jeśli taki odcisk palca jest używana w kodzie `X509FindType`, Usuń spacje między cyfry szesnastkowe.</span><span class="sxs-lookup"><span data-stu-id="1305d-126">If this thumbprint is used in code for the `X509FindType`, remove the spaces between the hexadecimal numbers.</span></span> <span data-ttu-id="1305d-127">Na przykład odciskiem palca "a9 09 50 2d d8 2a e4 14 33 e6 f8 38 86 b0 0d 42 77 a3 2a 7b" powinny być określone jako "a909502dd82ae41433e6f83886b00d4277a32a7b" w kodzie.</span><span class="sxs-lookup"><span data-stu-id="1305d-127">For example, the thumbprint "a9 09 50 2d d8 2a e4 14 33 e6 f8 38 86 b0 0d 42 77 a3 2a 7b" should be specified as "a909502dd82ae41433e6f83886b00d4277a32a7b" in code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1305d-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1305d-128">See Also</span></span>  
 <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindByThumbprint>  
 <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A>  
 [<span data-ttu-id="1305d-129">Porady: Konfigurowanie portu z certyfikatem SSL</span><span class="sxs-lookup"><span data-stu-id="1305d-129">How to: Configure a Port with an SSL Certificate</span></span>](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)  
 [<span data-ttu-id="1305d-130">Porady: wyświetlanie certyfikatów w przystawce programu MMC</span><span class="sxs-lookup"><span data-stu-id="1305d-130">How to: View Certificates with the MMC Snap-in</span></span>](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md)  
 [<span data-ttu-id="1305d-131">Porady: Tworzenie certyfikatów tymczasowych do użytku w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="1305d-131">How to: Create Temporary Certificates for Use During Development</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-temporary-certificates-for-use-during-development.md)
