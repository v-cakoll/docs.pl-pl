---
title: Instrukcje dotyczące hostowania internetowej usługi informacyjnej
ms.date: 03/30/2017
ms.assetid: 959a21c8-9d9d-4757-b255-4e57793ae9d6
ms.openlocfilehash: 226b47bfd90dc4cffb0a364a804016043cc25d02
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929111"
---
# <a name="internet-information-service-hosting-instructions"></a>Instrukcje dotyczące hostowania internetowej usługi informacyjnej
Aby uruchomić przykłady, które są hostowane przez Internet Information Services (IIS), należy upewnić się, że usługi IIS są prawidłowo zainstalowane i uruchomione.  
  
### <a name="to-install-iis-version-75-on-windows-server-2008-r2"></a>Aby zainstalować usługi IIS w wersji 7,5 w systemie Windows Server 2008 R2  
  
1. W obszarze **Menedżer serwera**wybierz pozycję **role.** W obszarze **Podsumowanie ról**kliknij pozycję **Dodaj role**.  
  
2. Kliknij przycisk **dalej** , aby wyświetlić okno dialogowe **Wybieranie ról serwera** .  
  
3. Wybierz pozycję **serwer aplikacji** z listy **role** , a następnie kliknij przycisk **dalej** dwa razy, aby wyświetlić okno dialogowe **Wybieranie usług ról** dla roli serwera aplikacji.  
  
4. Zaznacz pole wyboru **serwer sieci Web (IIS)** . Jeśli zostanie wyświetlony monit o zainstalowanie dodatkowych usług ról i funkcji, kliknij przycisk **Dodaj wymagane funkcje**. Kliknij dwukrotnie przycisk **dalej** , aby wyświetlić okno dialogowe **Wybieranie usług ról** dla roli Serwer sieci Web (IIS).  
  
5. Rozwiń węzeł **Narzędzia do zarządzania**, a następnie rozwiń pozycję Zgodność z zarządzaniem **usługami IIS**w wersji 6. Wybierz pozycję **Narzędzia obsługi skryptów w usługach IIS 6**. Jeśli zostanie wyświetlony monit o zainstalowanie dodatkowych usług ról i funkcji, kliknij przycisk **Dodaj wymagane usługi ról**. Kliknij przycisk **Dalej**.  
  
6. Jeśli podsumowanie wybranych opcji jest poprawne, kliknij przycisk **Instaluj**.  
  
7. Po zakończeniu instalacji kliknij przycisk **Zamknij**.  
  
### <a name="to-install-iis-version-75-on-windows-7"></a>Aby zainstalować usługi IIS w wersji 7,5 w systemie Windows 7  
  
1. Kliknij przycisk **Start**, a następnie kliknij pozycję **Panel sterowania**.  
  
2. Otwórz grupę **programy** .  
  
3. W obszarze **programy i funkcje**kliknij pozycję **Włącz lub wyłącz funkcje systemu Windows**.  
  
4. Zostanie wyświetlone okno dialogowe **Kontrola konta użytkownika** . Kliknij przycisk **Kontynuuj**.  
  
5. Zostanie wyświetlone okno dialogowe **funkcje systemu Windows** . Rozwiń element oznaczony **Internet Information Services**.  
  
6. Rozwiń element oznaczony **World Wide Web Services**.  
  
7. Rozwiń element zatytułowany **Programowanie aplikacji**.  
  
8. Upewnij się, że wybrano następujące elementy:  
  
    1. **Rozszerzalność platformy .NET**  
  
    2. **ASP.NET**  
  
    3. **Rozszerzenia ISAPI**  
  
    4. **Filtry ISAPI**  
  
9. W obszarze elementu **World Wide Web usługach**rozwiń węzeł **wspólne funkcje http**.  
  
10. Upewnij się, że jest zaznaczona **Zawartość statyczna** .  
  
11. W obszarze elementu **World Wide Web usługach**rozwiń węzeł **zabezpieczenia**.  
  
12. Upewnij się, że wybrano **uwierzytelnianie systemu Windows** .  
  
13. W katalogu **Internet Information Services** rozwiń element **Narzędzia do zarządzania siecią Web**, a następnie wybierz pozycję **Konsola zarządzania usługami IIS**.  
  
14. Rozwiń element o nazwie **zgodność z usługami IIS 6**, a następnie wybierz pozycję **Narzędzia do obsługi skryptów w usługach IIS 6**.  
  
15. W katalogu **Internet Information Services** rozwiń element z etykietą **Microsoft .NET Framework 3.5.1**, a następnie wybierz pozycję **Windows Communication Foundation Aktywacja HTTP**.  
  
16. Kliknij przycisk **OK**.  
  
### <a name="to-install-iis-version-70-on-windows-server-2008"></a>Aby zainstalować usługi IIS w wersji 7,0 w systemie Windows Server 2008  
  
1. W obszarze **Menedżer serwera**wybierz pozycję **role**. W obszarze **Podsumowanie ról**kliknij pozycję **Dodaj role**.  
  
2. Kliknij przycisk **dalej** , aby wyświetlić okno dialogowe **Wybieranie ról serwera** .  
  
3. Wybierz pozycję **serwer aplikacji** z listy **role** , a następnie kliknij przycisk **dalej** dwa razy, aby wyświetlić okno dialogowe **Wybieranie usług ról** dla roli serwera aplikacji.  
  
4. Zaznacz pole wyboru **serwer sieci Web (IIS)** . Jeśli zostanie wyświetlony monit o zainstalowanie dodatkowych usług ról i funkcji, kliknij przycisk **Dodaj wymagane funkcje**. Kliknij dwukrotnie przycisk **dalej** , aby wyświetlić okno dialogowe **Wybieranie usług ról** dla roli Serwer sieci Web (IIS).  
  
5. Rozwiń węzeł **Narzędzia do zarządzania**, a następnie rozwiń pozycję Zgodność z zarządzaniem **usługami IIS**w wersji 6. Wybierz pozycję **Narzędzia obsługi skryptów w usługach IIS 6**. Jeśli zostanie wyświetlony monit o zainstalowanie dodatkowych usług ról i funkcji, kliknij przycisk **Dodaj wymagane usługi ról**. Kliknij przycisk **Dalej**.  
  
6. Jeśli podsumowanie wybranych opcji jest poprawne, kliknij przycisk **Instaluj**.  
  
7. Po zakończeniu instalacji kliknij przycisk **Zamknij**.  
  
### <a name="to-install-iis-version-70-on-windows-vista"></a>Aby zainstalować usługi IIS w wersji 7,0 w systemie Windows Vista  
  
1. Kliknij przycisk Start, a następnie kliknij pozycję Panel sterowania.  
  
2. Wybierz grupę **programy** .  
  
3. W obszarze **programy i funkcje**kliknij pozycję **Włącz lub wyłącz funkcje systemu Windows**.  
  
4. Zostanie wyświetlone okno dialogowe **Kontrola konta użytkownika** . Kliknij przycisk **Kontynuuj**.  
  
5. Zostanie wyświetlone okno dialogowe **funkcje systemu Windows** . Rozwiń element oznaczony **Internet Information Services**.  
  
6. Rozwiń element oznaczony **World Wide Web Services**.  
  
7. Rozwiń element zatytułowany **Programowanie aplikacji**.  
  
8. Upewnij się, że wybrano następujące elementy:  
  
    1. **Rozszerzalność platformy .NET**  
  
    2. **ASP.NET**  
  
    3. **Rozszerzenia ISAPI**  
  
    4. **Filtry ISAPI**  
  
9. Rozwiń element zatytułowany **Narzędzia do zarządzania siecią Web**, a następnie wybierz pozycję **Konsola zarządzania usługami IIS**.  
  
10. W obszarze elementu **World Wide Web usługach**rozwiń węzeł **wspólne funkcje http**.  
  
11. Upewnij się, że jest zaznaczona **Zawartość statyczna** .  
  
12. W obszarze elementu **World Wide Web usługach**rozwiń węzeł **zabezpieczenia**.  
  
13. Upewnij się, że wybrano **uwierzytelnianie systemu Windows** .  
  
14. Rozwiń element o nazwie **zgodność z usługami IIS 6**, a następnie wybierz pozycję **Narzędzia do obsługi skryptów w usługach IIS 6**.  
  
15. Rozwiń element oznaczony **Microsoft .NET Framework 3,0**, a następnie wybierz pozycję **Windows Communication Foundation Aktywacja HTTP**.  
  
16. Kliknij przycisk **OK**.  
  
### <a name="to-install-iis-version-60-on-windows-server-2003"></a>Aby zainstalować usługi IIS w wersji 6,0 w systemie Windows Server 2003  
  
1. W obszarze **Zarządzanie serwerem**, kliknij przycisk **Dodaj lub Usuń rolę**, a następnie kliknij przycisk **dalej**.  
  
2. Wybierz pozycję **serwer aplikacji (IIS, ASP.NET)** z listy **rola serwera** , a następnie kliknij przycisk **dalej**.  
  
3. Zaznacz pole wyboru **włącz ASP.NET** , a następnie kliknij przycisk **dalej**.  
  
4. Jeśli podsumowanie wybranych opcji jest poprawne, kliknij przycisk Dalej.  
  
### <a name="to-install-iis-version-51-on-windows-xp-with-service-pack-2-and-service-pack-3-installed"></a>Aby zainstalować usługi IIS w wersji 5,1 w systemie Windows XP z zainstalowanym dodatkiem Service Pack 2 i Service Pack 3  
  
1. W panelu sterowania kliknij pozycję **Dodaj lub usuń programy**.  
  
2. W oknie dialogowym **Dodawanie lub usuwanie programów** kliknij pozycję **Dodaj/Usuń składniki systemu Windows**.  
  
3. W **Kreatorze składników systemu Windows**zaznacz pole wyboru **Internet Information Services (IIS)** , a następnie kliknij przycisk **dalej**.  
  
4. Jeśli zostanie wyświetlone okno dialogowe **wymagające plików** , włóż dysk instalacyjny systemu operacyjnego, przejdź do folderu i386, a następnie kliknij przycisk **OK**.  
  
5. Po zakończeniu instalacji kliknij przycisk **Zakończ**.  
  
6. Zamknij okno dialogowe **Dodaj lub usuń programy** , a następnie zamknij **Panel sterowania**.  
  
### <a name="to-verify-the-installation-of-iis-and-aspnet"></a>Aby zweryfikować instalację usług IIS i ASP.NET  
  
1. Zapisz plik HTML znaleziony na końcu tego tematu w katalogu głównym \InetPub\wwwroot i nadaj mu nazwę default. aspx.  
  
2. Otwórz okno przeglądarki.  
  
3. Wpisz `http://localhost/Default.aspx` w polu adres, a następnie naciśnij klawisz ENTER.  
  
4. Zostanie wyświetlona strona sieci Web z tekstem "Hello world".  
  
> [!NOTE]
> Za każdym razem, gdy instalujesz nową wersję .NET Framework, należy ponownie zarejestrować program aspnet_isapi jako rozszerzenie usługi sieci Web dla usług IIS. Aby to zrobić, wydaj `aspnet_regiis –I –enable` polecenie.  
  
## <a name="sample-code"></a>Przykładowy kod  
  
```xml  
<html>  
   <body>  
       <form >  
           <h3> Hello World  
           </h3>  
       </form>  
   </body>  
</html>  
```
