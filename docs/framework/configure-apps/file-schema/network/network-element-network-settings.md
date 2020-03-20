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
# <a name="network-element-network-settings"></a>\<element> sieci (ustawienia sieciowe)
Konfiguruje opcje sieciowe zewnętrznego serwera SMTP (Simple Mail Transport Protocol).  

[**\<>konfiguracyjne**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<mailSettings>**](mailsettings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>smtp**](smtp-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<>sieci**

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
|`clientDomain`|Określa nazwę domeny klienta, która ma być używana w początkowym żądaniu protokołu SMTP do łączenia się z serwerem poczty SMTP. Wartością domyślną jest nazwa hosta lokalnego komputera lokalnego wysyłającego żądanie.|  
|`defaultCredentials`|Określa, czy domyślne poświadczenia użytkownika mają być używane do uzyskiwania dostępu do serwera poczty SMTP dla transakcji SMTP. Wartością domyślną jest `false`.|  
|`enableSsl`|Określa, czy protokół SSL jest używany do uzyskiwania dostępu do serwera poczty SMTP. Wartością domyślną jest `false`.|  
|`host`|Określa nazwa hosta serwera poczty SMTP, który ma być używany do obsługi transakcji SMTP. Ten atrybut nie ma wartości domyślnej.|  
|`password`|Określa hasło używane do uwierzytelniania na serwerze poczty SMTP. Ten atrybut nie ma wartości domyślnej.|  
|`port`|Określa numer portu, który ma być używany do łączenia się z serwerem poczty SMTP. Wartość domyślna to 25.|  
|`targetName`|Określa nazwę dostawcy usług (SPN) do użycia do uwierzytelniania podczas korzystania z rozszerzonej ochrony transakcji SMTP. Ten atrybut nie ma wartości domyślnej.|  
|`userName`|Określa nazwę użytkownika, która ma być używana do uwierzytelniania na serwerze poczty SMTP. Ten atrybut nie ma wartości domyślnej.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<element> smtp (ustawienia sieciowe)](smtp-element-network-settings.md)|Konfiguruje opcje wysyłania poczty SMTP (Simple Mail Transport Protocol).|  
  
## <a name="remarks"></a>Uwagi  
 Niektóre serwery SMTP wymagają uwierzytelnienia się na serwerze przed użyciem. Jeśli chcesz uwierzytelnić się przy użyciu domyślnych poświadczeń sieciowych na hoście, ustaw `defaultCredentials` atrybut na `true`. Właściwość <xref:System.Net.Configuration.SmtpNetworkElement.DefaultCredentials%2A?displayProperty=nameWithType> może służyć do uzyskania bieżącej wartości atrybutu `defaultCredentials` z odpowiednich plików konfiguracyjnych.  
  
 Można również użyć uwierzytelniania podstawowego (nazwy użytkownika i hasła) do uwierzytelniania się na serwerze SMTP. Aby użyć tej opcji, należy określić prawidłową nazwę użytkownika i hasło dla określonego serwera SMTP.  
  
> [!NOTE]
> Uwierzytelnianie podstawowe `userName` `password` wysyła wartości i wartości do serwera w stanie niezaszyfrowanym. Każdy, kto monitoruje ruch sieciowy, może wyświetlać poświadczenia i używać ich do łączenia się z serwerem. Należy rozważyć użycie bezpieczniejszego mechanizmu uwierzytelniania, takiego jak Kerberos lub NT LAN Manager (NTLM). Jeśli `defaultCredentials` `true`tak , Kerberos lub NTLM będą używane, jeśli serwer obsługuje te protokoły.  
  
 Podstawowe uwierzytelnianie i domyślne opcje poświadczeń sieci wzajemnie się wykluczają; Jeśli `defaultCredentials` ustawiono `true` i określisz nazwę użytkownika i hasło, używane jest domyślne poświadczenie sieciowe, a podstawowe dane uwierzytelniania są ignorowane.  
  
 W przypadku uwierzytelniania `userName`podstawowego, jeśli `password` określisz program , należy również określić uwierzytelnianie samodzielnie na serwerze poczty.  
  
 Właściwość <xref:System.Net.Configuration.SmtpNetworkElement.UserName%2A?displayProperty=nameWithType> może służyć do uzyskania bieżącej wartości atrybutu `userName` z odpowiednich plików konfiguracyjnych. Właściwość <xref:System.Net.Configuration.SmtpNetworkElement.Password%2A?displayProperty=nameWithType> może służyć do uzyskania bieżącej wartości atrybutu `password` z odpowiednich plików konfiguracyjnych. Atrybut `password` zwykle nie zostanie wprowadzony w plikach konfiguracyjnych ze względów bezpieczeństwa.  
  
 Atrybut `clientDomain` zmienia nazwę domeny klienta używaną w początkowym żądaniu protokołu SMTP na serwerze SMTP. Atrybut `clientDomain` można ustawić na w pełni kwalifikowaną nazwę domeny komputera lokalnego, a nie nazwę localhost, która jest używana domyślnie. Zapewnia to większą zgodność ze standardami protokołu SMTP. Wartością domyślną jest nazwa hosta lokalnego komputera lokalnego wysyłającego żądanie. Właściwość <xref:System.Net.Configuration.SmtpNetworkElement.ClientDomain%2A?displayProperty=nameWithType> może służyć do uzyskania bieżącej wartości atrybutu `clientDomain` z odpowiednich plików konfiguracyjnych.  
  
 Atrybut `targetName` jest używany do uwierzytelniania podczas korzystania z ochrony rozszerzonej. Wartością domyślną jest formularz "SMTPSVC/\<host>", w którym \<> hosta jest nazwa hosta serwera poczty SMTP. Właściwość <xref:System.Net.Configuration.SmtpNetworkElement.TargetName%2A?displayProperty=nameWithType> może służyć do uzyskania bieżącej wartości atrybutu `targetName` z odpowiednich plików konfiguracyjnych.  
  
 Atrybut `enableSsl` określa, czy protokół SSL jest używany do uzyskiwania dostępu do serwera poczty SMTP. Klasa <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType> obsługuje tylko rozszerzenie usługi SMTP dla bezpiecznego protokołu SMTP za transport bezpieczeństwa warstwy zdefiniowane w RFC 3207. W tym trybie sesja SMTP rozpoczyna się na kanale niezaszyfrowanym, a następnie klient wystawia na serwerze polecenie STARTTLS w celu przełączenia się do bezpiecznej komunikacji przy użyciu protokołu SSL. Zobacz RFC 3207 opublikowane przez Internet Engineering Task Force (IETF), aby uzyskać więcej informacji.  
  
 Alternatywna metoda połączenia to miejsce, w którym sesja SSL jest ustanawiana z góry przed wysłaniem jakichkolwiek poleceń protokołu. Ta metoda połączenia jest czasami nazywana SMTPS i domyślnie używa portu 465. Ta alternatywna metoda połączenia przy użyciu SSL nie jest obecnie obsługiwana.  
  
 Właściwość <xref:System.Net.Configuration.SmtpNetworkElement.EnableSsl%2A?displayProperty=nameWithType> może służyć do uzyskania bieżącej wartości atrybutu `enableSsl` z odpowiednich plików konfiguracyjnych.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład określa odpowiednie parametry SMTP do wysyłania wiadomości e-mail przy użyciu domyślnych poświadczeń sieci.  
  
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

- <xref:System.Net.Configuration.SmtpNetworkElement?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- [Schemat ustawień sieci](index.md)
