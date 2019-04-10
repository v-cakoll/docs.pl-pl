---
title: Niestandardowe działanie SendMail
ms.date: 03/30/2017
ms.assetid: 947a9ae6-379c-43a3-9cd5-87f573a5739f
ms.openlocfilehash: 89252098402deee991ea01b8e76082a5f4b8c389
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59321864"
---
# <a name="sendmail-custom-activity"></a>Niestandardowe działanie SendMail
W tym przykładzie pokazano, jak utworzyć niestandardowe działanie, która pochodzi od klasy <xref:System.Activities.AsyncCodeActivity> do wysyłania wiadomości e-mail przy użyciu protokołu SMTP do użycia w aplikacji przepływu pracy. Niestandardowe działanie korzysta z możliwości <xref:System.Net.Mail.SmtpClient> asynchroniczne wysyłanie wiadomości e-mail i Wyślij wiadomość e-mail z uwierzytelnianiem. Umożliwia także niektóre funkcje użytkowników końcowych, takich jak przetestować tryb zastępowania tokenu, Szablony plików i przetestować ścieżki docelowej.  
  
 W poniższej tabeli przedstawiono argumenty `SendMail` działania.  
  
|Nazwa|Typ|Opis|  
|-|-|-|  
|Host|String|Adres hosta serwera SMTP.|  
|Port|String|Port usługi SMTP na hoście.|  
|EnableSsl|bool|Określa, czy <xref:System.Net.Mail.SmtpClient> używa protokołu Secure Sockets Layer (SSL) do szyfrowania połączenia.|  
|UserName|String|Nazwa użytkownika, aby ustawić poświadczenia, aby uwierzytelnić nadawcę <xref:System.Net.Mail.SmtpClient.Credentials%2A> właściwości.|  
|Hasło|String|Hasło, aby ustawić poświadczenia, aby uwierzytelnić nadawcę <xref:System.Net.Mail.SmtpClient.Credentials%2A> właściwości.|  
|Podmiot|<xref:System.Activities.InArgument%601>\<ciąg >|Temat wiadomości.|  
|Treść|<xref:System.Activities.InArgument%601>\<ciąg >|Treść wiadomości.|  
|Załączniki|<xref:System.Activities.InArgument%601>\<ciąg >|Kolekcja załącznika używany do przechowywania danych dołączone do tej wiadomości e-mail.|  
|Z|<xref:System.Net.Mail.MailAddress>|Adres początkowy dla tej wiadomości e-mail.|  
|Zadanie|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|Kolekcja adresów, która zawiera adresatów wiadomości e-mail.|  
|CC|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|Adres kolekcji, która zawiera Adresaci kopii (DW) dla tej wiadomości e-mail.|  
|BCC|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|Kolekcja adresów, zawierający adresatów kopii (UDW) dla tej wiadomości e-mail.|  
|Tokeny|<xref:System.Activities.InArgument%601>< IDictionary\<ciąg, ciąg >>|Tokeny do zastąpienia w treści. Ta funkcja umożliwia użytkownikom wskazanie niektóre wartości w treści, niż można zastąpić później przez tokeny zabezpieczające udostępniane przy użyciu tej właściwości.|  
|BodyTemplateFilePath|String|Ścieżka szablonu dla treści. `SendMail` Działanie kopiuje zawartość tego pliku do jego właściwości treści.<br /><br /> Szablon może zawierać tokenów, które są zastępowane przez zawartość właściwości tokenów.|  
|TestMailTo|<xref:System.Net.Mail.MailAddress>|Gdy ta właściwość jest ustawiona, wszystkie wiadomości e-mail są wysyłane na adres określony w nim.<br /><br /> Ta właściwość jest przeznaczona do użycia podczas testowania przepływów pracy. Na przykład jeśli chcesz upewnić się, że wszystkie wiadomości e-mail są wysyłane bez wysyłania ich do rzeczywistych adresatów.|  
|TestDropPath|String|Gdy ta właściwość jest ustawiona, wszystkie wiadomości e-mail również są zapisywane w określonym pliku.<br /><br /> Ta właściwość jest przeznaczona do użycia podczas testowania i debugowania przepływów pracy, aby upewnić się, że format i zawartość wychodzących wiadomości e-mail jest odpowiednia.|  
  
## <a name="solution-contents"></a>Zawartość rozwiązania  
 Rozwiązanie zawiera dwa projekty.  
  
|Projekt|Opis|Ważnych plików|  
|-------------|-----------------|---------------------|  
|SendMail|Działanie SendMail|1.  SendMail.cs: implementacja dla głównego działania<br />2.  SendMailDesigner.xaml i SendMailDesigner.xaml.cs: projektanta za działanie SendMail<br />3.  MailTemplateBody.htm: szablon wiadomości e-mail, które zostaną wysłane.|  
|SendMailTestClient|Klient, aby przetestować działanie SendMail.  Ten projekt przedstawia dwa sposoby wywoływania działanie SendMail: sposób deklaratywny i programowy.|1.  Sequence1.XAML: przepływ pracy, który wywołuje działanie SendMail.<br />2.  Plik program.CS: wywołuje Sequence1, a także tworzy programowo używającej SendMail przepływu pracy.|  
  
## <a name="further-configuration-of-the-sendmail-activity"></a>Dalsza konfiguracja działanie SendMail  
 Mimo że nie pokazano w przykładzie, użytkownicy mogą wykonywać dodatkowe konfiguracji działanie SendMail. Następne trzy sekcje pokazują, jak to zrobić.  
  
### <a name="sending-an-email-using-tokens-specified-in-the-body"></a>Wysyłanie wiadomości e-mail przy użyciu tokenów określona w treści  
 Ten fragment kodu pokazuje, jak możesz wysłać wiadomość e-mail z tokenami w treści. Zwróć uwagę, jak tokeny znajdują się we właściwości treść. Właściwość tokenów podano wartości dla tych tokenów.  
  
```html  
IDictionary<string, string> tokens = new Dictionary<string, string>();  
tokens.Add("@name", "John Doe");  
tokens.Add("@date", DateTime.Now.ToString());  
tokens.Add("@server", "localhost");  
  
new SendMail  
{  
    From = new LambdaValue<MailAddress>(ctx => new MailAddress("john.doe@contoso.com")),  
    To = new LambdaValue<MailAddressCollection>(  
                    ctx => new MailAddressCollection() { new MailAddress("someone@microsoft.com") }),  
    Subject = "Test email",  
    Body = "Hello @name. This is a test email sent from @server. Current date is @date",  
    Host = "localhost",  
    Port = 25,  
    Tokens = new LambdaValue<IDictionary<string, string>>(ctx => tokens)  
};  
```  
  
### <a name="sending-an-email-using-a-template"></a>Wysyłanie wiadomości e-mail przy użyciu szablonu  
 Ten fragment kodu przedstawia sposób wysłania wiadomości e-mail przy użyciu tokenów szablonu w treści. Należy zauważyć, że podczas ustawiania `BodyTemplateFilePath` właściwości nie należy podać wartość dla właściwości treści (zawartość pliku szablonu zostaną skopiowane do treści).  
  
```  
new SendMail  
{    
    From = new LambdaValue<MailAddress>(ctx => new MailAddress("john.doe@contoso.com")),  
    To = new LambdaValue<MailAddressCollection>(  
                    ctx => new MailAddressCollection() { new MailAddress("someone@microsoft.com") }),  
    Subject = "Test email",  
    Host = "localhost",  
    Port = 25,  
    Tokens = new LambdaValue<IDictionary<string, string>>(ctx => tokens),  
    BodyTemplateFilePath = @"..\..\..\SendMail\Templates\MailTemplateBody.htm",   
};  
```  
  
### <a name="sending-mails-in-testing-mode"></a>Wysyłanie wiadomości E-mail w tryb testowania  
 Następujący fragment kodu przedstawia sposób ustawiania dwie właściwości testowania: ustawiając `TestMailTo` na wszystkie komunikaty zostaną wysłane do `john.doe@contoso.con` (bez uwzględniania wartości do, DW, UDW). Ustawiając TestDropPath wszystkie wychodzących wiadomości e-mail będą również rejestrowane w podanej ścieżce. Te właściwości można skonfigurować niezależnie (nie jest ona powiązana).  
  
```  
new SendMail  
{    
   From = new LambdaValue<MailAddress>(ctx => new MailAddress("john.doe@contoso.com")),  
   To = new LambdaValue<MailAddressCollection>(  
                    ctx => new MailAddressCollection() { new MailAddress("someone@microsoft.com") }),  
   Subject = "Test email",  
   Host = "localhost",  
   Port = 25,  
   Tokens = new LambdaValue<IDictionary<string, string>>(ctx => tokens),  
   BodyTemplateFilePath = @"..\..\..\SendMail\Templates\MailTemplateBody.htm",  
   TestMailTo= new LambdaValue<MailAddress>(ctx => new MailAddress("john.doe@contoso.com")),  
   TestDropPath = @"c:\Samples\SendMail\TestDropPath\",  
};  
```  
  
## <a name="set-up-instructions"></a>Instrukcje dotyczące konfiguracji  
 Dostęp do serwera SMTP jest wymagany dla tego przykładu.  
  
 Aby uzyskać więcej informacji na temat konfigurowania serwera SMTP zobacz poniższe linki.  
  
-   [Microsoft Technet](https://go.microsoft.com/fwlink/?LinkId=166060)  
  
-   [Konfigurowanie usługi SMTP (IIS 6.0)](https://go.microsoft.com/fwlink/?LinkId=150456)  
  
-   [IIS 7.0: Konfigurowanie wiadomości E-Mail SMTP](https://go.microsoft.com/fwlink/?LinkId=150457)  
  
-   [Jak zainstalować usługę SMTP](https://go.microsoft.com/fwlink/?LinkId=150458)  
  
 Emulatory SMTP udostępniane przez inne firmy są dostępne do pobrania.  
  
##### <a name="to-run-this-sample"></a>Aby uruchomić ten przykład  
  
1. Za pomocą programu Visual Studio 2010, otwórz plik rozwiązania SendMail.sln.  
  
2. Upewnij się, że masz dostęp do prawidłowego serwera SMTP. Zobacz instrukcje dotyczące konfiguracji.  
  
3. Skonfiguruj program za pomocą adres swojego serwera i z adresów e-mail.  
  
     Aby prawidłowo uruchomić ten przykład, może być konieczne skonfigurowanie wartości od i do adresów e-mail i adres serwera SMTP w pliku Program.cs i Sequence.xaml. Trzeba będzie zmienić adres w obu lokalizacjach, ponieważ program wysyła wiadomość e-mail na dwa różne sposoby  
  
4. Aby skompilować rozwiązanie, naciśnij klawisze CTRL + SHIFT + B.  
  
5. Aby uruchomić rozwiązanie, naciśnij kombinację klawiszy CTRL + F5.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\SendMail`