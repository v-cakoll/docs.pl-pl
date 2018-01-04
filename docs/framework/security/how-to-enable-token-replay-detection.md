---
title: "Porady: Włączanie wykrywania powtórzeń tokenów"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5a9f5771-f5f6-4100-8501-406aa20d731a
caps.latest.revision: "4"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: a7c72d77b4894376fb6cb8aed2d1c6641a3977da
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-enable-token-replay-detection"></a>Porady: Włączanie wykrywania powtórzeń tokenów
## <a name="applies-to"></a>Dotyczy:  
  
-   Microsoft® Windows® Identity Foundation (WIF)  
  
-   ASP.NET® formularzy sieci Web  
  
## <a name="summary"></a>Podsumowanie  
 Porada ten zawiera szczegółowe procedury krok po kroku umożliwiających wykrywanie powtórzeń tokenów w aplikacji ASP.NET, która używa WIF. Umożliwia także instrukcje przetestować aplikację, aby sprawdzić, czy włączono wykrywania powtórzeń tokenów. Instruktaż nie zawiera szczegółowych instrukcji tworzenia usługi tokenów zabezpieczających (STS). Zamiast tego wykorzystuje deweloperską usługę STS wbudowaną w narzędziu Tożsamość i dostęp. Deweloperska usługa STS nie wykonuje faktycznego uwierzytelniania i jest przeznaczona tylko do celów testowych. Narzędzie Tożsamość i dostęp jest koniecznie do ukończenia całego instruktażu. Można go pobrać z następującej lokalizacji: [tożsamości i dostępu do narzędzia](http://go.microsoft.com/fwlink/?LinkID=245849)  
  
## <a name="contents"></a>Spis treści  
  
-   Cele  
  
-   Omówienie  
  
-   Zestawienie czynności  
  
-   Krok 1: tworzenie aplikacji formularzy sieci Web ASP.NET proste i włączyć wykrywanie powtarzania  
  
-   Krok 2 – Sprawdź swoje rozwiązanie  
  
## <a name="objectives"></a>Cele  
  
-   Utwórz prostą aplikację ASP.NET, która używa WIF i STS programowanie z tożsamości i dostępu do narzędzia  
  
-   Umożliwia to wykrywanie powtórzeń tokenów i sprawdź, czy działa ona  
  
## <a name="overview"></a>Omówienie  
 Atak powtarzania występuje, gdy klient podejmie próbę uwierzytelnienia do jednostki uzależnionej z tokenem STS została już użyta przez klienta. Aby zapobiec atakom, WIF zawiera pamięci podręcznej wykrywania powtórzeń tokenów STS poprzednio. Po włączeniu wykrywania powtórzeń sprawdza token żądania przychodzącego i sprawdza, czy token został wcześniej użyty. Jeśli token został już użyty, żądanie jest odrzucane i <xref:System.IdentityModel.Tokens.SecurityTokenReplayDetectedException> wyjątku.  
  
 Następująca procedura przedstawia zmiany w konfiguracji wymagane do włączenia wykrywania powtarzania.  
  
## <a name="summary-of-steps"></a>Zestawienie czynności  
  
-   Krok 1: tworzenie aplikacji formularzy sieci Web ASP.NET proste i włączyć wykrywanie powtarzania  
  
-   Krok 2 – Sprawdź swoje rozwiązanie  
  
## <a name="step-1--create-a-simple-aspnet-web-forms-application-and-enable-replay-detection"></a>Krok 1: tworzenie aplikacji formularzy sieci Web ASP.NET proste i włączyć wykrywanie powtarzania  
 W tym kroku zostanie utworzenie nowej aplikacji formularzy sieci Web ASP.NET i zmodyfikować *Web.config* pliku, aby włączyć wykrywanie powtarzania.  
  
#### <a name="to-create-a-simple-aspnet-application"></a>Aby utworzyć prostą aplikację ASP.NET  
  
1.  Uruchom program Visual Studio, a następnie kliknij przycisk **pliku**, **nowy**, a następnie **projektu**.  
  
2.  W **nowy projekt** okna, kliknij przycisk **aplikacji formularzy sieci Web ASP.NET**.  
  
3.  W **nazwa**, wprowadź `TestApp` i naciśnij klawisz **OK**.  
  
4.  Kliknij prawym przyciskiem myszy **TestApp** projektu w obszarze **Eksploratora rozwiązań**, a następnie wybierz pozycję **tożsamościami i dostępem**.  
  
5.  **Tożsamościami i dostępem** zostanie wyświetlone okno. W obszarze **dostawców**, wybierz pozycję **testowania aplikacji z lokalnej usługi STS programowanie**, następnie kliknij przycisk **Zastosuj**.  
  
6.  Dodaj następujące  **\<tokenReplayDetection >** elementu *Web.config* pliku konfiguracji bezpośrednio po  **\<system.identityModel >** i  **\<identityConfiguration >** elementów, takich jak pokazano:  
  
    ```xml  
    <system.identityModel>  
        <identityConfiguration>  
            <tokenReplayDetection enabled="true"/>  
    ```  
  
## <a name="step-2--test-your-solution"></a>Krok 2 – Sprawdź swoje rozwiązanie  
 W tym kroku zostanie przetestować aplikację ASP.NET włączoną WIF, aby sprawdzić, czy włączono wykrywania powtórzeń.  
  
#### <a name="to-test-your-wif-enabled-aspnet-application-for-replay-detection"></a>Aby przetestować aplikację ASP.NET włączoną WIF do wykrywania powtórzeń  
  
1.  Uruchom rozwiązanie, naciskając klawisz **F5** klucza. Powinna być wyświetlana domyślna strona główna programu ASP.NET i automatycznie uwierzytelniony nazwy użytkownika *Jakub*, która jest zwracana przez usługę STS programowanie domyślny użytkownik.  
  
2.  Naciśnij klawisz przeglądarki **ponownie** przycisku. Powinna pojawić się **błąd serwera w "/" aplikacja** strona zawierająca następujący opis: *ID1062: wykryto powtarzania: tokenu: "System.IdentityModel.Tokens.SamlSecurityToken"* , a następnie *identyfikator potwierdzenia* i *wystawcy*.  
  
     Ta strona błędu jest wyświetlany, ponieważ wystąpił wyjątek typu <xref:System.IdentityModel.Tokens.SecurityTokenReplayDetectedException> został zgłoszony, gdy wykryto powtórzeń tokenów. Ten błąd występuje, ponieważ próbujesz ponownie wysłać początkowe żądanie POST, gdy token najpierw został przedstawiony. **Ponownie** przycisku nie spowoduje to zachowanie na kolejnych żądań wysyłanych do serwera.
