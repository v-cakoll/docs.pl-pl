---
title: Atrybuty modelu ServiceModel i odwołanie modelu ServiceDescription
ms.date: 03/30/2017
ms.assetid: 4ab86b17-eab9-4846-a881-0099f9a7cc64
ms.openlocfilehash: 5e39a63d399edccc580b27ad4bfbc9ab05015ef9
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600351"
---
# <a name="servicemodel-attributes-and-servicedescription-reference"></a>Atrybuty modelu ServiceModel i odwołanie modelu ServiceDescription
*Drzewo opisów* jest hierarchią typów (począwszy od <xref:System.ServiceModel.Description.ServiceDescription?displayProperty=nameWithType> klasy), które razem opisują każdy aspekt usługi. Windows Communication Foundation (WCF) korzysta z drzewa opisowego do tworzenia prawidłowego środowiska uruchomieniowego usługi, publikowania Web Services Description Language (WSDL), języka definicji schematu XML (XSD) i potwierdzeń zasad (metadanych) dotyczących usługi, których klienci mogą używać do nawiązywania połączeń z usługą i korzystania z niej oraz do generowania różnych reprezentacji kodu i pliku konfiguracji dla wartości drzewa opisu.  
  
 W tym temacie opisano, jak właściwości powiązane z umową są uzyskiwane z kontraktu usługi i jak są one zaimplementowane i dodawane do drzewa opis. W niektórych przypadkach wartości atrybutów są konwertowane na właściwości zachowań, a zachowanie jest następnie wstawiane do drzewa opisu. Aby uzyskać więcej informacji na temat sposobu konwertowania wartości drzewa Description na metadane, zobacz temat [ServiceDescription and WSDL Reference](servicedescription-and-wsdl-reference.md).  
  
## <a name="mapping-operations-to-the-description-tree"></a>Mapowanie operacji do drzewa opisów  
 W aplikacjach WCF kontrakty usług są modelowane przez interfejsy (lub klasy), które używają atrybutów do oznaczania interfejsu lub klasy i jej metod jako grupy operacji. Gdy <xref:System.ServiceModel.ServiceHost> Klasa jest otwarta, wszelkie kontrakty i implementacje usług są uwzględniane i scalane z informacjami o konfiguracji w drzewie opisu.  
  
 Istnieją dwa typy modeli operacji: model *parametrów* i model *kontraktu komunikatów* . Model parametrów używa metod zarządzanych, które nie mają parametru lub typu wartości zwracanej oznaczonej przez <xref:System.ServiceModel.MessageContractAttribute?displayProperty=nameWithType> klasę. W tym modelu deweloperzy kontrolują serializację parametrów i zwracanych wartości, ale program WCF generuje wartości, które są używane do wypełniania drzewa opisowego dla usługi i jej kontraktu.  
  
 Powiązania określone w plikach konfiguracji są ładowane bezpośrednio do <xref:System.ServiceModel.Description.ServiceEndpoint.Binding%2A?displayProperty=nameWithType> właściwości.  
  
|Właściwość ServiceBehaviorAttribute|Wartość drzewa opisu|  
|---------------------------------------|-------------------------------------|  
|Nazwa|<xref:System.ServiceModel.Description.ServiceDescription.Name%2A>|  
|Przestrzeń nazw|<xref:System.ServiceModel.Description.ServiceDescription.Namespace%2A>|  
|ConfigurationName|<xref:System.ServiceModel.Description.ServiceDescription.ConfigurationName%2A>|  
|IgnoreExtensionDataObject|Ustawia <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior.IgnoreExtensionDataObject%2A> Właściwość dla wszystkich operacji.|  
|MaxItemsInObjectGraph|Ustawia <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior.MaxItemsInObjectGraph%2A> Właściwość dla wszystkich operacji.|  
  
|ServiceContractAttribute — Właściwość|Wartość drzewa opisu|  
|---------------------------------------|-------------------------------------|  
|Typach|<xref:System.ServiceModel.Description.ContractDescription.CallbackContractType%2A><xref:System.ServiceModel.Description.MessageDescription>dodano do wszystkich operacji <xref:System.ServiceModel.Description.OperationDescription.Messages%2A> .|  
|ConfigurationName|<xref:System.ServiceModel.Description.ContractDescription.ConfigurationName%2A>|  
|ProtectionLevel|<xref:System.ServiceModel.Description.ContractDescription.ProtectionLevel%2A>i prawdopodobnie podrzędnymi poziomami ochrony. Aby uzyskać więcej informacji na temat hierarchii poziomu ochrony, zobacz [Opis poziomu ochrony](../understanding-protection-level.md).|  
|SessionMode|<xref:System.ServiceModel.Description.ContractDescription.SessionMode%2A>|  
  
|ServiceKnownTypesAttribute wartość|Wartość drzewa opisu|  
|--------------------------------------|-------------------------------------|  
|MethodName|<xref:System.ServiceModel.Description.OperationDescription.KnownTypes%2A>|  
  
|Wartość atrybutu OperationContractAttribute|Wartość drzewa opisu|  
|--------------------------------------|-------------------------------------|  
|Akcja|<xref:System.ServiceModel.Description.MessageDescription.Action%2A>w przypadku wiadomości wyjściowej lub wiadomości wejściowej w zależności od kontraktu kontraktu/wywołania zwrotnego.|  
|AsyncPattern|W przypadku wartości true <xref:System.ServiceModel.Description.OperationDescription.BeginMethod%2A> i<xref:System.ServiceModel.Description.OperationDescription.EndMethod%2A>|  
|IsOneWay|Mapuje do pojedynczego elementu <xref:System.ServiceModel.Description.MessageDescription> w<xref:System.ServiceModel.Description.OperationDescription.Messages%2A>|  
|Operację IsInitiating|<xref:System.ServiceModel.Description.OperationDescription.IsInitiating%2A>|  
|IsTerminating|<xref:System.ServiceModel.Description.OperationDescription.IsTerminating%2A>|  
|Nazwa|<xref:System.ServiceModel.Description.OperationDescription.Name%2A>|  
|ProtectionLevel|<xref:System.ServiceModel.Description.OperationDescription.ProtectionLevel%2A>i prawdopodobnie podrzędnymi poziomami ochrony. Aby uzyskać więcej informacji na temat hierarchii poziomu ochrony, zobacz [Opis poziomu ochrony](../understanding-protection-level.md).|  
|ReplyAction|<xref:System.ServiceModel.Description.MessageDescription.Action%2A>w przypadku wiadomości wyjściowej lub wiadomości wejściowej w zależności od kontraktu kontraktu/wywołania zwrotnego.|  
  
|FaultContractAttribute wartość|Wartość drzewa opisu|  
|----------------------------------|-------------------------------------|  
|Akcja|<xref:System.ServiceModel.Description.FaultDescription.Action%2A>w zależności od kontraktu kontraktu/wywołania zwrotnego.|  
|DetailType|<xref:System.ServiceModel.Description.FaultDescription.DetailType%2A>|  
|Nazwa|<xref:System.ServiceModel.Description.FaultDescription.Name%2A>|  
|Przestrzeń nazw|<xref:System.ServiceModel.Description.FaultDescription.Namespace%2A>|  
|ProtectionLevel|<xref:System.ServiceModel.Description.FaultDescription.ProtectionLevel%2A>|  
  
|DataContractFormatAttribute wartość|Wartość drzewa opisu|  
|---------------------------------------|-------------------------------------|  
|Użycie|<xref:System.ServiceModel.DataContractFormatAttribute.Style%2A>Wartość jest ustawiona na <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> dla operacji.|  
  
|XmlSerializerFormatAttribute wartość|Wartość drzewa opisu|  
|----------------------------------------|-------------------------------------|  
|Styl|Ta <xref:System.ServiceModel.XmlSerializerFormatAttribute> Właściwość jest ustawiona na <xref:System.ServiceModel.Description.XmlSerializerOperationBehavior> dla operacji.|  
|Użycie|<xref:System.ServiceModel.XmlSerializerFormatAttribute>Jest ustawiony na <xref:System.ServiceModel.Description.XmlSerializerOperationBehavior> dla operacji.|  
  
|TransactionFlowAttribute wartość|Wartość drzewa opisu|  
|------------------------------------|-------------------------------------|  
|Parametru TransactionFlowOption|<xref:System.ServiceModel.TransactionFlowAttribute>Element jest dodawany jako zachowanie operacji do <xref:System.ServiceModel.Description.OperationDescription.Behaviors%2A> właściwości.|  
  
|Wartość MessageContractAttribute|Wartość drzewa opisu|  
|------------------------------------|-------------------------------------|  
|ProtectionLevel|<xref:System.ServiceModel.Description.MessageDescription.ProtectionLevel%2A>|  
|Nr otoki|<xref:System.ServiceModel.Description.MessageBodyDescription.WrapperName%2A>|  
|WrapperNamespace|<xref:System.ServiceModel.Description.MessageBodyDescription.WrapperNamespace%2A>|  
  
|Parametrze MessageHeaderAttribute wartość|Wartość drzewa opisu|  
|----------------------------------|-------------------------------------|  
|Zewnętrzny|<xref:System.ServiceModel.Description.MessageHeaderDescription.Actor%2A>dla odpowiedniego nagłówka w<xref:System.ServiceModel.Description.MessageDescription.Headers%2A>|  
|Atrybut|<xref:System.ServiceModel.Description.MessageHeaderDescription.MustUnderstand%2A>dla odpowiedniego nagłówka w<xref:System.ServiceModel.Description.MessageDescription.Headers%2A>|  
|Nazwa|<xref:System.ServiceModel.Description.MessagePartDescription.Name%2A>dla odpowiedniego nagłówka w<xref:System.ServiceModel.Description.MessageDescription.Headers%2A>|  
|Przestrzeń nazw|<xref:System.ServiceModel.Description.MessagePartDescription.Namespace%2A>dla odpowiedniego nagłówka w<xref:System.ServiceModel.Description.MessageDescription.Headers%2A>|  
|ProtectionLevel|<xref:System.ServiceModel.Description.MessagePartDescription.ProtectionLevel%2A>dla odpowiedniego nagłówka w<xref:System.ServiceModel.Description.MessageDescription.Headers%2A>|  
|Usługa Relay|<xref:System.ServiceModel.Description.MessageHeaderDescription.Relay%2A>dla odpowiedniego nagłówka w<xref:System.ServiceModel.Description.MessageDescription.Headers%2A>|  
  
|MessageBodyMemberAttribute wartość|Wartość drzewa opisu|  
|--------------------------------------|-------------------------------------|  
|Nazwa|<xref:System.ServiceModel.Description.MessagePartDescription.Name%2A>dla odpowiedniej części w<xref:System.ServiceModel.Description.MessageBodyDescription.Parts%2A>|  
|Przestrzeń nazw|<xref:System.ServiceModel.Description.MessagePartDescription.Namespace%2A>dla odpowiedniej części w<xref:System.ServiceModel.Description.MessageBodyDescription.Parts%2A>|  
|Zamówienie|<xref:System.ServiceModel.Description.MessagePartDescription.Index%2A>dla odpowiedniej części w<xref:System.ServiceModel.Description.MessageBodyDescription.Parts%2A>|  
|ProtectionLevel|<xref:System.ServiceModel.Description.MessagePartDescription.ProtectionLevel%2A>dla odpowiedniej części w<xref:System.ServiceModel.Description.MessageBodyDescription.Parts%2A>|  
  
|MessageHeaderArrayAttribute wartość|Wartość drzewa opisu|  
|---------------------------------------|-------------------------------------|  
|Zewnętrzny|<xref:System.ServiceModel.Description.MessageHeaderDescription.Actor%2A>|  
|Atrybut|<xref:System.ServiceModel.Description.MessageHeaderDescription.MustUnderstand%2A>|  
|Nazwa|<xref:System.ServiceModel.Description.MessagePartDescription.Name%2A>|  
|Przestrzeń nazw|<xref:System.ServiceModel.Description.MessagePartDescription.Namespace%2A>|  
|ProtectionLevel|<xref:System.ServiceModel.Description.MessagePartDescription.ProtectionLevel%2A>|  
|Usługa Relay|<xref:System.ServiceModel.Description.MessageHeaderDescription.Relay%2A>|  
  
|MessagePropertyAttribute wartość|Wartość drzewa opisu|  
|------------------------------------|-------------------------------------|  
|Nazwa|<xref:System.ServiceModel.Description.MessagePartDescription.Name%2A>|  
  
|MessageParameterAttribute wartość|Wartość drzewa opisu|  
|-------------------------------------|-------------------------------------|  
|Nazwa|<xref:System.ServiceModel.Description.MessagePartDescription.Name%2A>dla odpowiedniej części w<xref:System.ServiceModel.Description.MessageBodyDescription.Parts%2A>|  
  
 Aby uzyskać więcej informacji na temat sposobu konwertowania wartości drzewa Description na metadane, zobacz temat [ServiceDescription and WSDL Reference](servicedescription-and-wsdl-reference.md).  
  
## <a name="see-also"></a>Zobacz też

- [Odwołania do elementu ServiceDescription i kodu WSDL](servicedescription-and-wsdl-reference.md)
