---
title: Instrukcje dotyczące hostowania internetowej usługi informacyjnej
ms.date: 03/30/2017
ms.assetid: 959a21c8-9d9d-4757-b255-4e57793ae9d6
ms.openlocfilehash: 5d315fa482e423461eab171a19746b6ea792aac5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33507577"
---
# <a name="internet-information-service-hosting-instructions"></a>Instrukcje dotyczące hostowania internetowej usługi informacyjnej
Aby uruchomić przykłady, które są obsługiwane przez Internet Information Services (IIS), należy się upewnić, że usługi IIS jest poprawnie zainstalowany i działa.  
  
### <a name="to-install-iis-version-75-on-windows-server-2008-r2"></a>Aby zainstalować usługi IIS w wersji 7.5 w systemie Windows Server 2008 R2  
  
1.  Z **Menedżera serwera**, wybierz pozycję **ról.** W obszarze **Podsumowanie ról**, kliknij przycisk **Dodaj role**.  
  
2.  Kliknij przycisk **dalej** do wyświetlenia **Wybieranie ról serwera** okna dialogowego.  
  
3.  Wybierz **serwera aplikacji** z **ról** , a następnie kliknij przycisk **dalej** dwa razy, aby wyświetlić **Wybieranie usług ról** okno dialogowe Rola serwera aplikacji.  
  
4.  Wybierz **serwer sieci Web (IIS)** pole wyboru. Jeśli zostanie wyświetlony monit, aby zainstalować dodatkowe usługi ról i funkcje, kliknij przycisk **Dodaj wymagane funkcje**. Kliknij przycisk **dalej** dwa razy, aby wyświetlić **Wybieranie usług ról** okna dialogowego dla roli Serwer sieci Web (IIS).  
  
5.  Rozwiń węzeł **narzędzia do zarządzania**, a następnie rozwiń węzeł **zgodność z narzędziami zarządzania usług IIS 6**. Wybierz **IIS narzędzia obsługi skryptów 6**. Jeśli zostanie wyświetlony monit, aby zainstalować dodatkowe usługi ról i funkcje, kliknij przycisk **Dodaj wymagane usługi ról**. Kliknij przycisk **Dalej**.  
  
6.  Podsumowanie wybrane opcje są poprawne, kliknij przycisk **zainstalować**.  
  
7.  Po zakończeniu instalacji kliknij przycisk **Zamknij**.  
  
### <a name="to-install-iis-version-75-on-windows-7"></a>Aby zainstalować usługi IIS w wersji 7.5 w systemie Windows 7  
  
1.  Kliknij przycisk **Start**, a następnie kliknij przycisk **Panelu sterowania**.  
  
2.  Otwórz **programy** grupy.  
  
3.  W obszarze **programy i funkcje**, kliknij przycisk **Włącz lub wyłącz funkcje systemu Windows**.  
  
4.  **Kontrola konta użytkownika** zostanie wyświetlone okno dialogowe. Kliknij przycisk **Kontynuuj**.  
  
5.  **Funkcje systemu Windows** zostanie wyświetlone okno dialogowe. Rozwiń element etykietą **Internetowe usługi informacyjne**.  
  
6.  Rozwiń element etykietą **usługi sieci World Wide Web**.  
  
7.  Rozwiń element etykietą **funkcje tworzenia aplikacji**.  
  
8.  Upewnij się, że wybrane są następujące elementy:  
  
    1.  **Rozszerzenia architektury .NET**  
  
    2.  **ASP.NET**  
  
    3.  **Rozszerzenia ISAPI**  
  
    4.  **Filtry ISAPI**  
  
9. W obszarze elementu etykietą **usługi sieci World Wide Web**, rozwiń węzeł **wspólne funkcje Http**.  
  
10. Upewnij się, że **zawartość statyczna** jest zaznaczone.  
  
11. W obszarze elementu etykietą **usługi sieci World Wide Web**, rozwiń węzeł **zabezpieczeń**.  
  
12. Upewnij się, że **uwierzytelniania systemu Windows** jest zaznaczone.  
  
13. W obszarze **Internetowe usługi informacyjne** katalogu, rozwiń element etykietą **narzędzia zarządzania siecią Web**, a następnie wybierz **Konsola zarządzania usługami IIS**.  
  
14. Rozwiń element etykietą **zgodność z narzędziami zarządzania usług IIS 6**, a następnie wybierz **narzędzia obsługi skryptów w usługach IIS 6**.  
  
15. W obszarze **Internetowe usługi informacyjne** katalogu, rozwiń element etykietą **Microsoft .NET Framework 3.5.1**, a następnie wybierz **Http operacyjnych**.  
  
16. Kliknij przycisk **OK**.  
  
### <a name="to-install-iis-version-70-on-windows-server-2008"></a>Aby zainstalować usługi IIS w wersji 7.0 w systemie Windows Server 2008  
  
1.  Z **Menedżera serwera**, wybierz pozycję **ról**. W obszarze **Podsumowanie ról**, kliknij przycisk **Dodaj role**.  
  
2.  Kliknij przycisk **dalej** do wyświetlenia **Wybieranie ról serwera** okna dialogowego.  
  
3.  Wybierz **serwera aplikacji** z **ról** , a następnie kliknij przycisk **dalej** dwa razy, aby wyświetlić **Wybieranie usług ról** okno dialogowe Rola serwera aplikacji.  
  
4.  Wybierz **serwer sieci Web (IIS)** pole wyboru. Jeśli zostanie wyświetlony monit, aby zainstalować dodatkowe usługi ról i funkcje, kliknij przycisk **Dodaj wymagane funkcje**. Kliknij przycisk **dalej** dwa razy, aby wyświetlić **Wybieranie usług ról** okna dialogowego dla roli Serwer sieci Web (IIS).  
  
5.  Rozwiń węzeł **narzędzia do zarządzania**, a następnie rozwiń węzeł **zgodność z narzędziami zarządzania usług IIS 6**. Wybierz **IIS narzędzia obsługi skryptów 6**. Jeśli zostanie wyświetlony monit, aby zainstalować dodatkowe usługi ról i funkcje, kliknij przycisk **Dodaj wymagane usługi ról**. Kliknij przycisk **Dalej**.  
  
6.  Podsumowanie wybrane opcje są poprawne, kliknij przycisk **zainstalować**.  
  
7.  Po zakończeniu instalacji kliknij przycisk **Zamknij**.  
  
### <a name="to-install-iis-version-70-on-windows-vista"></a>Aby zainstalować usługi IIS w wersji 7.0 w systemie Windows Vista  
  
1.  Kliknij przycisk Start, a następnie kliknij Panel sterowania.  
  
2.  Wybierz **programy** grupy.  
  
3.  W obszarze **programy i funkcje**, kliknij przycisk **Włącz lub wyłącz funkcje systemu Windows**.  
  
4.  **Kontrola konta użytkownika** zostanie wyświetlone okno dialogowe. Kliknij przycisk **Kontynuuj**.  
  
5.  **Funkcje systemu Windows** zostanie wyświetlone okno dialogowe. Rozwiń element etykietą **Internetowe usługi informacyjne**.  
  
6.  Rozwiń element etykietą **usługi sieci World Wide Web**.  
  
7.  Rozwiń element etykietą **funkcje tworzenia aplikacji**.  
  
8.  Upewnij się, że wybrane są następujące elementy:  
  
    1.  **Rozszerzenia architektury .NET**  
  
    2.  **ASP.NET**  
  
    3.  **Rozszerzenia ISAPI**  
  
    4.  **Filtry ISAPI**  
  
9. Rozwiń element etykietą **narzędzia zarządzania siecią Web**, a następnie wybierz **Konsola zarządzania usługami IIS**.  
  
10. W obszarze elementu etykietą **usługi sieci World Wide Web**, rozwiń węzeł **wspólne funkcje Http**.  
  
11. Upewnij się, że **zawartość statyczna** jest zaznaczone.  
  
12. W obszarze elementu etykietą **usługi sieci World Wide Web**, rozwiń węzeł **zabezpieczeń**.  
  
13. Upewnij się, że **uwierzytelniania systemu Windows** jest zaznaczone.  
  
14. Rozwiń element etykietą **zgodność z narzędziami zarządzania usług IIS 6**, a następnie wybierz **narzędzia obsługi skryptów w usługach IIS 6**.  
  
15. Rozwiń element etykietą **Microsoft .NET Framework 3.0**, a następnie wybierz **Aktywacja Http programu Windows Communication Foundation**.  
  
16. Kliknij przycisk**OK**.  
  
### <a name="to-install-iis-version-60-on-windows-server-2003"></a>Aby zainstalować usługi IIS w wersji 6.0 w systemie Windows Server 2003  
  
1.  Z **Zarządzanie serwerem**, kliknij przycisk **Dodaj lub Usuń rolę**, a następnie kliknij przycisk **dalej**.  
  
2.  Wybierz **serwer aplikacji (IIS, platformy ASP.NET)** z **roli serwera** , a następnie kliknij przycisk **dalej**.  
  
3.  Wybierz **Włącz ASP.NET** pole wyboru, a następnie kliknij przycisk **dalej**.  
  
4.  Jeśli podsumowanie wybrane opcje są poprawne, kliknij przycisk Dalej.  
  
### <a name="to-install-iis-version-51-on-windows-xp-with-service-pack-2-and-service-pack-3-installed"></a>Aby zainstalować usługi IIS w wersji 5.1 w systemie Windows XP z dodatkiem Service Pack 2 i dodatkiem Service Pack 3 zainstalowany  
  
1.  W Panelu sterowania kliknij **Dodaj lub usuń programy**.  
  
2.  W **Dodaj lub usuń programy** okno dialogowe, kliknij przycisk **Dodaj/Usuń składniki systemu Windows**.  
  
3.  W **Kreatora składników systemu Windows**, wybierz pozycję **Internet Information Services (IIS)** pole wyboru, a następnie kliknij przycisk **dalej**.  
  
4.  Jeśli **pliki potrzebne** zostanie wyświetlone okno dialogowe, włóż dysk instalacyjny systemu operacyjnego, przejdź do folderu i386, a następnie kliknij przycisk **OK**.  
  
5.  Po zakończeniu instalacji kliknij przycisk **Zakończ**.  
  
6.  Zamknij **Dodaj lub usuń programy** okno dialogowe, a następnie Zamknij **Panelu sterowania**.  
  
### <a name="to-verify-the-installation-of-iis-and-aspnet"></a>Aby sprawdzić poprawność instalacji usług IIS i platformy ASP.NET  
  
1.  Zapisz plik HTML znajdującą się na końcu tego tematu w katalogu głównym \InetPub\wwwroot i nadaj mu nazwę Default.aspx.  
  
2.  Otwórz okno przeglądarki.  
  
3.  Typ `http://localhost/Default.aspx` w polu adres, a następnie naciśnij klawisz ENTER.  
  
4.  Strony sieci Web z tekstu "Hello World" powinny być wyświetlane.  
  
> [!NOTE]
>  Zawsze zainstalować nową wersję [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], należy ponownie zarejestrować Biblioteka aspnet_isapi jako rozszerzenie usługi sieci Web dla usług IIS. Aby to zrobić, należy wydać `aspnet_regiis –I –enable` polecenia.  
  
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
