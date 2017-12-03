---
title: "Instrukcje: Wyświetlanie certyfikatów w przystawce programu MMC"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: certificates [WCF], viewing with the MMC snap-in
ms.assetid: 2b8782aa-ebb4-4ee7-974b-90299e356dc5
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5981e68ebe2870870fff5e92e87d7582ac2c42b5
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-view-certificates-with-the-mmc-snap-in"></a>Instrukcje: Wyświetlanie certyfikatów w przystawce programu MMC
Typowe typ poświadczeń jest certyfikat X.509. Podczas tworzenia bezpiecznych usług lub klientów, można określić, można użyć certyfikatu jako poświadczeń klienta lub usługi przy użyciu metod, takich jak <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> metody. Metoda wymaga różnych parametrów, takich jak magazyn, gdy certyfikat jest przechowywany i wartości używana podczas wyszukiwania certyfikatu. W poniższej procedurze przedstawiono sposób badania w magazynie na komputerze można znaleźć odpowiedniego certyfikatu. Na przykład wyszukiwanie odcisk palca certyfikatu, zobacz [porady: Pobieranie odcisku palca certyfikatu](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).  
  
### <a name="to-view-certificates-in-the-mmc-snap-in"></a>Aby wyświetlić certyfikaty w przystawce programu MMC  
  
1.  Otwórz okno wiersza polecenia.  
  
2.  Typ `mmc` i naciśnij klawisz ENTER. Należy pamiętać, że aby wyświetlić certyfikaty w magazynie komputera lokalnego, musi należeć do roli administratora.  
  
3.  Na **pliku** menu, kliknij przycisk **przystawka Dodaj lub usuń**.  
  
4.  Kliknij przycisk **Dodaj**.  
  
5.  W **Dodawanie przystawki autonomicznej** okno dialogowe, wybierz opcję **certyfikaty**.  
  
6.  Kliknij przycisk **Dodaj**.  
  
7.  W **certyfikatów przystawki** okno dialogowe, wybierz opcję **konto komputera** i kliknij przycisk **dalej**. Opcjonalnie można wybrać **Moje konto** lub **konto usługi**. Jeśli nie jesteś administratorem komputera, mogą zarządzać certyfikatami tylko dla tego konta użytkownika.  
  
8.  W **Wybieranie komputera** okno dialogowe, kliknij przycisk **Zakończ**.  
  
9. W **Dodawanie przystawki autonomicznej** okno dialogowe, kliknij przycisk **Zamknij**.  
  
10. Na **Dodaj/Usuń przystawkę** okno dialogowe, kliknij przycisk **OK**.  
  
11. W **katalog główny konsoli** okna, kliknij przycisk **certyfikaty (komputer lokalny)** Aby wyświetlić certyfikat są przechowywane na komputerze.  
  
12. Opcjonalny. Aby wyświetlić certyfikaty dla konta, powtórz kroki od 3 do 6. W kroku 7, zamiast zaznaczania **konto komputera**, kliknij przycisk **Moje konto** i powtórz kroki od 8 do 10.  
  
13. Opcjonalny. Na **pliku** menu, kliknij przycisk **zapisać** lub **Zapisz jako**. Zapisz plik konsoli do użytku w przyszłości.  
  
## <a name="viewing-certificates-with-internet-explorer"></a>Wyświetlanie certyfikatów w programie Internet Explorer  
 Można również wyświetlić, eksportowanie, importowania i usunąć certyfikaty w programie Internet Explorer.  
  
#### <a name="to-view-certificates-with-internet-explorer"></a>Aby wyświetlić certyfikaty z programem Internet Explorer  
  
1.  W programie Internet Explorer, kliknij przycisk **narzędzia**, następnie kliknij przycisk **Opcje internetowe** do wyświetlenia **Opcje internetowe** okno dialogowe.  
  
2.  Kliknij przycisk **zawartości** kartę.  
  
3.  W obszarze **certyfikaty**, kliknij przycisk **certyfikaty**.  
  
4.  Aby wyświetlić szczegóły każdego certyfikatu, zaznacz certyfikat i kliknij **widoku**.  
  
## <a name="see-also"></a>Zobacz też  
 [Praca z certyfikatami](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [Porady: Tworzenie certyfikatów tymczasowych do użytku w czasie projektowania](../../../../docs/framework/wcf/feature-details/how-to-create-temporary-certificates-for-use-during-development.md)  
 [Porady: Pobieranie odcisku palca certyfikatu](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md)
