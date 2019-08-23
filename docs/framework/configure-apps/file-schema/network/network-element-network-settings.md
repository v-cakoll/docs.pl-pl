---
title: <network>, element (ustawienia sieci)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#network
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings/smtp/network
helpviewer_keywords:
- <network> element
- network element
ms.assetid: 2c2c6ad4-ed11-48ab-b28e-2bc0ba9b42c7
ms.openlocfilehash: ee60b990bc749dbb9c5d0e7426c57e9392ddf9d4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920975"
---
# <a name="network-element-network-settings"></a><span data-ttu-id="7f09d-102">\<Network >, element (Ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="7f09d-102">\<network> Element (Network Settings)</span></span>
<span data-ttu-id="7f09d-103">Konfiguruje opcje sieci dla serwera zewnętrznego protokołu SMTP (Simple Mail Transport Protocol).</span><span class="sxs-lookup"><span data-stu-id="7f09d-103">Configures the network options for an external Simple Mail Transport Protocol (SMTP) server.</span></span>  
  
 <span data-ttu-id="7f09d-104">\<> konfiguracji</span><span class="sxs-lookup"><span data-stu-id="7f09d-104">\<configuration></span></span>  
<span data-ttu-id="7f09d-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="7f09d-105">\<system.net></span></span>  
<span data-ttu-id="7f09d-106">\<mailSettings></span><span class="sxs-lookup"><span data-stu-id="7f09d-106">\<mailSettings></span></span>  
<span data-ttu-id="7f09d-107">\<smtp></span><span class="sxs-lookup"><span data-stu-id="7f09d-107">\<smtp></span></span>  
<span data-ttu-id="7f09d-108">\<network></span><span class="sxs-lookup"><span data-stu-id="7f09d-108">\<network></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f09d-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="7f09d-109">Syntax</span></span>  
  
```xml  
<network  
  clientDomain="string"   
  defaultCredentials="true|false"  
  enableSsl="true|false"  
  host="string"   
  password="string"  
  port="integer"   
  targetName="string"  
  userName="string"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7f09d-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="7f09d-110">Attributes and Elements</span></span>  
 <span data-ttu-id="7f09d-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="7f09d-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7f09d-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="7f09d-112">Attributes</span></span>  
  
|<span data-ttu-id="7f09d-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="7f09d-113">Attribute</span></span>|<span data-ttu-id="7f09d-114">Opis</span><span class="sxs-lookup"><span data-stu-id="7f09d-114">Description</span></span>|  
|---------------|-----------------|  
|`clientDomain`|<span data-ttu-id="7f09d-115">Określa nazwę domeny klienta do użycia w początkowym żądaniu protokołu SMTP do nawiązania połączenia z serwerem poczty SMTP.</span><span class="sxs-lookup"><span data-stu-id="7f09d-115">Specifies the client domain name to use in the initial SMTP protocol request to connect to the SMTP mail server.</span></span> <span data-ttu-id="7f09d-116">Wartość domyślna to nazwa localhost komputera lokalnego wysyłającego żądanie.</span><span class="sxs-lookup"><span data-stu-id="7f09d-116">The default value is the localhost name of the local computer sending the request.</span></span>|  
|`defaultCredentials`|<span data-ttu-id="7f09d-117">Określa, czy domyślne poświadczenia użytkownika mają być używane do uzyskiwania dostępu do serwera poczty SMTP dla transakcji SMTP.</span><span class="sxs-lookup"><span data-stu-id="7f09d-117">Specifies whether the default user credentials should be used to access the SMTP mail server for SMTP transactions.</span></span> <span data-ttu-id="7f09d-118">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="7f09d-118">The default value is `false`.</span></span>|  
|`enableSsl`|<span data-ttu-id="7f09d-119">Określa, czy protokół SSL jest używany do uzyskiwania dostępu do serwera poczty SMTP.</span><span class="sxs-lookup"><span data-stu-id="7f09d-119">Specifies whether SSL is used to access an SMTP mail server.</span></span> <span data-ttu-id="7f09d-120">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="7f09d-120">The default value is `false`.</span></span>|  
|`host`|<span data-ttu-id="7f09d-121">Określa nazwę hosta serwera poczty SMTP, który ma być używany dla transakcji SMTP.</span><span class="sxs-lookup"><span data-stu-id="7f09d-121">Specifies the hostname of the SMTP mail server to use for SMTP transactions.</span></span> <span data-ttu-id="7f09d-122">Ten atrybut nie ma wartości domyślnej.</span><span class="sxs-lookup"><span data-stu-id="7f09d-122">This attribute has no default value.</span></span>|  
|`password`|<span data-ttu-id="7f09d-123">Określa hasło, które ma być używane do uwierzytelniania na serwerze poczty SMTP.</span><span class="sxs-lookup"><span data-stu-id="7f09d-123">Specifies the password to use for authentication to the SMTP mail server.</span></span> <span data-ttu-id="7f09d-124">Ten atrybut nie ma wartości domyślnej.</span><span class="sxs-lookup"><span data-stu-id="7f09d-124">This attribute has no default value.</span></span>|  
|`port`|<span data-ttu-id="7f09d-125">Określa numer portu, który ma być używany do nawiązywania połączenia z serwerem poczty SMTP.</span><span class="sxs-lookup"><span data-stu-id="7f09d-125">Specifies the port number to use to connect to the SMTP mail server.</span></span> <span data-ttu-id="7f09d-126">Wartość domyślna to 25.</span><span class="sxs-lookup"><span data-stu-id="7f09d-126">The default value is 25.</span></span>|  
|`targetName`|<span data-ttu-id="7f09d-127">Określa nazwę dostawcy usług (SPN), która ma być używana do uwierzytelniania podczas korzystania z rozszerzonej ochrony dla transakcji SMTP.</span><span class="sxs-lookup"><span data-stu-id="7f09d-127">Specifies the Service Provider Name (SPN) to use for authentication when using extended protection for SMTP transactions.</span></span> <span data-ttu-id="7f09d-128">Ten atrybut nie ma wartości domyślnej.</span><span class="sxs-lookup"><span data-stu-id="7f09d-128">This attribute has no default value.</span></span>|  
|`userName`|<span data-ttu-id="7f09d-129">Określa nazwę użytkownika, który ma być używany do uwierzytelniania na serwerze poczty SMTP.</span><span class="sxs-lookup"><span data-stu-id="7f09d-129">Specifies the user name to use for authentication to the SMTP mail server.</span></span> <span data-ttu-id="7f09d-130">Ten atrybut nie ma wartości domyślnej.</span><span class="sxs-lookup"><span data-stu-id="7f09d-130">This attribute has no default value.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7f09d-131">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="7f09d-131">Child Elements</span></span>  
 <span data-ttu-id="7f09d-132">Brak.</span><span class="sxs-lookup"><span data-stu-id="7f09d-132">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7f09d-133">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="7f09d-133">Parent Elements</span></span>  
  
|<span data-ttu-id="7f09d-134">Element</span><span class="sxs-lookup"><span data-stu-id="7f09d-134">Element</span></span>|<span data-ttu-id="7f09d-135">Opis</span><span class="sxs-lookup"><span data-stu-id="7f09d-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7f09d-136">\<> SMTP — element (Ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="7f09d-136">\<smtp> Element (Network Settings)</span></span>](smtp-element-network-settings.md)|<span data-ttu-id="7f09d-137">Konfiguruje opcje wysyłania poczty SMTP (Simple Mail Transport Protocol).</span><span class="sxs-lookup"><span data-stu-id="7f09d-137">Configures Simple Mail Transport Protocol (SMTP) mail sending options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7f09d-138">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7f09d-138">Remarks</span></span>  
 <span data-ttu-id="7f09d-139">Niektóre serwery SMTP wymagają uwierzytelnienia na serwerze przed użyciem.</span><span class="sxs-lookup"><span data-stu-id="7f09d-139">Some SMTP servers require that you authenticate yourself to the server before use.</span></span> <span data-ttu-id="7f09d-140">Aby uwierzytelnić się samodzielnie przy użyciu domyślnych poświadczeń sieciowych na hoście, należy ustawić `defaultCredentials` atrybut na. `true`</span><span class="sxs-lookup"><span data-stu-id="7f09d-140">If you want to authenticate yourself using the default network credentials on your host, set the `defaultCredentials` attribute to `true`.</span></span> <span data-ttu-id="7f09d-141">Właściwość może służyć do uzyskiwania bieżącej wartości `defaultCredentials` atrybutu z odpowiednich plików konfiguracji. <xref:System.Net.Configuration.SmtpNetworkElement.DefaultCredentials%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="7f09d-141">The <xref:System.Net.Configuration.SmtpNetworkElement.DefaultCredentials%2A?displayProperty=nameWithType> property can be used to get the current value of the `defaultCredentials` attribute from applicable configuration files.</span></span>  
  
 <span data-ttu-id="7f09d-142">Możesz również użyć uwierzytelniania podstawowego (nazwy użytkownika i hasła), aby uwierzytelnić się na serwerze SMTP.</span><span class="sxs-lookup"><span data-stu-id="7f09d-142">You can also use basic authentication (a user name and password) to authenticate yourself to the SMTP server.</span></span> <span data-ttu-id="7f09d-143">Aby użyć tej opcji, należy określić prawidłową nazwę użytkownika i hasło dla określonego serwera SMTP.</span><span class="sxs-lookup"><span data-stu-id="7f09d-143">To use this option, you must specify a valid user name and password for the specified SMTP server.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7f09d-144">Uwierzytelnianie podstawowe wysyła `userName` wartości i `password` do nieszyfrowanego serwera.</span><span class="sxs-lookup"><span data-stu-id="7f09d-144">Basic authentication sends the `userName` and `password` values to the server unencrypted.</span></span> <span data-ttu-id="7f09d-145">Każdy może monitorować ruch sieciowy i używać ich do łączenia się z serwerem.</span><span class="sxs-lookup"><span data-stu-id="7f09d-145">Anyone monitoring network traffic can view your credentials and use them to connect to the server.</span></span> <span data-ttu-id="7f09d-146">Należy rozważyć użycie bezpieczniejszego mechanizmu uwierzytelniania, takiego jak Kerberos lub NT LAN Manager (NTLM). Jeśli `defaultCredentials` jest `true`, zostanie użyta wartość Kerberos lub NTLM, jeśli serwer obsługuje te protokoły.</span><span class="sxs-lookup"><span data-stu-id="7f09d-146">You should consider using a more secure authentication mechanism, such as Kerberos or NT LAN Manager (NTLM.) If `defaultCredentials` is `true`, Kerberos or NTLM will be used if the server supports these protocols.</span></span>  
  
 <span data-ttu-id="7f09d-147">Opcje uwierzytelniania podstawowego i domyślne poświadczenia sieciowe wzajemnie się wykluczają; Jeśli ustawisz `defaultCredentials` `true` i określisz nazwę użytkownika i hasło, zostanie użyte domyślne poświadczenia sieci, a podstawowe dane uwierzytelniania zostaną zignorowane.</span><span class="sxs-lookup"><span data-stu-id="7f09d-147">The basic authentication and default network credentials options are mutually exclusive; if you set `defaultCredentials` to `true` and specify a user name and password, the default network credential is used, and the basic authentication data is ignored.</span></span>  
  
 <span data-ttu-id="7f09d-148">W przypadku uwierzytelniania `userName`podstawowego należy również `password` określić uwierzytelnianie na serwerze poczty.</span><span class="sxs-lookup"><span data-stu-id="7f09d-148">For basic authentication if you specify a `userName`, you should also specify a `password` to authentication yourself to the mail server.</span></span>  
  
 <span data-ttu-id="7f09d-149">Właściwość może służyć do uzyskiwania bieżącej wartości `userName` atrybutu z odpowiednich plików konfiguracji. <xref:System.Net.Configuration.SmtpNetworkElement.UserName%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="7f09d-149">The <xref:System.Net.Configuration.SmtpNetworkElement.UserName%2A?displayProperty=nameWithType> property can be used to get the current value of the `userName` attribute from applicable configuration files.</span></span> <span data-ttu-id="7f09d-150">Właściwość może służyć do uzyskiwania bieżącej wartości `password` atrybutu z odpowiednich plików konfiguracji. <xref:System.Net.Configuration.SmtpNetworkElement.Password%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="7f09d-150">The <xref:System.Net.Configuration.SmtpNetworkElement.Password%2A?displayProperty=nameWithType> property can be used to get the current value of the `password` attribute from applicable configuration files.</span></span> <span data-ttu-id="7f09d-151">`password` Atrybut nie jest zwykle wprowadzany w plikach konfiguracyjnych ze względów bezpieczeństwa.</span><span class="sxs-lookup"><span data-stu-id="7f09d-151">A `password` attribute would not normally be entered in configuration files for security reasons.</span></span>  
  
 <span data-ttu-id="7f09d-152">Ten `clientDomain` atrybut zmienia nazwę domeny klienta używaną w początkowym żądaniu protokołu SMTP na serwerze SMTP.</span><span class="sxs-lookup"><span data-stu-id="7f09d-152">The `clientDomain` attribute changes the client domain name used in the initial SMTP protocol request to an SMTP server.</span></span> <span data-ttu-id="7f09d-153">Ten `clientDomain` atrybut może być ustawiony na w pełni kwalifikowaną nazwę domeny komputera lokalnego zamiast nazwy hosta lokalnego, która jest używana domyślnie.</span><span class="sxs-lookup"><span data-stu-id="7f09d-153">The `clientDomain` attribute can be set to the fully-qualified domain name of the local machine, rather than the localhost name that is used by default.</span></span> <span data-ttu-id="7f09d-154">Zapewnia to lepszą zgodność ze standardami protokołu SMTP.</span><span class="sxs-lookup"><span data-stu-id="7f09d-154">This provides greater compliance with the SMTP protocol standards.</span></span> <span data-ttu-id="7f09d-155">Wartość domyślna to nazwa localhost komputera lokalnego wysyłającego żądanie.</span><span class="sxs-lookup"><span data-stu-id="7f09d-155">The default value is the localhost name of the local computer sending the request.</span></span> <span data-ttu-id="7f09d-156">Właściwość może służyć do uzyskiwania bieżącej wartości `clientDomain` atrybutu z odpowiednich plików konfiguracji. <xref:System.Net.Configuration.SmtpNetworkElement.ClientDomain%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="7f09d-156">The <xref:System.Net.Configuration.SmtpNetworkElement.ClientDomain%2A?displayProperty=nameWithType> property can be used to get the current value of the `clientDomain` attribute from applicable configuration files.</span></span>  
  
 <span data-ttu-id="7f09d-157">Ten `targetName` atrybut jest używany do uwierzytelniania w przypadku korzystania z ochrony rozszerzonej.</span><span class="sxs-lookup"><span data-stu-id="7f09d-157">The `targetName` attribute is used for authentication when using extended protection.</span></span> <span data-ttu-id="7f09d-158">Wartość domyślna ma postać "SMTPSVC/\<Host >", gdzie \<Host > jest nazwą hosta serwera poczty SMTP.</span><span class="sxs-lookup"><span data-stu-id="7f09d-158">The default value is of the form "SMTPSVC/\<host>" where \<host> is the hostname of the SMTP mail server.</span></span> <span data-ttu-id="7f09d-159">Właściwość może służyć do uzyskiwania bieżącej wartości `targetName` atrybutu z odpowiednich plików konfiguracji. <xref:System.Net.Configuration.SmtpNetworkElement.TargetName%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="7f09d-159">The <xref:System.Net.Configuration.SmtpNetworkElement.TargetName%2A?displayProperty=nameWithType> property can be used to get the current value of the `targetName` attribute from applicable configuration files.</span></span>  
  
 <span data-ttu-id="7f09d-160">Ten `enableSsl` atrybut określa, czy protokół SSL jest używany do uzyskiwania dostępu do serwera poczty SMTP.</span><span class="sxs-lookup"><span data-stu-id="7f09d-160">The `enableSsl` attribute specifies whether SSL is used to access an SMTP mail server.</span></span> <span data-ttu-id="7f09d-161"><xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType> Klasa obsługuje tylko rozszerzenie usługi SMTP dla bezpiecznego protokołu SMTP dla Transport Layer Security zgodnie z definicją w dokumencie RFC 3207.</span><span class="sxs-lookup"><span data-stu-id="7f09d-161">The <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType> class only supports the SMTP Service Extension for Secure SMTP over Transport Layer Security as defined in RFC 3207.</span></span> <span data-ttu-id="7f09d-162">W tym trybie sesja SMTP rozpoczyna się na nieszyfrowanym kanale, a następnie polecenie STARTTLS zostaje wystawione przez klienta na serwer w celu przełączenia do bezpiecznej komunikacji przy użyciu protokołu SSL.</span><span class="sxs-lookup"><span data-stu-id="7f09d-162">In this mode, the SMTP session begins on an unencrypted channel, then a STARTTLS command is issued by the client to the server to switch to secure communication using SSL.</span></span> <span data-ttu-id="7f09d-163">Więcej informacji można znaleźć w dokumencie RFC 3207 opublikowanym przez Internet Engineering Task Force (IETF).</span><span class="sxs-lookup"><span data-stu-id="7f09d-163">See RFC 3207 published by the Internet Engineering Task Force (IETF) for more information.</span></span>  
  
 <span data-ttu-id="7f09d-164">Alternatywna metoda połączenia polega na tym, że sesja SSL jest ustanawiana przed wysłaniem jakichkolwiek poleceń protokołu.</span><span class="sxs-lookup"><span data-stu-id="7f09d-164">An alternate connection method is where an SSL session is established up front before any protocol commands are sent.</span></span> <span data-ttu-id="7f09d-165">Ta metoda połączenia jest czasami nazywana protokołami SMTP i domyślnie używa portu 465.</span><span class="sxs-lookup"><span data-stu-id="7f09d-165">This connection method is sometimes called SMTPS and by default uses port 465.</span></span> <span data-ttu-id="7f09d-166">Ta alternatywna metoda łączenia przy użyciu protokołu SSL nie jest obecnie obsługiwana.</span><span class="sxs-lookup"><span data-stu-id="7f09d-166">This alternate connection method using SSL is not currently supported.</span></span>  
  
 <span data-ttu-id="7f09d-167">Właściwość może służyć do uzyskiwania bieżącej wartości `enableSsl` atrybutu z odpowiednich plików konfiguracji. <xref:System.Net.Configuration.SmtpNetworkElement.EnableSsl%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="7f09d-167">The <xref:System.Net.Configuration.SmtpNetworkElement.EnableSsl%2A?displayProperty=nameWithType> property can be used to get the current value of the `enableSsl` attribute from applicable configuration files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7f09d-168">Przykład</span><span class="sxs-lookup"><span data-stu-id="7f09d-168">Example</span></span>  
 <span data-ttu-id="7f09d-169">W poniższym przykładzie określono odpowiednie parametry SMTP do wysyłania wiadomości e-mail przy użyciu domyślnych poświadczeń sieciowych.</span><span class="sxs-lookup"><span data-stu-id="7f09d-169">The following example specifies the appropriate SMTP parameters to send email using the default network credentials.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <mailSettings>  
      <smtp deliveryMethod="Network">  
        <network  
          clientDomain="www.contoso.com"  
          defaultCredentials="true"  
          enableSsl="false"  
          host="mail.contoso.com"  
          port="25"  
        />  
      </smtp>  
    </mailSettings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7f09d-170">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7f09d-170">See also</span></span>

- <xref:System.Net.Configuration.SmtpNetworkElement?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- [<span data-ttu-id="7f09d-171">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="7f09d-171">Network Settings Schema</span></span>](index.md)
