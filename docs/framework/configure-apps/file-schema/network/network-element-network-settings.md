---
title: <network>, element (ustawienia sieci)
description: <network>Element ustawienia sieci służy do konfigurowania opcji sieci dla zewnętrznych opcji serwera SMTP w .NET Framework.
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#network
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings/smtp/network
helpviewer_keywords:
- <network> element
- network element
ms.assetid: 2c2c6ad4-ed11-48ab-b28e-2bc0ba9b42c7
ms.openlocfilehash: 36857e63871b4672df349934594f0887a042609e
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504553"
---
# <a name="network-element-network-settings"></a><span data-ttu-id="ff974-103">\<network>, element (ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="ff974-103">\<network> Element (Network Settings)</span></span>
<span data-ttu-id="ff974-104">Konfiguruje opcje sieci dla serwera zewnętrznego protokołu SMTP (Simple Mail Transport Protocol).</span><span class="sxs-lookup"><span data-stu-id="ff974-104">Configures the network options for an external Simple Mail Transport Protocol (SMTP) server.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<mailSettings>**](mailsettings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<smtp>**](smtp-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<network>**

## <a name="syntax"></a><span data-ttu-id="ff974-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="ff974-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ff974-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="ff974-106">Attributes and Elements</span></span>  
 <span data-ttu-id="ff974-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="ff974-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ff974-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="ff974-108">Attributes</span></span>  
  
|<span data-ttu-id="ff974-109">Atrybut</span><span class="sxs-lookup"><span data-stu-id="ff974-109">Attribute</span></span>|<span data-ttu-id="ff974-110">Opis</span><span class="sxs-lookup"><span data-stu-id="ff974-110">Description</span></span>|  
|---------------|-----------------|  
|`clientDomain`|<span data-ttu-id="ff974-111">Określa nazwę domeny klienta do użycia w początkowym żądaniu protokołu SMTP do nawiązania połączenia z serwerem poczty SMTP.</span><span class="sxs-lookup"><span data-stu-id="ff974-111">Specifies the client domain name to use in the initial SMTP protocol request to connect to the SMTP mail server.</span></span> <span data-ttu-id="ff974-112">Wartość domyślna to nazwa localhost komputera lokalnego wysyłającego żądanie.</span><span class="sxs-lookup"><span data-stu-id="ff974-112">The default value is the localhost name of the local computer sending the request.</span></span>|  
|`defaultCredentials`|<span data-ttu-id="ff974-113">Określa, czy domyślne poświadczenia użytkownika mają być używane do uzyskiwania dostępu do serwera poczty SMTP dla transakcji SMTP.</span><span class="sxs-lookup"><span data-stu-id="ff974-113">Specifies whether the default user credentials should be used to access the SMTP mail server for SMTP transactions.</span></span> <span data-ttu-id="ff974-114">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="ff974-114">The default value is `false`.</span></span>|  
|`enableSsl`|<span data-ttu-id="ff974-115">Określa, czy protokół SSL jest używany do uzyskiwania dostępu do serwera poczty SMTP.</span><span class="sxs-lookup"><span data-stu-id="ff974-115">Specifies whether SSL is used to access an SMTP mail server.</span></span> <span data-ttu-id="ff974-116">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="ff974-116">The default value is `false`.</span></span>|  
|`host`|<span data-ttu-id="ff974-117">Określa nazwę hosta serwera poczty SMTP, który ma być używany dla transakcji SMTP.</span><span class="sxs-lookup"><span data-stu-id="ff974-117">Specifies the hostname of the SMTP mail server to use for SMTP transactions.</span></span> <span data-ttu-id="ff974-118">Ten atrybut nie ma wartości domyślnej.</span><span class="sxs-lookup"><span data-stu-id="ff974-118">This attribute has no default value.</span></span>|  
|`password`|<span data-ttu-id="ff974-119">Określa hasło, które ma być używane do uwierzytelniania na serwerze poczty SMTP.</span><span class="sxs-lookup"><span data-stu-id="ff974-119">Specifies the password to use for authentication to the SMTP mail server.</span></span> <span data-ttu-id="ff974-120">Ten atrybut nie ma wartości domyślnej.</span><span class="sxs-lookup"><span data-stu-id="ff974-120">This attribute has no default value.</span></span>|  
|`port`|<span data-ttu-id="ff974-121">Określa numer portu, który ma być używany do nawiązywania połączenia z serwerem poczty SMTP.</span><span class="sxs-lookup"><span data-stu-id="ff974-121">Specifies the port number to use to connect to the SMTP mail server.</span></span> <span data-ttu-id="ff974-122">Wartość domyślna to 25.</span><span class="sxs-lookup"><span data-stu-id="ff974-122">The default value is 25.</span></span>|  
|`targetName`|<span data-ttu-id="ff974-123">Określa nazwę dostawcy usług (SPN), która ma być używana do uwierzytelniania podczas korzystania z rozszerzonej ochrony dla transakcji SMTP.</span><span class="sxs-lookup"><span data-stu-id="ff974-123">Specifies the Service Provider Name (SPN) to use for authentication when using extended protection for SMTP transactions.</span></span> <span data-ttu-id="ff974-124">Ten atrybut nie ma wartości domyślnej.</span><span class="sxs-lookup"><span data-stu-id="ff974-124">This attribute has no default value.</span></span>|  
|`userName`|<span data-ttu-id="ff974-125">Określa nazwę użytkownika, który ma być używany do uwierzytelniania na serwerze poczty SMTP.</span><span class="sxs-lookup"><span data-stu-id="ff974-125">Specifies the user name to use for authentication to the SMTP mail server.</span></span> <span data-ttu-id="ff974-126">Ten atrybut nie ma wartości domyślnej.</span><span class="sxs-lookup"><span data-stu-id="ff974-126">This attribute has no default value.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ff974-127">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="ff974-127">Child Elements</span></span>  
 <span data-ttu-id="ff974-128">Brak.</span><span class="sxs-lookup"><span data-stu-id="ff974-128">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ff974-129">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="ff974-129">Parent Elements</span></span>  
  
|<span data-ttu-id="ff974-130">Element</span><span class="sxs-lookup"><span data-stu-id="ff974-130">Element</span></span>|<span data-ttu-id="ff974-131">Opis</span><span class="sxs-lookup"><span data-stu-id="ff974-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ff974-132">\<smtp>— Element (Ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="ff974-132">\<smtp> Element (Network Settings)</span></span>](smtp-element-network-settings.md)|<span data-ttu-id="ff974-133">Konfiguruje opcje wysyłania poczty SMTP (Simple Mail Transport Protocol).</span><span class="sxs-lookup"><span data-stu-id="ff974-133">Configures Simple Mail Transport Protocol (SMTP) mail sending options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ff974-134">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ff974-134">Remarks</span></span>  
 <span data-ttu-id="ff974-135">Niektóre serwery SMTP wymagają uwierzytelnienia na serwerze przed użyciem.</span><span class="sxs-lookup"><span data-stu-id="ff974-135">Some SMTP servers require that you authenticate yourself to the server before use.</span></span> <span data-ttu-id="ff974-136">Aby uwierzytelnić się samodzielnie przy użyciu domyślnych poświadczeń sieciowych na hoście, należy ustawić `defaultCredentials` atrybut na `true` .</span><span class="sxs-lookup"><span data-stu-id="ff974-136">If you want to authenticate yourself using the default network credentials on your host, set the `defaultCredentials` attribute to `true`.</span></span> <span data-ttu-id="ff974-137"><xref:System.Net.Configuration.SmtpNetworkElement.DefaultCredentials%2A?displayProperty=nameWithType>Właściwość może służyć do uzyskiwania bieżącej wartości `defaultCredentials` atrybutu z odpowiednich plików konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="ff974-137">The <xref:System.Net.Configuration.SmtpNetworkElement.DefaultCredentials%2A?displayProperty=nameWithType> property can be used to get the current value of the `defaultCredentials` attribute from applicable configuration files.</span></span>  
  
 <span data-ttu-id="ff974-138">Możesz również użyć uwierzytelniania podstawowego (nazwy użytkownika i hasła), aby uwierzytelnić się na serwerze SMTP.</span><span class="sxs-lookup"><span data-stu-id="ff974-138">You can also use basic authentication (a user name and password) to authenticate yourself to the SMTP server.</span></span> <span data-ttu-id="ff974-139">Aby użyć tej opcji, należy określić prawidłową nazwę użytkownika i hasło dla określonego serwera SMTP.</span><span class="sxs-lookup"><span data-stu-id="ff974-139">To use this option, you must specify a valid user name and password for the specified SMTP server.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ff974-140">Uwierzytelnianie podstawowe wysyła `userName` wartości i `password` do nieszyfrowanego serwera.</span><span class="sxs-lookup"><span data-stu-id="ff974-140">Basic authentication sends the `userName` and `password` values to the server unencrypted.</span></span> <span data-ttu-id="ff974-141">Każdy może monitorować ruch sieciowy i używać ich do łączenia się z serwerem.</span><span class="sxs-lookup"><span data-stu-id="ff974-141">Anyone monitoring network traffic can view your credentials and use them to connect to the server.</span></span> <span data-ttu-id="ff974-142">Należy rozważyć użycie bezpieczniejszego mechanizmu uwierzytelniania, takiego jak Kerberos lub NT LAN Manager (NTLM). Jeśli `defaultCredentials` jest `true` , zostanie użyta wartość Kerberos lub NTLM, jeśli serwer obsługuje te protokoły.</span><span class="sxs-lookup"><span data-stu-id="ff974-142">You should consider using a more secure authentication mechanism, such as Kerberos or NT LAN Manager (NTLM.) If `defaultCredentials` is `true`, Kerberos or NTLM will be used if the server supports these protocols.</span></span>  
  
 <span data-ttu-id="ff974-143">Opcje uwierzytelniania podstawowego i domyślne poświadczenia sieciowe wzajemnie się wykluczają; Jeśli ustawisz `defaultCredentials` `true` i określisz nazwę użytkownika i hasło, zostanie użyte domyślne poświadczenia sieci, a podstawowe dane uwierzytelniania zostaną zignorowane.</span><span class="sxs-lookup"><span data-stu-id="ff974-143">The basic authentication and default network credentials options are mutually exclusive; if you set `defaultCredentials` to `true` and specify a user name and password, the default network credential is used, and the basic authentication data is ignored.</span></span>  
  
 <span data-ttu-id="ff974-144">W przypadku uwierzytelniania podstawowego należy `userName` również określić `password` uwierzytelnianie na serwerze poczty.</span><span class="sxs-lookup"><span data-stu-id="ff974-144">For basic authentication if you specify a `userName`, you should also specify a `password` to authentication yourself to the mail server.</span></span>  
  
 <span data-ttu-id="ff974-145"><xref:System.Net.Configuration.SmtpNetworkElement.UserName%2A?displayProperty=nameWithType>Właściwość może służyć do uzyskiwania bieżącej wartości `userName` atrybutu z odpowiednich plików konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="ff974-145">The <xref:System.Net.Configuration.SmtpNetworkElement.UserName%2A?displayProperty=nameWithType> property can be used to get the current value of the `userName` attribute from applicable configuration files.</span></span> <span data-ttu-id="ff974-146"><xref:System.Net.Configuration.SmtpNetworkElement.Password%2A?displayProperty=nameWithType>Właściwość może służyć do uzyskiwania bieżącej wartości `password` atrybutu z odpowiednich plików konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="ff974-146">The <xref:System.Net.Configuration.SmtpNetworkElement.Password%2A?displayProperty=nameWithType> property can be used to get the current value of the `password` attribute from applicable configuration files.</span></span> <span data-ttu-id="ff974-147">`password`Atrybut nie jest zwykle wprowadzany w plikach konfiguracyjnych ze względów bezpieczeństwa.</span><span class="sxs-lookup"><span data-stu-id="ff974-147">A `password` attribute would not normally be entered in configuration files for security reasons.</span></span>  
  
 <span data-ttu-id="ff974-148">Ten `clientDomain` atrybut zmienia nazwę domeny klienta używaną w początkowym żądaniu protokołu SMTP na serwerze SMTP.</span><span class="sxs-lookup"><span data-stu-id="ff974-148">The `clientDomain` attribute changes the client domain name used in the initial SMTP protocol request to an SMTP server.</span></span> <span data-ttu-id="ff974-149">Ten `clientDomain` atrybut może być ustawiony na w pełni kwalifikowaną nazwę domeny komputera lokalnego zamiast nazwy hosta lokalnego, która jest używana domyślnie.</span><span class="sxs-lookup"><span data-stu-id="ff974-149">The `clientDomain` attribute can be set to the fully-qualified domain name of the local machine, rather than the localhost name that is used by default.</span></span> <span data-ttu-id="ff974-150">Zapewnia to lepszą zgodność ze standardami protokołu SMTP.</span><span class="sxs-lookup"><span data-stu-id="ff974-150">This provides greater compliance with the SMTP protocol standards.</span></span> <span data-ttu-id="ff974-151">Wartość domyślna to nazwa localhost komputera lokalnego wysyłającego żądanie.</span><span class="sxs-lookup"><span data-stu-id="ff974-151">The default value is the localhost name of the local computer sending the request.</span></span> <span data-ttu-id="ff974-152"><xref:System.Net.Configuration.SmtpNetworkElement.ClientDomain%2A?displayProperty=nameWithType>Właściwość może służyć do uzyskiwania bieżącej wartości `clientDomain` atrybutu z odpowiednich plików konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="ff974-152">The <xref:System.Net.Configuration.SmtpNetworkElement.ClientDomain%2A?displayProperty=nameWithType> property can be used to get the current value of the `clientDomain` attribute from applicable configuration files.</span></span>  
  
 <span data-ttu-id="ff974-153">Ten `targetName` atrybut jest używany do uwierzytelniania w przypadku korzystania z ochrony rozszerzonej.</span><span class="sxs-lookup"><span data-stu-id="ff974-153">The `targetName` attribute is used for authentication when using extended protection.</span></span> <span data-ttu-id="ff974-154">Wartość domyślna ma postać "SMTPSVC/ \<host> " \<host> , gdzie jest nazwą hosta serwera poczty SMTP.</span><span class="sxs-lookup"><span data-stu-id="ff974-154">The default value is of the form "SMTPSVC/\<host>" where \<host> is the hostname of the SMTP mail server.</span></span> <span data-ttu-id="ff974-155"><xref:System.Net.Configuration.SmtpNetworkElement.TargetName%2A?displayProperty=nameWithType>Właściwość może służyć do uzyskiwania bieżącej wartości `targetName` atrybutu z odpowiednich plików konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="ff974-155">The <xref:System.Net.Configuration.SmtpNetworkElement.TargetName%2A?displayProperty=nameWithType> property can be used to get the current value of the `targetName` attribute from applicable configuration files.</span></span>  
  
 <span data-ttu-id="ff974-156">Ten `enableSsl` atrybut określa, czy protokół SSL jest używany do uzyskiwania dostępu do serwera poczty SMTP.</span><span class="sxs-lookup"><span data-stu-id="ff974-156">The `enableSsl` attribute specifies whether SSL is used to access an SMTP mail server.</span></span> <span data-ttu-id="ff974-157"><xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>Klasa obsługuje tylko rozszerzenie usługi SMTP dla bezpiecznego protokołu SMTP dla Transport Layer Security zgodnie z definicją w dokumencie RFC 3207.</span><span class="sxs-lookup"><span data-stu-id="ff974-157">The <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType> class only supports the SMTP Service Extension for Secure SMTP over Transport Layer Security as defined in RFC 3207.</span></span> <span data-ttu-id="ff974-158">W tym trybie sesja SMTP rozpoczyna się na nieszyfrowanym kanale, a następnie polecenie STARTTLS zostaje wystawione przez klienta na serwer w celu przełączenia do bezpiecznej komunikacji przy użyciu protokołu SSL.</span><span class="sxs-lookup"><span data-stu-id="ff974-158">In this mode, the SMTP session begins on an unencrypted channel, then a STARTTLS command is issued by the client to the server to switch to secure communication using SSL.</span></span> <span data-ttu-id="ff974-159">Więcej informacji można znaleźć w dokumencie RFC 3207 opublikowanym przez Internet Engineering Task Force (IETF).</span><span class="sxs-lookup"><span data-stu-id="ff974-159">See RFC 3207 published by the Internet Engineering Task Force (IETF) for more information.</span></span>  
  
 <span data-ttu-id="ff974-160">Alternatywna metoda połączenia polega na tym, że sesja SSL jest ustanawiana przed wysłaniem jakichkolwiek poleceń protokołu.</span><span class="sxs-lookup"><span data-stu-id="ff974-160">An alternate connection method is where an SSL session is established up front before any protocol commands are sent.</span></span> <span data-ttu-id="ff974-161">Ta metoda połączenia jest czasami nazywana protokołami SMTP i domyślnie używa portu 465.</span><span class="sxs-lookup"><span data-stu-id="ff974-161">This connection method is sometimes called SMTPS and by default uses port 465.</span></span> <span data-ttu-id="ff974-162">Ta alternatywna metoda łączenia przy użyciu protokołu SSL nie jest obecnie obsługiwana.</span><span class="sxs-lookup"><span data-stu-id="ff974-162">This alternate connection method using SSL is not currently supported.</span></span>  
  
 <span data-ttu-id="ff974-163"><xref:System.Net.Configuration.SmtpNetworkElement.EnableSsl%2A?displayProperty=nameWithType>Właściwość może służyć do uzyskiwania bieżącej wartości `enableSsl` atrybutu z odpowiednich plików konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="ff974-163">The <xref:System.Net.Configuration.SmtpNetworkElement.EnableSsl%2A?displayProperty=nameWithType> property can be used to get the current value of the `enableSsl` attribute from applicable configuration files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ff974-164">Przykład</span><span class="sxs-lookup"><span data-stu-id="ff974-164">Example</span></span>  
 <span data-ttu-id="ff974-165">W poniższym przykładzie określono odpowiednie parametry SMTP do wysyłania wiadomości e-mail przy użyciu domyślnych poświadczeń sieciowych.</span><span class="sxs-lookup"><span data-stu-id="ff974-165">The following example specifies the appropriate SMTP parameters to send email using the default network credentials.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ff974-166">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ff974-166">See also</span></span>

- <xref:System.Net.Configuration.SmtpNetworkElement?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- [<span data-ttu-id="ff974-167">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="ff974-167">Network Settings Schema</span></span>](index.md)
