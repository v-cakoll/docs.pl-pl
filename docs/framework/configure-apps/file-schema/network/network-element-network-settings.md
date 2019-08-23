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
# <a name="network-element-network-settings"></a>\<Network >, element (Ustawienia sieci)
Konfiguruje opcje sieci dla serwera zewnętrznego protokołu SMTP (Simple Mail Transport Protocol).  
  
 \<> konfiguracji  
\<system.net>  
\<mailSettings>  
\<smtp>  
\<network>  
  
## <a name="syntax"></a>Składnia  
  
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
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`clientDomain`|Określa nazwę domeny klienta do użycia w początkowym żądaniu protokołu SMTP do nawiązania połączenia z serwerem poczty SMTP. Wartość domyślna to nazwa localhost komputera lokalnego wysyłającego żądanie.|  
|`defaultCredentials`|Określa, czy domyślne poświadczenia użytkownika mają być używane do uzyskiwania dostępu do serwera poczty SMTP dla transakcji SMTP. Wartość domyślna to `false`.|  
|`enableSsl`|Określa, czy protokół SSL jest używany do uzyskiwania dostępu do serwera poczty SMTP. Wartość domyślna to `false`.|  
|`host`|Określa nazwę hosta serwera poczty SMTP, który ma być używany dla transakcji SMTP. Ten atrybut nie ma wartości domyślnej.|  
|`password`|Określa hasło, które ma być używane do uwierzytelniania na serwerze poczty SMTP. Ten atrybut nie ma wartości domyślnej.|  
|`port`|Określa numer portu, który ma być używany do nawiązywania połączenia z serwerem poczty SMTP. Wartość domyślna to 25.|  
|`targetName`|Określa nazwę dostawcy usług (SPN), która ma być używana do uwierzytelniania podczas korzystania z rozszerzonej ochrony dla transakcji SMTP. Ten atrybut nie ma wartości domyślnej.|  
|`userName`|Określa nazwę użytkownika, który ma być używany do uwierzytelniania na serwerze poczty SMTP. Ten atrybut nie ma wartości domyślnej.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<> SMTP — element (Ustawienia sieci)](smtp-element-network-settings.md)|Konfiguruje opcje wysyłania poczty SMTP (Simple Mail Transport Protocol).|  
  
## <a name="remarks"></a>Uwagi  
 Niektóre serwery SMTP wymagają uwierzytelnienia na serwerze przed użyciem. Aby uwierzytelnić się samodzielnie przy użyciu domyślnych poświadczeń sieciowych na hoście, należy ustawić `defaultCredentials` atrybut na. `true` Właściwość może służyć do uzyskiwania bieżącej wartości `defaultCredentials` atrybutu z odpowiednich plików konfiguracji. <xref:System.Net.Configuration.SmtpNetworkElement.DefaultCredentials%2A?displayProperty=nameWithType>  
  
 Możesz również użyć uwierzytelniania podstawowego (nazwy użytkownika i hasła), aby uwierzytelnić się na serwerze SMTP. Aby użyć tej opcji, należy określić prawidłową nazwę użytkownika i hasło dla określonego serwera SMTP.  
  
> [!NOTE]
> Uwierzytelnianie podstawowe wysyła `userName` wartości i `password` do nieszyfrowanego serwera. Każdy może monitorować ruch sieciowy i używać ich do łączenia się z serwerem. Należy rozważyć użycie bezpieczniejszego mechanizmu uwierzytelniania, takiego jak Kerberos lub NT LAN Manager (NTLM). Jeśli `defaultCredentials` jest `true`, zostanie użyta wartość Kerberos lub NTLM, jeśli serwer obsługuje te protokoły.  
  
 Opcje uwierzytelniania podstawowego i domyślne poświadczenia sieciowe wzajemnie się wykluczają; Jeśli ustawisz `defaultCredentials` `true` i określisz nazwę użytkownika i hasło, zostanie użyte domyślne poświadczenia sieci, a podstawowe dane uwierzytelniania zostaną zignorowane.  
  
 W przypadku uwierzytelniania `userName`podstawowego należy również `password` określić uwierzytelnianie na serwerze poczty.  
  
 Właściwość może służyć do uzyskiwania bieżącej wartości `userName` atrybutu z odpowiednich plików konfiguracji. <xref:System.Net.Configuration.SmtpNetworkElement.UserName%2A?displayProperty=nameWithType> Właściwość może służyć do uzyskiwania bieżącej wartości `password` atrybutu z odpowiednich plików konfiguracji. <xref:System.Net.Configuration.SmtpNetworkElement.Password%2A?displayProperty=nameWithType> `password` Atrybut nie jest zwykle wprowadzany w plikach konfiguracyjnych ze względów bezpieczeństwa.  
  
 Ten `clientDomain` atrybut zmienia nazwę domeny klienta używaną w początkowym żądaniu protokołu SMTP na serwerze SMTP. Ten `clientDomain` atrybut może być ustawiony na w pełni kwalifikowaną nazwę domeny komputera lokalnego zamiast nazwy hosta lokalnego, która jest używana domyślnie. Zapewnia to lepszą zgodność ze standardami protokołu SMTP. Wartość domyślna to nazwa localhost komputera lokalnego wysyłającego żądanie. Właściwość może służyć do uzyskiwania bieżącej wartości `clientDomain` atrybutu z odpowiednich plików konfiguracji. <xref:System.Net.Configuration.SmtpNetworkElement.ClientDomain%2A?displayProperty=nameWithType>  
  
 Ten `targetName` atrybut jest używany do uwierzytelniania w przypadku korzystania z ochrony rozszerzonej. Wartość domyślna ma postać "SMTPSVC/\<Host >", gdzie \<Host > jest nazwą hosta serwera poczty SMTP. Właściwość może służyć do uzyskiwania bieżącej wartości `targetName` atrybutu z odpowiednich plików konfiguracji. <xref:System.Net.Configuration.SmtpNetworkElement.TargetName%2A?displayProperty=nameWithType>  
  
 Ten `enableSsl` atrybut określa, czy protokół SSL jest używany do uzyskiwania dostępu do serwera poczty SMTP. <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType> Klasa obsługuje tylko rozszerzenie usługi SMTP dla bezpiecznego protokołu SMTP dla Transport Layer Security zgodnie z definicją w dokumencie RFC 3207. W tym trybie sesja SMTP rozpoczyna się na nieszyfrowanym kanale, a następnie polecenie STARTTLS zostaje wystawione przez klienta na serwer w celu przełączenia do bezpiecznej komunikacji przy użyciu protokołu SSL. Więcej informacji można znaleźć w dokumencie RFC 3207 opublikowanym przez Internet Engineering Task Force (IETF).  
  
 Alternatywna metoda połączenia polega na tym, że sesja SSL jest ustanawiana przed wysłaniem jakichkolwiek poleceń protokołu. Ta metoda połączenia jest czasami nazywana protokołami SMTP i domyślnie używa portu 465. Ta alternatywna metoda łączenia przy użyciu protokołu SSL nie jest obecnie obsługiwana.  
  
 Właściwość może służyć do uzyskiwania bieżącej wartości `enableSsl` atrybutu z odpowiednich plików konfiguracji. <xref:System.Net.Configuration.SmtpNetworkElement.EnableSsl%2A?displayProperty=nameWithType>  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie określono odpowiednie parametry SMTP do wysyłania wiadomości e-mail przy użyciu domyślnych poświadczeń sieciowych.  
  
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
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Net.Configuration.SmtpNetworkElement?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- [Schemat ustawień sieci](index.md)
