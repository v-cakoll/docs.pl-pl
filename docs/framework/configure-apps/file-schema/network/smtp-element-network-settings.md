---
title: '&lt;SMTP&gt; — Element (ustawienia sieci)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings/smtp
- http://schemas.microsoft.com/.NetConfiguration/v2.0#smtp
helpviewer_keywords:
- <smtp> element
- smtp element
ms.assetid: 220b0329-e384-4e0c-86b4-0945ad17efd9
ms.openlocfilehash: 4a2947594f5adc9cc4c11471e133c6a4f2662a50
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54638018"
---
# <a name="ltsmtpgt-element-network-settings"></a>&lt;SMTP&gt; — Element (ustawienia sieci)
Konfiguruje format dostarczania, metodę dostarczania i z adresu do wysyłania wiadomości e-mail.  
  
 \<Konfiguracja >  
\<system.net>  
\<mailSettings>  
\<smtp>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<smtp  
  deliveryFormat="format"  
  deliveryMethod="method"  
  from="from address">
    <specifiedPickupDirectory>...</specifiedPickupDirectory>  
    <network>...</network>  
</smtp>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`deliveryFormat`|Określa format dostarczania wychodzących wiadomości e-mail. Dopuszczalne wartości to SevenBit i międzynarodowe.|  
|`deliveryMethod`|Określa metodę dostarczania wiadomości e-mail. Dopuszczalne wartości to sieć, PickupDirectoryFromIis i SpecifiedPickupDirectory.|  
|`from`|Określa adres początkowy dla wychodzących wiadomości e-mail.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`specifiedPickupDirectory`|Konfiguruje katalog lokalny dla serwera transportu protokołu SMTP (Simple Mail).|  
|`network`|Konfiguruje opcje sieciowe dla zewnętrznego serwera SMTP.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|**Element**|**Opis**|  
|-----------------|---------------------|  
|[\<mailSettings — >, Element (ustawienia sieci)](../../../../../docs/framework/configure-apps/file-schema/network/mailsettings-element-network-settings.md)|Konfiguruje opcje wysyłania poczty.|  
  
## <a name="example"></a>Przykład  
 Poniższy przykład określa odpowiednie parametry SMTP do wysyłania wiadomości e-mail przy użyciu poświadczeń domyślnych sieci.  
  
```xml  
<configuration>  
  <system.net>  
    <mailSettings>  
      <smtp deliveryMethod="Network" deliveryFormat="SevenBit"  from="ben@contoso.com">  
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
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpDeliveryFormat>
- <xref:System.Net.Mail.SmtpDeliveryMethod>
- [Schemat ustawień sieci](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
