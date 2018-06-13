---
title: '&lt;TransactionFlow&gt;'
ms.date: 03/30/2017
ms.assetid: 8c7b4c5b-ace3-4fe3-89ff-7b13c9aacd13
ms.openlocfilehash: c708098676e5634281e29c17639304a1a9cf5afe
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32748714"
---
# <a name="lttransactionflowgt"></a>&lt;TransactionFlow&gt;
Określa obsługę przepływu transakcji dla niestandardowego powiązania.  
  
 \<system.serviceModel>  
\<powiązania >  
\<customBinding>  
\<Powiązanie >  
\<transactionFlow >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<transactionFlow transactionProtocol="OleTransactions/WSAtomicTransactionOctober2004"/>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|Element TransactionProtocol|Określa protokół transakcji do użycia. Prawidłowe wartości są następujące:<br /><br /> -OleTransactions<br />-WSAtomicTransactionOctober2004<br /><br /> Wartość domyślna to OleTransactions.<br /><br /> Ten atrybut jest typu <xref:System.ServiceModel.TransactionProtocol>.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Powiązanie >](../../../../../docs/framework/misc/binding.md)|Definiuje wszystkie możliwości powiązania niestandardowego powiązania.|  
  
## <a name="remarks"></a>Uwagi  
 Ten element pozwala włączyć lub wyłączyć przychodzący transakcji w ustawienia powiązania punktu końcowego, a także określić format odpowiedni protokół dla przychodzących transakcji. Aby uzyskać więcej informacji na temat używania tego elementu konfiguracji, zobacz [Konfiguracja transakcji modelu ServiceModel](../../../../../docs/framework/wcf/feature-details/servicemodel-transaction-configuration.md) i [Włączanie przepływu transakcji](../../../../../docs/framework/wcf/feature-details/enabling-transaction-flow.md).  
  
> [!CAUTION]
>  Korzystając z `OleTransactions` protokołu przepływ transakcji punktu końcowego endpoint, limit czasu transakcji mogą zostać utracone, jeśli docelowy punkt końcowy podejmie próbę przepływu ponownie przy użyciu protokołów innych niż `OleTransactions`. Może to spowodować wszystkich węzłów na niższym poziomie po przeskoku OleTransactions limit później niż oczekiwano.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Configuration.TransactionFlowElement>  
 <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [Konfiguracja transakcji modelu ServiceModel](../../../../../docs/framework/wcf/feature-details/servicemodel-transaction-configuration.md)  
 [Włączanie przepływu transakcji](../../../../../docs/framework/wcf/feature-details/enabling-transaction-flow.md)  
 [Powiązania](../../../../../docs/framework/wcf/bindings.md)  
 [Rozszerzanie powiązań](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [Powiązania niestandardowe](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
