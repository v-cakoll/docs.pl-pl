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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154819"
---
# <a name="network-element-network-settings"></a><span data-ttu-id="63a6b-102">\<network>, element (ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="63a6b-102">\<network> Element (Network Settings)</span></span>
<span data-ttu-id="63a6b-103">Konfiguruje opcje sieci dla serwera zewnętrznego protokołu SMTP (Simple Mail Transport Protocol).</span><span class="sxs-lookup"><span data-stu-id="63a6b-103">Configures the network options for an external Simple Mail Transport Protocol (SMTP) server.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<mailSettings>**](mailsettings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<smtp>**](smtp-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<network>**

## <a name="syntax"></a><span data-ttu-id="63a6b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="63a6b-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="63a6b-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="63a6b-105">Attributes and Elements</span></span>  
 <span data-ttu-id="63a6b-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="63a6b-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="63a6b-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="63a6b-107">Attributes</span></span>  
  
|<span data-ttu-id="63a6b-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="63a6b-108">Attribute</span></span>|<span data-ttu-id="63a6b-109">Opis</span><span class="sxs-lookup"><span data-stu-id="63a6b-109">Description</span></span>|  
|---------------|-----------------|  
|`clientDomain`|<span data-ttu-id="63a6b-110">Określa nazwę domeny klienta do użycia w początkowym żądaniu protokołu SMTP do nawiązania połączenia z serwerem poczty SMTP.</span><span class="sxs-lookup"><span data-stu-id="63a6b-110">Specifies the client domain name to use in the initial SMTP protocol request to connect to the SMTP mail server.</span></span> <span data-ttu-id="63a6b-111">Wartość domyślna to nazwa localhost komputera lokalnego wysyłającego żądanie.</span><span class="sxs-lookup"><span data-stu-id="63a6b-111">The default value is the localhost name of the local computer sending the request.</span></span>|  
|`defaultCredentials`|<span data-ttu-id="63a6b-112">Określa, czy domyślne poświadczenia użytkownika mają być używane do uzyskiwania dostępu do serwera poczty SMTP dla transakcji SMTP.</span><span class="sxs-lookup"><span data-stu-id="63a6b-112">Specifies whether the default user credentials should be used to access the SMTP mail server for SMTP transactions.</span></span> <span data-ttu-id="63a6b-113">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="63a6b-113">The default value is `false`.</span></span>|  
|`enableSsl`|<span data-ttu-id="63a6b-114">Określa, czy protokół SSL jest używany do uzyskiwania dostępu do serwera poczty SMTP.</span><span class="sxs-lookup"><span data-stu-id="63a6b-114">Specifies whether SSL is used to access an SMTP mail server.</span></span> <span data-ttu-id="63a6b-115">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="63a6b-115">The default value is `false`.</span></span>|  
|`host`|<span data-ttu-id="63a6b-116">Określa nazwę hosta serwera poczty SMTP, który ma być używany dla transakcji SMTP.</span><span class="sxs-lookup"><span data-stu-id="63a6b-116">Specifies the hostname of the SMTP mail server to use for SMTP transactions.</span></span> <span data-ttu-id="63a6b-117">Ten atrybut nie ma wartości domyślnej.</span><span class="sxs-lookup"><span data-stu-id="63a6b-117">This attribute has no default value.</span></span>|  
|`password`|<span data-ttu-id="63a6b-118">Określa hasło, które ma być używane do uwierzytelniania na serwerze poczty SMTP.</span><span class="sxs-lookup"><span data-stu-id="63a6b-118">Specifies the password to use for authentication to the SMTP mail server.</span></span> <span data-ttu-id="63a6b-119">Ten atrybut nie ma wartości domyślnej.</span><span class="sxs-lookup"><span data-stu-id="63a6b-119">This attribute has no default value.</span></span>|  
|`port`|<span data-ttu-id="63a6b-120">Określa numer portu, który ma być używany do nawiązywania połączenia z serwerem poczty SMTP.</span><span class="sxs-lookup"><span data-stu-id="63a6b-120">Specifies the port number to use to connect to the SMTP mail server.</span></span> <span data-ttu-id="63a6b-121">Wartość domyślna to 25.</span><span class="sxs-lookup"><span data-stu-id="63a6b-121">The default value is 25.</span></span>|  
|`targetName`|<span data-ttu-id="63a6b-122">Określa nazwę dostawcy usług (SPN), która ma być używana do uwierzytelniania podczas korzystania z rozszerzonej ochrony dla transakcji SMTP.</span><span class="sxs-lookup"><span data-stu-id="63a6b-122">Specifies the Service Provider Name (SPN) to use for authentication when using extended protection for SMTP transactions.</span></span> <span data-ttu-id="63a6b-123">Ten atrybut nie ma wartości domyślnej.</span><span class="sxs-lookup"><span data-stu-id="63a6b-123">This attribute has no default value.</span></span>|  
|`userName`|<span data-ttu-id="63a6b-124">Określa nazwę użytkownika, który ma być używany do uwierzytelniania na serwerze poczty SMTP.</span><span class="sxs-lookup"><span data-stu-id="63a6b-124">Specifies the user name to use for authentication to the SMTP mail server.</span></span> <span data-ttu-id="63a6b-125">Ten atrybut nie ma wartości domyślnej.</span><span class="sxs-lookup"><span data-stu-id="63a6b-125">This attribute has no default value.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="63a6b-126">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="63a6b-126">Child Elements</span></span>  
 <span data-ttu-id="63a6b-127">Brak.</span><span class="sxs-lookup"><span data-stu-id="63a6b-127">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="63a6b-128">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="63a6b-128">Parent Elements</span></span>  
  
|<span data-ttu-id="63a6b-129">Element</span><span class="sxs-lookup"><span data-stu-id="63a6b-129">Element</span></span>|<span data-ttu-id="63a6b-130">Opis</span><span class="sxs-lookup"><span data-stu-id="63a6b-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="63a6b-131">\<smtp>— Element (Ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="63a6b-131">\<smtp> Element (Network Settings)</span></span>](smtp-element-network-settings.md)|<span data-ttu-id="63a6b-132">Konfiguruje opcje wysyłania poczty SMTP (Simple Mail Transport Protocol).</span><span class="sxs-lookup"><span data-stu-id="63a6b-132">Configures Simple Mail Transport Protocol (SMTP) mail sending options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="63a6b-133">Uwagi</span><span class="sxs-lookup"><span data-stu-id="63a6b-133">Remarks</span></span>  
 <span data-ttu-id="63a6b-134">Niektóre serwery SMTP wymagają uwierzytelnienia na serwerze przed użyciem.</span><span class="sxs-lookup"><span data-stu-id="63a6b-134">Some SMTP servers require that you authenticate yourself to the server before use.</span></span> <span data-ttu-id="63a6b-135">Aby uwierzytelnić się samodzielnie przy użyciu domyślnych poświadczeń sieciowych na hoście, należy ustawić `defaultCredentials` atrybut na `true` .</span><span class="sxs-lookup"><span data-stu-id="63a6b-135">If you want to authenticate yourself using the default network credentials on your host, set the `defaultCredentials` attribute to `true`.</span></span> <span data-ttu-id="63a6b-136"><xref:System.Net.Configuration.SmtpNetworkElement.DefaultCredentials%2A?displayProperty=nameWithType>Właściwość może służyć do uzyskiwania bieżącej wartości `defaultCredentials` atrybutu z odpowiednich plików konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="63a6b-136">The <xref:System.Net.Configuration.SmtpNetworkElement.DefaultCredentials%2A?displayProperty=nameWithType> property can be used to get the current value of the `defaultCredentials` attribute from applicable configuration files.</span></span>  
  
 <span data-ttu-id="63a6b-137">Możesz również użyć uwierzytelniania podstawowego (nazwy użytkownika i hasła), aby uwierzytelnić się na serwerze SMTP.</span><span class="sxs-lookup"><span data-stu-id="63a6b-137">You can also use basic authentication (a user name and password) to authenticate yourself to the SMTP server.</span></span> <span data-ttu-id="63a6b-138">Aby użyć tej opcji, należy określić prawidłową nazwę użytkownika i hasło dla określonego serwera SMTP.</span><span class="sxs-lookup"><span data-stu-id="63a6b-138">To use this option, you must specify a valid user name and password for the specified SMTP server.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="63a6b-139">Uwierzytelnianie podstawowe wysyła `userName` wartości i `password` do nieszyfrowanego serwera.</span><span class="sxs-lookup"><span data-stu-id="63a6b-139">Basic authentication sends the `userName` and `password` values to the server unencrypted.</span></span> <span data-ttu-id="63a6b-140">Każdy może monitorować ruch sieciowy i używać ich do łączenia się z serwerem.</span><span class="sxs-lookup"><span data-stu-id="63a6b-140">Anyone monitoring network traffic can view your credentials and use them to connect to the server.</span></span> <span data-ttu-id="63a6b-141">Należy rozważyć użycie bezpieczniejszego mechanizmu uwierzytelniania, takiego jak Kerberos lub NT LAN Manager (NTLM). Jeśli `defaultCredentials` jest `true` , zostanie użyta wartość Kerberos lub NTLM, jeśli serwer obsługuje te protokoły.</span><span class="sxs-lookup"><span data-stu-id="63a6b-141">You should consider using a more secure authentication mechanism, such as Kerberos or NT LAN Manager (NTLM.) If `defaultCredentials` is `true`, Kerberos or NTLM will be used if the server supports these protocols.</span></span>  
  
 <span data-ttu-id="63a6b-142">Opcje uwierzytelniania podstawowego i domyślne poświadczenia sieciowe wzajemnie się wykluczają; Jeśli ustawisz `defaultCredentials` `true` i określisz nazwę użytkownika i hasło, zostanie użyte domyślne poświadczenia sieci, a podstawowe dane uwierzytelniania zostaną zignorowane.</span><span class="sxs-lookup"><span data-stu-id="63a6b-142">The basic authentication and default network credentials options are mutually exclusive; if you set `defaultCredentials` to `true` and specify a user name and password, the default network credential is used, and the basic authentication data is ignored.</span></span>  
  
 <span data-ttu-id="63a6b-143">W przypadku uwierzytelniania podstawowego należy `userName` również określić `password` uwierzytelnianie na serwerze poczty.</span><span class="sxs-lookup"><span data-stu-id="63a6b-143">For basic authentication if you specify a `userName`, you should also specify a `password` to authentication yourself to the mail server.</span></span>  
  
 <span data-ttu-id="63a6b-144"><xref:System.Net.Configuration.SmtpNetworkElement.UserName%2A?displayProperty=nameWithType>Właściwość może służyć do uzyskiwania bieżącej wartości `userName` atrybutu z odpowiednich plików konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="63a6b-144">The <xref:System.Net.Configuration.SmtpNetworkElement.UserName%2A?displayProperty=nameWithType> property can be used to get the current value of the `userName` attribute from applicable configuration files.</span></span> <span data-ttu-id="63a6b-145"><xref:System.Net.Configuration.SmtpNetworkElement.Password%2A?displayProperty=nameWithType>Właściwość może służyć do uzyskiwania bieżącej wartości `password` atrybutu z odpowiednich plików konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="63a6b-145">The <xref:System.Net.Configuration.SmtpNetworkElement.Password%2A?displayProperty=nameWithType> property can be used to get the current value of the `password` attribute from applicable configuration files.</span></span> <span data-ttu-id="63a6b-146">`password`Atrybut nie jest zwykle wprowadzany w plikach konfiguracyjnych ze względów bezpieczeństwa.</span><span class="sxs-lookup"><span data-stu-id="63a6b-146">A `password` attribute would not normally be entered in configuration files for security reasons.</span></span>  
  
 <span data-ttu-id="63a6b-147">Ten `clientDomain` atrybut zmienia nazwę domeny klienta używaną w początkowym żądaniu protokołu SMTP na serwerze SMTP.</span><span class="sxs-lookup"><span data-stu-id="63a6b-147">The `clientDomain` attribute changes the client domain name used in the initial SMTP protocol request to an SMTP server.</span></span> <span data-ttu-id="63a6b-148">Ten `clientDomain` atrybut może być ustawiony na w pełni kwalifikowaną nazwę domeny komputera lokalnego zamiast nazwy hosta lokalnego, która jest używana domyślnie.</span><span class="sxs-lookup"><span data-stu-id="63a6b-148">The `clientDomain` attribute can be set to the fully-qualified domain name of the local machine, rather than the localhost name that is used by default.</span></span> <span data-ttu-id="63a6b-149">Zapewnia to lepszą zgodność ze standardami protokołu SMTP.</span><span class="sxs-lookup"><span data-stu-id="63a6b-149">This provides greater compliance with the SMTP protocol standards.</span></span> <span data-ttu-id="63a6b-150">Wartość domyślna to nazwa localhost komputera lokalnego wysyłającego żądanie.</span><span class="sxs-lookup"><span data-stu-id="63a6b-150">The default value is the localhost name of the local computer sending the request.</span></span> <span data-ttu-id="63a6b-151"><xref:System.Net.Configuration.SmtpNetworkElement.ClientDomain%2A?displayProperty=nameWithType>Właściwość może służyć do uzyskiwania bieżącej wartości `clientDomain` atrybutu z odpowiednich plików konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="63a6b-151">The <xref:System.Net.Configuration.SmtpNetworkElement.ClientDomain%2A?displayProperty=nameWithType> property can be used to get the current value of the `clientDomain` attribute from applicable configuration files.</span></span>  
  
 <span data-ttu-id="63a6b-152">Ten `targetName` atrybut jest używany do uwierzytelniania w przypadku korzystania z ochrony rozszerzonej.</span><span class="sxs-lookup"><span data-stu-id="63a6b-152">The `targetName` attribute is used for authentication when using extended protection.</span></span> <span data-ttu-id="63a6b-153">Wartość domyślna ma postać "SMTPSVC/ \<host> " \<host> , gdzie jest nazwą hosta serwera poczty SMTP.</span><span class="sxs-lookup"><span data-stu-id="63a6b-153">The default value is of the form "SMTPSVC/\<host>" where \<host> is the hostname of the SMTP mail server.</span></span> <span data-ttu-id="63a6b-154"><xref:System.Net.Configuration.SmtpNetworkElement.TargetName%2A?displayProperty=nameWithType>Właściwość może służyć do uzyskiwania bieżącej wartości `targetName` atrybutu z odpowiednich plików konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="63a6b-154">The <xref:System.Net.Configuration.SmtpNetworkElement.TargetName%2A?displayProperty=nameWithType> property can be used to get the current value of the `targetName` attribute from applicable configuration files.</span></span>  
  
 <span data-ttu-id="63a6b-155">Ten `enableSsl` atrybut określa, czy protokół SSL jest używany do uzyskiwania dostępu do serwera poczty SMTP.</span><span class="sxs-lookup"><span data-stu-id="63a6b-155">The `enableSsl` attribute specifies whether SSL is used to access an SMTP mail server.</span></span> <span data-ttu-id="63a6b-156"><xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>Klasa obsługuje tylko rozszerzenie usługi SMTP dla bezpiecznego protokołu SMTP dla Transport Layer Security zgodnie z definicją w dokumencie RFC 3207.</span><span class="sxs-lookup"><span data-stu-id="63a6b-156">The <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType> class only supports the SMTP Service Extension for Secure SMTP over Transport Layer Security as defined in RFC 3207.</span></span> <span data-ttu-id="63a6b-157">W tym trybie sesja SMTP rozpoczyna się na nieszyfrowanym kanale, a następnie polecenie STARTTLS zostaje wystawione przez klienta na serwer w celu przełączenia do bezpiecznej komunikacji przy użyciu protokołu SSL.</span><span class="sxs-lookup"><span data-stu-id="63a6b-157">In this mode, the SMTP session begins on an unencrypted channel, then a STARTTLS command is issued by the client to the server to switch to secure communication using SSL.</span></span> <span data-ttu-id="63a6b-158">Więcej informacji można znaleźć w dokumencie RFC 3207 opublikowanym przez Internet Engineering Task Force (IETF).</span><span class="sxs-lookup"><span data-stu-id="63a6b-158">See RFC 3207 published by the Internet Engineering Task Force (IETF) for more information.</span></span>  
  
 <span data-ttu-id="63a6b-159">Alternatywna metoda połączenia polega na tym, że sesja SSL jest ustanawiana przed wysłaniem jakichkolwiek poleceń protokołu.</span><span class="sxs-lookup"><span data-stu-id="63a6b-159">An alternate connection method is where an SSL session is established up front before any protocol commands are sent.</span></span> <span data-ttu-id="63a6b-160">Ta metoda połączenia jest czasami nazywana protokołami SMTP i domyślnie używa portu 465.</span><span class="sxs-lookup"><span data-stu-id="63a6b-160">This connection method is sometimes called SMTPS and by default uses port 465.</span></span> <span data-ttu-id="63a6b-161">Ta alternatywna metoda łączenia przy użyciu protokołu SSL nie jest obecnie obsługiwana.</span><span class="sxs-lookup"><span data-stu-id="63a6b-161">This alternate connection method using SSL is not currently supported.</span></span>  
  
 <span data-ttu-id="63a6b-162"><xref:System.Net.Configuration.SmtpNetworkElement.EnableSsl%2A?displayProperty=nameWithType>Właściwość może służyć do uzyskiwania bieżącej wartości `enableSsl` atrybutu z odpowiednich plików konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="63a6b-162">The <xref:System.Net.Configuration.SmtpNetworkElement.EnableSsl%2A?displayProperty=nameWithType> property can be used to get the current value of the `enableSsl` attribute from applicable configuration files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="63a6b-163">Przykład</span><span class="sxs-lookup"><span data-stu-id="63a6b-163">Example</span></span>  
 <span data-ttu-id="63a6b-164">W poniższym przykładzie określono odpowiednie parametry SMTP do wysyłania wiadomości e-mail przy użyciu domyślnych poświadczeń sieciowych.</span><span class="sxs-lookup"><span data-stu-id="63a6b-164">The following example specifies the appropriate SMTP parameters to send email using the default network credentials.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="63a6b-165">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="63a6b-165">See also</span></span>

- <xref:System.Net.Configuration.SmtpNetworkElement?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- [<span data-ttu-id="63a6b-166">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="63a6b-166">Network Settings Schema</span></span>](index.md)
