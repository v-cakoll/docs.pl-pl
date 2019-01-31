---
title: <transactionFlow>
ms.date: 03/30/2017
ms.assetid: 8c7b4c5b-ace3-4fe3-89ff-7b13c9aacd13
ms.openlocfilehash: ef3d92e07aaf4d4ba9d90e381017db104f2cc8fe
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55276995"
---
# <a name="transactionflow"></a>\<transactionFlow >
Określa obsługę przepływu transakcji dla niestandardowego powiązania.  
  
 \<system.serviceModel>  
\<powiązania >  
\<customBinding>  
\<Powiązanie >  
\<transactionFlow >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<transactionFlow transactionProtocol="OleTransactions/WSAtomicTransactionOctober2004" />
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|transactionProtocol|Określa protokół transakcji do użycia. Prawidłowe wartości są następujące:<br /><br /> -OleTransactions<br />-WSAtomicTransactionOctober2004<br /><br /> Wartość domyślna to OleTransactions.<br /><br /> Ten atrybut jest typu <xref:System.ServiceModel.TransactionProtocol>.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Powiązanie >](../../../../../docs/framework/misc/binding.md)|Definiuje wszystkie funkcje powiązania niestandardowego powiązania.|  
  
## <a name="remarks"></a>Uwagi  
 Ten element pozwala włączyć lub wyłączyć przychodzącego przepływu transakcji w ustawieniach powiązania punktu końcowego, a także określić format odpowiedni protokół dla transakcji przychodzących. Aby uzyskać więcej informacji na temat korzystania z tego elementu konfiguracji, zobacz [Konfiguracja transakcji modelu ServiceModel](../../../../../docs/framework/wcf/feature-details/servicemodel-transaction-configuration.md) i [Włączanie przepływu transakcji](../../../../../docs/framework/wcf/feature-details/enabling-transaction-flow.md).  
  
> [!CAUTION]
>  Korzystając z `OleTransactions` protokołu przepływ transakcji z punktu końcowego do endpoint, limit czasu transakcji mogą zostać utracone, jeśli docelowy punkt końcowy podejmie próbę przepływ ponownie przy użyciu dowolnego protokołu innego niż `OleTransactions`. Może to spowodować wszystkich węzłów niskiego poziomu po przeskoku OleTransactions przekroczenie limitu czasu później niż oczekiwano.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.ServiceModel.Configuration.TransactionFlowElement>
- <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Konfiguracja transakcji modelu ServiceModel](../../../../../docs/framework/wcf/feature-details/servicemodel-transaction-configuration.md)
- [Włączanie przepływu transakcji](../../../../../docs/framework/wcf/feature-details/enabling-transaction-flow.md)
- [Powiązania](../../../../../docs/framework/wcf/bindings.md)
- [Rozszerzanie powiązań](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [Powiązania niestandardowe](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [\<customBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
