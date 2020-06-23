---
title: 'Instrukcje: Wyświetlanie certyfikatów w przystawce programu MMC'
description: Bezpieczny klient lub usługa WCF mogą używać certyfikatu jako poświadczenia. Dowiedz się więcej na temat typów magazynów certyfikatów, które można sprawdzić za pomocą wtyczki programu MMC.
ms.date: 02/25/2019
helpviewer_keywords:
- certificates [WCF], viewing with the MMC snap-in
ms.assetid: 2b8782aa-ebb4-4ee7-974b-90299e356dc5
ms.openlocfilehash: e63034e48ae836f67f89b454829f7196c94610cd
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246678"
---
# <a name="how-to-view-certificates-with-the-mmc-snap-in"></a>Instrukcje: Wyświetlanie certyfikatów w przystawce programu MMC
Podczas tworzenia bezpiecznego klienta lub usługi można użyć [certyfikatu](working-with-certificates.md) jako poświadczenia. Typowym typem poświadczeń jest na przykład certyfikat X. 509, który tworzysz przy użyciu <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A?displayProperty=nameWithType> metody.

Istnieją trzy różne typy magazynów certyfikatów, które można przeanalizować za pomocą programu Microsoft Management Console (MMC) w systemach Windows:

- Komputer lokalny: Magazyn jest lokalny dla urządzenia i globalny dla wszystkich użytkowników na urządzeniu.

- Bieżący użytkownik: Magazyn jest lokalny dla bieżącego konta użytkownika na urządzeniu.

- Konto usługi: Magazyn jest lokalny dla określonej usługi na urządzeniu.

## <a name="view-certificates-in-the-mmc-snap-in"></a>Wyświetlanie certyfikatów w przystawce programu MMC

Poniższa procedura przedstawia sposób badania magazynów na urządzeniu lokalnym w celu znalezienia odpowiedniego certyfikatu:
  
1. Z menu **Start** wybierz polecenie **Uruchom** , a następnie wprowadź *MMC*.

    Zostanie wyświetlony program MMC.
  
2. Z menu **plik** wybierz pozycję **Dodaj/Usuń przystawkę**.

    Zostanie wyświetlone okno **Dodawanie lub usuwanie przystawek** .
  
3. Z listy **Dostępne przystawki** wybierz pozycję **Certyfikaty**, a następnie wybierz pozycję **Dodaj**.  

    ![Dodaj przystawkę certyfikatów](./media/mmc-add-certificate-snap-in.png)
  
4. W oknie **Przystawka certyfikatów** wybierz pozycję **konto komputera**, a następnie wybierz przycisk **dalej**.
  
    Opcjonalnie możesz wybrać **konto użytkownika** dla bieżącego użytkownika lub **usługi** dla określonej usługi.

    > [!NOTE]
    > Jeśli nie jesteś administratorem urządzenia, możesz zarządzać certyfikatami tylko dla Twojego konta użytkownika.
  
5. W oknie **Wybieranie komputera** pozostaw wybraną opcję **komputer lokalny** , a następnie wybierz pozycję **Zakończ**.  
  
6. W oknie **Dodawanie lub usuwanie przystawki** wybierz pozycję **OK**.  
  
    ![Dodaj przystawkę certyfikatów](./media/mmc-certificate-snap-in-selected.png)

7. Opcjonalne: z menu **plik** wybierz polecenie **Zapisz** lub **Zapisz jako** , aby zapisać plik konsoli programu MMC do późniejszego użycia.  

8. Aby wyświetlić certyfikaty w przystawce programu MMC, w okienku po lewej stronie wybierz pozycję **katalog główny konsoli** , a następnie rozwiń węzeł **Certyfikaty (komputer lokalny)**.

    Zostanie wyświetlona lista katalogów dla każdego typu certyfikatu. W każdym katalogu certyfikatów można wyświetlać, eksportować, importować i usuwać jego certyfikaty.

## <a name="view-certificates-with-the-certificate-manager-tool"></a>Wyświetlanie certyfikatów za pomocą narzędzia Menedżer certyfikatów

Można również wyświetlać, eksportować, importować i usuwać certyfikaty przy użyciu narzędzia Menedżer certyfikatów.

### <a name="to-view-certificates-for-the-local-device"></a>Aby wyświetlić certyfikaty dla urządzenia lokalnego

1. Z menu **Start** wybierz polecenie **Uruchom** , a następnie wprowadź *certlm. msc*.

    Zostanie wyświetlone narzędzie Menedżer certyfikatów dla urządzenia lokalnego.
  
2. Aby wyświetlić certyfikaty, w obszarze **Certyfikaty — komputer lokalny** w okienku po lewej stronie rozwiń katalog dla typu certyfikatu, który chcesz wyświetlić.

### <a name="to-view-certificates-for-the-current-user"></a>Aby wyświetlić certyfikaty dla bieżącego użytkownika

1. Z menu **Start** wybierz polecenie **Uruchom** , a następnie wprowadź *certmgr. msc*.

    Zostanie wyświetlone narzędzie Menedżer certyfikatów dla bieżącego użytkownika.
  
2. Aby wyświetlić certyfikaty, w obszarze **Certyfikaty — bieżący użytkownik** w lewym okienku rozwiń katalog dla typu certyfikatu, który chcesz wyświetlić.

## <a name="see-also"></a>Zobacz też

- [Praca z certyfikatami](working-with-certificates.md)
- [Instrukcje: Tworzenie certyfikatów tymczasowych do użycia podczas opracowywania](how-to-create-temporary-certificates-for-use-during-development.md)
- [Instrukcje: Pobieranie odcisku palca certyfikatu](how-to-retrieve-the-thumbprint-of-a-certificate.md)
