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
# <a name="sendmail-custom-activity"></a><span data-ttu-id="e4ae0-102">Niestandardowe działanie SendMail</span><span class="sxs-lookup"><span data-stu-id="e4ae0-102">SendMail Custom Activity</span></span>
<span data-ttu-id="e4ae0-103">W tym przykładzie pokazano, jak utworzyć <xref:System.Activities.AsyncCodeActivity> działanie niestandardowe, które pochodzi z wysyłania poczty przy użyciu protokołu SMTP do użycia w aplikacji przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="e4ae0-103">This sample demonstrates how to create a custom activity that derives from <xref:System.Activities.AsyncCodeActivity> to send mail using SMTP for use within a workflow application.</span></span> <span data-ttu-id="e4ae0-104">Działanie niestandardowe używa możliwości <xref:System.Net.Mail.SmtpClient> wysyłania wiadomości e-mail asynchronicznie i wysyłania poczty z uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="e4ae0-104">The custom activity uses the capabilities of <xref:System.Net.Mail.SmtpClient> to send email asynchronously and to send mail with authentication.</span></span> <span data-ttu-id="e4ae0-105">Zapewnia również niektóre funkcje użytkownika końcowego, takie jak tryb testowy, zastępowanie tokenów, szablony plików i ścieżka upuszczania testu.</span><span class="sxs-lookup"><span data-stu-id="e4ae0-105">It also provides some end-user features like test mode, token replacement, file templates, and test drop path.</span></span>  
  
 <span data-ttu-id="e4ae0-106">W poniższej tabeli `SendMail` przedstawiono argumenty działania.</span><span class="sxs-lookup"><span data-stu-id="e4ae0-106">The following table details the arguments for the `SendMail` activity.</span></span>  
  
|<span data-ttu-id="e4ae0-107">Nazwa</span><span class="sxs-lookup"><span data-stu-id="e4ae0-107">Name</span></span>|<span data-ttu-id="e4ae0-108">Typ</span><span class="sxs-lookup"><span data-stu-id="e4ae0-108">Type</span></span>|<span data-ttu-id="e4ae0-109">Opis</span><span class="sxs-lookup"><span data-stu-id="e4ae0-109">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="e4ae0-110">Host</span><span class="sxs-lookup"><span data-stu-id="e4ae0-110">Host</span></span>|<span data-ttu-id="e4ae0-111">Ciąg</span><span class="sxs-lookup"><span data-stu-id="e4ae0-111">String</span></span>|<span data-ttu-id="e4ae0-112">Adres hosta serwera SMTP.</span><span class="sxs-lookup"><span data-stu-id="e4ae0-112">Address of the SMTP server host.</span></span>|  
|<span data-ttu-id="e4ae0-113">Port</span><span class="sxs-lookup"><span data-stu-id="e4ae0-113">Port</span></span>|<span data-ttu-id="e4ae0-114">Ciąg</span><span class="sxs-lookup"><span data-stu-id="e4ae0-114">String</span></span>|<span data-ttu-id="e4ae0-115">Port usługi SMTP w hoście.</span><span class="sxs-lookup"><span data-stu-id="e4ae0-115">Port of the SMTP service in the host.</span></span>|  
|<span data-ttu-id="e4ae0-116">Enablessl</span><span class="sxs-lookup"><span data-stu-id="e4ae0-116">EnableSsl</span></span>|<span data-ttu-id="e4ae0-117">bool</span><span class="sxs-lookup"><span data-stu-id="e4ae0-117">bool</span></span>|<span data-ttu-id="e4ae0-118">Określa, <xref:System.Net.Mail.SmtpClient> czy do szyfrowania połączenia używa warstwy SSL (Secure Sockets Layer).</span><span class="sxs-lookup"><span data-stu-id="e4ae0-118">Specifies whether the <xref:System.Net.Mail.SmtpClient> uses Secure Sockets Layer (SSL) to encrypt the connection.</span></span>|  
|<span data-ttu-id="e4ae0-119">UserName</span><span class="sxs-lookup"><span data-stu-id="e4ae0-119">UserName</span></span>|<span data-ttu-id="e4ae0-120">Ciąg</span><span class="sxs-lookup"><span data-stu-id="e4ae0-120">String</span></span>|<span data-ttu-id="e4ae0-121">Nazwa użytkownika, aby skonfigurować poświadczenia do <xref:System.Net.Mail.SmtpClient.Credentials%2A> uwierzytelniania właściwości nadawcy.</span><span class="sxs-lookup"><span data-stu-id="e4ae0-121">Username to set up the credentials to authenticate the sender <xref:System.Net.Mail.SmtpClient.Credentials%2A> property.</span></span>|  
|<span data-ttu-id="e4ae0-122">Hasło</span><span class="sxs-lookup"><span data-stu-id="e4ae0-122">Password</span></span>|<span data-ttu-id="e4ae0-123">Ciąg</span><span class="sxs-lookup"><span data-stu-id="e4ae0-123">String</span></span>|<span data-ttu-id="e4ae0-124">Hasło do konfigurowania poświadczeń <xref:System.Net.Mail.SmtpClient.Credentials%2A> w celu uwierzytelnienia właściwości nadawcy.</span><span class="sxs-lookup"><span data-stu-id="e4ae0-124">Password to set up the credentials to authenticate the sender <xref:System.Net.Mail.SmtpClient.Credentials%2A> property.</span></span>|  
|<span data-ttu-id="e4ae0-125">Podmiot</span><span class="sxs-lookup"><span data-stu-id="e4ae0-125">Subject</span></span>|<span data-ttu-id="e4ae0-126"><xref:System.Activities.InArgument%601>\<> ciągu</span><span class="sxs-lookup"><span data-stu-id="e4ae0-126"><xref:System.Activities.InArgument%601>\<string></span></span>|<span data-ttu-id="e4ae0-127">Temat wiadomości.</span><span class="sxs-lookup"><span data-stu-id="e4ae0-127">Subject of the message.</span></span>|  
|<span data-ttu-id="e4ae0-128">Treść</span><span class="sxs-lookup"><span data-stu-id="e4ae0-128">Body</span></span>|<span data-ttu-id="e4ae0-129"><xref:System.Activities.InArgument%601>\<> ciągu</span><span class="sxs-lookup"><span data-stu-id="e4ae0-129"><xref:System.Activities.InArgument%601>\<string></span></span>|<span data-ttu-id="e4ae0-130">Treść wiadomości.</span><span class="sxs-lookup"><span data-stu-id="e4ae0-130">Body of the message.</span></span>|  
|<span data-ttu-id="e4ae0-131">Załączniki</span><span class="sxs-lookup"><span data-stu-id="e4ae0-131">Attachments</span></span>|<span data-ttu-id="e4ae0-132"><xref:System.Activities.InArgument%601>\<> ciągu</span><span class="sxs-lookup"><span data-stu-id="e4ae0-132"><xref:System.Activities.InArgument%601>\<string></span></span>|<span data-ttu-id="e4ae0-133">Zbieranie załączników używane do przechowywania danych dołączonych do tej wiadomości e-mail.</span><span class="sxs-lookup"><span data-stu-id="e4ae0-133">Attachment collection used to store data attached to this email message.</span></span>|  
|<span data-ttu-id="e4ae0-134">Z</span><span class="sxs-lookup"><span data-stu-id="e4ae0-134">From</span></span>|<xref:System.Net.Mail.MailAddress>|<span data-ttu-id="e4ae0-135">Z adresu dla tej wiadomości e-mail.</span><span class="sxs-lookup"><span data-stu-id="e4ae0-135">From address for this email message.</span></span>|  
|<span data-ttu-id="e4ae0-136">Do</span><span class="sxs-lookup"><span data-stu-id="e4ae0-136">To</span></span>|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|<span data-ttu-id="e4ae0-137">Kolekcja adresów zawierająca adresatów tej wiadomości e-mail.</span><span class="sxs-lookup"><span data-stu-id="e4ae0-137">Address collection that contains the recipients of this email message.</span></span>|  
|<span data-ttu-id="e4ae0-138">CC</span><span class="sxs-lookup"><span data-stu-id="e4ae0-138">CC</span></span>|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|<span data-ttu-id="e4ae0-139">Zbieranie adresów, które zawiera adresatów kopii węgla (CC) dla tej wiadomości e-mail.</span><span class="sxs-lookup"><span data-stu-id="e4ae0-139">Address collection that contains the carbon copy (CC) recipients for this email message.</span></span>|  
|<span data-ttu-id="e4ae0-140">Udw</span><span class="sxs-lookup"><span data-stu-id="e4ae0-140">BCC</span></span>|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|<span data-ttu-id="e4ae0-141">Kolekcja adresów zawierająca adresatów blind carbon copy (BCC) dla tej wiadomości e-mail.</span><span class="sxs-lookup"><span data-stu-id="e4ae0-141">Address collection that contains the blind carbon copy (BCC) recipients for this email message.</span></span>|  
|<span data-ttu-id="e4ae0-142">Tokeny</span><span class="sxs-lookup"><span data-stu-id="e4ae0-142">Tokens</span></span>|<span data-ttu-id="e4ae0-143"><xref:System.Activities.InArgument%601><ciągiem IDictionary,\<>> ciągu</span><span class="sxs-lookup"><span data-stu-id="e4ae0-143"><xref:System.Activities.InArgument%601><IDictionary\<string, string>></span></span>|<span data-ttu-id="e4ae0-144">Tokeny do zastąpienia w organizmie.</span><span class="sxs-lookup"><span data-stu-id="e4ae0-144">Tokens to replace in the body.</span></span> <span data-ttu-id="e4ae0-145">Ta funkcja umożliwia użytkownikom określić niektóre wartości w treści, niż można zastąpić później tokeny dostarczone przy użyciu tej właściwości.</span><span class="sxs-lookup"><span data-stu-id="e4ae0-145">This feature allows users to specify some values in the body than can be replaced later by the tokens provided using this property.</span></span>|  
|<span data-ttu-id="e4ae0-146">Ścieżka bodytemplatefilepath</span><span class="sxs-lookup"><span data-stu-id="e4ae0-146">BodyTemplateFilePath</span></span>|<span data-ttu-id="e4ae0-147">Ciąg</span><span class="sxs-lookup"><span data-stu-id="e4ae0-147">String</span></span>|<span data-ttu-id="e4ae0-148">Ścieżka szablonu dla treści.</span><span class="sxs-lookup"><span data-stu-id="e4ae0-148">Path of a template for the body.</span></span> <span data-ttu-id="e4ae0-149">Działanie `SendMail` kopiuje zawartość tego pliku do jego właściwości treści.</span><span class="sxs-lookup"><span data-stu-id="e4ae0-149">The `SendMail` activity copies the contents of this file to its body property.</span></span><br /><br /> <span data-ttu-id="e4ae0-150">Szablon może zawierać tokeny, które są zastępowane przez zawartość właściwości tokens.</span><span class="sxs-lookup"><span data-stu-id="e4ae0-150">The template can contain tokens that are replaced by the contents of the tokens property.</span></span>|  
|<span data-ttu-id="e4ae0-151">TestMailTo (Poczta testowa)</span><span class="sxs-lookup"><span data-stu-id="e4ae0-151">TestMailTo</span></span>|<xref:System.Net.Mail.MailAddress>|<span data-ttu-id="e4ae0-152">Gdy ta właściwość jest ustawiona, wszystkie wiadomości e-mail są wysyłane na adres określony w niej.</span><span class="sxs-lookup"><span data-stu-id="e4ae0-152">When this property is set, all emails are sent to the address specified in it.</span></span><br /><br /> <span data-ttu-id="e4ae0-153">Ta właściwość jest przeznaczona do użycia podczas testowania przepływów pracy.</span><span class="sxs-lookup"><span data-stu-id="e4ae0-153">This property is intended to be used when testing workflows.</span></span> <span data-ttu-id="e4ae0-154">Na przykład, jeśli chcesz się upewnić, że wszystkie wiadomości e-mail są wysyłane bez wysyłania ich do rzeczywistych adresatów.</span><span class="sxs-lookup"><span data-stu-id="e4ae0-154">For example, when you want to make sure that all emails are sent without sending them to the actual recipients.</span></span>|  
|<span data-ttu-id="e4ae0-155">Ścieżka testowa</span><span class="sxs-lookup"><span data-stu-id="e4ae0-155">TestDropPath</span></span>|<span data-ttu-id="e4ae0-156">Ciąg</span><span class="sxs-lookup"><span data-stu-id="e4ae0-156">String</span></span>|<span data-ttu-id="e4ae0-157">Po ustawieniu tej właściwości wszystkie wiadomości e-mail są również zapisywane w określonym pliku.</span><span class="sxs-lookup"><span data-stu-id="e4ae0-157">When this property is set, all emails are also saved in the specified file.</span></span><br /><br /> <span data-ttu-id="e4ae0-158">Ta właściwość jest przeznaczona do użycia podczas testowania lub debugowania przepływów pracy, aby upewnić się, że format i zawartość wychodzących wiadomości e-mail jest odpowiednia.</span><span class="sxs-lookup"><span data-stu-id="e4ae0-158">This property is intended to be used when you are testing or debugging workflows, to make sure that the format and contents of the outgoing emails is appropriate.</span></span>|  
  
## <a name="solution-contents"></a><span data-ttu-id="e4ae0-159">Zawartość rozwiązania</span><span class="sxs-lookup"><span data-stu-id="e4ae0-159">Solution Contents</span></span>  
 <span data-ttu-id="e4ae0-160">Rozwiązanie zawiera dwa projekty.</span><span class="sxs-lookup"><span data-stu-id="e4ae0-160">The solution contains two projects.</span></span>  
  
|<span data-ttu-id="e4ae0-161">Project</span><span class="sxs-lookup"><span data-stu-id="e4ae0-161">Project</span></span>|<span data-ttu-id="e4ae0-162">Opis</span><span class="sxs-lookup"><span data-stu-id="e4ae0-162">Description</span></span>|<span data-ttu-id="e4ae0-163">Ważne pliki</span><span class="sxs-lookup"><span data-stu-id="e4ae0-163">Important Files</span></span>|  
|-------------|-----------------|---------------------|  
|<span data-ttu-id="e4ae0-164">Sendmail</span><span class="sxs-lookup"><span data-stu-id="e4ae0-164">SendMail</span></span>|<span data-ttu-id="e4ae0-165">Aktywność SendMail</span><span class="sxs-lookup"><span data-stu-id="e4ae0-165">The SendMail activity</span></span>|<span data-ttu-id="e4ae0-166">1. SendMail.cs: realizacja głównego działania</span><span class="sxs-lookup"><span data-stu-id="e4ae0-166">1.  SendMail.cs: implementation for the main activity</span></span><br /><span data-ttu-id="e4ae0-167">2. SendMailDesigner.xaml i SendMailDesigner.xaml.cs: projektant dla działania SendMail</span><span class="sxs-lookup"><span data-stu-id="e4ae0-167">2.  SendMailDesigner.xaml and SendMailDesigner.xaml.cs: designer for the SendMail activity</span></span><br /><span data-ttu-id="e4ae0-168">3. MailTemplateBody.htm: szablon dla wiadomości e-mail, które mają być wysyłane.</span><span class="sxs-lookup"><span data-stu-id="e4ae0-168">3.  MailTemplateBody.htm: template for the email to be sent out.</span></span>|  
|<span data-ttu-id="e4ae0-169">SendMailTestClient (SendMailTestClient)</span><span class="sxs-lookup"><span data-stu-id="e4ae0-169">SendMailTestClient</span></span>|<span data-ttu-id="e4ae0-170">Klienta, aby przetestować działanie SendMail.</span><span class="sxs-lookup"><span data-stu-id="e4ae0-170">Client to test the SendMail activity.</span></span>  <span data-ttu-id="e4ae0-171">Ten projekt pokazuje dwa sposoby wywoływania działania SendMail: deklaratywnie i programowo.</span><span class="sxs-lookup"><span data-stu-id="e4ae0-171">This project demonstrates two ways of invoking the SendMail activity: declaratively, and programmatically.</span></span>|<span data-ttu-id="e4ae0-172">1. Sequence1.xaml: przepływ pracy, który wywołuje działanie SendMail.</span><span class="sxs-lookup"><span data-stu-id="e4ae0-172">1.  Sequence1.xaml: workflow that invokes the SendMail activity.</span></span><br /><span data-ttu-id="e4ae0-173">2. Program.cs: wywołuje Sequence1, a także tworzy przepływ pracy programowo, który używa SendMail.</span><span class="sxs-lookup"><span data-stu-id="e4ae0-173">2.  Program.cs: invokes Sequence1 and also creates a workflow programmatically that uses SendMail.</span></span>|  
  
## <a name="further-configuration-of-the-sendmail-activity"></a><span data-ttu-id="e4ae0-174">Dalsza konfiguracja działania SendMail</span><span class="sxs-lookup"><span data-stu-id="e4ae0-174">Further configuration of the SendMail activity</span></span>  
 <span data-ttu-id="e4ae0-175">Chociaż nie pokazano w przykładzie, użytkownicy mogą wykonywać dodawanie konfiguracji działania SendMail.</span><span class="sxs-lookup"><span data-stu-id="e4ae0-175">Although not shown in the sample, users can perform addition configuration of the SendMail activity.</span></span> <span data-ttu-id="e4ae0-176">Następne trzy sekcje pokazują, jak to się robi.</span><span class="sxs-lookup"><span data-stu-id="e4ae0-176">The next three sections demonstrate how this is done.</span></span>  
  
### <a name="sending-an-email-using-tokens-specified-in-the-body"></a><span data-ttu-id="e4ae0-177">Wysyłanie wiadomości e-mail przy użyciu tokenów określonych w treści</span><span class="sxs-lookup"><span data-stu-id="e4ae0-177">Sending an email using tokens specified in the body</span></span>  
 <span data-ttu-id="e4ae0-178">Ten fragment kodu pokazuje, jak można wysyłać wiadomości e-mail z tokenami w treści.</span><span class="sxs-lookup"><span data-stu-id="e4ae0-178">This code snippet demonstrates how you can send email with tokens in the body.</span></span> <span data-ttu-id="e4ae0-179">Zwróć uwagę, jak tokeny są dostarczane w właściwości treści.</span><span class="sxs-lookup"><span data-stu-id="e4ae0-179">Notice how the tokens are provided in the body property.</span></span> <span data-ttu-id="e4ae0-180">Wartości dla tych tokenów są dostarczane do właściwości tokens.</span><span class="sxs-lookup"><span data-stu-id="e4ae0-180">Values for those tokens are provided to the tokens property.</span></span>  
  
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
  
### <a name="sending-an-email-using-a-template"></a><span data-ttu-id="e4ae0-181">Wysyłanie wiadomości e-mail przy użyciu szablonu</span><span class="sxs-lookup"><span data-stu-id="e4ae0-181">Sending an email using a template</span></span>  
 <span data-ttu-id="e4ae0-182">Ten fragment kodu pokazuje, jak wysłać wiadomość e-mail przy użyciu tokenów szablonu w treści.</span><span class="sxs-lookup"><span data-stu-id="e4ae0-182">This snippet shows how to send an email using a template tokens in the body.</span></span> <span data-ttu-id="e4ae0-183">Należy zauważyć, `BodyTemplateFilePath` że podczas ustawiania właściwości nie musimy podawać wartość body właściwości (zawartość pliku szablonu zostaną skopiowane do treści).</span><span class="sxs-lookup"><span data-stu-id="e4ae0-183">Notice that when setting the `BodyTemplateFilePath` property we don’t need to provide the value for Body property (the contents of the template file will be copied to the body).</span></span>  
  
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
  
### <a name="sending-mails-in-testing-mode"></a><span data-ttu-id="e4ae0-184">Wysyłanie wiadomości e-mail w trybie testowym</span><span class="sxs-lookup"><span data-stu-id="e4ae0-184">Sending Mails in Testing Mode</span></span>  
 <span data-ttu-id="e4ae0-185">Ten fragment kodu pokazuje, jak ustawić dwie właściwości testowania: przez ustawienie `TestMailTo` `john.doe@contoso.con` wszystkich wiadomości będą wysyłane do (bez względu na wartości Do, CC, UDW).</span><span class="sxs-lookup"><span data-stu-id="e4ae0-185">This code snippet shows how to set the two testing properties: by setting `TestMailTo` to all messages will be sent to `john.doe@contoso.con` (without regard of the values of To, Cc, Bcc).</span></span> <span data-ttu-id="e4ae0-186">Przez ustawienie TestDropPath wszystkie wychodzące wiadomości e-mail będą również rejestrowane w podanej ścieżce.</span><span class="sxs-lookup"><span data-stu-id="e4ae0-186">By setting TestDropPath all outgoing emails will be also recorded in the provided path.</span></span> <span data-ttu-id="e4ae0-187">Te właściwości można ustawić niezależnie (nie są one powiązane).</span><span class="sxs-lookup"><span data-stu-id="e4ae0-187">These properties can be set independently (they are not related).</span></span>  
  
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
  
## <a name="set-up-instructions"></a><span data-ttu-id="e4ae0-188">Instrukcje dotyczące konfiguracji</span><span class="sxs-lookup"><span data-stu-id="e4ae0-188">Set-Up Instructions</span></span>  
 <span data-ttu-id="e4ae0-189">Dostęp do serwera SMTP jest wymagany dla tego przykładu.</span><span class="sxs-lookup"><span data-stu-id="e4ae0-189">Access to a SMTP server is required for this sample.</span></span>  
  
 <span data-ttu-id="e4ae0-190">Aby uzyskać więcej informacji na temat konfigurowania serwera SMTP, zobacz następujące łącza.</span><span class="sxs-lookup"><span data-stu-id="e4ae0-190">For more information about setting up a SMTP server, see the following links.</span></span>  
  
- <span data-ttu-id="e4ae0-191">[Konfigurowanie usługi SMTP (IIS 6.0)](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc784968(v=ws.10))</span><span class="sxs-lookup"><span data-stu-id="e4ae0-191">[Configuring the SMTP Service (IIS 6.0)](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc784968(v=ws.10))</span></span>  
  
- <span data-ttu-id="e4ae0-192">[IIS 7.0: Konfigurowanie poczty e-mail SMTP](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc772058(v=ws.10))</span><span class="sxs-lookup"><span data-stu-id="e4ae0-192">[IIS 7.0: Configure SMTP E-Mail](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc772058(v=ws.10))</span></span>  
  
- <span data-ttu-id="e4ae0-193">[Jak zainstalować usługę SMTP](https://docs.microsoft.com/previous-versions/tn-archive/aa997480(v=exchg.65))</span><span class="sxs-lookup"><span data-stu-id="e4ae0-193">[How to Install the SMTP Service](https://docs.microsoft.com/previous-versions/tn-archive/aa997480(v=exchg.65))</span></span>  
  
 <span data-ttu-id="e4ae0-194">Emulatory SMTP dostarczone przez osoby trzecie są dostępne do pobrania.</span><span class="sxs-lookup"><span data-stu-id="e4ae0-194">SMTP emulators provided by third parties are available for download.</span></span>  
  
##### <a name="to-run-this-sample"></a><span data-ttu-id="e4ae0-195">Aby uruchomić ten przykład</span><span class="sxs-lookup"><span data-stu-id="e4ae0-195">To run this sample</span></span>  
  
1. <span data-ttu-id="e4ae0-196">Za pomocą programu Visual Studio 2010 otwórz plik rozwiązania SendMail.sln.</span><span class="sxs-lookup"><span data-stu-id="e4ae0-196">Using Visual Studio 2010, open the SendMail.sln solution file.</span></span>  
  
2. <span data-ttu-id="e4ae0-197">Upewnij się, że masz dostęp do prawidłowego serwera SMTP.</span><span class="sxs-lookup"><span data-stu-id="e4ae0-197">Ensure that you have access to a valid SMTP server.</span></span> <span data-ttu-id="e4ae0-198">Zapoznaj się z instrukcjami konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="e4ae0-198">See the set-up instructions.</span></span>  
  
3. <span data-ttu-id="e4ae0-199">Skonfiguruj program z adresem serwera oraz adresami e-mail od i do.</span><span class="sxs-lookup"><span data-stu-id="e4ae0-199">Configure the program with your server address, and From and To email addresses.</span></span>  
  
     <span data-ttu-id="e4ae0-200">Aby poprawnie uruchomić ten przykład, może być konieczne skonfigurowanie wartości adresów e-mail od i do oraz adresu serwera SMTP w Program.cs i sequence.xaml.</span><span class="sxs-lookup"><span data-stu-id="e4ae0-200">To correctly run this sample, you may need to configure the value of From and To email addresses and the address of the SMTP server in  Program.cs and in Sequence.xaml.</span></span> <span data-ttu-id="e4ae0-201">Należy zmienić adres w obu lokalizacjach, ponieważ program wysyła pocztę na dwa różne sposoby</span><span class="sxs-lookup"><span data-stu-id="e4ae0-201">You will need to change the address in both locations since the program sends mail in two different ways</span></span>  
  
4. <span data-ttu-id="e4ae0-202">Aby utworzyć rozwiązanie, naciśnij klawisze CTRL+SHIFT+B.</span><span class="sxs-lookup"><span data-stu-id="e4ae0-202">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
5. <span data-ttu-id="e4ae0-203">Aby uruchomić rozwiązanie, naciśnij klawisze CTRL+F5.</span><span class="sxs-lookup"><span data-stu-id="e4ae0-203">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="e4ae0-204">Próbki mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="e4ae0-204">The samples may already be installed on your machine.</span></span> <span data-ttu-id="e4ae0-205">Przed kontynuowaniem sprawdź następujący (domyślny) katalog.</span><span class="sxs-lookup"><span data-stu-id="e4ae0-205">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="e4ae0-206">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="e4ae0-206">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e4ae0-207">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="e4ae0-207">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\SendMail`
