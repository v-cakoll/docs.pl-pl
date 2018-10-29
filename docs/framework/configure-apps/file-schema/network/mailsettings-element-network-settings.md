---
title: '&lt;mailSettings&gt; — Element (ustawienia sieci)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#mailSettings
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings
helpviewer_keywords:
- mailSettings element
- <mailSettings> element
ms.assetid: 54f0f153-17e5-4f49-afdc-deadb940c9c1
ms.openlocfilehash: 5c7b4d8fae2774fe8e52718fbce91e4bc193c124
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/28/2018
ms.locfileid: "50198435"
---
# <a name="ltmailsettingsgt-element-network-settings"></a>&lt;mailSettings&gt; — Element (ustawienia sieci)
Konfiguruje opcje wysyłania poczty.  

\<Konfiguracja >  
\<system.net>  
\<mailSettings>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<mailSettings>
  <smtp> … </smtp>  
</mailSettings>
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
 Brak.  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|[\<SMTP >, Element (ustawienia sieci)](../../../../../docs/framework/configure-apps/file-schema/network/smtp-element-network-settings.md)|Służy do konfigurowania opcji prostego protokołu transportowego poczty.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|**Element**|**Opis**|  
|-----------------|---------------------|  
|[\<przestrzeni nazw system.Net >, Element (ustawienia sieci)](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|Zawiera ustawienia, które określają, jak .NET Framework łączy się z siecią.|  
  
## <a name="example"></a>Przykład  
 Poniższy przykład określa odpowiednie parametry SMTP do wysyłania wiadomości e-mail przy użyciu poświadczeń domyślnych sieci.  
  
```xml  
<configuration>  
  <system.net>  
    <mailSettings>  
      <smtp deliveryMethod="Network">  
        <network  
          host="localhost"  
          port="25"  
          defaultCredentials="true"  
        />  
      </smtp>  
    </mailSettings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz też  
- <xref:System.Net.Mail.SmtpClient>  
- [Schemat ustawień sieci](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
