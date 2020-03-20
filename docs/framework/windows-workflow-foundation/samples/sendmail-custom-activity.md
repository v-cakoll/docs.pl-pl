---
title: Niestandardowe działanie SendMail
ms.date: 03/30/2017
ms.assetid: 947a9ae6-379c-43a3-9cd5-87f573a5739f
ms.openlocfilehash: e7cc64e68c3d78b9ee7ec813700e96a52c239141
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182782"
---
# <a name="sendmail-custom-activity"></a>Niestandardowe działanie SendMail
W tym przykładzie pokazano, jak utworzyć <xref:System.Activities.AsyncCodeActivity> działanie niestandardowe, które pochodzi z wysyłania poczty przy użyciu protokołu SMTP do użycia w aplikacji przepływu pracy. Działanie niestandardowe używa możliwości <xref:System.Net.Mail.SmtpClient> wysyłania wiadomości e-mail asynchronicznie i wysyłania poczty z uwierzytelnianiem. Zapewnia również niektóre funkcje użytkownika końcowego, takie jak tryb testowy, zastępowanie tokenów, szablony plików i ścieżka upuszczania testu.  
  
 W poniższej tabeli `SendMail` przedstawiono argumenty działania.  
  
|Nazwa|Typ|Opis|  
|-|-|-|  
|Host|Ciąg|Adres hosta serwera SMTP.|  
|Port|Ciąg|Port usługi SMTP w hoście.|  
|Enablessl|bool|Określa, <xref:System.Net.Mail.SmtpClient> czy do szyfrowania połączenia używa warstwy SSL (Secure Sockets Layer).|  
|UserName|Ciąg|Nazwa użytkownika, aby skonfigurować poświadczenia do <xref:System.Net.Mail.SmtpClient.Credentials%2A> uwierzytelniania właściwości nadawcy.|  
|Hasło|Ciąg|Hasło do konfigurowania poświadczeń <xref:System.Net.Mail.SmtpClient.Credentials%2A> w celu uwierzytelnienia właściwości nadawcy.|  
|Podmiot|<xref:System.Activities.InArgument%601>\<> ciągu|Temat wiadomości.|  
|Treść|<xref:System.Activities.InArgument%601>\<> ciągu|Treść wiadomości.|  
|Załączniki|<xref:System.Activities.InArgument%601>\<> ciągu|Zbieranie załączników używane do przechowywania danych dołączonych do tej wiadomości e-mail.|  
|Z|<xref:System.Net.Mail.MailAddress>|Z adresu dla tej wiadomości e-mail.|  
|Do|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|Kolekcja adresów zawierająca adresatów tej wiadomości e-mail.|  
|CC|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|Zbieranie adresów, które zawiera adresatów kopii węgla (CC) dla tej wiadomości e-mail.|  
|Udw|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|Kolekcja adresów zawierająca adresatów blind carbon copy (BCC) dla tej wiadomości e-mail.|  
|Tokeny|<xref:System.Activities.InArgument%601><ciągiem IDictionary,\<>> ciągu|Tokeny do zastąpienia w organizmie. Ta funkcja umożliwia użytkownikom określić niektóre wartości w treści, niż można zastąpić później tokeny dostarczone przy użyciu tej właściwości.|  
|Ścieżka bodytemplatefilepath|Ciąg|Ścieżka szablonu dla treści. Działanie `SendMail` kopiuje zawartość tego pliku do jego właściwości treści.<br /><br /> Szablon może zawierać tokeny, które są zastępowane przez zawartość właściwości tokens.|  
|TestMailTo (Poczta testowa)|<xref:System.Net.Mail.MailAddress>|Gdy ta właściwość jest ustawiona, wszystkie wiadomości e-mail są wysyłane na adres określony w niej.<br /><br /> Ta właściwość jest przeznaczona do użycia podczas testowania przepływów pracy. Na przykład, jeśli chcesz się upewnić, że wszystkie wiadomości e-mail są wysyłane bez wysyłania ich do rzeczywistych adresatów.|  
|Ścieżka testowa|Ciąg|Po ustawieniu tej właściwości wszystkie wiadomości e-mail są również zapisywane w określonym pliku.<br /><br /> Ta właściwość jest przeznaczona do użycia podczas testowania lub debugowania przepływów pracy, aby upewnić się, że format i zawartość wychodzących wiadomości e-mail jest odpowiednia.|  
  
## <a name="solution-contents"></a>Zawartość rozwiązania  
 Rozwiązanie zawiera dwa projekty.  
  
|Project|Opis|Ważne pliki|  
|-------------|-----------------|---------------------|  
|Sendmail|Aktywność SendMail|1. SendMail.cs: realizacja głównego działania<br />2. SendMailDesigner.xaml i SendMailDesigner.xaml.cs: projektant dla działania SendMail<br />3. MailTemplateBody.htm: szablon dla wiadomości e-mail, które mają być wysyłane.|  
|SendMailTestClient (SendMailTestClient)|Klienta, aby przetestować działanie SendMail.  Ten projekt pokazuje dwa sposoby wywoływania działania SendMail: deklaratywnie i programowo.|1. Sequence1.xaml: przepływ pracy, który wywołuje działanie SendMail.<br />2. Program.cs: wywołuje Sequence1, a także tworzy przepływ pracy programowo, który używa SendMail.|  
  
## <a name="further-configuration-of-the-sendmail-activity"></a>Dalsza konfiguracja działania SendMail  
 Chociaż nie pokazano w przykładzie, użytkownicy mogą wykonywać dodawanie konfiguracji działania SendMail. Następne trzy sekcje pokazują, jak to się robi.  
  
### <a name="sending-an-email-using-tokens-specified-in-the-body"></a>Wysyłanie wiadomości e-mail przy użyciu tokenów określonych w treści  
 Ten fragment kodu pokazuje, jak można wysyłać wiadomości e-mail z tokenami w treści. Zwróć uwagę, jak tokeny są dostarczane w właściwości treści. Wartości dla tych tokenów są dostarczane do właściwości tokens.  
  
```csharp  
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
 Ten fragment kodu pokazuje, jak wysłać wiadomość e-mail przy użyciu tokenów szablonu w treści. Należy zauważyć, `BodyTemplateFilePath` że podczas ustawiania właściwości nie musimy podawać wartość body właściwości (zawartość pliku szablonu zostaną skopiowane do treści).  
  
```csharp  
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
  
### <a name="sending-mails-in-testing-mode"></a>Wysyłanie wiadomości e-mail w trybie testowym  
 Ten fragment kodu pokazuje, jak ustawić dwie właściwości testowania: przez ustawienie `TestMailTo` `john.doe@contoso.con` wszystkich wiadomości będą wysyłane do (bez względu na wartości Do, CC, UDW). Przez ustawienie TestDropPath wszystkie wychodzące wiadomości e-mail będą również rejestrowane w podanej ścieżce. Te właściwości można ustawić niezależnie (nie są one powiązane).  
  
```csharp  
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
  
 Aby uzyskać więcej informacji na temat konfigurowania serwera SMTP, zobacz następujące łącza.  
  
- [Konfigurowanie usługi SMTP (IIS 6.0)](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc784968(v=ws.10))  
  
- [IIS 7.0: Konfigurowanie poczty e-mail SMTP](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc772058(v=ws.10))  
  
- [Jak zainstalować usługę SMTP](https://docs.microsoft.com/previous-versions/tn-archive/aa997480(v=exchg.65))  
  
 Emulatory SMTP dostarczone przez osoby trzecie są dostępne do pobrania.  
  
##### <a name="to-run-this-sample"></a>Aby uruchomić ten przykład  
  
1. Za pomocą programu Visual Studio 2010 otwórz plik rozwiązania SendMail.sln.  
  
2. Upewnij się, że masz dostęp do prawidłowego serwera SMTP. Zapoznaj się z instrukcjami konfiguracji.  
  
3. Skonfiguruj program z adresem serwera oraz adresami e-mail od i do.  
  
     Aby poprawnie uruchomić ten przykład, może być konieczne skonfigurowanie wartości adresów e-mail od i do oraz adresu serwera SMTP w Program.cs i sequence.xaml. Należy zmienić adres w obu lokalizacjach, ponieważ program wysyła pocztę na dwa różne sposoby  
  
4. Aby utworzyć rozwiązanie, naciśnij klawisze CTRL+SHIFT+B.  
  
5. Aby uruchomić rozwiązanie, naciśnij klawisze CTRL+F5.  
  
> [!IMPORTANT]
> Próbki mogą być już zainstalowane na komputerze. Przed kontynuowaniem sprawdź następujący (domyślny) katalog.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\SendMail`
