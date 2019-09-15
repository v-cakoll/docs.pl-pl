---
title: Niestandardowe działanie SendMail
ms.date: 03/30/2017
ms.assetid: 947a9ae6-379c-43a3-9cd5-87f573a5739f
ms.openlocfilehash: 5797620c4938d7dcffb1f506b682141336b21eab
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2019
ms.locfileid: "70988983"
---
# <a name="sendmail-custom-activity"></a><span data-ttu-id="bb21b-102">Niestandardowe działanie SendMail</span><span class="sxs-lookup"><span data-stu-id="bb21b-102">SendMail Custom Activity</span></span>
<span data-ttu-id="bb21b-103">Ten przykład pokazuje, jak utworzyć niestandardowe działanie, które wynika z <xref:System.Activities.AsyncCodeActivity> programu w celu wysłania wiadomości e-mail przy użyciu protokołu SMTP do użycia w aplikacji przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="bb21b-103">This sample demonstrates how to create a custom activity that derives from <xref:System.Activities.AsyncCodeActivity> to send mail using SMTP for use within a workflow application.</span></span> <span data-ttu-id="bb21b-104">Działanie niestandardowe umożliwia wysyłanie wiadomości e-mail asynchronicznie i wysyłanie wiadomości z uwierzytelnianiem przy użyciu funkcji programu <xref:System.Net.Mail.SmtpClient> .</span><span class="sxs-lookup"><span data-stu-id="bb21b-104">The custom activity uses the capabilities of <xref:System.Net.Mail.SmtpClient> to send email asynchronously and to send mail with authentication.</span></span> <span data-ttu-id="bb21b-105">Zapewnia również pewne funkcje użytkownika końcowego, takie jak tryb testu, Zastępowanie tokenu, szablony plików i ścieżka do usuwania testów.</span><span class="sxs-lookup"><span data-stu-id="bb21b-105">It also provides some end-user features like test mode, token replacement, file templates, and test drop path.</span></span>  
  
 <span data-ttu-id="bb21b-106">Poniższa tabela zawiera szczegółowe informacje o argumentach `SendMail` działania.</span><span class="sxs-lookup"><span data-stu-id="bb21b-106">The following table details the arguments for the `SendMail` activity.</span></span>  
  
|<span data-ttu-id="bb21b-107">Nazwa</span><span class="sxs-lookup"><span data-stu-id="bb21b-107">Name</span></span>|<span data-ttu-id="bb21b-108">Typ</span><span class="sxs-lookup"><span data-stu-id="bb21b-108">Type</span></span>|<span data-ttu-id="bb21b-109">Opis</span><span class="sxs-lookup"><span data-stu-id="bb21b-109">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="bb21b-110">Host</span><span class="sxs-lookup"><span data-stu-id="bb21b-110">Host</span></span>|<span data-ttu-id="bb21b-111">String</span><span class="sxs-lookup"><span data-stu-id="bb21b-111">String</span></span>|<span data-ttu-id="bb21b-112">Adres hosta serwera SMTP.</span><span class="sxs-lookup"><span data-stu-id="bb21b-112">Address of the SMTP server host.</span></span>|  
|<span data-ttu-id="bb21b-113">Port</span><span class="sxs-lookup"><span data-stu-id="bb21b-113">Port</span></span>|<span data-ttu-id="bb21b-114">String</span><span class="sxs-lookup"><span data-stu-id="bb21b-114">String</span></span>|<span data-ttu-id="bb21b-115">Port usługi SMTP na hoście.</span><span class="sxs-lookup"><span data-stu-id="bb21b-115">Port of the SMTP service in the host.</span></span>|  
|<span data-ttu-id="bb21b-116">EnableSsl</span><span class="sxs-lookup"><span data-stu-id="bb21b-116">EnableSsl</span></span>|<span data-ttu-id="bb21b-117">bool</span><span class="sxs-lookup"><span data-stu-id="bb21b-117">bool</span></span>|<span data-ttu-id="bb21b-118">Określa, <xref:System.Net.Mail.SmtpClient> czy program używa SSL (SSL) do szyfrowania połączenia.</span><span class="sxs-lookup"><span data-stu-id="bb21b-118">Specifies whether the <xref:System.Net.Mail.SmtpClient> uses Secure Sockets Layer (SSL) to encrypt the connection.</span></span>|  
|<span data-ttu-id="bb21b-119">UserName</span><span class="sxs-lookup"><span data-stu-id="bb21b-119">UserName</span></span>|<span data-ttu-id="bb21b-120">String</span><span class="sxs-lookup"><span data-stu-id="bb21b-120">String</span></span>|<span data-ttu-id="bb21b-121">Nazwa użytkownika, aby skonfigurować poświadczenia w celu uwierzytelnienia <xref:System.Net.Mail.SmtpClient.Credentials%2A> właściwości nadawcy.</span><span class="sxs-lookup"><span data-stu-id="bb21b-121">Username to set up the credentials to authenticate the sender <xref:System.Net.Mail.SmtpClient.Credentials%2A> property.</span></span>|  
|<span data-ttu-id="bb21b-122">Hasło</span><span class="sxs-lookup"><span data-stu-id="bb21b-122">Password</span></span>|<span data-ttu-id="bb21b-123">String</span><span class="sxs-lookup"><span data-stu-id="bb21b-123">String</span></span>|<span data-ttu-id="bb21b-124">Hasło w celu skonfigurowania poświadczeń w celu uwierzytelnienia <xref:System.Net.Mail.SmtpClient.Credentials%2A> właściwości nadawcy.</span><span class="sxs-lookup"><span data-stu-id="bb21b-124">Password to set up the credentials to authenticate the sender <xref:System.Net.Mail.SmtpClient.Credentials%2A> property.</span></span>|  
|<span data-ttu-id="bb21b-125">Subject</span><span class="sxs-lookup"><span data-stu-id="bb21b-125">Subject</span></span>|<span data-ttu-id="bb21b-126"><xref:System.Activities.InArgument%601>\<ciąg ></span><span class="sxs-lookup"><span data-stu-id="bb21b-126"><xref:System.Activities.InArgument%601>\<string></span></span>|<span data-ttu-id="bb21b-127">Temat wiadomości.</span><span class="sxs-lookup"><span data-stu-id="bb21b-127">Subject of the message.</span></span>|  
|<span data-ttu-id="bb21b-128">Treść</span><span class="sxs-lookup"><span data-stu-id="bb21b-128">Body</span></span>|<span data-ttu-id="bb21b-129"><xref:System.Activities.InArgument%601>\<ciąg ></span><span class="sxs-lookup"><span data-stu-id="bb21b-129"><xref:System.Activities.InArgument%601>\<string></span></span>|<span data-ttu-id="bb21b-130">Treść wiadomości.</span><span class="sxs-lookup"><span data-stu-id="bb21b-130">Body of the message.</span></span>|  
|<span data-ttu-id="bb21b-131">Załączniki</span><span class="sxs-lookup"><span data-stu-id="bb21b-131">Attachments</span></span>|<span data-ttu-id="bb21b-132"><xref:System.Activities.InArgument%601>\<ciąg ></span><span class="sxs-lookup"><span data-stu-id="bb21b-132"><xref:System.Activities.InArgument%601>\<string></span></span>|<span data-ttu-id="bb21b-133">Kolekcja załączników służąca do przechowywania danych dołączonych do tej wiadomości e-mail.</span><span class="sxs-lookup"><span data-stu-id="bb21b-133">Attachment collection used to store data attached to this email message.</span></span>|  
|<span data-ttu-id="bb21b-134">Z</span><span class="sxs-lookup"><span data-stu-id="bb21b-134">From</span></span>|<xref:System.Net.Mail.MailAddress>|<span data-ttu-id="bb21b-135">Adres od dla tej wiadomości e-mail.</span><span class="sxs-lookup"><span data-stu-id="bb21b-135">From address for this email message.</span></span>|  
|<span data-ttu-id="bb21b-136">Zadanie</span><span class="sxs-lookup"><span data-stu-id="bb21b-136">To</span></span>|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|<span data-ttu-id="bb21b-137">Kolekcja adresów zawierająca adresatów tej wiadomości e-mail.</span><span class="sxs-lookup"><span data-stu-id="bb21b-137">Address collection that contains the recipients of this email message.</span></span>|  
|<span data-ttu-id="bb21b-138">CC</span><span class="sxs-lookup"><span data-stu-id="bb21b-138">CC</span></span>|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|<span data-ttu-id="bb21b-139">Kolekcja adresów zawierająca adresatów kopii wiadomości e-mail.</span><span class="sxs-lookup"><span data-stu-id="bb21b-139">Address collection that contains the carbon copy (CC) recipients for this email message.</span></span>|  
|<span data-ttu-id="bb21b-140">BCC</span><span class="sxs-lookup"><span data-stu-id="bb21b-140">BCC</span></span>|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|<span data-ttu-id="bb21b-141">Kolekcja adresów zawierająca adresatów (UDW) dla tej wiadomości e-mail.</span><span class="sxs-lookup"><span data-stu-id="bb21b-141">Address collection that contains the blind carbon copy (BCC) recipients for this email message.</span></span>|  
|<span data-ttu-id="bb21b-142">Tokeny</span><span class="sxs-lookup"><span data-stu-id="bb21b-142">Tokens</span></span>|<span data-ttu-id="bb21b-143"><xref:System.Activities.InArgument%601>< ciąg\<IDictionary > ></span><span class="sxs-lookup"><span data-stu-id="bb21b-143"><xref:System.Activities.InArgument%601><IDictionary\<string, string>></span></span>|<span data-ttu-id="bb21b-144">Tokeny do zamiany w treści.</span><span class="sxs-lookup"><span data-stu-id="bb21b-144">Tokens to replace in the body.</span></span> <span data-ttu-id="bb21b-145">Ta funkcja umożliwia użytkownikom Określanie niektórych wartości w treści, niż można zastąpić je później za pomocą tokenów dostarczonych przy użyciu tej właściwości.</span><span class="sxs-lookup"><span data-stu-id="bb21b-145">This feature allows users to specify some values in the body than can be replaced later by the tokens provided using this property.</span></span>|  
|<span data-ttu-id="bb21b-146">BodyTemplateFilePath</span><span class="sxs-lookup"><span data-stu-id="bb21b-146">BodyTemplateFilePath</span></span>|<span data-ttu-id="bb21b-147">String</span><span class="sxs-lookup"><span data-stu-id="bb21b-147">String</span></span>|<span data-ttu-id="bb21b-148">Ścieżka szablonu dla treści.</span><span class="sxs-lookup"><span data-stu-id="bb21b-148">Path of a template for the body.</span></span> <span data-ttu-id="bb21b-149">`SendMail` Działanie kopiuje zawartość tego pliku do jego właściwości Body.</span><span class="sxs-lookup"><span data-stu-id="bb21b-149">The `SendMail` activity copies the contents of this file to its body property.</span></span><br /><br /> <span data-ttu-id="bb21b-150">Szablon może zawierać tokeny, które są zastępowane przez zawartość właściwości tokens.</span><span class="sxs-lookup"><span data-stu-id="bb21b-150">The template can contain tokens that are replaced by the contents of the tokens property.</span></span>|  
|<span data-ttu-id="bb21b-151">TestMailTo</span><span class="sxs-lookup"><span data-stu-id="bb21b-151">TestMailTo</span></span>|<xref:System.Net.Mail.MailAddress>|<span data-ttu-id="bb21b-152">Gdy ta właściwość jest ustawiona, wszystkie wiadomości e-mail są wysyłane na adres określony w tym polu.</span><span class="sxs-lookup"><span data-stu-id="bb21b-152">When this property is set, all emails are sent to the address specified in it.</span></span><br /><br /> <span data-ttu-id="bb21b-153">Ta właściwość jest przeznaczona do użycia podczas testowania przepływów pracy.</span><span class="sxs-lookup"><span data-stu-id="bb21b-153">This property is intended to be used when testing workflows.</span></span> <span data-ttu-id="bb21b-154">Na przykład jeśli chcesz upewnić się, że wszystkie wiadomości e-mail są wysyłane bez wysyłania ich do rzeczywistych adresatów.</span><span class="sxs-lookup"><span data-stu-id="bb21b-154">For example, when you want to make sure that all emails are sent without sending them to the actual recipients.</span></span>|  
|<span data-ttu-id="bb21b-155">TestDropPath</span><span class="sxs-lookup"><span data-stu-id="bb21b-155">TestDropPath</span></span>|<span data-ttu-id="bb21b-156">String</span><span class="sxs-lookup"><span data-stu-id="bb21b-156">String</span></span>|<span data-ttu-id="bb21b-157">Gdy ta właściwość jest ustawiona, wszystkie wiadomości e-mail są również zapisywane w określonym pliku.</span><span class="sxs-lookup"><span data-stu-id="bb21b-157">When this property is set, all emails are also saved in the specified file.</span></span><br /><br /> <span data-ttu-id="bb21b-158">Ta właściwość jest przeznaczona do użycia podczas testowania lub debugowania przepływów pracy, aby upewnić się, że format i zawartość wychodzących wiadomości e-mail są odpowiednie.</span><span class="sxs-lookup"><span data-stu-id="bb21b-158">This property is intended to be used when you are testing or debugging workflows, to make sure that the format and contents of the outgoing emails is appropriate.</span></span>|  
  
## <a name="solution-contents"></a><span data-ttu-id="bb21b-159">Zawartość rozwiązania</span><span class="sxs-lookup"><span data-stu-id="bb21b-159">Solution Contents</span></span>  
 <span data-ttu-id="bb21b-160">Rozwiązanie zawiera dwa projekty.</span><span class="sxs-lookup"><span data-stu-id="bb21b-160">The solution contains two projects.</span></span>  
  
|<span data-ttu-id="bb21b-161">Projekt</span><span class="sxs-lookup"><span data-stu-id="bb21b-161">Project</span></span>|<span data-ttu-id="bb21b-162">Opis</span><span class="sxs-lookup"><span data-stu-id="bb21b-162">Description</span></span>|<span data-ttu-id="bb21b-163">Ważne pliki</span><span class="sxs-lookup"><span data-stu-id="bb21b-163">Important Files</span></span>|  
|-------------|-----------------|---------------------|  
|<span data-ttu-id="bb21b-164">SendMail</span><span class="sxs-lookup"><span data-stu-id="bb21b-164">SendMail</span></span>|<span data-ttu-id="bb21b-165">Działanie SendMail</span><span class="sxs-lookup"><span data-stu-id="bb21b-165">The SendMail activity</span></span>|<span data-ttu-id="bb21b-166">1.  SendMail.cs: implementacja głównego działania</span><span class="sxs-lookup"><span data-stu-id="bb21b-166">1.  SendMail.cs: implementation for the main activity</span></span><br /><span data-ttu-id="bb21b-167">2.  SendMailDesigner. XAML i SendMailDesigner.xaml.cs: Projektant dla działania SendMail</span><span class="sxs-lookup"><span data-stu-id="bb21b-167">2.  SendMailDesigner.xaml and SendMailDesigner.xaml.cs: designer for the SendMail activity</span></span><br /><span data-ttu-id="bb21b-168">3.  MailTemplateBody. htm: szablon wiadomości e-mail do wysłania.</span><span class="sxs-lookup"><span data-stu-id="bb21b-168">3.  MailTemplateBody.htm: template for the email to be sent out.</span></span>|  
|<span data-ttu-id="bb21b-169">SendMailTestClient</span><span class="sxs-lookup"><span data-stu-id="bb21b-169">SendMailTestClient</span></span>|<span data-ttu-id="bb21b-170">Klient do testowania działania SendMail.</span><span class="sxs-lookup"><span data-stu-id="bb21b-170">Client to test the SendMail activity.</span></span>  <span data-ttu-id="bb21b-171">Ten projekt przedstawia dwa sposoby wywoływania działania SendMail: deklaratywnie i programistyczne.</span><span class="sxs-lookup"><span data-stu-id="bb21b-171">This project demonstrates two ways of invoking the SendMail activity: declaratively, and programmatically.</span></span>|<span data-ttu-id="bb21b-172">1.  Sequence1. XAML: przepływ pracy, który wywołuje działanie SendMail.</span><span class="sxs-lookup"><span data-stu-id="bb21b-172">1.  Sequence1.xaml: workflow that invokes the SendMail activity.</span></span><br /><span data-ttu-id="bb21b-173">2.  Program.cs: wywołuje Sequence1, a także programowo tworzy przepływ pracy, który używa SendMail.</span><span class="sxs-lookup"><span data-stu-id="bb21b-173">2.  Program.cs: invokes Sequence1 and also creates a workflow programmatically that uses SendMail.</span></span>|  
  
## <a name="further-configuration-of-the-sendmail-activity"></a><span data-ttu-id="bb21b-174">Dodatkowa konfiguracja działania SendMail</span><span class="sxs-lookup"><span data-stu-id="bb21b-174">Further configuration of the SendMail activity</span></span>  
 <span data-ttu-id="bb21b-175">Chociaż nie są wyświetlane w przykładzie, użytkownicy mogą wykonać dodatkowe czynności konfiguracyjne działania SendMail.</span><span class="sxs-lookup"><span data-stu-id="bb21b-175">Although not shown in the sample, users can perform addition configuration of the SendMail activity.</span></span> <span data-ttu-id="bb21b-176">W następnych trzech sekcjach pokazano, jak to zrobić.</span><span class="sxs-lookup"><span data-stu-id="bb21b-176">The next three sections demonstrate how this is done.</span></span>  
  
### <a name="sending-an-email-using-tokens-specified-in-the-body"></a><span data-ttu-id="bb21b-177">Wysyłanie wiadomości e-mail przy użyciu tokenów określonych w treści</span><span class="sxs-lookup"><span data-stu-id="bb21b-177">Sending an email using tokens specified in the body</span></span>  
 <span data-ttu-id="bb21b-178">W tym fragmencie kodu pokazano, jak można wysyłać wiadomości e-mail z tokenami w treści.</span><span class="sxs-lookup"><span data-stu-id="bb21b-178">This code snippet demonstrates how you can send email with tokens in the body.</span></span> <span data-ttu-id="bb21b-179">Zwróć uwagę na to, jak tokeny są udostępniane we właściwości treść.</span><span class="sxs-lookup"><span data-stu-id="bb21b-179">Notice how the tokens are provided in the body property.</span></span> <span data-ttu-id="bb21b-180">Wartości tych tokenów są udostępniane właściwości tokens.</span><span class="sxs-lookup"><span data-stu-id="bb21b-180">Values for those tokens are provided to the tokens property.</span></span>  
  
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
  
### <a name="sending-an-email-using-a-template"></a><span data-ttu-id="bb21b-181">Wysyłanie wiadomości e-mail przy użyciu szablonu</span><span class="sxs-lookup"><span data-stu-id="bb21b-181">Sending an email using a template</span></span>  
 <span data-ttu-id="bb21b-182">W tym fragmencie kodu pokazano, jak wysłać wiadomość e-mail przy użyciu tokenów szablonu w treści.</span><span class="sxs-lookup"><span data-stu-id="bb21b-182">This snippet shows how to send an email using a template tokens in the body.</span></span> <span data-ttu-id="bb21b-183">Należy zauważyć, że podczas `BodyTemplateFilePath` ustawiania właściwości nie musimy podawać wartości właściwości Body (zawartość pliku szablonu zostanie skopiowana do treści).</span><span class="sxs-lookup"><span data-stu-id="bb21b-183">Notice that when setting the `BodyTemplateFilePath` property we don’t need to provide the value for Body property (the contents of the template file will be copied to the body).</span></span>  
  
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
  
### <a name="sending-mails-in-testing-mode"></a><span data-ttu-id="bb21b-184">Wysyłanie wiadomości w trybie testowania</span><span class="sxs-lookup"><span data-stu-id="bb21b-184">Sending Mails in Testing Mode</span></span>  
 <span data-ttu-id="bb21b-185">W tym fragmencie kodu pokazano, jak ustawić dwie właściwości testowania: według ustawienia `TestMailTo` dla wszystkich wiadomości będą wysyłane do `john.doe@contoso.con` (bez względu na wartości do, DW, UDW).</span><span class="sxs-lookup"><span data-stu-id="bb21b-185">This code snippet shows how to set the two testing properties: by setting `TestMailTo` to all messages will be sent to `john.doe@contoso.con` (without regard of the values of To, Cc, Bcc).</span></span> <span data-ttu-id="bb21b-186">Ustawienie TestDropPath wszystkie wychodzące wiadomości e-mail zostanie również zarejestrowane w podanej ścieżce.</span><span class="sxs-lookup"><span data-stu-id="bb21b-186">By setting TestDropPath all outgoing emails will be also recorded in the provided path.</span></span> <span data-ttu-id="bb21b-187">Te właściwości można ustawiać niezależnie (nie są powiązane).</span><span class="sxs-lookup"><span data-stu-id="bb21b-187">These properties can be set independently (they are not related).</span></span>  
  
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
  
## <a name="set-up-instructions"></a><span data-ttu-id="bb21b-188">Instrukcje dotyczące konfiguracji</span><span class="sxs-lookup"><span data-stu-id="bb21b-188">Set-Up Instructions</span></span>  
 <span data-ttu-id="bb21b-189">Dla tego przykładu wymagany jest dostęp do serwera SMTP.</span><span class="sxs-lookup"><span data-stu-id="bb21b-189">Access to a SMTP server is required for this sample.</span></span>  
  
 <span data-ttu-id="bb21b-190">Aby uzyskać więcej informacji na temat konfigurowania serwera SMTP, zobacz poniższe linki.</span><span class="sxs-lookup"><span data-stu-id="bb21b-190">For more information about setting up a SMTP server, see the following links.</span></span>  
  
- [<span data-ttu-id="bb21b-191">Microsoft Technet</span><span class="sxs-lookup"><span data-stu-id="bb21b-191">Microsoft Technet</span></span>](https://go.microsoft.com/fwlink/?LinkId=166060)  
  
- [<span data-ttu-id="bb21b-192">Konfigurowanie usługi SMTP (IIS 6,0)</span><span class="sxs-lookup"><span data-stu-id="bb21b-192">Configuring the SMTP Service (IIS 6.0)</span></span>](https://go.microsoft.com/fwlink/?LinkId=150456)  
  
- [<span data-ttu-id="bb21b-193">IIS 7.0: Konfigurowanie poczty E-Mail SMTP</span><span class="sxs-lookup"><span data-stu-id="bb21b-193">IIS 7.0: Configure SMTP E-Mail</span></span>](https://go.microsoft.com/fwlink/?LinkId=150457)  
  
- [<span data-ttu-id="bb21b-194">Jak zainstalować usługę SMTP</span><span class="sxs-lookup"><span data-stu-id="bb21b-194">How to Install the SMTP Service</span></span>](https://go.microsoft.com/fwlink/?LinkId=150458)  
  
 <span data-ttu-id="bb21b-195">Emulatory SMTP udostępniane przez inne firmy są dostępne do pobrania.</span><span class="sxs-lookup"><span data-stu-id="bb21b-195">SMTP emulators provided by third parties are available for download.</span></span>  
  
##### <a name="to-run-this-sample"></a><span data-ttu-id="bb21b-196">Aby uruchomić ten przykład</span><span class="sxs-lookup"><span data-stu-id="bb21b-196">To run this sample</span></span>  
  
1. <span data-ttu-id="bb21b-197">Za pomocą programu Visual Studio 2010 Otwórz plik rozwiązania SendMail. sln.</span><span class="sxs-lookup"><span data-stu-id="bb21b-197">Using Visual Studio 2010, open the SendMail.sln solution file.</span></span>  
  
2. <span data-ttu-id="bb21b-198">Upewnij się, że masz dostęp do prawidłowego serwera SMTP.</span><span class="sxs-lookup"><span data-stu-id="bb21b-198">Ensure that you have access to a valid SMTP server.</span></span> <span data-ttu-id="bb21b-199">Zapoznaj się z instrukcjami konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="bb21b-199">See the set-up instructions.</span></span>  
  
3. <span data-ttu-id="bb21b-200">Skonfiguruj program przy użyciu adresu serwera oraz od i do adresów e-mail.</span><span class="sxs-lookup"><span data-stu-id="bb21b-200">Configure the program with your server address, and From and To email addresses.</span></span>  
  
     <span data-ttu-id="bb21b-201">Aby prawidłowo uruchomić ten przykład, może być konieczne skonfigurowanie wartości z i na adresy e-mail oraz adres serwera SMTP w Program.cs i w sekwencji. XAML.</span><span class="sxs-lookup"><span data-stu-id="bb21b-201">To correctly run this sample, you may need to configure the value of From and To email addresses and the address of the SMTP server in  Program.cs and in Sequence.xaml.</span></span> <span data-ttu-id="bb21b-202">Należy zmienić adres w obu lokalizacjach, ponieważ program wysyła pocztę e-mail na dwa różne sposoby</span><span class="sxs-lookup"><span data-stu-id="bb21b-202">You will need to change the address in both locations since the program sends mail in two different ways</span></span>  
  
4. <span data-ttu-id="bb21b-203">Aby skompilować rozwiązanie, naciśnij klawisze CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="bb21b-203">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
5. <span data-ttu-id="bb21b-204">Aby uruchomić rozwiązanie, naciśnij klawisze CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="bb21b-204">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="bb21b-205">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="bb21b-205">The samples may already be installed on your machine.</span></span> <span data-ttu-id="bb21b-206">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="bb21b-206">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="bb21b-207">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="bb21b-207">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="bb21b-208">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="bb21b-208">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\SendMail`
