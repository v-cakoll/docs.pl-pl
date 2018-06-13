---
title: 'Instrukcje: Wyświetlanie certyfikatów w przystawce programu MMC'
ms.date: 03/30/2017
helpviewer_keywords:
- certificates [WCF], viewing with the MMC snap-in
ms.assetid: 2b8782aa-ebb4-4ee7-974b-90299e356dc5
ms.openlocfilehash: d924121b9d9fa267fa7d1ada13c9dc5f5bf1523d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33493353"
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
  
12. Opcjonalna. Aby wyświetlić certyfikaty dla konta, powtórz kroki od 3 do 6. W kroku 7, zamiast zaznaczania **konto komputera**, kliknij przycisk **Moje konto** i powtórz kroki od 8 do 10.  
  
13. Opcjonalna. Na **pliku** menu, kliknij przycisk **zapisać** lub **Zapisz jako**. Zapisz plik konsoli do użytku w przyszłości.  
  
## <a name="viewing-certificates-with-internet-explorer"></a>Wyświetlanie certyfikatów w programie Internet Explorer  
 Można również wyświetlić, eksportowanie, importowania i usunąć certyfikaty w programie Internet Explorer.  
  
#### <a name="to-view-certificates-with-internet-explorer"></a>Aby wyświetlić certyfikaty z programem Internet Explorer  
  
1.  W programie Internet Explorer, kliknij przycisk **narzędzia**, następnie kliknij przycisk **Opcje internetowe** do wyświetlenia **Opcje internetowe** okno dialogowe.  
  
2.  Kliknij przycisk **zawartości** kartę.  
  
3.  W obszarze **certyfikaty**, kliknij przycisk **certyfikaty**.  
  
4.  Aby wyświetlić szczegóły każdego certyfikatu, zaznacz certyfikat i kliknij **widoku**.  
  
## <a name="see-also"></a>Zobacz też  
 [Praca z certyfikatami](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [Instrukcje: tworzenie certyfikatów tymczasowych do używania w trakcie opracowywania](../../../../docs/framework/wcf/feature-details/how-to-create-temporary-certificates-for-use-during-development.md)  
 [Instrukcje: pobieranie odcisku palca certyfikatu](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md)
