---
title: Instrukcje dotyczące konfigurowania katalogów wirtualnych
ms.date: 03/30/2017
ms.assetid: 3c62cab5-81a4-48b6-ac8c-9ce33a85a157
ms.openlocfilehash: 2d9443431601ffc712da40bd1c085f595471336b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602365"
---
# <a name="virtual-directory-setup-instructions"></a>Instrukcje dotyczące konfigurowania katalogów wirtualnych
Przykłady Windows Communication Foundation (WCF) są przeznaczone do udostępniania wspólnego katalogu wirtualnego o nazwie servicemodelsamples, który jest mapowany do folderu%SystemDrive%\inetpub\wwwroot\servicemodelsamples.  
  
> [!NOTE]
> Dysk% SystemDrive% jest zwykle C: lub D:, w zależności od lokalizacji dysku, w której zainstalowano Internet Information Services (IIS).  
  
 Pliki Setupvroot. bat i cleanupvroot. bat można uruchomić z [procedury konfiguracji jednorazowej dla przykładów Windows Communication Foundation,](one-time-setup-procedure-for-the-wcf-samples.md) aby utworzyć katalog wirtualny. Jeśli wolisz ręcznie utworzyć katalog wirtualny, Użyj poniższych procedur.  
  
## <a name="procedures"></a>Procedury  
  
#### <a name="to-create-a-virtual-directory-in-iis-70-or-75"></a>Aby utworzyć katalog wirtualny w usługach IIS 7,0 lub 7,5  
  
1. W menu **Start** kliknij polecenie **Uruchom**, a następnie wpisz **inetmgr** , aby otworzyć przystawkę MMC Internet Information Services (IIS).  
  
2. W lewym okienku rozwiń węzeł nazwą komputera, a następnie rozwiń węzeł **Lokacje** .  
  
3. Kliknij prawym przyciskiem myszy pozycję **Domyślna witryna sieci Web**, a następnie wybierz polecenie **Dodaj aplikację** , aby otworzyć **okno Dodawanie aplikacji**.  
  
4. W oknie wpisz `servicemodelsamples` jako alias tworzonego katalogu wirtualnego.  
  
5. Utwórz następujący katalog:%SystemDrive%\inetpub\wwwroot\servicemodelsamples  
  
6. Ustaw ścieżkę fizyczną na%SystemDrive%\inetpub\wwwroot\servicemodelsamples.  Większość przykładów WCF kopiuje pliki wykonywalne usługi do tej lokalizacji po skompilowaniu.  
  
7. Kliknij przycisk **OK**. Aplikacja sieci Web jest teraz utworzona dla przykładów WCF.  
  
    > [!NOTE]
    > To zadanie należy wykonać tylko raz, ponieważ wszystkie przykłady WCF używają tej samej aplikacji sieci Web servicemodelsamples.  
  
    > [!NOTE]
    > Na potrzeby tej dokumentacji termin `virtual directory` jest równoznaczny z `Web application` .  
  
     Oprócz tworzenia katalogu wirtualnego, należy również ustawić jego właściwości, aby umożliwić uruchamianie usług WCF. Aby uzyskać szczegółowe informacje, zobacz poniżej.  
  
#### <a name="to-create-a-virtual-directory-in-iis-51-or-60"></a>Aby utworzyć katalog wirtualny w usługach IIS 5,1 lub 6,0  
  
1. Otwórz okno wiersza polecenia i wpisz, `start inetmgr` Aby otworzyć przystawkę MMC Internet Information Services (IIS).  
  
2. W lewym okienku rozwiń węzeł nazwą komputera, a następnie rozwiń węzeł **witryny sieci Web** .  
  
3. Kliknij prawym przyciskiem myszy pozycję **Domyślna witryna sieci Web** i wybierz pozycję **Nowy, katalog wirtualny,** aby otworzyć Kreatora tworzenia katalogów wirtualnych.  
  
4. W Kreatorze wpisz `servicemodelsamples` jako alias tworzonego katalogu wirtualnego.  
  
5. Ustaw ścieżkę do%SystemDrive%\inetpub\wwwroot\servicemodelsamples. Większość przykładów WCF kopiuje pliki wykonywalne usługi do tej lokalizacji po skompilowaniu.  
  
6. Kliknij przycisk **Dalej**.  
  
7. Domyślnie są zaznaczone następujące pola wyboru:  
  
    - **Odczyt**  
  
    - **Uruchamianie skryptów (takich jak ASP)**  
  
8. Kliknij przycisk **dalej**, a następnie kliknij przycisk **Zakończ** , aby zakończyć pracę kreatora.  
  
    > [!NOTE]
    > To zadanie należy wykonać tylko raz, ponieważ wszystkie przykłady WCF używają tego samego katalogu wirtualnego ServiceModelSamples.  
  
#### <a name="to-set-additional-virtual-directory-properties-in-iis-70-or-75"></a>Aby ustawić dodatkowe właściwości katalogu wirtualnego w usługach IIS 7,0 lub 7,5  
  
1. Kliknij węzeł servicemodelsamples. W dolnej części okna wyświetlane są dwa widoki. Wybierz pozycję **funkcje widok** , jeśli nie została jeszcze wybrana.  
  
2. Kliknij dwukrotnie wpis do **przeglądania katalogów**.  
  
3. W okienku Akcje wybierz opcję **Włącz** . Dzięki temu można uzyskać dostęp do katalogu katalogu przy użyciu programu Internet Explorer, który ułatwia debugowanie usługi.  
  
 Na koniec należy ustawić właściwości zabezpieczeń folderu servicemodelsamples, aby umożliwić dostęp innym osobom. Aby uzyskać szczegółowe informacje, zobacz poniżej.  
  
#### <a name="to-set-additional-virtual-directory-properties-in-iis-51-or-60"></a>Aby ustawić dodatkowe właściwości katalogu wirtualnego w usługach IIS 5,1 lub 6,0  
  
1. Kliknij prawym przyciskiem myszy węzeł servicemodelsamples, a następnie kliknij polecenie **Właściwości**.  
  
2. Domyślnie są zaznaczone następujące pola wyboru:  
  
    - **Odczyt**  
  
    - **Wizyty w dzienniku**  
  
    - **Indeksuj ten zasób**  
  
3. Zaznacz pole wyboru **Przeglądanie katalogów** . Dzięki temu można uzyskać dostęp do katalogu katalogu przy użyciu programu Internet Explorer, który ułatwia debugowanie usługi.  
  
#### <a name="to-set-security-properties-of-the-folder-in-iis-70-or-75"></a>Aby ustawić właściwości zabezpieczeń folderu w usługach IIS 7,0 lub 7,5  
  
1. Przejdź do%SystemDrive%\inetpub\wwwroot\servicemodelsamples.  
  
2. Kliknij prawym przyciskiem myszy folder servicemodelsamples, a następnie kliknij pozycję **Udostępnij** lub **Udostępnij**.  
  
3. Kliknij strzałkę w dół znajdującą się po lewej stronie przycisku **Dodaj** .  
  
4. Wybierz pozycję **Znajdź** . Zostanie otwarte okno **Wybieranie użytkowników lub grup** .  
  
5. Kliknij pozycję **Zaawansowane**.  
  
6. Kliknij pozycję **lokalizacje**. Okno **lokalizacje** jest teraz otwarte.  
  
7. Wybierz wpis dla używanego komputera. Ważne jest, aby wybrać komputer lokalny, a nie wpis dla dowolnych domen lub sieci, które są wymienione na liście. Po wybraniu komputera kliknij przycisk **OK**.  
  
8. Kliknij przycisk **Znajdź teraz**. Spowoduje to wypełnienie wyników wyszukiwania za pomocą obiektów skojarzonych z komputerem lokalnym.  
  
9. Znajdź wpis **IIS_IUSRS** w kolumnie **Nazwa (względna nazwa wyróżniająca)** . Wybierz ten wpis, a następnie kliknij przycisk **OK** , aby zamknąć okno wyników wyszukiwania.  
  
10. Kliknij przycisk **OK** , aby zamknąć okno **Wybieranie użytkowników lub grup** .  
  
11. Kliknij przycisk **Udostępnij** , aby zachować zmiany.  
  
12. Po zakończeniu wprowadzania zmian w celu włączenia udostępniania kliknij przycisk **gotowe** , aby zamknąć okno **udostępnianie plików** .  
  
#### <a name="to-set-security-properties-of-the-folder-in-iis-51-or-60"></a>Aby ustawić właściwości zabezpieczeń folderu w usługach IIS 5,1 lub 6,0  
  
1. Przejdź do%SystemDrive%\inetpub\wwwroot\servicemodelsamples.  
  
2. Kliknij prawym przyciskiem myszy folder **servicemodelsamples** , a następnie kliknij pozycję **udostępnianie i zabezpieczenia.**  
  
3. Kliknij kartę **Zabezpieczenia**.  
  
4. Jeśli używasz usług IIS 6,0, w polu **nazwy grupy lub użytkownika** Sprawdź, czy na liście znajdują się **konta gościa internetowego** .  
  
     Jeśli nie ma go na liście:  
  
    1. Kliknij przycisk **Start** , a następnie kliknij pozycję **Panel sterowania**.  
  
    2. Jeśli nie widzisz ikony **konta użytkowników** , kliknij przycisk **Przełącz do widoku kategorii**.  
  
    3. Kliknij ikonę **konta użytkowników** .  
  
    4. W obszarze "lub wybierz ikonę panelu sterowania" kliknij pozycję **konta użytkowników**.  
  
    5. W oknie dialogowym **konta użytkowników** kliknij kartę **Zaawansowane** .  
  
    6. Kliknij pozycję **Zaawansowane**.  
  
    7. W oknie dialogowym **lokalni użytkownicy i grupy** kliknij, aby rozwinąć folder **Users (Użytkownicy** ).  
  
    8. W prawym okienku kliknij dwukrotnie pozycję **konto gościa internetowego**.  
  
    9. W oknie dialogowym **Właściwości** skopiuj nazwę używaną jako konto gościa internetowego. Domyślnie nazwa rozpoczyna się od "USR_", po którym następuje nazwa komputera.  
  
    10. Zamknij okno dialogowe **Właściwości** .  
  
    11. Zamknij okno dialogowe **Użytkownicy i grupy lokalne** .  
  
    12. Zamknij okno dialogowe **konta użytkowników** .  
  
    13. Zamknij okno dialogowe inne **konta użytkowników** .  
  
    14. W oknie dialogowym **Właściwości servicemodelsamples** na karcie **zabezpieczenia** kliknij przycisk **Dodaj**.  
  
    15. Wpisz nazwę komputera, a następnie ukośnik odwrotny, a następnie wklej nazwę konta użytkownika internetowego, na przykład MojKomputer \\ % InternetGuestAccountName%  
  
    16. Kliknij przycisk **Sprawdź nazwy** , aby zweryfikować dodanie. Jeśli jest to prawidłowe, nazwa jest w Wielkiej litery i jest podkreślona.  
  
5. W przypadku usług IIS 6,0 Sprawdź, czy usługa sieciowa znajduje się w polu **nazwy grupy lub użytkownika** .  
  
     Jeśli usługa sieciowa nie jest wymieniona na liście:  
  
    1. Kliknij pozycję **Dodaj**.  
  
    2. W oknie dialogowym **Wybieranie użytkowników lub grup** wpisz nazwę komputera, a następnie ukośnik odwrotny.  
  
    3. Wpisz **usługę** po ukośniku odwrotnym (bez spacji).  
  
    4. Kliknij przycisk **Sprawdź nazwy**.  
  
    5. Jeśli zostanie znalezionych wiele nazw, wybierz pozycję **Usługa sieciowa** , a następnie kliknij przycisk **OK**.  
  
    6. Kliknij przycisk **OK** , aby zamknąć okno dialogowe **Wybieranie użytkowników lub grup** .  
  
6. Jeśli używasz systemu Windows XP z dodatkiem SP2 z usługami IIS 5,1, sprawdź, czy w polu **nazwy grupy lub użytkownika** są wyświetlane zarówno konto gościa internetowego, jak i ASPNET.  
  
     Należy pamiętać, że użytkownik ASPNET może być członkiem wbudowanej grupy zabezpieczeń **Użytkownicy** . Jeśli tak, to jeśli w oknie dialogowym zostanie wyświetlona Grupa **Użytkownicy** , nie musisz dodawać jej jako osobnego elementu do listy dozwolonych użytkowników.  
  
     Aby sprawdzić, czy ASPNET jest częścią grupy zabezpieczeń **Użytkownicy** :  
  
    1. W menu **Start** kliknij pozycję **Panel sterowania**.  
  
    2. Kliknij ikonę **konta użytkowników** .  
  
    3. W kolumnie **Grupa** Sprawdź, czy wartość **ASPNET** to "Users".  
  
## <a name="see-also"></a>Zobacz też

- [Instrukcje dotyczące hostowania internetowej usługi informacyjnej](internet-information-service-hosting-instructions.md)
