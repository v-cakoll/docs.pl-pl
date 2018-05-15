---
title: '&lt;sieci&gt; elementu (ustawienia sieciowe)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#network
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings/smtp/network
helpviewer_keywords:
- <network> element
- network element
ms.assetid: 2c2c6ad4-ed11-48ab-b28e-2bc0ba9b42c7
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: e53d39f15a01f751a93c5531b3079d77bf0040e4
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltnetworkgt-element-network-settings"></a><span data-ttu-id="48067-102">&lt;sieci&gt; elementu (ustawienia sieciowe)</span><span class="sxs-lookup"><span data-stu-id="48067-102">&lt;network&gt; Element (Network Settings)</span></span>
<span data-ttu-id="48067-103">Służy do konfigurowania opcji sieciowych do zewnętrznego serwera transportu protokołu SMTP (Simple Mail).</span><span class="sxs-lookup"><span data-stu-id="48067-103">Configures the network options for an external Simple Mail Transport Protocol (SMTP) server.</span></span>  
  
 <span data-ttu-id="48067-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="48067-104">\<configuration></span></span>  
<span data-ttu-id="48067-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="48067-105">\<system.net></span></span>  
<span data-ttu-id="48067-106">\<mailSettings></span><span class="sxs-lookup"><span data-stu-id="48067-106">\<mailSettings></span></span>  
<span data-ttu-id="48067-107">\<smtp></span><span class="sxs-lookup"><span data-stu-id="48067-107">\<smtp></span></span>  
<span data-ttu-id="48067-108">\<network></span><span class="sxs-lookup"><span data-stu-id="48067-108">\<network></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48067-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="48067-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="48067-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="48067-110">Attributes and Elements</span></span>  
 <span data-ttu-id="48067-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="48067-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="48067-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="48067-112">Attributes</span></span>  
  
|<span data-ttu-id="48067-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="48067-113">Attribute</span></span>|<span data-ttu-id="48067-114">Opis</span><span class="sxs-lookup"><span data-stu-id="48067-114">Description</span></span>|  
|---------------|-----------------|  
|`clientDomain`|<span data-ttu-id="48067-115">Określa nazwę domeny klienta do użycia w początkowe żądanie protokołu SMTP, aby nawiązać połączenie z serwerem poczty SMTP.</span><span class="sxs-lookup"><span data-stu-id="48067-115">Specifies the client domain name to use in the initial SMTP protocol request to connect to the SMTP mail server.</span></span> <span data-ttu-id="48067-116">Wartość domyślna to nazwa hosta lokalnego komputera lokalnego wysyłania żądania.</span><span class="sxs-lookup"><span data-stu-id="48067-116">The default value is the localhost name of the local computer sending the request.</span></span>|  
|`defaultCredentials`|<span data-ttu-id="48067-117">Określa, czy domyślne poświadczenia użytkownika powinny być używane do uzyskania dostępu do serwera poczty SMTP dla transakcji SMTP.</span><span class="sxs-lookup"><span data-stu-id="48067-117">Specifies whether the default user credentials should be used to access the SMTP mail server for SMTP transactions.</span></span> <span data-ttu-id="48067-118">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="48067-118">The default value is `false`.</span></span>|  
|`enableSsl`|<span data-ttu-id="48067-119">Określa, czy dostęp do serwera poczty SMTP używany jest protokół SSL.</span><span class="sxs-lookup"><span data-stu-id="48067-119">Specifies whether SSL is used to access an SMTP mail server.</span></span> <span data-ttu-id="48067-120">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="48067-120">The default value is `false`.</span></span>|  
|`host`|<span data-ttu-id="48067-121">Określa nazwę hosta serwera poczty SMTP, który ma być używany dla transakcji SMTP.</span><span class="sxs-lookup"><span data-stu-id="48067-121">Specifies the hostname of the SMTP mail server to use for SMTP transactions.</span></span> <span data-ttu-id="48067-122">Ten atrybut nie ma wartości domyślnej.</span><span class="sxs-lookup"><span data-stu-id="48067-122">This attribute has no default value.</span></span>|  
|`password`|<span data-ttu-id="48067-123">Określa hasło używane do uwierzytelniania serwera poczty SMTP.</span><span class="sxs-lookup"><span data-stu-id="48067-123">Specifies the password to use for authentication to the SMTP mail server.</span></span> <span data-ttu-id="48067-124">Ten atrybut nie ma wartości domyślnej.</span><span class="sxs-lookup"><span data-stu-id="48067-124">This attribute has no default value.</span></span>|  
|`port`|<span data-ttu-id="48067-125">Określa numer portu na potrzeby nawiązania połączenia z serwerem poczty SMTP.</span><span class="sxs-lookup"><span data-stu-id="48067-125">Specifies the port number to use to connect to the SMTP mail server.</span></span> <span data-ttu-id="48067-126">Wartość domyślna to 25.</span><span class="sxs-lookup"><span data-stu-id="48067-126">The default value is 25.</span></span>|  
|`targetName`|<span data-ttu-id="48067-127">Określa nazwę dostawcy usługi (SPN) na potrzeby uwierzytelniania w przypadku używania ochrony rozszerzonej dla transakcji SMTP.</span><span class="sxs-lookup"><span data-stu-id="48067-127">Specifies the Service Provider Name (SPN) to use for authentication when using extended protection for SMTP transactions.</span></span> <span data-ttu-id="48067-128">Ten atrybut nie ma wartości domyślnej.</span><span class="sxs-lookup"><span data-stu-id="48067-128">This attribute has no default value.</span></span>|  
|`userName`|<span data-ttu-id="48067-129">Określa nazwę użytkownika do uwierzytelniania z serwerem poczty SMTP.</span><span class="sxs-lookup"><span data-stu-id="48067-129">Specifies the user name to use for authentication to the SMTP mail server.</span></span> <span data-ttu-id="48067-130">Ten atrybut nie ma wartości domyślnej.</span><span class="sxs-lookup"><span data-stu-id="48067-130">This attribute has no default value.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="48067-131">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="48067-131">Child Elements</span></span>  
 <span data-ttu-id="48067-132">Brak.</span><span class="sxs-lookup"><span data-stu-id="48067-132">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="48067-133">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="48067-133">Parent Elements</span></span>  
  
|<span data-ttu-id="48067-134">Element</span><span class="sxs-lookup"><span data-stu-id="48067-134">Element</span></span>|<span data-ttu-id="48067-135">Opis</span><span class="sxs-lookup"><span data-stu-id="48067-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="48067-136">\<SMTP > elementu (ustawienia sieciowe)</span><span class="sxs-lookup"><span data-stu-id="48067-136">\<smtp> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/smtp-element-network-settings.md)|<span data-ttu-id="48067-137">Konfiguruje opcje wysyłania poczty transportu protokołu SMTP (Simple Mail).</span><span class="sxs-lookup"><span data-stu-id="48067-137">Configures Simple Mail Transport Protocol (SMTP) mail sending options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="48067-138">Uwagi</span><span class="sxs-lookup"><span data-stu-id="48067-138">Remarks</span></span>  
 <span data-ttu-id="48067-139">Niektóre serwery SMTP wymagają uwierzytelnienia użytkownika na serwerze przed użyciem.</span><span class="sxs-lookup"><span data-stu-id="48067-139">Some SMTP servers require that you authenticate yourself to the server before use.</span></span> <span data-ttu-id="48067-140">Jeśli chcesz uwierzytelnienia przy użyciu domyślnych poświadczeń sieci na hoście, ustaw `defaultCredentials` atrybutu `true`.</span><span class="sxs-lookup"><span data-stu-id="48067-140">If you want to authenticate yourself using the default network credentials on your host, set the `defaultCredentials` attribute to `true`.</span></span> <span data-ttu-id="48067-141"><xref:System.Net.Configuration.SmtpNetworkElement.DefaultCredentials%2A?displayProperty=nameWithType> Właściwości można pobrać wartości bieżącego `defaultCredentials` atrybutu z plików zastosowania konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="48067-141">The <xref:System.Net.Configuration.SmtpNetworkElement.DefaultCredentials%2A?displayProperty=nameWithType> property can be used to get the current value of the `defaultCredentials` attribute from applicable configuration files.</span></span>  
  
 <span data-ttu-id="48067-142">Można również użyć uwierzytelnianie podstawowe (nazwa użytkownika i hasło) do uwierzytelniania osoby do serwera SMTP.</span><span class="sxs-lookup"><span data-stu-id="48067-142">You can also use basic authentication (a user name and password) to authenticate yourself to the SMTP server.</span></span> <span data-ttu-id="48067-143">Aby użyć tej opcji, należy określić prawidłową nazwę użytkownika i hasło dla określonego serwera SMTP.</span><span class="sxs-lookup"><span data-stu-id="48067-143">To use this option, you must specify a valid user name and password for the specified SMTP server.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="48067-144">Uwierzytelnianie podstawowe przesyła `userName` i `password` wartości do serwera bez szyfrowania.</span><span class="sxs-lookup"><span data-stu-id="48067-144">Basic authentication sends the `userName` and `password` values to the server unencrypted.</span></span> <span data-ttu-id="48067-145">Każda osoba, która monitorowanie ruchu w sieci można wyświetlać swoje poświadczenia i ich używać do łączenia się z serwerem.</span><span class="sxs-lookup"><span data-stu-id="48067-145">Anyone monitoring network traffic can view your credentials and use them to connect to the server.</span></span> <span data-ttu-id="48067-146">Należy rozważyć zastosowanie bardziej bezpieczne mechanizm uwierzytelniania, takie jak Kerberos lub programu NT LAN Manager (NTLM). Jeśli `defaultCredentials` jest `true`, protokołu Kerberos lub NTLM zostaną użyte, jeśli serwer obsługuje te protokoły.</span><span class="sxs-lookup"><span data-stu-id="48067-146">You should consider using a more secure authentication mechanism, such as Kerberos or NT LAN Manager (NTLM.) If `defaultCredentials` is `true`, Kerberos or NTLM will be used if the server supports these protocols.</span></span>  
  
 <span data-ttu-id="48067-147">Podstawowe opcje poświadczenia sieci uwierzytelniania i domyślne wykluczają się wzajemnie; Jeśli ustawisz `defaultCredentials` do `true` i określ nazwę użytkownika i hasło, domyślnych poświadczeń sieciowych jest używany i danych uwierzytelniania podstawowego jest ignorowana.</span><span class="sxs-lookup"><span data-stu-id="48067-147">The basic authentication and default network credentials options are mutually exclusive; if you set `defaultCredentials` to `true` and specify a user name and password, the default network credential is used, and the basic authentication data is ignored.</span></span>  
  
 <span data-ttu-id="48067-148">Dla uwierzytelniania podstawowego w przypadku określenia `userName`, należy określić również `password` uwierzytelnienia do serwera poczty.</span><span class="sxs-lookup"><span data-stu-id="48067-148">For basic authentication if you specify a `userName`, you should also specify a `password` to authentication yourself to the mail server.</span></span>  
  
 <span data-ttu-id="48067-149"><xref:System.Net.Configuration.SmtpNetworkElement.UserName%2A?displayProperty=nameWithType> Właściwości można pobrać wartości bieżącego `userName` atrybutu z plików zastosowania konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="48067-149">The <xref:System.Net.Configuration.SmtpNetworkElement.UserName%2A?displayProperty=nameWithType> property can be used to get the current value of the `userName` attribute from applicable configuration files.</span></span> <span data-ttu-id="48067-150"><xref:System.Net.Configuration.SmtpNetworkElement.Password%2A?displayProperty=nameWithType> Właściwości można pobrać wartości bieżącego `password` atrybutu z plików zastosowania konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="48067-150">The <xref:System.Net.Configuration.SmtpNetworkElement.Password%2A?displayProperty=nameWithType> property can be used to get the current value of the `password` attribute from applicable configuration files.</span></span> <span data-ttu-id="48067-151">A `password` atrybutu nie zwykle zostaną wprowadzone w plikach konfiguracji ze względów bezpieczeństwa.</span><span class="sxs-lookup"><span data-stu-id="48067-151">A `password` attribute would not normally be entered in configuration files for security reasons.</span></span>  
  
 <span data-ttu-id="48067-152">`clientDomain` Atrybut zmiany nazwy domeny klienta używany w początkowej żądania protokołu SMTP do serwera SMTP.</span><span class="sxs-lookup"><span data-stu-id="48067-152">The `clientDomain` attribute changes the client domain name used in the initial SMTP protocol request to an SMTP server.</span></span> <span data-ttu-id="48067-153">`clientDomain` Atrybut można określać do w pełni kwalifikowaną nazwą domeny komputera lokalnego, a nie nazwy localhost, który jest używany domyślnie.</span><span class="sxs-lookup"><span data-stu-id="48067-153">The `clientDomain` attribute can be set to the fully-qualified domain name of the local machine, rather than the localhost name that is used by default.</span></span> <span data-ttu-id="48067-154">Zapewnia to większą zgodności ze standardami protokołu SMTP.</span><span class="sxs-lookup"><span data-stu-id="48067-154">This provides greater compliance with the SMTP protocol standards.</span></span> <span data-ttu-id="48067-155">Wartość domyślna to nazwa hosta lokalnego komputera lokalnego wysyłania żądania.</span><span class="sxs-lookup"><span data-stu-id="48067-155">The default value is the localhost name of the local computer sending the request.</span></span> <span data-ttu-id="48067-156"><xref:System.Net.Configuration.SmtpNetworkElement.ClientDomain%2A?displayProperty=nameWithType> Właściwości można pobrać wartości bieżącego `clientDomain` atrybutu z plików zastosowania konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="48067-156">The <xref:System.Net.Configuration.SmtpNetworkElement.ClientDomain%2A?displayProperty=nameWithType> property can be used to get the current value of the `clientDomain` attribute from applicable configuration files.</span></span>  
  
 <span data-ttu-id="48067-157">`targetName` Atrybut jest używany do uwierzytelniania, korzystając z ochrony rozszerzonej.</span><span class="sxs-lookup"><span data-stu-id="48067-157">The `targetName` attribute is used for authentication when using extended protection.</span></span> <span data-ttu-id="48067-158">Wartość domyślna to w postaci "SMTPSVC /\<hosta >" gdzie \<hosta > jest nazwą hosta serwera poczty SMTP.</span><span class="sxs-lookup"><span data-stu-id="48067-158">The default value is of the form "SMTPSVC/\<host>" where \<host> is the hostname of the SMTP mail server.</span></span> <span data-ttu-id="48067-159"><xref:System.Net.Configuration.SmtpNetworkElement.TargetName%2A?displayProperty=nameWithType> Właściwości można pobrać wartości bieżącego `targetName` atrybutu z plików zastosowania konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="48067-159">The <xref:System.Net.Configuration.SmtpNetworkElement.TargetName%2A?displayProperty=nameWithType> property can be used to get the current value of the `targetName` attribute from applicable configuration files.</span></span>  
  
 <span data-ttu-id="48067-160">`enableSsl` Atrybut określa, czy dostęp do serwera poczty SMTP używany jest protokół SSL.</span><span class="sxs-lookup"><span data-stu-id="48067-160">The `enableSsl` attribute specifies whether SSL is used to access an SMTP mail server.</span></span> <span data-ttu-id="48067-161"><xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType> Klasa obsługuje tylko rozszerzenia usługi SMTP dla zabezpieczenia SMTP za pośrednictwem zabezpieczeń warstwy transportu zgodnie z definicją w dokumencie RFC 3207.</span><span class="sxs-lookup"><span data-stu-id="48067-161">The <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType> class only supports the SMTP Service Extension for Secure SMTP over Transport Layer Security as defined in RFC 3207.</span></span> <span data-ttu-id="48067-162">W tym trybie sesji SMTP zaczyna się od nieszyfrowany kanał, a następnie polecenie STARTTLS wystawiony przez klienta do serwera, aby przełączyć się do zapewnienia bezpiecznej komunikacji przy użyciu protokołu SSL.</span><span class="sxs-lookup"><span data-stu-id="48067-162">In this mode, the SMTP session begins on an unencrypted channel, then a STARTTLS command is issued by the client to the server to switch to secure communication using SSL.</span></span> <span data-ttu-id="48067-163">Zobacz dokument RFC 3207 opublikowane przez Internet Engineering Task Force (IETF) Aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="48067-163">See RFC 3207 published by the Internet Engineering Task Force (IETF) for more information.</span></span>  
  
 <span data-ttu-id="48067-164">Metoda alternatywnego połączenia jest, gdzie sesji SSL nawiązaniu góry przed każdego protokołu, które polecenia są wysyłane.</span><span class="sxs-lookup"><span data-stu-id="48067-164">An alternate connection method is where an SSL session is established up front before any protocol commands are sent.</span></span> <span data-ttu-id="48067-165">Ta metoda łączenia jest czasami nazywany SMTPS i domyślnie używa portu 465.</span><span class="sxs-lookup"><span data-stu-id="48067-165">This connection method is sometimes called SMTPS and by default uses port 465.</span></span> <span data-ttu-id="48067-166">Ta metoda alternatywnego połączenia przy użyciu protokołu SSL nie jest obecnie obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="48067-166">This alternate connection method using SSL is not currently supported.</span></span>  
  
 <span data-ttu-id="48067-167"><xref:System.Net.Configuration.SmtpNetworkElement.EnableSsl%2A?displayProperty=nameWithType> Właściwości można pobrać wartości bieżącego `enableSsl` atrybutu z plików zastosowania konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="48067-167">The <xref:System.Net.Configuration.SmtpNetworkElement.EnableSsl%2A?displayProperty=nameWithType> property can be used to get the current value of the `enableSsl` attribute from applicable configuration files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="48067-168">Przykład</span><span class="sxs-lookup"><span data-stu-id="48067-168">Example</span></span>  
 <span data-ttu-id="48067-169">W poniższym przykładzie odpowiednie parametry SMTP do wysyłania wiadomości e-mail przy użyciu poświadczeń domyślnych w sieci.</span><span class="sxs-lookup"><span data-stu-id="48067-169">The following example specifies the appropriate SMTP parameters to send email using the default network credentials.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <mailSettings>  
      <smtp deliveryMethod="network">  
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
  
## <a name="see-also"></a><span data-ttu-id="48067-170">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="48067-170">See Also</span></span>  
 <xref:System.Net.Configuration.SmtpNetworkElement?displayProperty=nameWithType>  
 <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>  
 <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>  
 [<span data-ttu-id="48067-171">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="48067-171">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
