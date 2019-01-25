---
title: 'Instrukcje: Wyświetlanie certyfikatów w przystawce programu MMC'
ms.date: 03/30/2017
helpviewer_keywords:
- certificates [WCF], viewing with the MMC snap-in
ms.assetid: 2b8782aa-ebb4-4ee7-974b-90299e356dc5
ms.openlocfilehash: 72fd6a1be2f33e1bfeb08fd43f3436627ee842e5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54521585"
---
# <a name="how-to-view-certificates-with-the-mmc-snap-in"></a>Instrukcje: Wyświetlanie certyfikatów w przystawce programu MMC
Spotykanym typem poświadczeń jest to certyfikat X.509. Podczas tworzenia bezpiecznych usług lub klientów, można określić, można użyć certyfikatu jako poświadczeń klienta lub usługi przy użyciu metod, takich jak <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> metody. Metoda wymaga różnych parametrów, takich jak magazyn, gdy certyfikat jest przechowywany i wartości do użycia podczas wyszukiwania certyfikatu. Poniższa procedura pokazuje, jak sprawdzić magazynów na komputerze, aby znaleźć odpowiedni certyfikat. Na przykład znajdowania odcisk palca certyfikatu, zobacz [jak: Pobieranie odcisku palca certyfikatu](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).  
  
### <a name="to-view-certificates-in-the-mmc-snap-in"></a>Aby wyświetlić certyfikaty w przystawce programu MMC  
  
1.  Otwórz okno wiersza polecenia.  
  
2.  Typ `mmc` i naciśnij klawisz ENTER. Należy pamiętać, że aby wyświetlić certyfikaty w magazynie komputera lokalnego, musisz mieć rolę administratora.  
  
3.  Na **pliku** menu, kliknij przycisk **Dodawanie/Usuwanie przystawki**.  
  
4.  Kliknij przycisk **Dodaj**.  
  
5.  W **Dodawanie przystawki autonomicznej** okno dialogowe, wybierz opcję **certyfikaty**.  
  
6.  Kliknij przycisk **Dodaj**.  
  
7.  W **certyfikatów w przystawce** okno dialogowe, wybierz opcję **konto komputera** i kliknij przycisk **dalej**. Opcjonalnie można wybrać **Moje konto** lub **konto usługi**. Jeśli nie jesteś administratorem komputera, można zarządzać certyfikaty tylko dla tego konta użytkownika.  
  
8.  W **Wybieranie komputera** okno dialogowe, kliknij przycisk **Zakończ**.  
  
9. W **Dodawanie przystawki autonomicznej** okno dialogowe, kliknij przycisk **Zamknij**.  
  
10. Na **Dodaj/Usuń przystawkę** okno dialogowe, kliknij przycisk **OK**.  
  
11. W **katalog główny konsoli** okna, kliknij przycisk **certyfikaty (komputer lokalny)** Aby wyświetlić certyfikat są przechowywane na komputerze.  
  
12. Opcjonalna. Aby wyświetlić certyfikaty dla konta, powtórz kroki od 3 do 6. W kroku 7, zamiast zaznaczania **konto komputera**, kliknij przycisk **Moje konto** i powtórz kroki od 8 do 10.  
  
13. Opcjonalna. Na **pliku** menu, kliknij przycisk **Zapisz** lub **Zapisz jako**. Zapisz plik konsoli do użytku w przyszłości.  
  
## <a name="viewing-certificates-with-internet-explorer"></a>Wyświetlanie certyfikatów w programie Internet Explorer  
 Można również wyświetlić, eksportować, importowanie i usunąć certyfikaty w programie Internet Explorer.  
  
#### <a name="to-view-certificates-with-internet-explorer"></a>Aby wyświetlić certyfikaty z programem Internet Explorer  
  
1.  W programie Internet Explorer kliknij **narzędzia**, następnie kliknij przycisk **Opcje internetowe** do wyświetlenia **Opcje internetowe** okno dialogowe.  
  
2.  Kliknij przycisk **zawartości** kartę.  
  
3.  W obszarze **certyfikaty**, kliknij przycisk **certyfikaty**.  
  
4.  Aby wyświetlić szczegóły każdego certyfikatu, wybierz certyfikat i kliknij **widoku**.  
  
## <a name="see-also"></a>Zobacz także
- [Praca z certyfikatami](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [Instrukcje: Tworzenie certyfikatów tymczasowych do użytku w trakcie opracowywania](../../../../docs/framework/wcf/feature-details/how-to-create-temporary-certificates-for-use-during-development.md)
- [Instrukcje: Pobieranie odcisku palca certyfikatu](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md)
