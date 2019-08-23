---
title: 'Instrukcje: Wyświetlanie stanu zalogowania przy użyciu programu WIF'
ms.date: 03/30/2017
ms.assetid: 4d1174e4-5397-4962-9a5f-3b1ad7b3fc14
author: BrucePerlerMS
ms.openlocfilehash: e44dc80260e46b81ac723ada32085390a18a153a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69945700"
---
# <a name="how-to-display-signed-in-status-using-wif"></a>Instrukcje: Wyświetlanie stanu zalogowania przy użyciu programu WIF
## <a name="applies-to"></a>Dotyczy:  
  
- Microsoft® Windows® Identity Foundation (WIF) 4,5  
  
- ASP.NET® Web Forms  
  
## <a name="summary"></a>Podsumowanie  
 W tym temacie opisano sposób wyświetlania stanu logowania w aplikacji ASP.NET z włączoną obsługą WIF. WIF zapewnia mechanizm tworzenia oświadczeń aplikacji i zarządzania uwierzytelnianiem i autoryzacją zasobów aplikacji.  
  
## <a name="contents"></a>Spis treści  
  
- Omówienie  
  
- Zestawienie czynności  
  
- Krok 1 — Instalowanie tożsamości i rozszerzenia dostępu  
  
- Krok 2 — Tworzenie aplikacji ASP.NET jednostki uzależnionej  
  
- Krok 3 — włączenie lokalnego programu STS do uwierzytelniania użytkowników  
  
- Krok 4 — modyfikowanie aplikacji ASP.NET na potrzeby wyświetlania stanu logowania  
  
- Krok 5 — testowanie integracji między WIF i ASP.NET aplikacji  
  
## <a name="overview"></a>Omówienie  
 W tym temacie pokazano, jak utworzyć prostą aplikację obsługującą oświadczenia przy użyciu WIF oraz jak łatwo wyświetlać informacje o tym, czy użytkownik jest zalogowany. W poniższych krokach użyto lokalnego tworzenia usługi STS dołączonego do rozszerzenia tożsamości i dostępu do programu Visual Studio. Lokalna programowanie w usłudze STS jest przeznaczone dla środowiska testowania i programowania, aby zapewnić prostą metodę integrowania oświadczeń z aplikacją. Nigdy nie powinna być używana w środowisku produkcyjnym, ponieważ nie wykonuje rzeczywistego uwierzytelniania i poświadczenia nie są wymagane. Jednak bezwzględny kod w poniższych krokach jest taki sam dla aplikacji gotowej do użycia w środowisku produkcyjnym przy użyciu rzeczywistego uwierzytelniania.  
  
## <a name="summary-of-steps"></a>Zestawienie czynności  
  
- Krok 1 — Instalowanie tożsamości i rozszerzenia dostępu  
  
- Krok 2 — Tworzenie aplikacji ASP.NET jednostki uzależnionej  
  
- Krok 3 — włączenie lokalnego programu STS do uwierzytelniania użytkowników  
  
- Krok 4 — modyfikowanie aplikacji ASP.NET na potrzeby wyświetlania stanu logowania  
  
- Krok 5 — testowanie integracji między WIF i ASP.NET aplikacji  
  
## <a name="step-1--install-the-identity-and-access-extension"></a>Krok 1 — Instalowanie tożsamości i rozszerzenia dostępu  
 W tym kroku opisano sposób konfigurowania rozszerzenia tożsamości i dostępu do programu Visual Studio 2012. To rozszerzenie automatyzuje proces konfigurowania aplikacji w celu komunikowania się z punktami końcowymi usługi STS.  
  
### <a name="to-install-the-identity-and-access-extension"></a>Aby zainstalować tożsamość i rozszerzenie dostępu  
  
1. Uruchom program Visual Studio w trybie podwyższonych uprawnień jako administrator.  
  
2. W programie Visual Studio kliknij pozycję **Narzędzia** , a następnie kliknij pozycję **Menedżer rozszerzeń**. Zostanie wyświetlone okno **Menedżer rozszerzeń** .  
  
3. W **Menedżerze rozszerzeń**kliknij pozycję **rozszerzenia online** w menu po lewej stronie, a następnie wybierz pozycję **Galeria Visual Studio**.  
  
4. W prawym górnym rogu **Menedżera rozszerzeń**Wyszukaj pozycję *tożsamość i dostęp*.  
  
5. **Tożsamość i element dostępu** będą widoczne w wynikach wyszukiwania. Kliknij go, a następnie kliknij pozycję **Pobierz**.  
  
6. Zostanie wyświetlone okno dialogowe **pobieranie i Instalowanie** . Jeśli zgadzasz się z postanowieniami licencyjnymi, kliknij przycisk **Instaluj**.  
  
7. Po zakończeniu instalacji rozszerzenia **tożsamości i dostępu** Uruchom ponownie program Visual Studio w trybie administratora.  
  
## <a name="step-2--create-a-relying-party-aspnet-application"></a>Krok 2 — Tworzenie aplikacji ASP.NET jednostki uzależnionej  
 W tym kroku opisano sposób tworzenia aplikacji ASP.NET Web Forms jednostki uzależnionej, która zostanie zintegrowana z WIF.  
  
### <a name="to-create-a-simple-aspnet-application"></a>Aby utworzyć prostą aplikację ASP.NET  
  
1. Uruchom program Visual Studio i kliknij kolejno pozycje **plik**, **Nowy**i **projekt**.  
  
2. W oknie **Nowy projekt** kliknij pozycję **ASP.NET Web Forms aplikacji**.  
  
3. W polu **Nazwa**wprowadź `TestApp` i naciśnij przycisk **OK**.  
  
## <a name="step-3--enable-local-development-sts-to-authenticate-users"></a>Krok 3 — włączenie lokalnego programu STS do uwierzytelniania użytkowników  
 W tym kroku opisano sposób włączania lokalnego tworzenia usługi STS w aplikacji. Lokalna programowanie usługi STS jest włączona przy użyciu rozszerzenia tożsamości i dostępu dla programu Visual Studio.  
  
### <a name="to-enable-local-development-sts-in-your-aspnet-application"></a>Aby włączyć lokalne programowanie usługi STS w aplikacji ASP.NET  
  
1. W programie Visual Studio kliknij prawym przyciskiem myszy projekt **TestApp** w obszarze **Eksplorator rozwiązań**, a następnie wybierz pozycję **tożsamość i dostęp**.  
  
2. Zostanie wyświetlone okno **tożsamość i dostęp** . W obszarze **dostawcy**wybierz pozycję **Testuj aplikację przy użyciu lokalnej usługi STS**, a następnie kliknij przycisk **Zastosuj**.  
  
## <a name="step-4--modify-your-aspnet-application-to-display-sign-in-status"></a>Krok 4 — modyfikowanie aplikacji ASP.NET na potrzeby wyświetlania stanu logowania  
 W tym kroku opisano sposób modyfikowania aplikacji ASP.NET w celu dynamicznego wyświetlania, czy bieżący użytkownik jest zalogowany. Po skonfigurowaniu dostawcy usługi STS WIF obsługuje oświadczenia przychodzące. Teraz musisz skonfigurować kod aplikacji, aby wyświetlić wynik uwierzytelniania.  
  
### <a name="to-display-sign-in-status"></a>Aby wyświetlić stan logowania  
  
1. W programie Visual Studio Otwórz plik **default. aspx** w projekcie **TestApp** .  
  
2. Zastąp istniejący znacznik w pliku **default. aspx** następującym znacznikiem:  
  
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
  
3. Zapisz plik **default. aspx**, a następnie otwórz jego kod w pliku o nazwie **default.aspx.cs**.  
  
    > [!NOTE]
    > **Default.aspx.cs** może być ukryty poniżej **default. aspx** w Eksplorator rozwiązań. Jeśli **default.aspx.cs** nie jest widoczny, rozwiń plik **default. aspx** , klikając trójkąt obok niego.  
  
4. Zastąp istniejący kod w **default.aspx.cs** następującym kodem:  
  
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
  
5. Zapisz **default.aspx.cs**i skompiluj aplikację.  
  
## <a name="step-5--test-the-integration-between-wif-and-your-aspnet-application"></a>Krok 5 — testowanie integracji między WIF i ASP.NET aplikacji  
 W tym kroku opisano, jak można testować integrację między programem WIF i aplikacją ASP.NET.  
  
### <a name="to-test-the-integration-between-wif-and-aspnet"></a>Aby przetestować integrację między WIF i ASP.NET  
  
1. W programie Visual Studio naciśnij klawisz **F5** , aby rozpocząć debugowanie aplikacji. Jeśli nie zostaną znalezione żadne błędy, zostanie otwarte nowe okno przeglądarki.  
  
2. Możesz zauważyć, że przeglądarka w trybie dyskretnym przekierowuje żądanie do usługi STS, a następnie otworzy stronę Default. aspx. Jeśli WIF jest prawidłowo skonfigurowany, powinna zostać wyświetlona następująca treść witryny: **"Jesteś zalogowany"** .
