---
title: 'Instrukcje: Włączanie wykrywania powtarzania tokenu'
ms.date: 03/30/2017
ms.assetid: 5a9f5771-f5f6-4100-8501-406aa20d731a
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: dd5adf39c37fce92d4caf1d85e2a6a12e9e6b59b
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2018
ms.locfileid: "43486519"
---
# <a name="how-to-enable-token-replay-detection"></a>Instrukcje: Włączanie wykrywania powtarzania tokenu
## <a name="applies-to"></a>Dotyczy:  
  
-   Microsoft® Windows® Identity Foundation (WIF)  
  
-   ASP.NET® formularzy sieci Web  
  
## <a name="summary"></a>Podsumowanie  
 Niniejszy instruktaż zawiera szczegółowe procedury krok po kroku dotyczące włączania wykrywania powtarzania tokenu w aplikacji ASP.NET, który używa programu WIF. On również instrukcje testowania aplikacji pozwalające sprawdzić, czy jest włączone wykrywanie powtórzeń tokenów. Instruktaż nie zawiera szczegółowych instrukcji tworzenia usługi tokenów zabezpieczających (STS). Zamiast tego wykorzystuje deweloperską usługę STS wbudowaną w narzędziu Tożsamość i dostęp. Deweloperska usługa STS nie wykonuje faktycznego uwierzytelniania i jest przeznaczona tylko do celów testowych. Narzędzie Tożsamość i dostęp jest koniecznie do ukończenia całego instruktażu. Można go pobrać z następującej lokalizacji: [narzędzie tożsamość i dostęp](https://go.microsoft.com/fwlink/?LinkID=245849)  
  
## <a name="contents"></a>Spis treści  
  
-   Cele  
  
-   Omówienie  
  
-   Zestawienie czynności  
  
-   Krok 1. Tworzenie prostych aplikacji ASP.NET Web Forms i włączanie wykrywania powtarzania  
  
-   Krok 2 — przetestowanie rozwiązania  
  
## <a name="objectives"></a>Cele  
  
-   Utwórz prostą aplikację platformy ASP.NET, który używa programu WIF i deweloperskiej usługi STS z narzędzie tożsamość i dostęp  
  
-   Włączanie wykrywania powtarzania tokenu i sprawdź, czy działa ona  
  
## <a name="overview"></a>Omówienie  
 Atak przez powtarzanie występuje, gdy klienci podejmują próbę uwierzytelnienia do jednostki uzależnionej przy użyciu tokenu usługi STS, została już użyta przez klienta. Aby uniknąć tego ataku, program WIF zawiera pamięci podręcznej wykrywania powtórzeń tokenów usługi STS, poprzednio używanych. Po włączeniu wykrywania powtarzania sprawdza token żądania przychodzącego i sprawdza, czy token został wcześniej użyty. Jeśli token został już użyty, żądanie zostało odrzucone i <xref:System.IdentityModel.Tokens.SecurityTokenReplayDetectedException> wyjątku.  
  
 Poniższe kroki pokazują zmiany konfiguracji wymagane do włączenia wykrywania powtarzania.  
  
## <a name="summary-of-steps"></a>Zestawienie czynności  
  
-   Krok 1. Tworzenie prostych aplikacji ASP.NET Web Forms i włączanie wykrywania powtarzania  
  
-   Krok 2 — przetestowanie rozwiązania  
  
## <a name="step-1--create-a-simple-aspnet-web-forms-application-and-enable-replay-detection"></a>Krok 1. Tworzenie prostych aplikacji ASP.NET Web Forms i włączanie wykrywania powtarzania  
 W tym kroku utworzysz nowej aplikacji ASP.NET Web Forms i zmodyfikować *Web.config* plik w celu włączenia wykrywania powtarzania.  
  
#### <a name="to-create-a-simple-aspnet-application"></a>Aby utworzyć prostą aplikację platformy ASP.NET  
  
1.  Uruchom program Visual Studio, a następnie kliknij przycisk **pliku**, **New**, a następnie **projektu**.  
  
2.  W **nowy projekt** okna, kliknij przycisk **aplikacji formularzy sieci Web ASP.NET**.  
  
3.  W **nazwa**, wprowadź `TestApp` i naciśnij klawisz **OK**.  
  
4.  Kliknij prawym przyciskiem myszy **TestApp** projekt **Eksploratora rozwiązań**, a następnie wybierz **tożsamościami i dostępem**.  
  
5.  **Tożsamościami i dostępem** zostanie wyświetlone okno. W obszarze **dostawców**, wybierz opcję **testować swoją aplikację za pomocą lokalnej deweloperskiej usługi STS**, następnie kliknij przycisk **Zastosuj**.  
  
6.  Dodaj następujący kod  **\<tokenReplayDetection >** elementu *Web.config* pliku konfiguracji, natychmiast po  **\<system.identityModel >** i  **\<identityConfiguration >** elementów, takich jak pokazano:  
  
    ```xml  
    <system.identityModel>  
        <identityConfiguration>  
            <tokenReplayDetection enabled="true"/>  
    ```  
  
## <a name="step-2--test-your-solution"></a>Krok 2 — przetestowanie rozwiązania  
 W tym kroku przetestujesz aplikację ASP.NET z włączoną obsługą programu WIF, aby sprawdzić, czy włączono wykrywania powtarzania.  
  
#### <a name="to-test-your-wif-enabled-aspnet-application-for-replay-detection"></a>Aby przetestować aplikację ASP.NET z włączoną obsługą programu WIF do wykrywania powtórzeń  
  
1.  Uruchom rozwiązanie, naciskając klawisz **F5** klucza. Użytkownik powinien być prezentowane z domyślną stronę główną struktury ASP.NET i automatycznie uwierzytelniana przy użyciu nazwy użytkownika *Terry*, która jest domyślny użytkownik, który jest zwracany za pomocą deweloperskiej usługi STS.  
  
2.  Naciśnij w przeglądarce **ponownie** przycisku. Powinna pojawić się **błąd serwera w aplikacji» /»** strony na następujący opis: *ID1062: wykryto powtarzania: Token: "System.IdentityModel.Tokens.SamlSecurityToken"* , a następnie *identyfikator potwierdzenia* i *wystawcy*.  
  
     Ta strona błędu jest wyświetlana, ponieważ wystąpił wyjątek typu <xref:System.IdentityModel.Tokens.SecurityTokenReplayDetectedException> był zgłaszany, gdy wykryto powtarzania tokenu. Ten błąd występuje, ponieważ próbujesz ponownie wysłać żądanie POST początkowej, najpierw umieszczeniem tokenu. **Ponownie** przycisku nie spowoduje to zachowanie dla kolejnych żądań do serwera.
