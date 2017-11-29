---
title: "Działania niestandardowe SendMail"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 947a9ae6-379c-43a3-9cd5-87f573a5739f
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 0e4501a4d1e9524a3631b29dba3cfee58bea5129
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="sendmail-custom-activity"></a>Działania niestandardowe SendMail
Ten przykład przedstawia sposób tworzenia działań niestandardowych, która jest pochodną <xref:System.Activities.AsyncCodeActivity> do wysyłania wiadomości e-mail do użycia w aplikacji przepływu pracy za pomocą protokołu SMTP. To niestandardowe działanie korzysta z funkcji programu <xref:System.Net.Mail.SmtpClient> do asynchronicznego wysyłania wiadomości e-mail i do wysyłania wiadomości e-mail z uwierzytelnianiem. Umożliwia także niektóre funkcje przez użytkownika końcowego, takie jak przetestować tryb, zastępujący tokenu, Szablony plików i test ścieżkę.  
  
 W poniższej tabeli przedstawiono argumenty `SendMail` działania.  
  
|Nazwa|Typ|Opis|  
|-|-|-|  
|Host|String|Adres hosta serwera SMTP.|  
|Port|String|Port usługi SMTP na hoście.|  
|enableSsl|bool|Określa, czy <xref:System.Net.Mail.SmtpClient> używa protokołu Secure Sockets Layer (SSL) do szyfrowania połączenia.|  
|UserName|String|Nazwa użytkownika, aby ustawić poświadczenia, aby uwierzytelnić nadawcę <xref:System.Net.Mail.SmtpClient.Credentials%2A> właściwości.|  
|Hasło|String|Hasło, aby ustawić poświadczenia, aby uwierzytelnić nadawcę <xref:System.Net.Mail.SmtpClient.Credentials%2A> właściwości.|  
|Temat|<xref:System.Activities.InArgument%601>\<ciąg >|Temat wiadomości.|  
|Treści|<xref:System.Activities.InArgument%601>\<ciąg >|Treść wiadomości.|  
|Załączniki|<xref:System.Activities.InArgument%601>\<ciąg >|Kolekcja załącznika używany do przechowywania danych dołączony do tej wiadomości e-mail.|  
|Z|<xref:System.Net.Mail.MailAddress>|Adres początkowy dla tej wiadomości e-mail.|  
|Do|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|Adres kolekcji, która zawiera adresatów wiadomości e-mail.|  
|DW|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|Adres kolekcji zawierającej Adresaci kopii (DW) dla tej wiadomości e-mail.|  
|UDW|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|Adres kolekcji, która zawiera adresatów kopii (UDW) dla tej wiadomości e-mail.|  
|Tokeny|<xref:System.Activities.InArgument%601>< IDictionary\<ciąg, ciąg >>|Tokeny zastąpić w treści. Ta funkcja umożliwia użytkownikom określanie niektórych wartości w treści, niż można później zastąpić tokeny realizowane przy użyciu tej właściwości.|  
|BodyTemplateFilePath|String|Ścieżka szablonu dla treści. `SendMail` Działanie kopiuje zawartość tego pliku do jej treści właściwości.<br /><br /> Szablon może zawierać tokeny, które są zastępowane przez wartości właściwości tokenów.|  
|TestMailTo|<xref:System.Net.Mail.MailAddress>|Gdy ta właściwość jest ustawiona, wszystkie wiadomości e-mail są wysyłane na adres określony w nim.<br /><br /> Ta właściwość jest przeznaczona do użycia podczas badania przepływów pracy. Na przykład jeśli chcesz upewnić się, że wszystkie wiadomości e-mail są wysyłane bez wysyłania ich do adresatów, do rzeczywistych.|  
|TestDropPath|String|Gdy ta właściwość jest ustawiona, wszystkie wiadomości e-mail zostały także zapisane w określonym pliku.<br /><br /> Ta właściwość jest przeznaczona do użycia podczas testowania i debugowania przepływów pracy, aby upewnić się, że format i zawartość wychodzących wiadomości e-mail jest odpowiednia.|  
  
## <a name="solution-contents"></a>Zawartość rozwiązania  
 Rozwiązanie zawiera dwa projekty.  
  
|Project|Opis|Ważnych plików|  
|-------------|-----------------|---------------------|  
|SendMail|Działanie SendMail|1.  SendMail.cs: implementacja dla działania głównego<br />2.  SendMailDesigner.xaml i SendMailDesigner.xaml.cs: projektanta dla działania SendMail<br />3.  MailTemplateBody.htm: szablon wiadomości e-mail do wysłania.|  
|SendMailTestClient|Klient, aby przetestować działanie SendMail.  Ten projekt przedstawia dwa sposoby wywoływania działania SendMail: programowo i deklaratywnie.|1.  Sequence1.XAML: przepływ pracy, który wywołuje aktywność SendMail.<br />2.  Plik program.CS: wywołuje Sequence1, a także tworzy programowo używającej SendMail przepływ pracy.|  
  
## <a name="further-configuration-of-the-sendmail-activity"></a>Dalsza konfiguracja działania SendMail  
 Wprawdzie nie pokazano w przykładzie, użytkownicy mogą wykonywać konfiguracji dodanie SendMail działania. Trzech kolejnych sekcjach pokazują, jak to zrobić.  
  
### <a name="sending-an-email-using-tokens-specified-in-the-body"></a>Wysyłanie wiadomości e-mail przy użyciu tokenów określony w treści  
 Następujący fragment kodu pokazano, jak można wysłać wiadomości e-mail z tokenami w treści. Zwróć uwagę, jak tokenów znajdują się w treści właściwości. Wartości te tokeny są dostarczane do właściwości tokenów.  
  
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
 Następujący fragment kodu przedstawia sposób wysłania wiadomości e-mail przy użyciu tokenów szablonu w treści. Zwróć uwagę, że podczas ustawiania `BodyTemplateFilePath` właściwość nie należy podać wartość dla właściwości Body (treść pliku szablonu zostaną skopiowane do treści).  
  
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
  
### <a name="sending-mails-in-testing-mode"></a>Wysyłanie wiadomości w tryb testowania  
 Następujący fragment kodu przedstawiono sposób ustawiania dwie właściwości testowych: ustawiając `TestMailTo` na wszystkie komunikaty będą wysyłane do john.doe@contoso.con (bez względu wartości do, DW, UDW). Przez ustawienie TestDropPath wszystkich wychodzących wiadomości e-mail będą również rejestrowane w podana ścieżka. Te właściwości można skonfigurować niezależnie (nie jest ona powiązana).  
  
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
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Konfigurowanie serwera SMTP, zobacz następujące linki.  
  
-   [Microsoft Technet](http://go.microsoft.com/fwlink/?LinkId=166060)  
  
-   [Konfigurowanie usługi SMTP (IIS 6.0)](http://go.microsoft.com/fwlink/?LinkId=150456)  
  
-   [Usługi IIS 7.0: Konfigurowanie poczty E-Mail SMTP](http://go.microsoft.com/fwlink/?LinkId=150457)  
  
-   [Jak zainstalować usługi SMTP](http://go.microsoft.com/fwlink/?LinkId=150458)  
  
 Emulatory SMTP zapewnianych przez strony trzecie są dostępne do pobrania.  
  
##### <a name="to-run-this-sample"></a>Aby uruchomić ten przykład  
  
1.  Przy użyciu [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania SendMail.sln.  
  
2.  Upewnij się, że masz dostęp do prawidłowego serwera SMTP. Zobacz instrukcje dotyczące konfiguracji.  
  
3.  Skonfiguruj program przy użyciu adresu serwera i od i do adresów e-mail.  
  
     Aby prawidłowo uruchomić ten przykład, może być konieczne skonfigurowanie wartości od i do adresów e-mail i adres serwera SMTP w pliku Program.cs i Sequence.xaml. Musisz zmienić adres w obu lokalizacjach, ponieważ program wysyła wiadomości na dwa różne sposoby  
  
4.  Aby tworzyć rozwiązania, naciśnij kombinację klawiszy CTRL + SHIFT + B.  
  
5.  Aby uruchomić rozwiązanie, naciśnij klawisze CTRL + F5.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\SendMail`  
  
## <a name="see-also"></a>Zobacz też
