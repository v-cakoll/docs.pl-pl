---
title: "Instrukcje dotyczące konfigurowania katalogów wirtualnych"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3c62cab5-81a4-48b6-ac8c-9ce33a85a157
caps.latest.revision: "36"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: b727f391abfeb1112de1b6cde3ceb564d3860974
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="virtual-directory-setup-instructions"></a>Instrukcje dotyczące konfigurowania katalogów wirtualnych
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Będą udostępniać wspólnej katalog wirtualny o nazwie servicemodelsamples, który jest zamapowany na %SystemDrive%\inetpub\wwwroot\servicemodelsamples folder próbek.  
  
> [!NOTE]
>  Dysk % SystemDrive % jest zwykle C: i D:, w zależności od lokalizacji dysku, na którym zainstalowano usługi Internet Information Services (IIS).  
  
 Możesz uruchamiać pliki Setupvroot.bat i Cleanupvroot.bat z [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) można utworzyć katalogu wirtualnego. Jeśli wolisz ręcznie utworzyć katalogu wirtualnego, należy użyć poniższych procedur.  
  
## <a name="procedures"></a>Procedury  
  
#### <a name="to-create-a-virtual-directory-in-iis-70-or-75"></a>Można utworzyć katalogu wirtualnego w usługach IIS 7.0 lub 7.5  
  
1.  Z **Start** menu, kliknij przycisk **Uruchom**, wpisz **inetmgr** do otwierania przystawki MMC usług Internet Information Services (IIS).  
  
2.  W okienku po lewej stronie rozwiń węzeł z nazwą komputera, a następnie rozwiń **witryny** węzła.  
  
3.  Kliknij prawym przyciskiem myszy **domyślna witryna sieci Web**, a następnie wybierz **Dodawanie aplikacji** otworzyć **okno Dodawanie aplikacji**.  
  
4.  W oknie wpisz `servicemodelsamples` jako alias katalogu wirtualnego, który tworzysz.  
  
5.  Utworzyć następującego katalogu: %SystemDrive%\inetpub\wwwroot\servicemodelsamples  
  
6.  Ustaw ścieżkę fizyczną % SystemDrive%\inetpub\wwwroot\servicemodelsamples.  Większość przykładów WCF skopiuj pliki wykonywalne usługi do tej lokalizacji, podczas tworzenia.  
  
7.  Kliknij przycisk **OK**. Aplikacja sieci Web został utworzony dla przykładów WCF.  
  
    > [!NOTE]
    >  To zadanie należy wykonać tylko raz, ponieważ wszystkie [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] przykłady użycia servicemodelsamples tej samej aplikacji sieci Web.  
  
    > [!NOTE]
    >  Na potrzeby tej dokumentacji termin `virtual directory` CGI `Web application`.  
  
     Oprócz tworzenia katalogu wirtualnego, należy także ustawić jej właściwości w celu włączenia [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] działanie usług. Aby uzyskać więcej informacji, zobacz poniżej.  
  
#### <a name="to-create-a-virtual-directory-in-iis-51-or-60"></a>Można utworzyć katalogu wirtualnego w wersji 5.1 usług IIS lub 6.0  
  
1.  Otwórz okno wiersza polecenia i wpisz `start inetmgr` do otwierania przystawki MMC usług Internet Information Services (IIS).  
  
2.  W okienku po lewej stronie rozwiń węzeł z nazwą komputera, a następnie rozwiń **witryn sieci Web** węzła.  
  
3.  Kliknij prawym przyciskiem myszy **domyślna witryna sieci Web** i wybierz **nowe, katalog wirtualny** aby otworzyć Kreatora tworzenia katalogów wirtualnych.  
  
4.  W kreatorze wpisz `servicemodelsamples` jako alias katalogu wirtualnego, który tworzysz.  
  
5.  Ustaw ścieżkę na % SystemDrive%\inetpub\wwwroot\servicemodelsamples. Większość [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] przykłady skopiuj pliki wykonywalne usługi do tej lokalizacji, podczas tworzenia.  
  
6.  Kliknij przycisk **Dalej**.  
  
7.  Domyślnie wybrane są następujące pola wyboru:  
  
    -   **Odczyt**  
  
    -   **Uruchamianie skryptów (np.)**  
  
8.  Kliknij przycisk **dalej**, a następnie kliknij przycisk **Zakończ** aby zakończyć pracę kreatora.  
  
    > [!NOTE]
    >  To zadanie należy wykonać tylko raz. ponieważ wszystkie [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] przykłady użyć tego samego servicemodelsamples katalogu wirtualnego.  
  
#### <a name="to-set-additional-virtual-directory-properties-in-iis-70-or-75"></a>Aby ustawić właściwości dodatkowe katalogu wirtualnego w usługach IIS 7.0 lub 7.5  
  
1.  Kliknij węzeł servicemodelsamples. Wzdłuż dolnej części okna wyświetlane są dwa widoki. Wybierz **widoku funkcji** Jeśli nie została jeszcze wybrana.  
  
2.  Kliknij dwukrotnie pozycję **przeglądanie katalogów**.  
  
3.  W okienku Akcje, wybierz **włączyć** opcji. Dzięki temu można uzyskać dostępu do katalogu katalogu przy użyciu programu Internet Explorer, która pomaga w przypadku debugowania usługi.  
  
 Ponadto należy ustawić właściwości zabezpieczeń folderu servicemodelsamples, aby zezwolić na dostęp do innych użytkowników. Aby uzyskać więcej informacji, zobacz poniżej.  
  
#### <a name="to-set-additional-virtual-directory-properties-in-iis-51-or-60"></a>Aby ustawić właściwości dodatkowe katalogu wirtualnego w wersji 5.1 usług IIS lub 6.0  
  
1.  Kliknij prawym przyciskiem myszy węzeł servicemodelsamples, a następnie kliknij przycisk **właściwości**.  
  
2.  Domyślnie wybrane są następujące pola wyboru:  
  
    -   **Odczyt**  
  
    -   **Odwiedza dziennika**  
  
    -   **Tego zasobu**  
  
3.  Wybierz **przeglądanie katalogów** pole wyboru. Dzięki temu można uzyskać dostępu do katalogu katalogu przy użyciu programu Internet Explorer, która pomaga w przypadku debugowania usługi.  
  
#### <a name="to-set-security-properties-of-the-folder-in-iis-70-or-75"></a>Aby ustawić właściwości zabezpieczeń folderu w usługach IIS 7.0 lub 7.5  
  
1.  Przejdź do % SystemDrive%\inetpub\wwwroot\servicemodelsamples.  
  
2.  Kliknij prawym przyciskiem myszy servicemodelsamples folder, a następnie kliknij przycisk **udziału** lub **udziału z**.  
  
3.  Kliknij strzałkę w dół do lewej strony **Dodaj** przycisku.  
  
4.  Wybierz **znaleźć** wpisu. **Wybieranie użytkowników lub grup** zostanie otwarte okno.  
  
5.  Kliknij przycisk **zaawansowane**.  
  
6.  Kliknij przycisk **lokalizacje**. **Lokalizacje** okno jest już otwarty.  
  
7.  Zaznacz wpis dla używanego komputera. Należy wybrać komputer lokalny i nie wpis dla wszystkich domen lub sieci wyświetlanych na liście. Po wybraniu komputera, kliknij przycisk **OK**.  
  
8.  Kliknij przycisk **Znajdź teraz**. Spowoduje to wypełnienie wyniki wyszukiwania z obiektów skojarzonych z komputerem lokalnym.  
  
9. Znajdź **IIS_IUSRS** wpis w **Name (nazwa wyróżniająca względną)** kolumny. Wybierz ten wpis i kliknij przycisk **OK** okno wyników aby zamknąć wyszukiwania.  
  
10. Kliknij przycisk **OK** zamknąć **Wybieranie użytkowników lub grup** okna.  
  
11. Kliknij przycisk **udziału** aby utrwalić zmiany.  
  
12. Po zakończeniu wprowadzania zmian, aby włączyć udostępnianie, kliknij przycisk **gotowe** zamknąć **udostępniania plików** okna.  
  
#### <a name="to-set-security-properties-of-the-folder-in-iis-51-or-60"></a>Aby ustawić właściwości zabezpieczeń folderu w wersji 5.1 usług IIS lub 6.0  
  
1.  Przejdź do % SystemDrive%\inetpub\wwwroot\servicemodelsamples.  
  
2.  Kliknij prawym przyciskiem myszy **servicemodelsamples** folder, a następnie kliknij przycisk **udostępnianie i zabezpieczenia.**  
  
3.  Kliknij przycisk **zabezpieczeń** kartę.  
  
4.  Jeśli korzystasz z usług IIS 6.0, w **nazwy grup lub użytkowników** zaznacz pole wyboru czy **konta gościa Internet** ma na liście.  
  
     Jeśli nie ma na liście:  
  
    1.  Kliknij przycisk **Start** , a następnie kliknij przycisk **Panelu sterowania**.  
  
    2.  Jeśli nie widzisz **kont użytkowników** ikony, kliknij przycisk **Przełącz do widoku kategorii**.  
  
    3.  Kliknij przycisk **kont użytkowników** ikony.  
  
    4.  W obszarze "lub wybierz ikonę Panelu sterowania," kliknij **kont użytkowników**.  
  
    5.  W **kont użytkowników** okno dialogowe, kliknij przycisk **zaawansowane** kartę.  
  
    6.  Kliknij przycisk **zaawansowane**.  
  
    7.  W **lokalnych użytkowników i grup** okno dialogowe, kliknij, aby rozwinąć **użytkowników** folderu.  
  
    8.  W prawym okienku kliknij dwukrotnie **konta gościa Internet**.  
  
    9. W **właściwości** okno dialogowe, kopiowania nazwę używane jako konto gościa Internet. Domyślnie nazwa rozpoczyna się od "USR_", po której następuje nazwa komputera.  
  
    10. Zamknij okno dialogowe **Właściwości** .  
  
    11. Zamknij **lokalnych użytkowników i grup** okno dialogowe.  
  
    12. Zamknij **kont użytkowników** okno dialogowe.  
  
    13. Zamknij innych **kont użytkowników** okno dialogowe.  
  
    14. W **servicemodelsamples właściwości** na okna dialogowego **zabezpieczeń** , kliknij pozycję **Dodaj**.  
  
    15. Wpisz nazwę komputera, a następnie ukośnik odwrotny, a następnie wklej nazwę konta użytkownika, Internet, na przykład myMachineName\\InternetGuestAccountName %  
  
    16. Kliknij przycisk **Sprawdź nazwy** można zweryfikować operacji dodawania. Jeśli jest on prawidłowy, nazwa jest wielkimi literami i podkreślony.  
  
5.  Dla usług IIS 6.0, również sprawdzić, czy Usługa sieciowa ma na liście **nazwy grup lub użytkowników** pole.  
  
     Jeśli usługa sieciowa nie ma na liście:  
  
    1.  Kliknij przycisk **Dodaj**.  
  
    2.  W **Wybieranie użytkowników lub grup** okno dialogowe, wpisz nazwę komputera, a następnie ukośnik odwrotny.  
  
    3.  Typ **usługi** po ukośniku odwrotnym (bez spacji).  
  
    4.  Kliknij przycisk **Sprawdź nazwy**.  
  
    5.  W przypadku odnalezienia wielu nazw wybierz **usługi SIECIOWEJ** i kliknij przycisk **OK**.  
  
    6.  Kliknij przycisk **OK** zamknąć **Wybieranie użytkowników lub grup** okno dialogowe.  
  
6.  Jeśli używasz systemu Windows XP z dodatkiem SP2 z wersji 5.1 usług IIS, sprawdź, czy zarówno konta gościa Internet i ASPNET są wymieniony w **nazwy grup lub użytkowników** pole.  
  
     Należy pamiętać, że użytkownik ASPNET może należeć do wbudowanych **użytkowników** grupy zabezpieczeń. Jeśli tak, jeśli następnie **użytkowników** grupy znajduje się w oknie dialogowym, ale nie trzeba go dodać jako osobny element do listy dozwolonych użytkowników.  
  
     Aby sprawdzić, czy ASPNET jest częścią **użytkowników** grupy zabezpieczeń:  
  
    1.  Na **Start** menu, kliknij przycisk **Panelu sterowania**.  
  
    2.  Kliknij przycisk **kont użytkowników** ikony.  
  
    3.  W **grupy** kolumny, sprawdź, czy wartość **ASPNET** jest "Użytkownicy".  
  
## <a name="see-also"></a>Zobacz też  
 [Informacje o usługi instrukcje dotyczące hostowania internetowej](../../../../docs/framework/wcf/samples/internet-information-service-hosting-instructions.md)
