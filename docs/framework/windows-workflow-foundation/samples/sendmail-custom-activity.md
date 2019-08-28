---
title: Niestandardowe działanie SendMail
ms.date: 03/30/2017
ms.assetid: 947a9ae6-379c-43a3-9cd5-87f573a5739f
ms.openlocfilehash: 9325817a24fee3ba04c2c305ebfdfbc6ff6da1bd
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70038112"
---
# <a name="sendmail-custom-activity"></a>Niestandardowe działanie SendMail
Ten przykład pokazuje, jak utworzyć niestandardowe działanie, które wynika z <xref:System.Activities.AsyncCodeActivity> programu w celu wysłania wiadomości e-mail przy użyciu protokołu SMTP do użycia w aplikacji przepływu pracy. Działanie niestandardowe umożliwia wysyłanie wiadomości e-mail asynchronicznie i wysyłanie wiadomości z uwierzytelnianiem przy użyciu funkcji programu <xref:System.Net.Mail.SmtpClient> . Zapewnia również pewne funkcje użytkownika końcowego, takie jak tryb testu, Zastępowanie tokenu, szablony plików i ścieżka do usuwania testów.  
  
 Poniższa tabela zawiera szczegółowe informacje o argumentach `SendMail` działania.  
  
|Nazwa|Typ|Opis|  
|-|-|-|  
|Host|String|Adres hosta serwera SMTP.|  
|Port|String|Port usługi SMTP na hoście.|  
|EnableSsl|bool|Określa, <xref:System.Net.Mail.SmtpClient> czy program używa SSL (SSL) do szyfrowania połączenia.|  
|UserName|String|Nazwa użytkownika, aby skonfigurować poświadczenia w celu uwierzytelnienia <xref:System.Net.Mail.SmtpClient.Credentials%2A> właściwości nadawcy.|  
|Hasło|String|Hasło w celu skonfigurowania poświadczeń w celu uwierzytelnienia <xref:System.Net.Mail.SmtpClient.Credentials%2A> właściwości nadawcy.|  
|Subject|<xref:System.Activities.InArgument%601>\<ciąg >|Temat wiadomości.|  
|Treść|<xref:System.Activities.InArgument%601>\<ciąg >|Treść wiadomości.|  
|Załączniki|<xref:System.Activities.InArgument%601>\<ciąg >|Kolekcja załączników służąca do przechowywania danych dołączonych do tej wiadomości e-mail.|  
|Z|<xref:System.Net.Mail.MailAddress>|Adres od dla tej wiadomości e-mail.|  
|Zadanie|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|Kolekcja adresów zawierająca adresatów tej wiadomości e-mail.|  
|CC|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|Kolekcja adresów zawierająca adresatów kopii wiadomości e-mail.|  
|BCC|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|Kolekcja adresów zawierająca adresatów (UDW) dla tej wiadomości e-mail.|  
|Tokeny|<xref:System.Activities.InArgument%601>< ciąg\<IDictionary > >|Tokeny do zamiany w treści. Ta funkcja umożliwia użytkownikom Określanie niektórych wartości w treści, niż można zastąpić je później za pomocą tokenów dostarczonych przy użyciu tej właściwości.|  
|BodyTemplateFilePath|String|Ścieżka szablonu dla treści. `SendMail` Działanie kopiuje zawartość tego pliku do jego właściwości Body.<br /><br /> Szablon może zawierać tokeny, które są zastępowane przez zawartość właściwości tokens.|  
|TestMailTo|<xref:System.Net.Mail.MailAddress>|Gdy ta właściwość jest ustawiona, wszystkie wiadomości e-mail są wysyłane na adres określony w tym polu.<br /><br /> Ta właściwość jest przeznaczona do użycia podczas testowania przepływów pracy. Na przykład jeśli chcesz upewnić się, że wszystkie wiadomości e-mail są wysyłane bez wysyłania ich do rzeczywistych adresatów.|  
|TestDropPath|String|Gdy ta właściwość jest ustawiona, wszystkie wiadomości e-mail są również zapisywane w określonym pliku.<br /><br /> Ta właściwość jest przeznaczona do użycia podczas testowania lub debugowania przepływów pracy, aby upewnić się, że format i zawartość wychodzących wiadomości e-mail są odpowiednie.|  
  
## <a name="solution-contents"></a>Zawartość rozwiązania  
 Rozwiązanie zawiera dwa projekty.  
  
|Projekt|Opis|Ważne pliki|  
|-------------|-----------------|---------------------|  
|SendMail|Działanie SendMail|1.  SendMail.cs: implementacja głównego działania<br />2.  SendMailDesigner. XAML i SendMailDesigner.xaml.cs: Projektant dla działania SendMail<br />3.  MailTemplateBody. htm: szablon wiadomości e-mail do wysłania.|  
|SendMailTestClient|Klient do testowania działania SendMail.  Ten projekt przedstawia dwa sposoby wywoływania działania SendMail: deklaratywnie i programistyczne.|1.  Sequence1. XAML: przepływ pracy, który wywołuje działanie SendMail.<br />2.  Program.cs: wywołuje Sequence1, a także programowo tworzy przepływ pracy, który używa SendMail.|  
  
## <a name="further-configuration-of-the-sendmail-activity"></a>Dodatkowa konfiguracja działania SendMail  
 Chociaż nie są wyświetlane w przykładzie, użytkownicy mogą wykonać dodatkowe czynności konfiguracyjne działania SendMail. W następnych trzech sekcjach pokazano, jak to zrobić.  
  
### <a name="sending-an-email-using-tokens-specified-in-the-body"></a>Wysyłanie wiadomości e-mail przy użyciu tokenów określonych w treści  
 W tym fragmencie kodu pokazano, jak można wysyłać wiadomości e-mail z tokenami w treści. Zwróć uwagę na to, jak tokeny są udostępniane we właściwości treść. Wartości tych tokenów są udostępniane właściwości tokens.  
  
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
 W tym fragmencie kodu pokazano, jak wysłać wiadomość e-mail przy użyciu tokenów szablonu w treści. Należy zauważyć, że podczas `BodyTemplateFilePath` ustawiania właściwości nie musimy podawać wartości właściwości Body (zawartość pliku szablonu zostanie skopiowana do treści).  
  
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
  
### <a name="sending-mails-in-testing-mode"></a>Wysyłanie wiadomości w trybie testowania  
 W tym fragmencie kodu pokazano, jak ustawić dwie właściwości testowania: według ustawienia `TestMailTo` dla wszystkich wiadomości będą wysyłane do `john.doe@contoso.con` (bez względu na wartości do, DW, UDW). Ustawienie TestDropPath wszystkie wychodzące wiadomości e-mail zostanie również zarejestrowane w podanej ścieżce. Te właściwości można ustawiać niezależnie (nie są powiązane).  
  
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
 Dla tego przykładu wymagany jest dostęp do serwera SMTP.  
  
 Aby uzyskać więcej informacji na temat konfigurowania serwera SMTP, zobacz poniższe linki.  
  
- [Microsoft Technet](https://go.microsoft.com/fwlink/?LinkId=166060)  
  
- [Konfigurowanie usługi SMTP (IIS 6,0)](https://go.microsoft.com/fwlink/?LinkId=150456)  
  
- [IIS 7.0: Konfigurowanie poczty E-Mail SMTP](https://go.microsoft.com/fwlink/?LinkId=150457)  
  
- [Jak zainstalować usługę SMTP](https://go.microsoft.com/fwlink/?LinkId=150458)  
  
 Emulatory SMTP udostępniane przez inne firmy są dostępne do pobrania.  
  
##### <a name="to-run-this-sample"></a>Aby uruchomić ten przykład  
  
1. Za pomocą programu Visual Studio 2010 Otwórz plik rozwiązania SendMail. sln.  
  
2. Upewnij się, że masz dostęp do prawidłowego serwera SMTP. Zapoznaj się z instrukcjami konfiguracji.  
  
3. Skonfiguruj program przy użyciu adresu serwera oraz od i do adresów e-mail.  
  
     Aby prawidłowo uruchomić ten przykład, może być konieczne skonfigurowanie wartości z i na adresy e-mail oraz adres serwera SMTP w Program.cs i w sekwencji. XAML. Należy zmienić adres w obu lokalizacjach, ponieważ program wysyła pocztę e-mail na dwa różne sposoby  
  
4. Aby skompilować rozwiązanie, naciśnij klawisze CTRL + SHIFT + B.  
  
5. Aby uruchomić rozwiązanie, naciśnij klawisze CTRL + F5.  
  
> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\SendMail`
