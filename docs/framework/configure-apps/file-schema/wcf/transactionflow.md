---
title: <transactionFlow>
ms.date: 03/30/2017
ms.assetid: 8c7b4c5b-ace3-4fe3-89ff-7b13c9aacd13
ms.openlocfilehash: f5bcd142fb2b032ea179bcbba68fee53b98d2d77
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "73736319"
---
# \<transactionFlow>
Określa obsługę przepływu transakcji dla niestandardowego powiązania.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transactionFlow>**  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<transactionFlow transactionProtocol="OleTransactions/WSAtomicTransactionOctober2004" />
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|Element TransactionProtocol|Określa protokół transakcji, który ma być używany. Prawidłowe wartości to:<br /><br /> -OleTransactions<br />- WSAtomicTransactionOctober2004<br /><br /> Wartość domyślna to OleTransactions.<br /><br /> Ten atrybut jest typu <xref:System.ServiceModel.TransactionProtocol> .|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|Definiuje wszystkie możliwości powiązań niestandardowego powiązania.|  
  
## <a name="remarks"></a>Uwagi  
 Ten element umożliwia włączenie lub wyłączenie przychodzącego przepływu transakcji w ustawieniach powiązań punktu końcowego, a także określenie żądanego formatu protokołu dla transakcji przychodzących. Aby uzyskać więcej informacji na temat korzystania z tego elementu konfiguracji, zobacz [Konfiguracja transakcji ServiceModel](../../../wcf/feature-details/servicemodel-transaction-configuration.md) i [Włączanie przepływu transakcji](../../../wcf/feature-details/enabling-transaction-flow.md).  
  
> [!CAUTION]
> W przypadku korzystania z `OleTransactions` protokołu do przepływu transakcji z punktu końcowego do punktu końcowego limit czasu transakcji może zostać utracony, jeśli docelowy punkt końcowy próbuje ponownie przepływać przy użyciu dowolnego protokołu innego niż `OleTransactions` . Może to spowodować, że wszystkie węzły wyższego poziomu po przejściu OleTransactions do limitu czasu później niż oczekiwano.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Configuration.TransactionFlowElement>
- <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Konfiguracja transakcji modelu ServiceModel](../../../wcf/feature-details/servicemodel-transaction-configuration.md)
- [Włączanie przepływu transakcji](../../../wcf/feature-details/enabling-transaction-flow.md)
- [Powiązania](../../../wcf/bindings.md)
- [Rozszerzanie powiązań](../../../wcf/extending/extending-bindings.md)
- [Powiązania niestandardowe](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
