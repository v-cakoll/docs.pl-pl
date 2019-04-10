---
title: Instrukcje dotyczące konfigurowania katalogów wirtualnych
ms.date: 03/30/2017
ms.assetid: 3c62cab5-81a4-48b6-ac8c-9ce33a85a157
ms.openlocfilehash: 7999a040dc14d75a34b75f320982dd3118eae670
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59225589"
---
# <a name="virtual-directory-setup-instructions"></a>Instrukcje dotyczące konfigurowania katalogów wirtualnych
Przykłady Windows Communication Foundation (WCF) będą udostępniać wspólnego katalogu wirtualnego o nazwie servicemodelsamples, który jest zamapowany na %SystemDrive%\inetpub\wwwroot\servicemodelsamples folder.  
  
> [!NOTE]
>  Dysk % SystemDrive % jest zwykle C: i D:, w zależności od lokalizacji dysku, na którym zainstalowano usługi Internet Information Services (IIS).  
  
 Możesz uruchamiać pliki Setupvroot.bat i Cleanupvroot.bat z [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) można utworzyć katalogu wirtualnego. Jeśli wolisz ręcznie utworzyć katalogu wirtualnego, należy użyć poniższych procedur.  
  
## <a name="procedures"></a>Procedury  
  
#### <a name="to-create-a-virtual-directory-in-iis-70-or-75"></a>Można utworzyć katalogu wirtualnego w usługach IIS 7.0 lub 7.5  
  
1.  Z **Start** menu, kliknij przycisk **Uruchom**, a następnie wpisz **inetmgr** aby otworzyć przystawkę MMC usług Internet Information Services (IIS).  
  
2.  W lewym okienku rozwiń węzeł z nazwą komputera, a następnie rozwiń **witryn** węzła.  
  
3.  Kliknij prawym przyciskiem myszy **domyślna witryna sieci Web**, a następnie wybierz pozycję **Add Application** otworzyć **okno Dodawanie aplikacji**.  
  
4.  W oknie wpisz `servicemodelsamples` jako alias katalogu wirtualnego, który tworzysz.  
  
5.  Utwórz następujący katalog: %SystemDrive%\inetpub\wwwroot\servicemodelsamples  
  
6.  Ustaw ścieżkę fizyczną na % SystemDrive%\inetpub\wwwroot\servicemodelsamples.  Większość przykładów WCF skopiuj pliki wykonywalne usługi do tej lokalizacji podczas kompilowania.  
  
7.  Kliknij przycisk **OK**. Aplikacja sieci Web został utworzony dla przykładów usługi WCF.  
  
    > [!NOTE]
    >  To zadanie można wykonać tylko raz, ponieważ jest używany przez wszystkie przykłady WCF servicemodelsamples tej samej aplikacji sieci Web.  
  
    > [!NOTE]
    >  Na potrzeby tej dokumentacji termin `virtual directory` jest synonimem `Web application`.  
  
     Oprócz tworzenia katalogu wirtualnego, można również ustawić jej właściwości, aby umożliwić działanie usług WCF. Zobacz szczegóły poniżej.  
  
#### <a name="to-create-a-virtual-directory-in-iis-51-or-60"></a>Można utworzyć katalogu wirtualnego w IIS 5.1 i 6.0  
  
1.  Otwórz okno wiersza polecenia i wpisz `start inetmgr` aby otworzyć przystawkę MMC usług Internet Information Services (IIS).  
  
2.  W lewym okienku rozwiń węzeł z nazwą komputera, a następnie rozwiń **witryn sieci Web** węzła.  
  
3.  Kliknij prawym przyciskiem myszy **domyślna witryna sieci Web** i wybierz **nowe, katalog wirtualny** aby otworzyć Kreatora tworzenia katalogów wirtualnych.  
  
4.  W kreatorze, wpisz `servicemodelsamples` jako alias katalogu wirtualnego, który tworzysz.  
  
5.  Ustaw ścieżkę na % SystemDrive%\inetpub\wwwroot\servicemodelsamples. Większość przykładów WCF skopiuj pliki wykonywalne usługi do tej lokalizacji podczas kompilowania.  
  
6.  Kliknij przycisk **Dalej**.  
  
7.  Domyślnie wybrane są następujące pola wyboru:  
  
    -   **Odczyt**  
  
    -   **Uruchamianie skryptów (np. ASP)**  
  
8.  Kliknij przycisk **dalej**, a następnie kliknij przycisk **Zakończ** aby zakończyć działanie kreatora.  
  
    > [!NOTE]
    >  To zadanie muszą być wykonywane tylko raz, ponieważ wszystkie przykłady WCF używają tego samego servicemodelsamples katalogu wirtualnego.  
  
#### <a name="to-set-additional-virtual-directory-properties-in-iis-70-or-75"></a>Aby ustawić właściwości dodatkowych katalogu wirtualnego w usługach IIS 7.0 lub 7.5  
  
1.  Kliknij węzeł servicemodelsamples. Wzdłuż dolnej części okna dwa widoki są wyświetlane. Wybierz **widoku funkcji** Jeśli nie została jeszcze wybrana.  
  
2.  Kliknij dwukrotnie pozycję **przeglądanie katalogów**.  
  
3.  W okienku akcji wybierz **Włącz** opcji. Dzięki temu można uzyskać dostępu do katalogu, w katalogu za pomocą programu Internet Explorer, która pomaga podczas debugowania usługi.  
  
 Na koniec należy ustawić właściwości zabezpieczeń folderu servicemodelsamples, aby zezwalała na można uzyskać dostępu do innych osób. Zobacz szczegóły poniżej.  
  
#### <a name="to-set-additional-virtual-directory-properties-in-iis-51-or-60"></a>Aby ustawić właściwości dodatkowych katalogu wirtualnego w usługach IIS 5.1 i 6.0  
  
1.  Kliknij prawym przyciskiem myszy węzeł servicemodelsamples, a następnie kliknij przycisk **właściwości**.  
  
2.  Domyślnie wybrane są następujące pola wyboru:  
  
    -   **Odczyt**  
  
    -   **Rejestruj wizyty**  
  
    -   **Indeksuj ten zasób**  
  
3.  Wybierz **przeglądanie katalogów** pole wyboru. Dzięki temu można uzyskać dostępu do katalogu, w katalogu za pomocą programu Internet Explorer, która pomaga podczas debugowania usługi.  
  
#### <a name="to-set-security-properties-of-the-folder-in-iis-70-or-75"></a>Aby ustawić właściwości zabezpieczeń folderu w usługach IIS 7.0 lub 7.5  
  
1.  Przejdź do % SystemDrive%\inetpub\wwwroot\servicemodelsamples.  
  
2.  Kliknij prawym przyciskiem myszy servicemodelsamples folder, a następnie kliknij przycisk **udziału** lub **udziału za pomocą**.  
  
3.  Kliknij strzałkę w dół po lewej stronie **Dodaj** przycisku.  
  
4.  Wybierz **znaleźć** wpisu. **Wybieranie użytkowników lub grup** zostanie otwarte okno.  
  
5.  Kliknij przycisk **zaawansowane**.  
  
6.  Kliknij przycisk **lokalizacje**. **Lokalizacje** jest teraz otwarte okno.  
  
7.  Zaznacz wpis dla komputera, używana. Należy wybrać komputer lokalny i nie wpis dla jak domeny, do których należą. Po wybraniu komputera, kliknij przycisk **OK**.  
  
8.  Kliknij przycisk **Znajdź teraz**. Spowoduje to wypełnienie wyników wyszukiwania za pomocą obiektów skojarzonych z komputerem lokalnym.  
  
9. Znajdź **IIS_IUSRS** wpis **Name (nazwa wyróżniająca względną)** kolumny. Wybierz odpowiedni wpis, a następnie kliknij przycisk **OK** Zamknij wyszukiwanie okno wyników.  
  
10. Kliknij przycisk **OK** zamknąć **Wybieranie użytkowników lub grup** okna.  
  
11. Kliknij przycisk **udziału** aby utrwalić zmiany.  
  
12. Po zakończeniu zmiany, co pozwala na udostępnianie kliknij **gotowe** zamknąć **udostępniania plików** okna.  
  
#### <a name="to-set-security-properties-of-the-folder-in-iis-51-or-60"></a>Do ustawiania właściwości zabezpieczeń folderu usługi IIS 5.1 i 6.0  
  
1.  Przejdź do % SystemDrive%\inetpub\wwwroot\servicemodelsamples.  
  
2.  Kliknij prawym przyciskiem myszy **servicemodelsamples** folder, a następnie kliknij przycisk **udostępnianie i zabezpieczenia.**  
  
3.  Kliknij przycisk **zabezpieczeń** kartę.  
  
4.  Jeśli używasz usług IIS 6.0 w **nazwy grupy lub użytkownika** zaznacz pole wyboru czy **konta gościa Internet** znajduje się na liście.  
  
     Jeśli nie ma na liście:  
  
    1.  Kliknij przycisk **Start** a następnie kliknij przycisk **Panelu sterowania**.  
  
    2.  Jeśli nie widzisz **kont użytkowników** ikonę, kliknij przycisk **Przełącz do widoku kategorii**.  
  
    3.  Kliknij przycisk **kont użytkowników** ikony.  
  
    4.  W obszarze "lub wybierz ikonę Panelu sterowania" kliknij **kont użytkowników**.  
  
    5.  W **kont użytkowników** okno dialogowe, kliknij przycisk **zaawansowane** kartę.  
  
    6.  Kliknij przycisk **zaawansowane**.  
  
    7.  W **lokalnych użytkowników i grup** okno dialogowe, kliknij, aby rozwinąć **użytkowników** folderu.  
  
    8.  W okienku po prawej stronie, kliknij dwukrotnie **konta gościa Internet**.  
  
    9. W **właściwości** okno dialogowe, kopia nazwa używana jako konto gościa internetowego. Domyślnie nazwa zaczyna się od "USR_", po której następuje nazwa komputera.  
  
    10. Zamknij okno dialogowe **Właściwości** .  
  
    11. Zamknij **lokalnych użytkowników i grup** okno dialogowe.  
  
    12. Zamknij **kont użytkowników** okno dialogowe.  
  
    13. Zamknij innych **kont użytkowników** okno dialogowe.  
  
    14. W **servicemodelsamples właściwości** dialogowym **zabezpieczeń** kliknij pozycję **Dodaj**.  
  
    15. Wpisz nazwę komputera, a następnie ukośnik odwrotny, a następnie wklej nazwę konta użytkownika Internet, na przykład myMachineName\\InternetGuestAccountName %  
  
    16. Kliknij przycisk **Sprawdź nazwy** do sprawdzenia poprawności operacji dodawania. Jeśli jest on prawidłowy, nazwa jest wpisany tylko wielkimi literami i jest podkreślony.  
  
5.  Dla usług IIS 6.0 również Sprawdź, czy Usługa sieciowa znajduje się w **nazwy grupy lub użytkownika** pole.  
  
     Jeśli usługa sieciowa nie ma na liście:  
  
    1.  Kliknij przycisk **Dodaj**.  
  
    2.  W **Wybieranie użytkowników lub grup** okno dialogowe, wpisz nazwę komputera, a następnie znakiem ukośnika odwrotnego.  
  
    3.  Typ **usługi** po ukośniku odwrotnym (bez spacji).  
  
    4.  Kliknij przycisk **Sprawdź nazwy**.  
  
    5.  Jeśli zostaną znalezione wiele nazw, zaznacz **Usługa sieciowa** i kliknij przycisk **OK**.  
  
    6.  Kliknij przycisk **OK** zamknąć **Wybieranie użytkowników lub grup** okno dialogowe.  
  
6.  Jeśli usługi IIS 5.1 za pomocą Windows XP z dodatkiem SP2, sprawdź, liście zarówno konta gościa Internet, jak i ASPNET **nazwy grupy lub użytkownika** pole.  
  
     Należy pamiętać, że użytkownik ASPNET może być członkiem wbudowanej **użytkowników** grupy zabezpieczeń. Jeśli tak, a w przypadku **użytkowników** grupy znajduje się w oknie dialogowym, nie trzeba go dodać jako osobny element do listy dozwolonych użytkowników.  
  
     Aby sprawdzić, czy ASPNET jest częścią **użytkowników** grupy zabezpieczeń:  
  
    1.  Na **Start** menu, kliknij przycisk **Panelu sterowania**.  
  
    2.  Kliknij przycisk **kont użytkowników** ikony.  
  
    3.  W **grupy** kolumny, sprawdź, czy wartość **ASPNET** jest "Użytkownicy".  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje dotyczące hostowania internetowej usługi informacyjnej](../../../../docs/framework/wcf/samples/internet-information-service-hosting-instructions.md)
