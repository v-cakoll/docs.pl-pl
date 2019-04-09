---
title: <compositeDuplex>
ms.date: 03/30/2017
ms.assetid: 725004d1-ce88-4405-a220-78e89844f81f
ms.openlocfilehash: 1e5ecc2b937aa0cdb159a6cbd1222fe6d4af79fb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59159851"
---
# <a name="compositeduplex"></a>\<compositeDuplex>
Definiuje element powiązania, który jest używany, gdy klient musi ujawniać punkt końcowy usługi by wysłać wiadomości do klienta.  
  
 \<system.serviceModel>  
\<powiązania >  
\<customBinding>  
\<Powiązanie >  
\<compositeDuplex>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<compositeDuplex clientBaseAddress="URI" />
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|clientBaseAddress|Identyfikator URI, który ustawia adres kanału zwrotnego w tryb dupleks. Usługa używa tego adresu, skontaktuj się z pomocą i nawiąż połączenie z klientem.<br /><br /> Jeśli ten atrybut nie jest ustawiony, domyślnego adresu "`full qualified name+default port\TemporaryIndigoAddress\guid`" jest generowany. Wartość domyślna to `null`.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Powiązanie >](../../../../../docs/framework/misc/binding.md)|Definiuje wszystkie funkcje powiązania niestandardowego powiązania.|  
  
## <a name="remarks"></a>Uwagi  
 Ten element konfiguracji jest używany z transportów, które nie zezwalają na komunikację dwukierunkowego natywnie, na przykład HTTP. TCP, z drugiej strony, natywnie umożliwia dwukierunkowe komunikacji i nie wymaga użycia tego elementu powiązania usługi można wysłać wiadomości zwrotnie do klienta.  
  
 Klient musi ujawniać adres korespondencyjny upewnić się, skontaktuj się z pomocą i nawiązania połączenia. Ten adres klienta są dostarczane przez `clientBaseAddress` atrybutu. Należy pamiętać, że usługi Windows Communication Foundation (WCF) automatycznie generuje ClientBaseAddress Jeśli jeden nie jest jawnie ustawiona przez użytkownika.  
  
## <a name="example"></a>Przykład  
  
```xml  
<compositeDuplex clientBaseAddress="http://www.contoso.com" />
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Configuration.CompositeDuplexElement>
- <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Powiązania](../../../../../docs/framework/wcf/bindings.md)
- [Rozszerzanie powiązań](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [Powiązania niestandardowe](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [\<customBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
