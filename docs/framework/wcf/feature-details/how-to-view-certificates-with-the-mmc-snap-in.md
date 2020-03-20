---
title: 'Jak: Wyświetlanie certyfikatów przy przystawce PROGRAMU MMC'
ms.date: 02/25/2019
helpviewer_keywords:
- certificates [WCF], viewing with the MMC snap-in
ms.assetid: 2b8782aa-ebb4-4ee7-974b-90299e356dc5
ms.openlocfilehash: 35048c24e838c513909fae8bedcba287001f5cef
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184785"
---
# <a name="how-to-view-certificates-with-the-mmc-snap-in"></a>Jak: Wyświetlanie certyfikatów przy przystawce PROGRAMU MMC
Podczas tworzenia bezpiecznego klienta lub usługi, można użyć [certyfikatu](working-with-certificates.md) jako poświadczenia. Na przykład typowym typem poświadczeń jest certyfikat X.509, który można utworzyć za <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A?displayProperty=nameWithType> pomocą metody.

Istnieją trzy różne typy magazynów certyfikatów, które można sprawdzić za pomocą programu Microsoft Management Console (MMC) w systemach Windows:

- Komputer lokalny: magazyn jest lokalny dla urządzenia i globalny dla wszystkich użytkowników na urządzeniu.

- Bieżący użytkownik: Sklep jest lokalny dla bieżącego konta użytkownika na urządzeniu.

- Konto usługi: sklep jest lokalny dla określonej usługi na urządzeniu.

## <a name="view-certificates-in-the-mmc-snap-in"></a>Wyświetlanie certyfikatów w przystawce programu MMC

Poniższa procedura pokazuje, jak sprawdzić sklepy na urządzeniu lokalnym, aby znaleźć odpowiedni certyfikat:
  
1. Wybierz **polecenie Uruchom** z menu **Start,** a następnie wprowadź *mmc*.

    Pojawi się program MMC.
  
2. Z menu **Plik** wybierz polecenie **Dodaj/Usuń przyciąganie .**

    Zostanie **wyświetlenie** okna Dodaj lub Usuń przystawki.
  
3. Z listy **Dostępne przystawki** wybierz pozycję **Certyfikaty**, a następnie wybierz pozycję **Dodaj**.  

    ![Dodawanie przystawki certyfikatu](./media/mmc-add-certificate-snap-in.png)
  
4. W oknie **przystawki Certyfikaty** wybierz pozycję **Konto komputera**, a następnie wybierz pozycję **Dalej**.
  
    Opcjonalnie można wybrać **moje konto użytkownika** dla bieżącego użytkownika lub konto **usługi** dla określonej usługi.

    > [!NOTE]
    > Jeśli nie jesteś administratorem urządzenia, możesz zarządzać certyfikatami tylko dla swojego konta użytkownika.
  
5. W oknie **Wybierz komputer** pozostaw zaznaczoną pozycję **Komputer lokalny,** a następnie wybierz pozycję **Zakończ**.  
  
6. W oknie **Dodawanie lub usuwanie przyciągania** wybierz pozycję **OK**.  
  
    ![Dodawanie przystawki certyfikatu](./media/mmc-certificate-snap-in-selected.png)

7. Opcjonalnie: z menu **Plik** wybierz polecenie **Zapisz** lub **Zapisz jako,** aby zapisać plik konsoli programu MMC do późniejszego użycia.  

8. Aby wyświetlić certyfikaty w przystawce programu MMC, wybierz pozycję **Katalog główny konsoli** w lewym okienku, a następnie rozwiń pozycję **Certyfikaty (komputer lokalny).**

    Pojawi się lista katalogów dla każdego typu certyfikatu. Z każdego katalogu certyfikatów można wyświetlać, eksportować, importować i usuwać jego certyfikaty.

## <a name="view-certificates-with-the-certificate-manager-tool"></a>Wyświetlanie certyfikatów za pomocą narzędzia Menedżer certyfikatów

Certyfikaty można również wyświetlać, eksportować, importować i usuwać za pomocą narzędzia Menedżer certyfikatów.

### <a name="to-view-certificates-for-the-local-device"></a>Aby wyświetlić certyfikaty dla urządzenia lokalnego

1. Wybierz **polecenie Uruchom** z menu **Start,** a następnie wprowadź *plik certlm.msc*.

    Zostanie wyświetlone narzędzie Menedżer certyfikatów dla urządzenia lokalnego.
  
2. Aby wyświetlić certyfikaty, w obszarze **Certyfikaty — Komputer lokalny** w lewym okienku rozwiń katalog typu certyfikatu, który chcesz wyświetlić.

### <a name="to-view-certificates-for-the-current-user"></a>Aby wyświetlić certyfikaty dla bieżącego użytkownika

1. Wybierz **polecenie Uruchom** z menu **Start,** a następnie wprowadź plik *certmgr.msc*.

    Pojawi się narzędzie Menedżer certyfikatów dla bieżącego użytkownika.
  
2. Aby wyświetlić certyfikaty, w obszarze **Certyfikaty — bieżący użytkownik** w lewym okienku rozwiń katalog dla typu certyfikatu, który chcesz wyświetlić.

## <a name="see-also"></a>Zobacz też

- [Praca z certyfikatami](working-with-certificates.md)
- [Jak: Tworzenie tymczasowych certyfikatów do użycia podczas tworzenia](how-to-create-temporary-certificates-for-use-during-development.md)
- [Jak: Pobieranie odcisku palca certyfikatu](how-to-retrieve-the-thumbprint-of-a-certificate.md)
