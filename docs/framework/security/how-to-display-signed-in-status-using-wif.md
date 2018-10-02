---
title: 'Instrukcje: Wyświetlanie stanu zalogowania przy użyciu programu WIF'
ms.date: 03/30/2017
ms.assetid: 4d1174e4-5397-4962-9a5f-3b1ad7b3fc14
author: BrucePerlerMS
ms.openlocfilehash: 7d3d23dc1f2e081c0a7c53fbdfaef749c9729fd4
ms.sourcegitcommit: daa8788af67ac2d1cecd24f9f3409babb2f978c9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/01/2018
ms.locfileid: "47863055"
---
# <a name="how-to-display-signed-in-status-using-wif"></a>Instrukcje: Wyświetlanie stanu zalogowania przy użyciu programu WIF
## <a name="applies-to"></a>Dotyczy:  
  
-   Microsoft® Windows® Identity Foundation (WIF) 4.5  
  
-   ASP.NET® formularzy sieci Web  
  
## <a name="summary"></a>Podsumowanie  
 W tym temacie opisano sposób wyświetlania znak w stanie w aplikacji ASP.NET z włączoną obsługą programu WIF. Program WIF oferuje mechanizm do tworzenia Twojej aplikacji obsługujących oświadczenia i zarządzanie uwierzytelniania i autoryzacji dla zasobów aplikacji.  
  
## <a name="contents"></a>Spis treści  
  
-   Omówienie  
  
-   Zestawienie czynności  
  
-   Krok 1: Zainstaluj tożsamość i dostęp do rozszerzenia  
  
-   Krok 2 — Tworzenie aplikacji jednostki uzależnionej strona ASP.NET  
  
-   Krok 3 — Włączanie lokalnej deweloperskiej usługi STS do uwierzytelniania kont użytkowników  
  
-   Krok 4 — zmodyfikować aplikację ASP.NET w celu wyświetlania logowania w stan  
  
-   Krok 5: Testowanie integracji między programu WIF i aplikacji ASP.NET  
  
## <a name="overview"></a>Omówienie  
 W tym temacie przedstawiono sposób tworzenia prostej aplikacji obsługującej oświadczenia, za pomocą programu WIF oraz jak łatwo wyświetlać, czy użytkownik jest zalogowany. Użyto lokalnej deweloperskiej usługi STS dołączoną tożsamości i dostępu rozszerzenie programu Visual Studio. Local Development STS jest przeznaczony dla środowisk testowych i programistycznych środowisku w celu zapewnienia to prosta metoda integrowania oświadczeń do aplikacji. Go nie należy używać w środowisku produkcyjnym, ponieważ nie wykonuje faktycznego uwierzytelniania i poświadczenia nie są wymagane. Jednak kodu imperatywnego w poniższych krokach jest taka sama dla aplikacji gotowych do produkcji rzeczywistego uwierzytelniania.  
  
## <a name="summary-of-steps"></a>Zestawienie czynności  
  
-   Krok 1: Zainstaluj tożsamość i dostęp do rozszerzenia  
  
-   Krok 2 — Tworzenie aplikacji jednostki uzależnionej strona ASP.NET  
  
-   Krok 3 — Włączanie lokalnej deweloperskiej usługi STS do uwierzytelniania kont użytkowników  
  
-   Krok 4 — zmodyfikować aplikację ASP.NET w celu wyświetlania logowania w stan  
  
-   Krok 5: Testowanie integracji między programu WIF i aplikacji ASP.NET  
  
## <a name="step-1--install-the-identity-and-access-extension"></a>Krok 1: Zainstaluj tożsamość i dostęp do rozszerzenia  
 W tym kroku opisano sposób konfigurowania rozszerzenia tożsamościami i dostępem do programu Visual Studio 2012. To rozszerzenie automatyzuje proces konfigurowania aplikacji do komunikowania się z punktami końcowymi usługi STS.  
  
#### <a name="to-install-the-identity-and-access-extension"></a>Aby zainstalować rozszerzenie tożsamościami i dostępem  
  
1.  Uruchom program Visual Studio w trybie podwyższonych uprawnień jako administrator.  
  
2.  W programie Visual Studio, kliknij przycisk **narzędzia** i kliknij przycisk **Menedżera rozszerzeń**. **Menedżera rozszerzeń** zostanie wyświetlone okno.  
  
3.  W **Menedżera rozszerzeń**, kliknij przycisk **rozszerzeń Online** menu po lewej stronie, następnie wybierz pozycję **galerii Visual Studio**.  
  
4.  W prawym górnym rogu **Menedżera rozszerzeń**, wyszukaj *tożsamościami i dostępem*.  
  
5.  **Tożsamościami i dostępem** element zostanie wyświetlony w wynikach wyszukiwania. Kliknij go, a następnie kliknij przycisk **Pobierz**.  
  
6.  **Pobierz i zainstaluj** zostanie wyświetlone okno dialogowe. Jeśli akceptujesz postanowienia licencyjne, kliknij przycisk **zainstalować**.  
  
7.  Gdy **tożsamościami i dostępem** instalacja rozszerzenia została ukończona, uruchom program Visual Studio w trybie administratora.  
  
## <a name="step-2--create-a-relying-party-aspnet-application"></a>Krok 2 — Tworzenie aplikacji jednostki uzależnionej strona ASP.NET  
 Tym kroku opisano sposób tworzenia jednostki uzależnionej ze stron aplikacji formularzy sieci Web ASP.NET, która integruje się z programu WIF.  
  
#### <a name="to-create-a-simple-aspnet-application"></a>Aby utworzyć prostą aplikację platformy ASP.NET  
  
1.  Uruchom program Visual Studio, a następnie kliknij przycisk **pliku**, **New**, a następnie **projektu**.  
  
2.  W **nowy projekt** okna, kliknij przycisk **aplikacji formularzy sieci Web ASP.NET**.  
  
3.  W **nazwa**, wprowadź `TestApp` i naciśnij klawisz **OK**.  
  
## <a name="step-3--enable-local-development-sts-to-authenticate-users"></a>Krok 3 — Włączanie lokalnej deweloperskiej usługi STS do uwierzytelniania kont użytkowników  
 W tym kroku opisano, jak włączyć lokalnej deweloperskiej usługi STS w aplikacji. Lokalnej deweloperskiej usługi STS jest włączona, przy użyciu rozszerzenia tożsamości i dostępu dla programu Visual Studio.  
  
#### <a name="to-enable-local-development-sts-in-your-aspnet-application"></a>Aby włączyć lokalnej deweloperskiej usługi STS w aplikacji programu ASP.NET  
  
1.  W programie Visual Studio, kliknij prawym przyciskiem myszy **TestApp** projekt **Eksploratora rozwiązań**, a następnie wybierz **tożsamościami i dostępem**.  
  
2.  **Tożsamościami i dostępem** zostanie wyświetlone okno. W obszarze **dostawców**, wybierz opcję **testować swoją aplikację za pomocą lokalnej deweloperskiej usługi STS**, następnie kliknij przycisk **Zastosuj**.  
  
## <a name="step-4--modify-your-aspnet-application-to-display-sign-in-status"></a>Krok 4 — zmodyfikować aplikację ASP.NET w celu wyświetlania logowania w stan  
 W tym kroku opisano, jak zmodyfikować aplikację ASP.NET w celu dynamicznego wyświetlania, czy bieżący użytkownik jest zalogowany. Po skonfigurowaniu dostawcy usługi STS program WIF obsługuje oświadczenia przychodzące. Teraz należy skonfigurować kod aplikacji, aby wyświetlić wynik uwierzytelniania.  
  
#### <a name="to-display-sign-in-status"></a>Aby wyświetlić logowania w stan  
  
1.  W programie Visual Studio, otwórz **Default.aspx** plik **TestApp** projektu.  
  
2.  Zastąp istniejący kod znaczników w **Default.aspx** pliku następującym kodem:  
  
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
  
3.  Zapisz **Default.aspx**, a następnie otwórz jego kod związany z pliku o nazwie **Default.aspx.cs**.  
  
    > [!NOTE]
    >  **Default.aspx.cs** może być ukryty pod **Default.aspx** w Eksploratorze rozwiązań. Jeśli **Default.aspx.cs** nie jest widoczny, rozwiń węzeł **Default.aspx** , klikając trójkąta obok niej.  
  
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
  
5.  Zapisz **Default.aspx.cs**i utworzyć aplikację.  
  
## <a name="step-5--test-the-integration-between-wif-and-your-aspnet-application"></a>Krok 5: Testowanie integracji między programu WIF i aplikacji ASP.NET  
 W tym kroku opisano, jak można przetestować integrację programu WIF i aplikacji ASP.NET.  
  
#### <a name="to-test-the-integration-between-wif-and-aspnet"></a>Aby przetestować integrację programu WIF i platformy ASP.NET  
  
1.  W programie Visual Studio, naciśnij klawisz **F5** można rozpocząć debugowania aplikacji. Jeśli nie znaleziono żadnych błędów, zostanie otwarte nowe okno przeglądarki.  
  
2.  Możesz zauważyć, że przeglądarki dyskretnie przekierowuje żądanie do usługi STS, a następnie spowoduje otwarcie strony Default.aspx. Jeśli program WIF jest poprawnie skonfigurowany, powinien zostać wyświetlony witryny, wyświetl następujący tekst: **"Użytkownik jest zalogowany"**.
