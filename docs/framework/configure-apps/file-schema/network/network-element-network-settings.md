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
ms.openlocfilehash: f7cfcc3b9d5a717c23175cd15aa48ae97c828e57
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154819"
---
# <a name="network-element-network-settings"></a><span data-ttu-id="9dae5-102">\<element> sieci (ustawienia sieciowe)</span><span class="sxs-lookup"><span data-stu-id="9dae5-102">\<network> Element (Network Settings)</span></span>
<span data-ttu-id="9dae5-103">Konfiguruje opcje sieciowe zewnętrznego serwera SMTP (Simple Mail Transport Protocol).</span><span class="sxs-lookup"><span data-stu-id="9dae5-103">Configures the network options for an external Simple Mail Transport Protocol (SMTP) server.</span></span>  

<span data-ttu-id="9dae5-104">[**\<>konfiguracyjne**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="9dae5-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="9dae5-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="9dae5-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="9dae5-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<mailSettings>**](mailsettings-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="9dae5-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<mailSettings>**](mailsettings-element-network-settings.md)</span></span>\
<span data-ttu-id="9dae5-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>smtp**](smtp-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="9dae5-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<smtp>**](smtp-element-network-settings.md)</span></span>\
<span data-ttu-id="9dae5-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<>sieci**</span><span class="sxs-lookup"><span data-stu-id="9dae5-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<network>**</span></span>

## <a name="syntax"></a><span data-ttu-id="9dae5-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="9dae5-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9dae5-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="9dae5-110">Attributes and Elements</span></span>  
 <span data-ttu-id="9dae5-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="9dae5-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9dae5-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="9dae5-112">Attributes</span></span>  
  
|<span data-ttu-id="9dae5-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="9dae5-113">Attribute</span></span>|<span data-ttu-id="9dae5-114">Opis</span><span class="sxs-lookup"><span data-stu-id="9dae5-114">Description</span></span>|  
|---------------|-----------------|  
|`clientDomain`|<span data-ttu-id="9dae5-115">Określa nazwę domeny klienta, która ma być używana w początkowym żądaniu protokołu SMTP do łączenia się z serwerem poczty SMTP.</span><span class="sxs-lookup"><span data-stu-id="9dae5-115">Specifies the client domain name to use in the initial SMTP protocol request to connect to the SMTP mail server.</span></span> <span data-ttu-id="9dae5-116">Wartością domyślną jest nazwa hosta lokalnego komputera lokalnego wysyłającego żądanie.</span><span class="sxs-lookup"><span data-stu-id="9dae5-116">The default value is the localhost name of the local computer sending the request.</span></span>|  
|`defaultCredentials`|<span data-ttu-id="9dae5-117">Określa, czy domyślne poświadczenia użytkownika mają być używane do uzyskiwania dostępu do serwera poczty SMTP dla transakcji SMTP.</span><span class="sxs-lookup"><span data-stu-id="9dae5-117">Specifies whether the default user credentials should be used to access the SMTP mail server for SMTP transactions.</span></span> <span data-ttu-id="9dae5-118">Wartością domyślną jest `false`.</span><span class="sxs-lookup"><span data-stu-id="9dae5-118">The default value is `false`.</span></span>|  
|`enableSsl`|<span data-ttu-id="9dae5-119">Określa, czy protokół SSL jest używany do uzyskiwania dostępu do serwera poczty SMTP.</span><span class="sxs-lookup"><span data-stu-id="9dae5-119">Specifies whether SSL is used to access an SMTP mail server.</span></span> <span data-ttu-id="9dae5-120">Wartością domyślną jest `false`.</span><span class="sxs-lookup"><span data-stu-id="9dae5-120">The default value is `false`.</span></span>|  
|`host`|<span data-ttu-id="9dae5-121">Określa nazwa hosta serwera poczty SMTP, który ma być używany do obsługi transakcji SMTP.</span><span class="sxs-lookup"><span data-stu-id="9dae5-121">Specifies the hostname of the SMTP mail server to use for SMTP transactions.</span></span> <span data-ttu-id="9dae5-122">Ten atrybut nie ma wartości domyślnej.</span><span class="sxs-lookup"><span data-stu-id="9dae5-122">This attribute has no default value.</span></span>|  
|`password`|<span data-ttu-id="9dae5-123">Określa hasło używane do uwierzytelniania na serwerze poczty SMTP.</span><span class="sxs-lookup"><span data-stu-id="9dae5-123">Specifies the password to use for authentication to the SMTP mail server.</span></span> <span data-ttu-id="9dae5-124">Ten atrybut nie ma wartości domyślnej.</span><span class="sxs-lookup"><span data-stu-id="9dae5-124">This attribute has no default value.</span></span>|  
|`port`|<span data-ttu-id="9dae5-125">Określa numer portu, który ma być używany do łączenia się z serwerem poczty SMTP.</span><span class="sxs-lookup"><span data-stu-id="9dae5-125">Specifies the port number to use to connect to the SMTP mail server.</span></span> <span data-ttu-id="9dae5-126">Wartość domyślna to 25.</span><span class="sxs-lookup"><span data-stu-id="9dae5-126">The default value is 25.</span></span>|  
|`targetName`|<span data-ttu-id="9dae5-127">Określa nazwę dostawcy usług (SPN) do użycia do uwierzytelniania podczas korzystania z rozszerzonej ochrony transakcji SMTP.</span><span class="sxs-lookup"><span data-stu-id="9dae5-127">Specifies the Service Provider Name (SPN) to use for authentication when using extended protection for SMTP transactions.</span></span> <span data-ttu-id="9dae5-128">Ten atrybut nie ma wartości domyślnej.</span><span class="sxs-lookup"><span data-stu-id="9dae5-128">This attribute has no default value.</span></span>|  
|`userName`|<span data-ttu-id="9dae5-129">Określa nazwę użytkownika, która ma być używana do uwierzytelniania na serwerze poczty SMTP.</span><span class="sxs-lookup"><span data-stu-id="9dae5-129">Specifies the user name to use for authentication to the SMTP mail server.</span></span> <span data-ttu-id="9dae5-130">Ten atrybut nie ma wartości domyślnej.</span><span class="sxs-lookup"><span data-stu-id="9dae5-130">This attribute has no default value.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9dae5-131">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="9dae5-131">Child Elements</span></span>  
 <span data-ttu-id="9dae5-132">Brak.</span><span class="sxs-lookup"><span data-stu-id="9dae5-132">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9dae5-133">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="9dae5-133">Parent Elements</span></span>  
  
|<span data-ttu-id="9dae5-134">Element</span><span class="sxs-lookup"><span data-stu-id="9dae5-134">Element</span></span>|<span data-ttu-id="9dae5-135">Opis</span><span class="sxs-lookup"><span data-stu-id="9dae5-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9dae5-136">\<element> smtp (ustawienia sieciowe)</span><span class="sxs-lookup"><span data-stu-id="9dae5-136">\<smtp> Element (Network Settings)</span></span>](smtp-element-network-settings.md)|<span data-ttu-id="9dae5-137">Konfiguruje opcje wysyłania poczty SMTP (Simple Mail Transport Protocol).</span><span class="sxs-lookup"><span data-stu-id="9dae5-137">Configures Simple Mail Transport Protocol (SMTP) mail sending options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9dae5-138">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9dae5-138">Remarks</span></span>  
 <span data-ttu-id="9dae5-139">Niektóre serwery SMTP wymagają uwierzytelnienia się na serwerze przed użyciem.</span><span class="sxs-lookup"><span data-stu-id="9dae5-139">Some SMTP servers require that you authenticate yourself to the server before use.</span></span> <span data-ttu-id="9dae5-140">Jeśli chcesz uwierzytelnić się przy użyciu domyślnych poświadczeń sieciowych na hoście, ustaw `defaultCredentials` atrybut na `true`.</span><span class="sxs-lookup"><span data-stu-id="9dae5-140">If you want to authenticate yourself using the default network credentials on your host, set the `defaultCredentials` attribute to `true`.</span></span> <span data-ttu-id="9dae5-141">Właściwość <xref:System.Net.Configuration.SmtpNetworkElement.DefaultCredentials%2A?displayProperty=nameWithType> może służyć do uzyskania bieżącej wartości atrybutu `defaultCredentials` z odpowiednich plików konfiguracyjnych.</span><span class="sxs-lookup"><span data-stu-id="9dae5-141">The <xref:System.Net.Configuration.SmtpNetworkElement.DefaultCredentials%2A?displayProperty=nameWithType> property can be used to get the current value of the `defaultCredentials` attribute from applicable configuration files.</span></span>  
  
 <span data-ttu-id="9dae5-142">Można również użyć uwierzytelniania podstawowego (nazwy użytkownika i hasła) do uwierzytelniania się na serwerze SMTP.</span><span class="sxs-lookup"><span data-stu-id="9dae5-142">You can also use basic authentication (a user name and password) to authenticate yourself to the SMTP server.</span></span> <span data-ttu-id="9dae5-143">Aby użyć tej opcji, należy określić prawidłową nazwę użytkownika i hasło dla określonego serwera SMTP.</span><span class="sxs-lookup"><span data-stu-id="9dae5-143">To use this option, you must specify a valid user name and password for the specified SMTP server.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9dae5-144">Uwierzytelnianie podstawowe `userName` `password` wysyła wartości i wartości do serwera w stanie niezaszyfrowanym.</span><span class="sxs-lookup"><span data-stu-id="9dae5-144">Basic authentication sends the `userName` and `password` values to the server unencrypted.</span></span> <span data-ttu-id="9dae5-145">Każdy, kto monitoruje ruch sieciowy, może wyświetlać poświadczenia i używać ich do łączenia się z serwerem.</span><span class="sxs-lookup"><span data-stu-id="9dae5-145">Anyone monitoring network traffic can view your credentials and use them to connect to the server.</span></span> <span data-ttu-id="9dae5-146">Należy rozważyć użycie bezpieczniejszego mechanizmu uwierzytelniania, takiego jak Kerberos lub NT LAN Manager (NTLM). Jeśli `defaultCredentials` `true`tak , Kerberos lub NTLM będą używane, jeśli serwer obsługuje te protokoły.</span><span class="sxs-lookup"><span data-stu-id="9dae5-146">You should consider using a more secure authentication mechanism, such as Kerberos or NT LAN Manager (NTLM.) If `defaultCredentials` is `true`, Kerberos or NTLM will be used if the server supports these protocols.</span></span>  
  
 <span data-ttu-id="9dae5-147">Podstawowe uwierzytelnianie i domyślne opcje poświadczeń sieci wzajemnie się wykluczają; Jeśli `defaultCredentials` ustawiono `true` i określisz nazwę użytkownika i hasło, używane jest domyślne poświadczenie sieciowe, a podstawowe dane uwierzytelniania są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="9dae5-147">The basic authentication and default network credentials options are mutually exclusive; if you set `defaultCredentials` to `true` and specify a user name and password, the default network credential is used, and the basic authentication data is ignored.</span></span>  
  
 <span data-ttu-id="9dae5-148">W przypadku uwierzytelniania `userName`podstawowego, jeśli `password` określisz program , należy również określić uwierzytelnianie samodzielnie na serwerze poczty.</span><span class="sxs-lookup"><span data-stu-id="9dae5-148">For basic authentication if you specify a `userName`, you should also specify a `password` to authentication yourself to the mail server.</span></span>  
  
 <span data-ttu-id="9dae5-149">Właściwość <xref:System.Net.Configuration.SmtpNetworkElement.UserName%2A?displayProperty=nameWithType> może służyć do uzyskania bieżącej wartości atrybutu `userName` z odpowiednich plików konfiguracyjnych.</span><span class="sxs-lookup"><span data-stu-id="9dae5-149">The <xref:System.Net.Configuration.SmtpNetworkElement.UserName%2A?displayProperty=nameWithType> property can be used to get the current value of the `userName` attribute from applicable configuration files.</span></span> <span data-ttu-id="9dae5-150">Właściwość <xref:System.Net.Configuration.SmtpNetworkElement.Password%2A?displayProperty=nameWithType> może służyć do uzyskania bieżącej wartości atrybutu `password` z odpowiednich plików konfiguracyjnych.</span><span class="sxs-lookup"><span data-stu-id="9dae5-150">The <xref:System.Net.Configuration.SmtpNetworkElement.Password%2A?displayProperty=nameWithType> property can be used to get the current value of the `password` attribute from applicable configuration files.</span></span> <span data-ttu-id="9dae5-151">Atrybut `password` zwykle nie zostanie wprowadzony w plikach konfiguracyjnych ze względów bezpieczeństwa.</span><span class="sxs-lookup"><span data-stu-id="9dae5-151">A `password` attribute would not normally be entered in configuration files for security reasons.</span></span>  
  
 <span data-ttu-id="9dae5-152">Atrybut `clientDomain` zmienia nazwę domeny klienta używaną w początkowym żądaniu protokołu SMTP na serwerze SMTP.</span><span class="sxs-lookup"><span data-stu-id="9dae5-152">The `clientDomain` attribute changes the client domain name used in the initial SMTP protocol request to an SMTP server.</span></span> <span data-ttu-id="9dae5-153">Atrybut `clientDomain` można ustawić na w pełni kwalifikowaną nazwę domeny komputera lokalnego, a nie nazwę localhost, która jest używana domyślnie.</span><span class="sxs-lookup"><span data-stu-id="9dae5-153">The `clientDomain` attribute can be set to the fully-qualified domain name of the local machine, rather than the localhost name that is used by default.</span></span> <span data-ttu-id="9dae5-154">Zapewnia to większą zgodność ze standardami protokołu SMTP.</span><span class="sxs-lookup"><span data-stu-id="9dae5-154">This provides greater compliance with the SMTP protocol standards.</span></span> <span data-ttu-id="9dae5-155">Wartością domyślną jest nazwa hosta lokalnego komputera lokalnego wysyłającego żądanie.</span><span class="sxs-lookup"><span data-stu-id="9dae5-155">The default value is the localhost name of the local computer sending the request.</span></span> <span data-ttu-id="9dae5-156">Właściwość <xref:System.Net.Configuration.SmtpNetworkElement.ClientDomain%2A?displayProperty=nameWithType> może służyć do uzyskania bieżącej wartości atrybutu `clientDomain` z odpowiednich plików konfiguracyjnych.</span><span class="sxs-lookup"><span data-stu-id="9dae5-156">The <xref:System.Net.Configuration.SmtpNetworkElement.ClientDomain%2A?displayProperty=nameWithType> property can be used to get the current value of the `clientDomain` attribute from applicable configuration files.</span></span>  
  
 <span data-ttu-id="9dae5-157">Atrybut `targetName` jest używany do uwierzytelniania podczas korzystania z ochrony rozszerzonej.</span><span class="sxs-lookup"><span data-stu-id="9dae5-157">The `targetName` attribute is used for authentication when using extended protection.</span></span> <span data-ttu-id="9dae5-158">Wartością domyślną jest formularz "SMTPSVC/\<host>", w którym \<> hosta jest nazwa hosta serwera poczty SMTP.</span><span class="sxs-lookup"><span data-stu-id="9dae5-158">The default value is of the form "SMTPSVC/\<host>" where \<host> is the hostname of the SMTP mail server.</span></span> <span data-ttu-id="9dae5-159">Właściwość <xref:System.Net.Configuration.SmtpNetworkElement.TargetName%2A?displayProperty=nameWithType> może służyć do uzyskania bieżącej wartości atrybutu `targetName` z odpowiednich plików konfiguracyjnych.</span><span class="sxs-lookup"><span data-stu-id="9dae5-159">The <xref:System.Net.Configuration.SmtpNetworkElement.TargetName%2A?displayProperty=nameWithType> property can be used to get the current value of the `targetName` attribute from applicable configuration files.</span></span>  
  
 <span data-ttu-id="9dae5-160">Atrybut `enableSsl` określa, czy protokół SSL jest używany do uzyskiwania dostępu do serwera poczty SMTP.</span><span class="sxs-lookup"><span data-stu-id="9dae5-160">The `enableSsl` attribute specifies whether SSL is used to access an SMTP mail server.</span></span> <span data-ttu-id="9dae5-161">Klasa <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType> obsługuje tylko rozszerzenie usługi SMTP dla bezpiecznego protokołu SMTP za transport bezpieczeństwa warstwy zdefiniowane w RFC 3207.</span><span class="sxs-lookup"><span data-stu-id="9dae5-161">The <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType> class only supports the SMTP Service Extension for Secure SMTP over Transport Layer Security as defined in RFC 3207.</span></span> <span data-ttu-id="9dae5-162">W tym trybie sesja SMTP rozpoczyna się na kanale niezaszyfrowanym, a następnie klient wystawia na serwerze polecenie STARTTLS w celu przełączenia się do bezpiecznej komunikacji przy użyciu protokołu SSL.</span><span class="sxs-lookup"><span data-stu-id="9dae5-162">In this mode, the SMTP session begins on an unencrypted channel, then a STARTTLS command is issued by the client to the server to switch to secure communication using SSL.</span></span> <span data-ttu-id="9dae5-163">Zobacz RFC 3207 opublikowane przez Internet Engineering Task Force (IETF), aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="9dae5-163">See RFC 3207 published by the Internet Engineering Task Force (IETF) for more information.</span></span>  
  
 <span data-ttu-id="9dae5-164">Alternatywna metoda połączenia to miejsce, w którym sesja SSL jest ustanawiana z góry przed wysłaniem jakichkolwiek poleceń protokołu.</span><span class="sxs-lookup"><span data-stu-id="9dae5-164">An alternate connection method is where an SSL session is established up front before any protocol commands are sent.</span></span> <span data-ttu-id="9dae5-165">Ta metoda połączenia jest czasami nazywana SMTPS i domyślnie używa portu 465.</span><span class="sxs-lookup"><span data-stu-id="9dae5-165">This connection method is sometimes called SMTPS and by default uses port 465.</span></span> <span data-ttu-id="9dae5-166">Ta alternatywna metoda połączenia przy użyciu SSL nie jest obecnie obsługiwana.</span><span class="sxs-lookup"><span data-stu-id="9dae5-166">This alternate connection method using SSL is not currently supported.</span></span>  
  
 <span data-ttu-id="9dae5-167">Właściwość <xref:System.Net.Configuration.SmtpNetworkElement.EnableSsl%2A?displayProperty=nameWithType> może służyć do uzyskania bieżącej wartości atrybutu `enableSsl` z odpowiednich plików konfiguracyjnych.</span><span class="sxs-lookup"><span data-stu-id="9dae5-167">The <xref:System.Net.Configuration.SmtpNetworkElement.EnableSsl%2A?displayProperty=nameWithType> property can be used to get the current value of the `enableSsl` attribute from applicable configuration files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9dae5-168">Przykład</span><span class="sxs-lookup"><span data-stu-id="9dae5-168">Example</span></span>  
 <span data-ttu-id="9dae5-169">Poniższy przykład określa odpowiednie parametry SMTP do wysyłania wiadomości e-mail przy użyciu domyślnych poświadczeń sieci.</span><span class="sxs-lookup"><span data-stu-id="9dae5-169">The following example specifies the appropriate SMTP parameters to send email using the default network credentials.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9dae5-170">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9dae5-170">See also</span></span>

- <xref:System.Net.Configuration.SmtpNetworkElement?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- [<span data-ttu-id="9dae5-171">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="9dae5-171">Network Settings Schema</span></span>](index.md)
