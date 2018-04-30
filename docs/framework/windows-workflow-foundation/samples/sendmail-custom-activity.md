---
title: Działania niestandardowe SendMail
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 947a9ae6-379c-43a3-9cd5-87f573a5739f
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 46038466233e7039229890b15b0ad6ca9d1a717f
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/30/2018
---
# <a name="sendmail-custom-activity"></a><span data-ttu-id="7cb51-102">Działania niestandardowe SendMail</span><span class="sxs-lookup"><span data-stu-id="7cb51-102">SendMail Custom Activity</span></span>
<span data-ttu-id="7cb51-103">Ten przykład przedstawia sposób tworzenia działań niestandardowych, która jest pochodną <xref:System.Activities.AsyncCodeActivity> do wysyłania wiadomości e-mail do użycia w aplikacji przepływu pracy za pomocą protokołu SMTP.</span><span class="sxs-lookup"><span data-stu-id="7cb51-103">This sample demonstrates how to create a custom activity that derives from <xref:System.Activities.AsyncCodeActivity> to send mail using SMTP for use within a workflow application.</span></span> <span data-ttu-id="7cb51-104">To niestandardowe działanie korzysta z funkcji programu <xref:System.Net.Mail.SmtpClient> do asynchronicznego wysyłania wiadomości e-mail i do wysyłania wiadomości e-mail z uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="7cb51-104">The custom activity uses the capabilities of <xref:System.Net.Mail.SmtpClient> to send email asynchronously and to send mail with authentication.</span></span> <span data-ttu-id="7cb51-105">Umożliwia także niektóre funkcje przez użytkownika końcowego, takie jak przetestować tryb, zastępujący tokenu, Szablony plików i test ścieżkę.</span><span class="sxs-lookup"><span data-stu-id="7cb51-105">It also provides some end-user features like test mode, token replacement, file templates, and test drop path.</span></span>  
  
 <span data-ttu-id="7cb51-106">W poniższej tabeli przedstawiono argumenty `SendMail` działania.</span><span class="sxs-lookup"><span data-stu-id="7cb51-106">The following table details the arguments for the `SendMail` activity.</span></span>  
  
|<span data-ttu-id="7cb51-107">Nazwa</span><span class="sxs-lookup"><span data-stu-id="7cb51-107">Name</span></span>|<span data-ttu-id="7cb51-108">Typ</span><span class="sxs-lookup"><span data-stu-id="7cb51-108">Type</span></span>|<span data-ttu-id="7cb51-109">Opis</span><span class="sxs-lookup"><span data-stu-id="7cb51-109">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="7cb51-110">Host</span><span class="sxs-lookup"><span data-stu-id="7cb51-110">Host</span></span>|<span data-ttu-id="7cb51-111">String</span><span class="sxs-lookup"><span data-stu-id="7cb51-111">String</span></span>|<span data-ttu-id="7cb51-112">Adres hosta serwera SMTP.</span><span class="sxs-lookup"><span data-stu-id="7cb51-112">Address of the SMTP server host.</span></span>|  
|<span data-ttu-id="7cb51-113">Port</span><span class="sxs-lookup"><span data-stu-id="7cb51-113">Port</span></span>|<span data-ttu-id="7cb51-114">String</span><span class="sxs-lookup"><span data-stu-id="7cb51-114">String</span></span>|<span data-ttu-id="7cb51-115">Port usługi SMTP na hoście.</span><span class="sxs-lookup"><span data-stu-id="7cb51-115">Port of the SMTP service in the host.</span></span>|  
|<span data-ttu-id="7cb51-116">EnableSsl</span><span class="sxs-lookup"><span data-stu-id="7cb51-116">EnableSsl</span></span>|<span data-ttu-id="7cb51-117">bool</span><span class="sxs-lookup"><span data-stu-id="7cb51-117">bool</span></span>|<span data-ttu-id="7cb51-118">Określa, czy <xref:System.Net.Mail.SmtpClient> używa protokołu Secure Sockets Layer (SSL) do szyfrowania połączenia.</span><span class="sxs-lookup"><span data-stu-id="7cb51-118">Specifies whether the <xref:System.Net.Mail.SmtpClient> uses Secure Sockets Layer (SSL) to encrypt the connection.</span></span>|  
|<span data-ttu-id="7cb51-119">UserName</span><span class="sxs-lookup"><span data-stu-id="7cb51-119">UserName</span></span>|<span data-ttu-id="7cb51-120">String</span><span class="sxs-lookup"><span data-stu-id="7cb51-120">String</span></span>|<span data-ttu-id="7cb51-121">Nazwa użytkownika, aby ustawić poświadczenia, aby uwierzytelnić nadawcę <xref:System.Net.Mail.SmtpClient.Credentials%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="7cb51-121">Username to set up the credentials to authenticate the sender <xref:System.Net.Mail.SmtpClient.Credentials%2A> property.</span></span>|  
|<span data-ttu-id="7cb51-122">Hasło</span><span class="sxs-lookup"><span data-stu-id="7cb51-122">Password</span></span>|<span data-ttu-id="7cb51-123">String</span><span class="sxs-lookup"><span data-stu-id="7cb51-123">String</span></span>|<span data-ttu-id="7cb51-124">Hasło, aby ustawić poświadczenia, aby uwierzytelnić nadawcę <xref:System.Net.Mail.SmtpClient.Credentials%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="7cb51-124">Password to set up the credentials to authenticate the sender <xref:System.Net.Mail.SmtpClient.Credentials%2A> property.</span></span>|  
|<span data-ttu-id="7cb51-125">Temat</span><span class="sxs-lookup"><span data-stu-id="7cb51-125">Subject</span></span>|<span data-ttu-id="7cb51-126"><xref:System.Activities.InArgument%601>\<ciąg ></span><span class="sxs-lookup"><span data-stu-id="7cb51-126"><xref:System.Activities.InArgument%601>\<string></span></span>|<span data-ttu-id="7cb51-127">Temat wiadomości.</span><span class="sxs-lookup"><span data-stu-id="7cb51-127">Subject of the message.</span></span>|  
|<span data-ttu-id="7cb51-128">Treści</span><span class="sxs-lookup"><span data-stu-id="7cb51-128">Body</span></span>|<span data-ttu-id="7cb51-129"><xref:System.Activities.InArgument%601>\<ciąg ></span><span class="sxs-lookup"><span data-stu-id="7cb51-129"><xref:System.Activities.InArgument%601>\<string></span></span>|<span data-ttu-id="7cb51-130">Treść wiadomości.</span><span class="sxs-lookup"><span data-stu-id="7cb51-130">Body of the message.</span></span>|  
|<span data-ttu-id="7cb51-131">Załączniki</span><span class="sxs-lookup"><span data-stu-id="7cb51-131">Attachments</span></span>|<span data-ttu-id="7cb51-132"><xref:System.Activities.InArgument%601>\<ciąg ></span><span class="sxs-lookup"><span data-stu-id="7cb51-132"><xref:System.Activities.InArgument%601>\<string></span></span>|<span data-ttu-id="7cb51-133">Kolekcja załącznika używany do przechowywania danych dołączony do wiadomości e-mail.</span><span class="sxs-lookup"><span data-stu-id="7cb51-133">Attachment collection used to store data attached to this email message.</span></span>|  
|<span data-ttu-id="7cb51-134">Z</span><span class="sxs-lookup"><span data-stu-id="7cb51-134">From</span></span>|<xref:System.Net.Mail.MailAddress>|<span data-ttu-id="7cb51-135">Adres początkowy dla tej wiadomości e-mail.</span><span class="sxs-lookup"><span data-stu-id="7cb51-135">From address for this email message.</span></span>|  
|<span data-ttu-id="7cb51-136">Do</span><span class="sxs-lookup"><span data-stu-id="7cb51-136">To</span></span>|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|<span data-ttu-id="7cb51-137">Kolekcja adresów, która zawiera adresatów wiadomości e-mail.</span><span class="sxs-lookup"><span data-stu-id="7cb51-137">Address collection that contains the recipients of this email message.</span></span>|  
|<span data-ttu-id="7cb51-138">CC</span><span class="sxs-lookup"><span data-stu-id="7cb51-138">CC</span></span>|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|<span data-ttu-id="7cb51-139">Adres kolekcji zawierającej Adresaci kopii (DW) dla tej wiadomości e-mail.</span><span class="sxs-lookup"><span data-stu-id="7cb51-139">Address collection that contains the carbon copy (CC) recipients for this email message.</span></span>|  
|<span data-ttu-id="7cb51-140">BCC</span><span class="sxs-lookup"><span data-stu-id="7cb51-140">BCC</span></span>|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|<span data-ttu-id="7cb51-141">Adres kolekcji, która zawiera adresatów kopii (UDW) dla tej wiadomości e-mail.</span><span class="sxs-lookup"><span data-stu-id="7cb51-141">Address collection that contains the blind carbon copy (BCC) recipients for this email message.</span></span>|  
|<span data-ttu-id="7cb51-142">Tokeny</span><span class="sxs-lookup"><span data-stu-id="7cb51-142">Tokens</span></span>|<span data-ttu-id="7cb51-143"><xref:System.Activities.InArgument%601>< IDictionary\<ciąg, ciąg >></span><span class="sxs-lookup"><span data-stu-id="7cb51-143"><xref:System.Activities.InArgument%601><IDictionary\<string, string>></span></span>|<span data-ttu-id="7cb51-144">Tokeny zastąpić w treści.</span><span class="sxs-lookup"><span data-stu-id="7cb51-144">Tokens to replace in the body.</span></span> <span data-ttu-id="7cb51-145">Ta funkcja umożliwia użytkownikom określanie niektórych wartości w treści, niż można później zastąpić tokeny realizowane przy użyciu tej właściwości.</span><span class="sxs-lookup"><span data-stu-id="7cb51-145">This feature allows users to specify some values in the body than can be replaced later by the tokens provided using this property.</span></span>|  
|<span data-ttu-id="7cb51-146">BodyTemplateFilePath</span><span class="sxs-lookup"><span data-stu-id="7cb51-146">BodyTemplateFilePath</span></span>|<span data-ttu-id="7cb51-147">String</span><span class="sxs-lookup"><span data-stu-id="7cb51-147">String</span></span>|<span data-ttu-id="7cb51-148">Ścieżka szablonu dla treści.</span><span class="sxs-lookup"><span data-stu-id="7cb51-148">Path of a template for the body.</span></span> <span data-ttu-id="7cb51-149">`SendMail` Działanie kopiuje zawartość tego pliku do jej treści właściwości.</span><span class="sxs-lookup"><span data-stu-id="7cb51-149">The `SendMail` activity copies the contents of this file to its body property.</span></span><br /><br /> <span data-ttu-id="7cb51-150">Szablon może zawierać tokeny, które są zastępowane przez wartości właściwości tokenów.</span><span class="sxs-lookup"><span data-stu-id="7cb51-150">The template can contain tokens that are replaced by the contents of the tokens property.</span></span>|  
|<span data-ttu-id="7cb51-151">TestMailTo</span><span class="sxs-lookup"><span data-stu-id="7cb51-151">TestMailTo</span></span>|<xref:System.Net.Mail.MailAddress>|<span data-ttu-id="7cb51-152">Gdy ta właściwość jest ustawiona, wszystkie wiadomości e-mail są wysyłane na adres określony w nim.</span><span class="sxs-lookup"><span data-stu-id="7cb51-152">When this property is set, all emails are sent to the address specified in it.</span></span><br /><br /> <span data-ttu-id="7cb51-153">Ta właściwość jest przeznaczona do użycia podczas badania przepływów pracy.</span><span class="sxs-lookup"><span data-stu-id="7cb51-153">This property is intended to be used when testing workflows.</span></span> <span data-ttu-id="7cb51-154">Na przykład jeśli chcesz upewnić się, że wszystkie wiadomości e-mail są wysyłane bez wysyłania ich do adresatów, do rzeczywistych.</span><span class="sxs-lookup"><span data-stu-id="7cb51-154">For example, when you want to make sure that all emails are sent without sending them to the actual recipients.</span></span>|  
|<span data-ttu-id="7cb51-155">TestDropPath</span><span class="sxs-lookup"><span data-stu-id="7cb51-155">TestDropPath</span></span>|<span data-ttu-id="7cb51-156">String</span><span class="sxs-lookup"><span data-stu-id="7cb51-156">String</span></span>|<span data-ttu-id="7cb51-157">Gdy ta właściwość jest ustawiona, wszystkie wiadomości e-mail zostały także zapisane w określonym pliku.</span><span class="sxs-lookup"><span data-stu-id="7cb51-157">When this property is set, all emails are also saved in the specified file.</span></span><br /><br /> <span data-ttu-id="7cb51-158">Ta właściwość jest przeznaczona do użycia podczas testowania i debugowania przepływów pracy, aby upewnić się, że format i zawartość wychodzących wiadomości e-mail jest odpowiednia.</span><span class="sxs-lookup"><span data-stu-id="7cb51-158">This property is intended to be used when you are testing or debugging workflows, to make sure that the format and contents of the outgoing emails is appropriate.</span></span>|  
  
## <a name="solution-contents"></a><span data-ttu-id="7cb51-159">Zawartość rozwiązania</span><span class="sxs-lookup"><span data-stu-id="7cb51-159">Solution Contents</span></span>  
 <span data-ttu-id="7cb51-160">Rozwiązanie zawiera dwa projekty.</span><span class="sxs-lookup"><span data-stu-id="7cb51-160">The solution contains two projects.</span></span>  
  
|<span data-ttu-id="7cb51-161">Projekt</span><span class="sxs-lookup"><span data-stu-id="7cb51-161">Project</span></span>|<span data-ttu-id="7cb51-162">Opis</span><span class="sxs-lookup"><span data-stu-id="7cb51-162">Description</span></span>|<span data-ttu-id="7cb51-163">Ważnych plików</span><span class="sxs-lookup"><span data-stu-id="7cb51-163">Important Files</span></span>|  
|-------------|-----------------|---------------------|  
|<span data-ttu-id="7cb51-164">SendMail</span><span class="sxs-lookup"><span data-stu-id="7cb51-164">SendMail</span></span>|<span data-ttu-id="7cb51-165">Działanie SendMail</span><span class="sxs-lookup"><span data-stu-id="7cb51-165">The SendMail activity</span></span>|<span data-ttu-id="7cb51-166">1.  SendMail.cs: implementacja dla działania głównego</span><span class="sxs-lookup"><span data-stu-id="7cb51-166">1.  SendMail.cs: implementation for the main activity</span></span><br /><span data-ttu-id="7cb51-167">2.  SendMailDesigner.xaml i SendMailDesigner.xaml.cs: projektanta dla działania SendMail</span><span class="sxs-lookup"><span data-stu-id="7cb51-167">2.  SendMailDesigner.xaml and SendMailDesigner.xaml.cs: designer for the SendMail activity</span></span><br /><span data-ttu-id="7cb51-168">3.  MailTemplateBody.htm: szablon wiadomości e-mail do wysłania.</span><span class="sxs-lookup"><span data-stu-id="7cb51-168">3.  MailTemplateBody.htm: template for the email to be sent out.</span></span>|  
|<span data-ttu-id="7cb51-169">SendMailTestClient</span><span class="sxs-lookup"><span data-stu-id="7cb51-169">SendMailTestClient</span></span>|<span data-ttu-id="7cb51-170">Klient, aby przetestować działanie SendMail.</span><span class="sxs-lookup"><span data-stu-id="7cb51-170">Client to test the SendMail activity.</span></span>  <span data-ttu-id="7cb51-171">Ten projekt przedstawia dwa sposoby wywoływania działania SendMail: programowo i deklaratywnie.</span><span class="sxs-lookup"><span data-stu-id="7cb51-171">This project demonstrates two ways of invoking the SendMail activity: declaratively, and programmatically.</span></span>|<span data-ttu-id="7cb51-172">1.  Sequence1.XAML: przepływ pracy, który wywołuje aktywność SendMail.</span><span class="sxs-lookup"><span data-stu-id="7cb51-172">1.  Sequence1.xaml: workflow that invokes the SendMail activity.</span></span><br /><span data-ttu-id="7cb51-173">2.  Plik program.CS: wywołuje Sequence1, a także tworzy programowo używającej SendMail przepływ pracy.</span><span class="sxs-lookup"><span data-stu-id="7cb51-173">2.  Program.cs: invokes Sequence1 and also creates a workflow programmatically that uses SendMail.</span></span>|  
  
## <a name="further-configuration-of-the-sendmail-activity"></a><span data-ttu-id="7cb51-174">Dalsza konfiguracja działania SendMail</span><span class="sxs-lookup"><span data-stu-id="7cb51-174">Further configuration of the SendMail activity</span></span>  
 <span data-ttu-id="7cb51-175">Wprawdzie nie pokazano w przykładzie, użytkownicy mogą wykonywać konfiguracji dodanie SendMail działania.</span><span class="sxs-lookup"><span data-stu-id="7cb51-175">Although not shown in the sample, users can perform addition configuration of the SendMail activity.</span></span> <span data-ttu-id="7cb51-176">Trzech kolejnych sekcjach pokazują, jak to zrobić.</span><span class="sxs-lookup"><span data-stu-id="7cb51-176">The next three sections demonstrate how this is done.</span></span>  
  
### <a name="sending-an-email-using-tokens-specified-in-the-body"></a><span data-ttu-id="7cb51-177">Wysyłanie wiadomości e-mail przy użyciu tokenów określony w treści</span><span class="sxs-lookup"><span data-stu-id="7cb51-177">Sending an email using tokens specified in the body</span></span>  
 <span data-ttu-id="7cb51-178">Następujący fragment kodu pokazano, jak można wysłać wiadomości e-mail z tokenami w treści.</span><span class="sxs-lookup"><span data-stu-id="7cb51-178">This code snippet demonstrates how you can send email with tokens in the body.</span></span> <span data-ttu-id="7cb51-179">Zwróć uwagę, jak tokenów znajdują się w treści właściwości.</span><span class="sxs-lookup"><span data-stu-id="7cb51-179">Notice how the tokens are provided in the body property.</span></span> <span data-ttu-id="7cb51-180">Wartości te tokeny są dostarczane do właściwości tokenów.</span><span class="sxs-lookup"><span data-stu-id="7cb51-180">Values for those tokens are provided to the tokens property.</span></span>  
  
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
  
### <a name="sending-an-email-using-a-template"></a><span data-ttu-id="7cb51-181">Wysyłanie wiadomości e-mail przy użyciu szablonu</span><span class="sxs-lookup"><span data-stu-id="7cb51-181">Sending an email using a template</span></span>  
 <span data-ttu-id="7cb51-182">Następujący fragment kodu przedstawia sposób wysłania wiadomości e-mail przy użyciu tokenów szablonu w treści.</span><span class="sxs-lookup"><span data-stu-id="7cb51-182">This snippet shows how to send an email using a template tokens in the body.</span></span> <span data-ttu-id="7cb51-183">Zwróć uwagę, że podczas ustawiania `BodyTemplateFilePath` właściwość nie należy podać wartość dla właściwości Body (treść pliku szablonu zostaną skopiowane do treści).</span><span class="sxs-lookup"><span data-stu-id="7cb51-183">Notice that when setting the `BodyTemplateFilePath` property we don’t need to provide the value for Body property (the contents of the template file will be copied to the body).</span></span>  
  
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
  
### <a name="sending-mails-in-testing-mode"></a><span data-ttu-id="7cb51-184">Wysyłanie wiadomości w tryb testowania</span><span class="sxs-lookup"><span data-stu-id="7cb51-184">Sending Mails in Testing Mode</span></span>  
 <span data-ttu-id="7cb51-185">Następujący fragment kodu przedstawiono sposób ustawiania dwie właściwości testowych: ustawiając `TestMailTo` na wszystkie komunikaty będą wysyłane do john.doe@contoso.con (bez względu wartości do, DW, UDW).</span><span class="sxs-lookup"><span data-stu-id="7cb51-185">This code snippet shows how to set the two testing properties: by setting `TestMailTo` to all messages will be sent to john.doe@contoso.con (without regard of the values of To, Cc, Bcc).</span></span> <span data-ttu-id="7cb51-186">Przez ustawienie TestDropPath wszystkich wychodzących wiadomości e-mail będą również rejestrowane w podana ścieżka.</span><span class="sxs-lookup"><span data-stu-id="7cb51-186">By setting TestDropPath all outgoing emails will be also recorded in the provided path.</span></span> <span data-ttu-id="7cb51-187">Te właściwości można skonfigurować niezależnie (nie jest ona powiązana).</span><span class="sxs-lookup"><span data-stu-id="7cb51-187">These properties can be set independently (they are not related).</span></span>  
  
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
  
## <a name="set-up-instructions"></a><span data-ttu-id="7cb51-188">Instrukcje dotyczące konfiguracji</span><span class="sxs-lookup"><span data-stu-id="7cb51-188">Set-Up Instructions</span></span>  
 <span data-ttu-id="7cb51-189">Dostęp do serwera SMTP jest wymagany dla tego przykładu.</span><span class="sxs-lookup"><span data-stu-id="7cb51-189">Access to a SMTP server is required for this sample.</span></span>  
  
 <span data-ttu-id="7cb51-190">Aby uzyskać więcej informacji na temat konfigurowania serwera SMTP zobacz następujące łącza.</span><span class="sxs-lookup"><span data-stu-id="7cb51-190">For more information about setting up a SMTP server, see the following links.</span></span>  
  
-   [<span data-ttu-id="7cb51-191">Microsoft Technet</span><span class="sxs-lookup"><span data-stu-id="7cb51-191">Microsoft Technet</span></span>](http://go.microsoft.com/fwlink/?LinkId=166060)  
  
-   [<span data-ttu-id="7cb51-192">Konfigurowanie usługi SMTP (IIS 6.0)</span><span class="sxs-lookup"><span data-stu-id="7cb51-192">Configuring the SMTP Service (IIS 6.0)</span></span>](http://go.microsoft.com/fwlink/?LinkId=150456)  
  
-   [<span data-ttu-id="7cb51-193">Usługi IIS 7.0: Konfigurowanie poczty E-Mail SMTP</span><span class="sxs-lookup"><span data-stu-id="7cb51-193">IIS 7.0: Configure SMTP E-Mail</span></span>](http://go.microsoft.com/fwlink/?LinkId=150457)  
  
-   [<span data-ttu-id="7cb51-194">Jak zainstalować usługi SMTP</span><span class="sxs-lookup"><span data-stu-id="7cb51-194">How to Install the SMTP Service</span></span>](http://go.microsoft.com/fwlink/?LinkId=150458)  
  
 <span data-ttu-id="7cb51-195">Emulatory SMTP zapewnianych przez strony trzecie są dostępne do pobrania.</span><span class="sxs-lookup"><span data-stu-id="7cb51-195">SMTP emulators provided by third parties are available for download.</span></span>  
  
##### <a name="to-run-this-sample"></a><span data-ttu-id="7cb51-196">Aby uruchomić ten przykład</span><span class="sxs-lookup"><span data-stu-id="7cb51-196">To run this sample</span></span>  
  
1.  <span data-ttu-id="7cb51-197">Przy użyciu [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania SendMail.sln.</span><span class="sxs-lookup"><span data-stu-id="7cb51-197">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the SendMail.sln solution file.</span></span>  
  
2.  <span data-ttu-id="7cb51-198">Upewnij się, że masz dostęp do prawidłowego serwera SMTP.</span><span class="sxs-lookup"><span data-stu-id="7cb51-198">Ensure that you have access to a valid SMTP server.</span></span> <span data-ttu-id="7cb51-199">Zobacz instrukcje dotyczące konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="7cb51-199">See the set-up instructions.</span></span>  
  
3.  <span data-ttu-id="7cb51-200">Skonfiguruj program przy użyciu adresu serwera i od i do adresów e-mail.</span><span class="sxs-lookup"><span data-stu-id="7cb51-200">Configure the program with your server address, and From and To email addresses.</span></span>  
  
     <span data-ttu-id="7cb51-201">Aby prawidłowo uruchomić ten przykład, może być konieczne skonfigurowanie wartości od i do adresów e-mail i adres serwera SMTP w pliku Program.cs i Sequence.xaml.</span><span class="sxs-lookup"><span data-stu-id="7cb51-201">To correctly run this sample, you may need to configure the value of From and To email addresses and the address of the SMTP server in  Program.cs and in Sequence.xaml.</span></span> <span data-ttu-id="7cb51-202">Musisz zmienić adres w obu lokalizacjach, ponieważ program wysyła wiadomości na dwa różne sposoby</span><span class="sxs-lookup"><span data-stu-id="7cb51-202">You will need to change the address in both locations since the program sends mail in two different ways</span></span>  
  
4.  <span data-ttu-id="7cb51-203">Aby tworzyć rozwiązania, naciśnij kombinację klawiszy CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="7cb51-203">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
5.  <span data-ttu-id="7cb51-204">Aby uruchomić rozwiązanie, naciśnij klawisze CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="7cb51-204">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="7cb51-205">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="7cb51-205">The samples may already be installed on your machine.</span></span> <span data-ttu-id="7cb51-206">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="7cb51-206">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="7cb51-207">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="7cb51-207">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7cb51-208">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="7cb51-208">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\SendMail`