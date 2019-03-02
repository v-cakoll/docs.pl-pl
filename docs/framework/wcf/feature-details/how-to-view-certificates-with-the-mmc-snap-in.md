---
title: 'Instrukcje: Wyświetlanie certyfikatów za pomocą przystawki programu MMC'
ms.date: 02/25/2019
helpviewer_keywords:
- certificates [WCF], viewing with the MMC snap-in
ms.assetid: 2b8782aa-ebb4-4ee7-974b-90299e356dc5
ms.openlocfilehash: 6ec86ffca9ae84a9c3276a3dd6de676919dcd2e0
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/01/2019
ms.locfileid: "57200289"
---
# <a name="how-to-view-certificates-with-the-mmc-snap-in"></a>Instrukcje: Wyświetlanie certyfikatów za pomocą przystawki programu MMC
Podczas tworzenia bezpiecznego klienta lub usługę, można użyć [certyfikatu](working-with-certificates.md) jako poświadczenie. Na przykład spotykanym typem poświadczeń jest certyfikat X.509, które są tworzone za pomocą <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A?displayProperty=nameWithType> metody. 

Istnieją trzy różne typy magazynów certyfikatów, które można sprawdzić za pomocą programu Microsoft Management Console (MMC) w systemach Windows:

- Komputer lokalny: Magazyn jest lokalne na urządzeniu i globalne dla wszystkich użytkowników na urządzeniu.

- Bieżący użytkownik: Magazyn jest lokalny dla bieżącego konta użytkownika na urządzeniu.

- Konto usługi: Magazyn jest lokalny dla określonej usługi na urządzeniu.

  
## <a name="view-certificates-in-the-mmc-snap-in"></a>Wyświetlanie certyfikatów w przystawce programu MMC 

Poniższa procedura pokazuje, jak sprawdzić magazynów na urządzeniu lokalnym, aby znaleźć odpowiedni certyfikat: 
  
1. Wybierz **Uruchom** z **Start** menu, a następnie wprowadź *mmc*. 

    Pojawi się programu MMC. 
  
2. Z **pliku** menu, wybierz opcję **Dodawanie/Usuwanie przystawki**. 
    
    **Dodawanie lub usuwanie przystawek** zostanie wyświetlone okno.
  
3. Z **dostępne przystawki** wybierz **certyfikaty**, a następnie wybierz **Dodaj**.  

    ![Dodawanie przystawki certyfikatów](./media/mmc-add-certificate-snap-in.png)
  
4. W **certyfikatów w przystawce** wybierz **konto komputera**, a następnie wybierz pozycję **dalej**. 
  
    Opcjonalnie można wybrać **Moje konto użytkownika** dla bieżącego użytkownika lub **konto usługi** określonej usługi. 

    > [!NOTE]
    > Jeśli nie masz uprawnienia administratora dla danego urządzenia, mogą zarządzać certyfikatami, tylko w przypadku konta użytkownika.
  
5. W **Wybieranie komputera** okna, pozostaw **komputera lokalnego** zaznaczone, a następnie wybierz pozycję **Zakończ**.  
  
6. W **Dodawanie lub usuwanie przystawki** wybierz **OK**.  
  
    ![Dodawanie przystawki certyfikatów](./media/mmc-certificate-snap-in-selected.png)

7. Opcjonalne: Z **pliku** menu, wybierz opcję **Zapisz** lub **Zapisz jako** można zapisać pliku konsoli MMC w celu późniejszego użycia.  

8. Zaznacz, aby wyświetlić certyfikaty w przystawce programu MMC **katalog główny konsoli** w okienku po lewej stronie, następnie rozwiń węzeł **certyfikaty (komputer lokalny)**.

    Zostanie wyświetlona lista katalogów dla każdego typu certyfikatu. Z każdego katalogu certyfikatu można wyświetlić, Eksportuj, importowanie i usunąć swoje certyfikaty.
  

## <a name="view-certificates-with-the-certificate-manager-tool"></a>Wyświetlanie certyfikatów za pomocą narzędzia Menedżer certyfikatów

Można również wyświetlić, Eksportuj, importowanie i usunąć certyfikaty przy użyciu narzędzia Menedżer certyfikatów.

### <a name="to-view-certificates-for-the-local-device"></a>Aby wyświetlić certyfikaty dla wybranego urządzenia lokalnego

1. Wybierz **Uruchom** z **Start** menu, a następnie wprowadź *certlm.msc*. 

    Zostanie wyświetlone narzędzie Menedżer certyfikatów dla wybranego urządzenia lokalnego. 
  
2. Aby wyświetlić certyfikaty, w obszarze **certyfikaty — komputer lokalny** w lewym okienku rozwiń węzeł katalogu dla typu certyfikatu, którą chcesz wyświetlić.

### <a name="to-view-certificates-for-the-current-user"></a>Aby wyświetlić certyfikaty dla bieżącego użytkownika

1. Wybierz **Uruchom** z **Start** menu, a następnie wprowadź *certmgr.msc*. 

    Zostanie wyświetlone narzędzie Menedżer certyfikatów dla bieżącego użytkownika. 
  
2. Aby wyświetlić certyfikaty, w obszarze **Certyfikaty — bieżący użytkownik** w lewym okienku rozwiń węzeł katalogu dla typu certyfikatu, którą chcesz wyświetlić.

  
## <a name="see-also"></a>Zobacz także
- [Praca z certyfikatami](working-with-certificates.md)
- [Instrukcje: Tworzenie certyfikatów tymczasowych do użytku w trakcie opracowywania](how-to-create-temporary-certificates-for-use-during-development.md)
- [Instrukcje: Pobieranie odcisku palca certyfikatu](how-to-retrieve-the-thumbprint-of-a-certificate.md)
