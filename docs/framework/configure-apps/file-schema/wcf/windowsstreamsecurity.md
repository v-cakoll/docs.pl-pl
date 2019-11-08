---
title: <windowsStreamSecurity>
ms.date: 03/30/2017
ms.assetid: 926bea29-90c7-4a26-9cf0-fb4aa44f6f70
ms.openlocfilehash: dab8505a9ddb348a6f7fe16ae9acb3a0119a8b06
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2019
ms.locfileid: "73735895"
---
# <a name="windowsstreamsecurity"></a>\<windowsStreamSecurity >
Określ ustawienia zabezpieczeń strumienia systemu Windows niestandardowego powiązania.  
  
[ **\<configuration >** ](../configuration-element.md) \
&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) \
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<powiązań**](bindings.md) >\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<[**CustomBinding**](custombinding.md) >\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<powiązania >** \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<windowsStreamSecurity >**  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<windowsStreamSecurity protectionLevel="None/Sign/EncryptAndSign" />
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|protectionLevel|Definiuje zabezpieczenia na poziomie wiadomości. Komunikaty podpisywania zmniejszają ryzyko naruszenia przez osobę trzecią komunikatu podczas jego przesyłania. Szyfrowanie zapewnia prywatność na poziomie danych podczas transportu. Prawidłowe wartości to:<br /><br /> -Brak: brak ochrony.<br />-Sign: komunikaty są podpisane.<br />-EncryptAndSign: komunikaty są podpisane i szyfrowane.<br /><br /> Wartość domyślna to EncryptAndSign.<br /><br /> Ten atrybut jest typu <xref:System.Net.Security.ProtectionLevel>.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[> powiązań \<](bindings.md)|Definiuje wszystkie możliwości powiązań niestandardowego powiązania.|  
  
## <a name="remarks"></a>Uwagi  
 Transporty korzystające z protokołu opartego na strumieniu, takiego jak TCP i nazwane potoki, obsługują uaktualnienia transportu na podstawie strumienia. W programie WCF dostępne są uaktualnienia zabezpieczeń. Konfiguracja tego zabezpieczenia transportu jest hermetyzowana przez ten element konfiguracji, a także [\<sslStreamSecurity >](sslstreamsecurity.md), który można skonfigurować i dodać do niestandardowego powiązania  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Configuration.WindowsStreamSecurityElement>
- <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>
- [Powiązania](../../../wcf/bindings.md)
- [Rozszerzanie powiązań](../../../wcf/extending/extending-bindings.md)
- [Powiązania niestandardowe](../../../wcf/extending/custom-bindings.md)
- [\<niestandardowebinding >](custombinding.md)
