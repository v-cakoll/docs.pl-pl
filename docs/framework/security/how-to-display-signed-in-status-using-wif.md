---
title: 'Porady: Wyświetlanie zalogowany stanu przy użyciu WIF'
ms.date: 03/30/2017
ms.assetid: 4d1174e4-5397-4962-9a5f-3b1ad7b3fc14
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 53ef5e8b3fae976bacff3be9a50c323a22aef0e9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-display-signed-in-status-using-wif"></a>Porady: Wyświetlanie zalogowany stanu przy użyciu WIF
## <a name="applies-to"></a>Dotyczy:  
  
-   Microsoft Windows® Identity Foundation (WIF) 4.5  
  
-   ASP.NET® formularzy sieci Web  
  
## <a name="summary"></a>Podsumowanie  
 W tym temacie opisano sposób wyświetlania znaku w stan w aplikacji z obsługą WIF ASP.NET. WIF udostępnia mechanizm do tworzenia aplikacji oświadczenia i zarządzanie uwierzytelniania i autoryzacji dla zasobów aplikacji.  
  
## <a name="contents"></a>Spis treści  
  
-   Omówienie  
  
-   Zestawienie czynności  
  
-   Krok 1: Instalowanie tożsamości i uzyskiwać dostęp do rozszerzenia  
  
-   Krok 2 — Tworzenie aplikacji ASP.NET firm jednostki uzależnionej  
  
-   Krok 3 — Włączanie lokalne działania projektowe STS do uwierzytelniania użytkowników  
  
-   Krok 4: modyfikowanie aplikacji ASP.NET do wyświetlenia w ramach stanu logowania  
  
-   Krok 5: Testowanie integracji między WIF i przez aplikację ASP.NET  
  
## <a name="overview"></a>Omówienie  
 W tym temacie przedstawiono sposób tworzenia prostej aplikacji obsługujących oświadczenia przy użyciu WIF oraz łatwo wyświetlać, czy użytkownik jest zalogowany. Poniższe kroki, użyj lokalnej usługi STS programowanie dołączonego tożsamości i rozszerzenia programu Visual Studio dostępu. Lokalnej usługi STS programowanie jest przeznaczony dla środowiska badań i rozwoju to prosta metoda integrowanie oświadczenia aplikacji. Nigdy nie powinien można użyć w środowisku produkcyjnym jako nie wykonuje rzeczywistą uwierzytelniania i poświadczenia nie są wymagane. Jednak konieczne kod w następujących krokach jest taki sam dla aplikacji gotowych do produkcji, przy użyciu uwierzytelniania prawdziwe.  
  
## <a name="summary-of-steps"></a>Zestawienie czynności  
  
-   Krok 1: Instalowanie tożsamości i uzyskiwać dostęp do rozszerzenia  
  
-   Krok 2 — Tworzenie aplikacji ASP.NET firm jednostki uzależnionej  
  
-   Krok 3 — Włączanie lokalne działania projektowe STS do uwierzytelniania użytkowników  
  
-   Krok 4: modyfikowanie aplikacji ASP.NET do wyświetlenia w ramach stanu logowania  
  
-   Krok 5: Testowanie integracji między WIF i przez aplikację ASP.NET  
  
## <a name="step-1--install-the-identity-and-access-extension"></a>Krok 1: Instalowanie tożsamości i uzyskiwać dostęp do rozszerzenia  
 W tym kroku opisano sposób konfigurowania rozszerzenia tożsamościami i dostępem do programu Visual Studio 2012. To rozszerzenie automatyzuje proces konfigurowania aplikacji do komunikowania się z punktów końcowych usługi STS.  
  
#### <a name="to-install-the-identity-and-access-extension"></a>Aby zainstalować rozszerzenie tożsamościami i dostępem  
  
1.  Uruchom program Visual Studio w trybie podwyższonych uprawnień jako administrator.  
  
2.  W programie Visual Studio, kliknij przycisk **narzędzia** i kliknij przycisk **Menedżera rozszerzenia**. **Menedżera rozszerzenia** zostanie wyświetlone okno.  
  
3.  W **Menedżera rozszerzenia**, kliknij przycisk **rozszerzeń Online** z menu po lewej stronie, następnie wybierz **galerii programu Visual Studio**.  
  
4.  W prawym górnym rogu **Menedżera rozszerzenia**, wyszukaj *tożsamościami i dostępem*.  
  
5.  **Tożsamościami i dostępem** element zostanie wyświetlony w wynikach wyszukiwania. Kliknij go, a następnie kliknij przycisk **Pobierz**.  
  
6.  **Pobierz i zainstaluj** zostanie wyświetlone okno dialogowe. Jeśli zgadzasz się z warunkami licencji, kliknij przycisk **zainstalować**.  
  
7.  Gdy **tożsamościami i dostępem** rozszerzenia zakończył instalowanie, uruchom ponownie program Visual Studio w trybie administratora.  
  
## <a name="step-2--create-a-relying-party-aspnet-application"></a>Krok 2 — Tworzenie aplikacji ASP.NET firm jednostki uzależnionej  
 W tym kroku opisano sposób tworzenia uzależnioną aplikacji formularzy sieci Web ASP.NET, która zostanie zintegrowana z WIF.  
  
#### <a name="to-create-a-simple-aspnet-application"></a>Aby utworzyć prostą aplikację ASP.NET  
  
1.  Uruchom program Visual Studio, a następnie kliknij przycisk **pliku**, **nowy**, a następnie **projektu**.  
  
2.  W **nowy projekt** okna, kliknij przycisk **aplikacji formularzy sieci Web ASP.NET**.  
  
3.  W **nazwa**, wprowadź `TestApp` i naciśnij klawisz **OK**.  
  
## <a name="step-3--enable-local-development-sts-to-authenticate-users"></a>Krok 3 — Włączanie lokalne działania projektowe STS do uwierzytelniania użytkowników  
 W tym kroku opisano sposób włączania lokalnej usługi STS Programowanie w aplikacji. Lokalne programowanie STS jest włączona przy użyciu rozszerzenia tożsamościami i dostępem dla programu Visual Studio.  
  
#### <a name="to-enable-local-development-sts-in-your-aspnet-application"></a>Aby włączyć lokalne STS Programowanie w aplikacji platformy ASP.NET  
  
1.  W programie Visual Studio, kliknij prawym przyciskiem myszy **TestApp** projektu w obszarze **Eksploratora rozwiązań**, a następnie wybierz pozycję **tożsamościami i dostępem**.  
  
2.  **Tożsamościami i dostępem** zostanie wyświetlone okno. W obszarze **dostawców**, wybierz pozycję **testowania aplikacji z lokalnej usługi STS programowanie**, następnie kliknij przycisk **Zastosuj**.  
  
## <a name="step-4--modify-your-aspnet-application-to-display-sign-in-status"></a>Krok 4: modyfikowanie aplikacji ASP.NET do wyświetlenia w ramach stanu logowania  
 W tym kroku opisano sposób modyfikowania aplikacji platformy ASP.NET można dynamicznie stwierdzenie, czy bieżący użytkownik jest zalogowany. Po skonfigurowaniu dostawcy usługi STS WIF obsługuje oświadczenia przychodzące. Teraz należy skonfigurować kod aplikacji, aby wyświetlić wynik uwierzytelniania.  
  
#### <a name="to-display-sign-in-status"></a>Aby wyświetlić znak w stan  
  
1.  W programie Visual Studio Otwórz **Default.aspx** plików w obszarze **TestApp** projektu.  
  
2.  Zastąp istniejący kod znaczników w **Default.aspx** pliku z następujący kod:  
  
    ```  
    <%@ Page Language="C#" AutoEventWireup="true" CodeFile="Default.aspx.cs" Inherits="_Default" %>  
  
    <!DOCTYPE html>  
  
    <html>  
    <head runat="server">  
        <title>Logged In Status</title>  
    </head>  
    <body>  
        <asp:label ID="myLabel" runat="server" />  
    </body>  
    </html>  
    ```  
  
3.  Zapisz **Default.aspx**, a następnie otwórz jego kodzie pliku o nazwie **Default.aspx.cs**.  
  
    > [!NOTE]
    >  **Default.aspx.cs** mogą być ukryte pod **Default.aspx** w Eksploratorze rozwiązań. Jeśli **Default.aspx.cs** nie jest widoczny, rozwiń węzeł **Default.aspx** , klikając trójkąt obok niej.  
  
4.  Zastąp istniejący kod w **Default.aspx.cs** następującym kodem:  
  
    ```csharp  
    using System;  
    using System.Web.UI;  
    using System.Security.Claims;  
  
    namespace TestApp  
    {  
        protected void Page_Load(object sender, EventArgs e)  
        {  
            ClaimsPrincipal claimsPrincipal = Thread.CurrentPrincipal as ClaimsPrincipal;  
  
            if (claimsPrincipal != null)  
            {  
                myLabel.Text = "You are signed in.";  
            }  
            else  
            {  
                myLabel.Text = "You are not signed in.";  
            }  
        }  
    }  
    ```  
  
5.  Zapisz **Default.aspx.cs**i kompilowania aplikacji.  
  
## <a name="step-5--test-the-integration-between-wif-and-your-aspnet-application"></a>Krok 5: Testowanie integracji między WIF i przez aplikację ASP.NET  
 W tym kroku opisano, jak można sprawdzić integrację między WIF i przez aplikację ASP.NET.  
  
#### <a name="to-test-the-integration-between-wif-and-aspnet"></a>Aby sprawdzić integrację między usługami WIF i platformy ASP.NET  
  
1.  W programie Visual Studio, naciśnij klawisz **F5** można rozpocząć debugowania aplikacji. Jeśli nie zostaną znalezione żadne błędy, zostanie otwarte nowe okno przeglądarki.  
  
2.  Można zauważyć dyskretnie przekierowuje żądanie do usługi STS przeglądarki, a następnie otwiera stronę Default.aspx. Jeśli WIF jest skonfigurowany prawidłowo, powinien zostać wyświetlony lokacji, wyświetl następujący tekst: **"Użytkownik jest zalogowany"**.
