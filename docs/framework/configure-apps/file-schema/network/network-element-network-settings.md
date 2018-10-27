---
title: '&lt;sieć&gt; — Element (ustawienia sieci)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#network
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings/smtp/network
helpviewer_keywords:
- <network> element
- network element
ms.assetid: 2c2c6ad4-ed11-48ab-b28e-2bc0ba9b42c7
ms.openlocfilehash: 242ee42ded339b349cb9e4eb93750b9f5db29b51
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/26/2018
ms.locfileid: "50135236"
---
# <a name="ltnetworkgt-element-network-settings"></a>&lt;sieć&gt; — Element (ustawienia sieci)
Konfiguruje opcje sieciowe dla zewnętrznego serwera transportu protokołu SMTP (Simple Mail).  
  
 \<Konfiguracja >  
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
|`clientDomain`|Określa nazwę domeny klienta do użycia w początkowego żądania protokołu SMTP, aby nawiązać połączenie z serwerem poczty SMTP. Wartość domyślna to nazwy localhost lokalnego komputera wysyłającego żądanie.|  
|`defaultCredentials`|Określa, czy domyślne poświadczenia użytkownika powinien być używany do uzyskania dostępu do serwera poczty SMTP dla transakcji SMTP. Wartość domyślna to `false`.|  
|`enableSsl`|Określa, czy protokół SSL umożliwia dostęp do serwera poczty SMTP. Wartość domyślna to `false`.|  
|`host`|Określa nazwę hosta serwera poczty SMTP, który ma być używany dla transakcji SMTP. Ten atrybut nie ma wartości domyślnej.|  
|`password`|Określa hasło używane do uwierzytelniania serwera poczty SMTP. Ten atrybut nie ma wartości domyślnej.|  
|`port`|Określa numer portu do nawiązywania połączenia z serwerem poczty SMTP. Wartość domyślna to 25.|  
|`targetName`|Określa nazwę dostawcy usługi (SPN) na potrzeby uwierzytelniania w przypadku używania mechanizmu rozszerzonej ochrony dla transakcji SMTP. Ten atrybut nie ma wartości domyślnej.|  
|`userName`|Określa nazwę użytkownika do uwierzytelniania z serwerem poczty SMTP. Ten atrybut nie ma wartości domyślnej.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<SMTP >, Element (ustawienia sieci)](../../../../../docs/framework/configure-apps/file-schema/network/smtp-element-network-settings.md)|Konfiguruje opcje wysyłania poczty transportu protokołu SMTP (Simple Mail).|  
  
## <a name="remarks"></a>Uwagi  
 Niektóre serwery SMTP wymagają uwierzytelnienia przy serwerowi przed użyciem. Jeśli chcesz uwierzytelnienia przy użyciu poświadczeń domyślnych sieci na hoście, ustaw `defaultCredentials` atrybutu `true`. <xref:System.Net.Configuration.SmtpNetworkElement.DefaultCredentials%2A?displayProperty=nameWithType> Właściwość może służyć do uzyskania bieżącej wartości `defaultCredentials` atrybut z właściwych plików konfiguracji.  
  
 Można również użyć uwierzytelniania podstawowego (nazwa użytkownika i hasło) do uwierzytelniania osoby do serwera SMTP. Aby użyć tej opcji, należy określić prawidłową nazwę użytkownika i hasło dla określonego serwera SMTP.  
  
> [!NOTE]
>  Uwierzytelnianie podstawowe przesyła `userName` i `password` wartości na serwer niezaszyfrowanego. Każdy monitorowania ruchu sieciowego może wyświetlić swoje poświadczenia i używać ich do łączenia z serwerem. Należy rozważyć użycie bardziej bezpieczne mechanizm uwierzytelniania, takich jak Kerberos lub NT LAN Manager (NTLM). Jeśli `defaultCredentials` jest `true`, Kerberos lub NTLM zostaną użyte, jeśli serwer obsługuje te protokoły.  
  
 Podstawowe opcje poświadczeń sieci uwierzytelniania i domyślnych wzajemnie się wykluczają; Jeśli ustawisz `defaultCredentials` do `true` i określ nazwę użytkownika i hasło, domyślnych poświadczeń sieciowych jest używany i dane uwierzytelniania podstawowego zostaną zignorowane.  
  
 Dla uwierzytelniania podstawowego w przypadku określenia `userName`, należy także określić `password` do uwierzytelniania użytkownika na serwerze poczty e-mail.  
  
 <xref:System.Net.Configuration.SmtpNetworkElement.UserName%2A?displayProperty=nameWithType> Właściwość może służyć do uzyskania bieżącej wartości `userName` atrybut z właściwych plików konfiguracji. <xref:System.Net.Configuration.SmtpNetworkElement.Password%2A?displayProperty=nameWithType> Właściwość może służyć do uzyskania bieżącej wartości `password` atrybut z właściwych plików konfiguracji. A `password` atrybutu nie zwykle zostaną wprowadzone w plikach konfiguracji ze względów bezpieczeństwa.  
  
 `clientDomain` Atrybut zmieni nazwę domeny klienta, które są używane w początkowego żądania protokołu SMTP do serwera SMTP. `clientDomain` Atrybut można określać w pełni kwalifikowana nazwa domeny komputera lokalnego, a nie nazwy localhost, który jest używany domyślnie. Zapewnia to większą zgodność ze standardami protokołu SMTP. Wartość domyślna to nazwy localhost lokalnego komputera wysyłającego żądanie. <xref:System.Net.Configuration.SmtpNetworkElement.ClientDomain%2A?displayProperty=nameWithType> Właściwość może służyć do uzyskania bieżącej wartości `clientDomain` atrybut z właściwych plików konfiguracji.  
  
 `targetName` Atrybut jest używany do uwierzytelniania przy użyciu mechanizmu rozszerzonej ochrony. Wartość domyślna ma postać "SMTPSVC /\<host >" gdzie \<host > jest nazwą hosta serwera poczty SMTP. <xref:System.Net.Configuration.SmtpNetworkElement.TargetName%2A?displayProperty=nameWithType> Właściwość może służyć do uzyskania bieżącej wartości `targetName` atrybut z właściwych plików konfiguracji.  
  
 `enableSsl` Atrybut określa, czy protokół SSL umożliwia dostęp do serwera poczty SMTP. <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType> Klasy obsługuje tylko rozszerzenia usługi SMTP dla bezpiecznego protokołu SMTP za pośrednictwem Transport Layer Security zgodnie z definicją w dokumencie RFC 3207. W tym trybie rozpoczyna się i niezaszyfrowanego kanału sesji SMTP, a następnie polecenie STARTTLS wystawiony przez klienta do serwera, aby przełączyć się do bezpiecznej komunikacji przy użyciu protokołu SSL. Zobacz RFC 3207 opublikowane przez Internet Engineering Task Force (IETF) Aby uzyskać więcej informacji.  
  
 Metody alternatywne połączenie jest, gdzie SSL zostanie utworzona sesja na początku przed protokołu wysłania polecenia. Tej metody połączenia jest czasami nazywane SMTPS i domyślnie używa portu 465. Ta metoda alternatywne połączenie przy użyciu protokołu SSL nie jest obecnie obsługiwane.  
  
 <xref:System.Net.Configuration.SmtpNetworkElement.EnableSsl%2A?displayProperty=nameWithType> Właściwość może służyć do uzyskania bieżącej wartości `enableSsl` atrybut z właściwych plików konfiguracji.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład określa odpowiednie parametry SMTP do wysyłania wiadomości e-mail przy użyciu poświadczeń domyślnych sieci.  
  
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
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Net.Configuration.SmtpNetworkElement?displayProperty=nameWithType>  
 <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>  
 <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>  
 [Schemat ustawień sieci](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
